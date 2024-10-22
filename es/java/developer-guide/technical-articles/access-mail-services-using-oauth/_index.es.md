---
title: "Acceso a servicios de correo utilizando OAuth"
url: /es/java/access-mail-services-using-oauth/
weight: 190
type: docs
---


El soporte para OAuth 2.0 se ha añadido a Aspose.Email y se puede utilizar para acceder a los servidores **SMTP**, **POP3**, **IMAP** y **EWS**.
En general, todos los servidores que admiten tokens portadores de **OAuth 2.0** se pueden utilizar con Aspose.Email, pero nuestros clientes de correo electrónico han sido probados con servidores de correo de Google y servidores de Microsoft Office 365.
El acceso al servidor desde el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient), [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client), [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/ImapClient) y [EWSClient](https://reference.aspose.com/email/java/com.aspose.email/EWSClient) con OAuth puede implementarse de 2 maneras.

1. Proporcionar el token de acceso directamente en el constructor del cliente de correo electrónico. En este caso, el usuario debe entender que la vida útil de los tokens de acceso es limitada. Cuando el token ha expirado, el cliente de correo electrónico no puede utilizarse para acceder al servidor.
2. Proporcionar una implementación personalizada del proveedor de tokens basada en la interfaz [ITokenProvider](https://reference.aspose.com/email/java/com.aspose.email/itokenprovider) en el constructor del cliente de correo electrónico. En este caso, el cliente verifica el tiempo de expiración del token y solicita a [ITokenProvider](https://reference.aspose.com/email/java/com.aspose.email/itokenprovider) un nuevo token de acceso cuando el anterior ha expirado. De esta manera, el cliente actualiza los tokens periódicamente y puede trabajar con el servidor de forma ilimitada. A menudo, los servicios admiten una forma simple de actualizar los tokens de acceso. Por ejemplo, se pueden utilizar tokens de actualización en los servicios de Google o el flujo de autenticación ROPC en la plataforma de identidad de Microsoft para implementar el proveedor de tokens.

## **Configurar una cuenta en el servidor adecuado**

Los siguientes artículos te ayudarán a configurar cuentas para acceder a los servicios de correo.

- Para [Office 365](https://docs.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth)
- Para [Gmail](https://developers.google.com/gmail/imap/imap-smtp)

## **Acceso a servicios de correo con los tokens de acceso**

Los siguientes ejemplos de código te muestran cómo conectarte a servicios de correo utilizando tokens de acceso.

```java
// Conectando al servidor SMTP
try (SmtpClient client = new SmtpClient(
        "smtp.gmail.com",
        587,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.SSLExplicit)) {

}

// Conectando al servidor IMAP
try (ImapClient client = new ImapClient(
        "imap.gmail.com",
        993,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.SSLImplicit)) {

}

// Conectando al servidor POP3
try (Pop3Client client = new Pop3Client(
        "pop.gmail.com",
        995,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.Auto)) {

}
```

## **Acceso a servicios de correo con los proveedores de tokens**

Los siguientes ejemplos de código te muestran cómo conectarte a servicios de correo utilizando un proveedor de tokens.

```java
ITokenProvider tokenProvider = TokenProvider.Google.getInstance(
        "ClientId",
        "ClientSecret",
        "RefreshToken");

// Conectando al servidor SMTP
try (SmtpClient client = new SmtpClient(
        "smtp.gmail.com",
        587,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.SSLExplicit)) {

}

// Conectando al servidor IMAP
try (ImapClient client = new ImapClient(
        "imap.gmail.com",
        993,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.SSLImplicit)) {

}

// Conectando al servidor POP3
try (Pop3Client client = new Pop3Client(
        "pop.gmail.com",
        995,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.Auto)) {

}
```

## **Implementación de un ITokenProvider personalizado para Office 365**

Puedes utilizar la implementación del proveedor de tokens a continuación para acceder a los servicios de correo de Office 365.

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
 * Proveedor de tokens de credencial de propietario de recurso de Azure (ROPC)
 * https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
 * https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth
 * https://portal.azure.com
 * https://developer.microsoft.com/en-us/graph/graph-explorer/#
 * analizador de tokens https://jwt.io
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
                throw new IllegalAccessError("Operación fallida: " + connection.getResponseCode() + "/" +
                        connection.getResponseMessage() + "\r\nDetalles:\r\n{2}"
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

Los siguientes ejemplos de código te muestran cómo conectarte a los servicios de Office 365 utilizando el proveedor de tokens personalizado.

```java
ITokenProvider tokenProvider = new AzureROPCTokenProvider(
        "Tenant",
        "ClientId",
        "ClientSecret",
        "EMail",
        "Password",
        scopes);

// Conectando al servidor SMTP
try (SmtpClient client = new SmtpClient(
        "smtp.office365.com",
        587,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.SSLExplicit)) {

}

// Conectando al servidor IMAP
try (ImapClient client = new ImapClient(
        "outlook.office365.com",
        993,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.SSLImplicit)) {

}

// Conectando al servidor POP3
try (Pop3Client client = new Pop3Client(
        "outlook.office365.com",
        995,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.Auto)) {

}

// Conectando al servidor EWS
final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
ICredentials credentials = new OAuthNetworkCredential(tokenProvider);
try (IEWSClient ewsClient = EWSClient.getEWSClient(mailboxUri, credentials)) {

}
```