---
title: "Usando OAuth para acessar Serviços de Email"
url: /pt/java/using-oauth-to-access-mail-services/
weight: 192
type: docs
---


O suporte ao OAuth 2.0 foi adicionado ao Aspose.Email e pode ser usado para acessar **SMTP**, **POP3**, **IMAP** e **EWS** servidores. Em geral, todos os servidores que suportam tokens portadores **OAuth 2.0** podem ser usados com o Aspose.Email, mas nossos clientes de email foram testados com servidores de email do Google e do Microsoft Office 365. O acesso ao servidor a partir do [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient), [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client), [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/ImapClient) e [EWSClient](https://reference.aspose.com/email/java/com.aspose.email/EWSClient) com OAuth pode ser implementado de 2 maneiras.

1. Fornecer o token de acesso diretamente no construtor do cliente de email. Nesse caso, o usuário deve entender que a vida útil dos tokens de acesso é limitada. Quando o token expira, o cliente de email não pode ser usado para acessar o servidor.
2. Fornecer uma implementação personalizada do provedor de tokens com base na interface [ITokenProvider](https://reference.aspose.com/email/java/com.aspose.email/itokenprovider) no construtor do cliente de email. Nesse caso, o cliente verifica o tempo de expiração do token e solicita um novo token de acesso ao [ITokenProvider](https://reference.aspose.com/email/java/com.aspose.email/itokenprovider) quando o anterior expira. Dessa forma, o cliente atualiza tokens periodicamente e pode trabalhar com o servidor por tempo ilimitado. Frequentemente, os serviços suportam uma maneira simples de atualizar tokens de acesso. Por exemplo, usando tokens de atualização em serviços do google ou o fluxo de autenticação ROPC na plataforma de identidade da Microsoft pode ser usado para implementar o provedor de tokens.

## **Configurar uma Conta no Servidor Apropriado**

Os seguintes artigos ajudam você a configurar contas para acessar os serviços de email.

- Para [Office 365](https://docs.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth)
- Para [Gmail](https://developers.google.com/gmail/imap/imap-smtp)

## **Acessar Serviços de Email com os Tokens de Acesso**

Os seguintes exemplos de código mostram como conectar-se aos serviços de email usando tokens de acesso.

```java
// Conectando ao servidor SMTP
try (SmtpClient client = new SmtpClient(
        "smtp.gmail.com",
        587,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.SSLExplicit)) {

}

// Conectando ao servidor IMAP
try (ImapClient client = new ImapClient(
        "imap.gmail.com",
        993,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.SSLImplicit)) {

}

// Conectando ao servidor POP3
try (Pop3Client client = new Pop3Client(
        "pop.gmail.com",
        995,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.Auto)) {

}
```

## **Acessar Serviços de Email com os Provedores de Token**

Os seguintes exemplos de código mostram como conectar-se aos serviços de email usando um provedor de token.

```java
ITokenProvider tokenProvider = TokenProvider.Google.getInstance(
        "ClientId",
        "ClientSecret",
        "RefreshToken");

// Conectando ao servidor SMTP
try (SmtpClient client = new SmtpClient(
        "smtp.gmail.com",
        587,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.SSLExplicit)) {

}

// Conectando ao servidor IMAP
try (ImapClient client = new ImapClient(
        "imap.gmail.com",
        993,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.SSLImplicit)) {

}

// Conectando ao servidor POP3
try (Pop3Client client = new Pop3Client(
        "pop.gmail.com",
        995,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.Auto)) {

}
```

## **Implementação de ITokenProvider Personalizado para Office 365**

Você pode usar a implementação do provedor de token abaixo para acessar os serviços de email do Office 365.

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.OutputStream;
import java.io.UnsupportedEncodingException;
import java.net.HttpURLConnection;
import java.net.URL;
import java.net.URLDecoder;
import java.net.URLEncoder;
import java.nio.charset.StandardCharsets;
import java.util.HashMap;
import java.util.Map;

/**
 * <p>
 * Provedor de token de credencial de proprietário de recurso Azure (ROPC)
 * https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
 * https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth
 * https://portal.azure.com
 * https://developer.microsoft.com/en-us/graph/graph-explorer/#
 * analisador de token https://jwt.io
 * </p>
 */
class AzureROPCTokenProvider implements ITokenProvider {

    private static final String GRANT_TYPE = "password";

    private final String clientId;
    private final String clientSecret;
    private final String userName;
    private final String password;
    private final String tenant;
    private final String scope;

    private OAuthToken token;

    public AzureROPCTokenProvider(String tenant, String clientId, String clientSecret,
                                  String userName, String password, String[] scopeAr) {
        this.tenant = tenant;
        this.clientId = clientId;
        this.clientSecret = clientSecret;
        this.userName = userName;
        this.password = password;
        this.scope = joinToStr(scopeAr, " ");
    }

    public synchronized OAuthToken getAccessToken(boolean ignoreExistingToken) {
        if (this.token != null && !this.token.getExpired() && !ignoreExistingToken)
            return this.token;
        token = null;

        Map<String, String> tokenArgs = geToken();

        java.util.Calendar c = java.util.Calendar.getInstance();
        c.add(java.util.Calendar.SECOND, Integer.parseInt(tokenArgs.get("expires_in")));
        token = new OAuthToken(tokenArgs.get("access_token"), TokenType.AccessToken, c.getTime());
        return token;
    }

    public final OAuthToken getAccessToken() {
        return getAccessToken(false);
    }

    public void dispose() {
    }

    private String getEncodedParameters() {
        return "client_id=" + urlEncode(clientId) + "&scope=" + urlEncode(scope) + "&username=" + urlEncode(userName)
                + "&password=" + urlEncode(password) + "&grant_type="
                + urlEncode(GRANT_TYPE);
    }

    private String getUri() {
        if (tenant == null || tenant.trim().isEmpty())
            return "https://login.microsoftonline.com/common/oauth2/v2.0/token";
        else
            return "https://login.microsoftonline.com/" + tenant + "/oauth2/v2.0/token";
    }

    private Map<String, String> geToken() {
        try {
            HttpURLConnection connection = (HttpURLConnection) new URL(getUri()).openConnection();
            connection.setRequestMethod("POST");

            byte[] requestData = getEncodedParameters().getBytes(StandardCharsets.UTF_8);

            connection.setUseCaches(false);
            connection.setDoInput(true);
            connection.setDoOutput(true);
            connection.setRequestProperty("Content-Type", "application/x-www-form-urlencoded");
            connection.setRequestProperty("Content-Length", "" + requestData.length);

            final OutputStream st = connection.getOutputStream();
            try {
                st.write(requestData, 0, requestData.length);
            } finally {
                st.flush();
                st.close();
            }

            connection.connect();

            if (connection.getResponseCode() >= HttpURLConnection.HTTP_BAD_REQUEST) {
                throw new IllegalAccessError("Operação falhou: " + connection.getResponseCode() + "/" +
                        connection.getResponseMessage() + "\r\nDetalhes:\r\n{2}"
                        + readInputStream(connection.getErrorStream()));
            }

            String responseText = readInputStream(connection.getInputStream());

            Map<String, String> result = new HashMap<>();
            String[] fromJsonToKeyValue = responseText.replace("{", "").replace("}", "")
                    .replace("\"", "").replace("\r", "")
                    .replace("\n", "").split(",");
            for (String keyValue : fromJsonToKeyValue) {
                String[] pair = keyValue.split(":");
                String name = pair[0].trim().toLowerCase();
                String value = urlDecode(pair[1].trim());
                result.put(name, value);
            }

            return result;
        } catch (IOException e) {
            throw new IllegalAccessError(e.getMessage());
        }
    }

    static String urlEncode(String value) {
        try {
            return URLEncoder.encode(value, StandardCharsets.UTF_8.toString());
        } catch (UnsupportedEncodingException e) {
            throw new IllegalAccessError(e.getMessage());
        }
    }

    static String urlDecode(String value) {
        try {
            return URLDecoder.decode(value, StandardCharsets.UTF_8.toString());
        } catch (UnsupportedEncodingException e) {
            throw new IllegalAccessError(e.getMessage());
        }
    }

    static String readInputStream(InputStream is) {
        if (is == null)
            return "";

        BufferedReader reader = new BufferedReader(new InputStreamReader(is));
        StringBuilder result = new StringBuilder();
        String line;
        try {
            while ((line = reader.readLine()) != null) {
                result.append(line);
            }
        } catch (IOException e) {
            // ignorar
        }
        return result.toString();
    }

    static String joinToStr(String[] arr, String sep) {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < arr.length; i++) {
            if (i > 0)
                sb.append(sep);
            sb.append(arr[i]);
        }
        return sb.toString();
    }
}
```

Os próximos exemplos de código mostram como conectar-se aos serviços do Office 365 usando o provedor de token personalizado.

```java
ITokenProvider tokenProvider = new AzureROPCTokenProvider(
        "Tenant",
        "ClientId",
        "ClientSecret",
        "EMail",
        "Password",
        scopes);

// Conectando ao servidor SMTP
try (SmtpClient client = new SmtpClient(
        "smtp.office365.com",
        587,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.SSLExplicit)) {

}

// Conectando ao servidor IMAP
try (ImapClient client = new ImapClient(
        "outlook.office365.com",
        993,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.SSLImplicit)) {

}

// Conectando ao servidor POP3
try (Pop3Client client = new Pop3Client(
        "outlook.office365.com",
        995,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.Auto)) {

}

// Conectando ao servidor EWS
final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
ICredentials credentials = new OAuthNetworkCredential(tokenProvider);
try (IEWSClient ewsClient = EWSClient.getEWSClient(mailboxUri, credentials)) {

}
```

## **Permissões para acessar o Office 365 via IMAP, POP3 ou SMTP**

Precisamos aplicar as permissões de API corretas e conceder o consentimento do administrador para acessar os serviços de email do Office 365:

![todo:image_alt_text](perm_conf.png)

Na tela de permissões de API / Adicionar um assistente de permissão, selecione Microsoft Graph e, em seguida, permissões delegadas para encontrar os seguintes escopos de permissão listados:

```
offline_access
IMAP.AccessAsUser.All
POP.AccessAsUser.All
SMTP.Send
```

Exemplo de provedor de token:

```java
ITokenProvider tokenProvider = new AzureROPCTokenProvider(OAuth.Tenant, OAuth.ClientId, OAuth.ClientSecret, User.EMail, User.Password,
        new String[] {
                "offline_access",
                "https://outlook.office.com/IMAP.AccessAsUser.All", // Escopo IMAP
                "https://outlook.office.com/POP.AccessAsUser.All",  // Escopo POP3
                "https://outlook.office.com/SMTP.Send"              // Escopo SMTP
        });
```