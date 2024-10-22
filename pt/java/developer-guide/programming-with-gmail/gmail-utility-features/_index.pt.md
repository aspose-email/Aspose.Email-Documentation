---
title: "Recursos de Utilitário do Gmail"
url: /pt/java/gmail-utility-features/
weight: 10
type: docs
---


## **Trabalhando com Consulta FreeBusy**
Aspose.Email fornece um mecanismo de consulta para verificar se uma consulta está devida ou não, conforme os critérios. A classe [FreebusyQuery](https://reference.aspose.com/email/java/com.aspose.email/FreebusyQuery) é fornecida para esse propósito, permitindo preparar uma consulta para um calendário específico.
### **Consultando um calendário**
Este exemplo de código demonstra a funcionalidade de consulta de um calendário. As seguintes tarefas são realizadas neste exemplo:

1. Criar e inserir um calendário
1. Criar um compromisso
1. Inserir compromisso
1. Preparar uma [FreebusyQuery](https://reference.aspose.com/email/java/com.aspose.email/FreebusyQuery)
1. Obter a [FreebusyResponse](https://reference.aspose.com/email/java/com.aspose.email/FreebusyResponse)

```java
// Use as classes OAuthUser e GoogleOAuthHelper abaixo para receber um token de acesso
IGmailClient client = GmailClient.getInstance(accessToken, "user@domain.com");
try {
    Calendar newCalendar = new Calendar("summary", null, null, "Europe/Kiev");

    // Inserir calendário e retornar o id do calendário recém-inserido e buscar o mesmo calendário usando o id do calendário
    String id = client.createCalendar(newCalendar);
    Calendar fetchedCalendar = client.fetchCalendar(id);
    String calendarId = fetchedCalendar.getId();
    try {
        // Obter lista de compromissos no calendário recém-inserido. Deve ser zero
        Appointment[] appointments = client.listAppointments(calendarId);

        // Criar um novo compromisso e calcular o início e fim do compromisso
        java.util.Calendar c = java.util.Calendar.getInstance();
        Date startDate = c.getTime();
        c.add(java.util.Calendar.HOUR_OF_DAY, 1);
        Date endDate = c.getTime();

        // Criar lista de participantes para o compromisso
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.add("user1@domain.com");
        attendees.add("user2@domain.com");

        // Criar compromisso
        Appointment app1 = new Appointment("Location", startDate, endDate, MailAddress.to_MailAddress("user2@domain.com"), attendees);
        app1.setSummary("Summary");
        app1.setDescription("Description");
        app1.setStartTimeZone("Europe/Kiev");
        app1.setEndTimeZone("Europe/Kiev");

        // Inserir o compromisso recém-criado e obter o mesmo em caso de inserção bem-sucedida
        Appointment newAppointment = client.createAppointment(calendarId, app1);

        // Criar consulta Freebusy definindo tempo mínimo/máximo e fuso horário
        FreebusyQuery query = new FreebusyQuery();
        c = java.util.Calendar.getInstance();
        c.add(java.util.Calendar.DATE, -1);
        query.setTimeMin(c.getTime());
        c.add(java.util.Calendar.DATE, 2);
        query.setTimeMax(c.getTime());
        query.setTimeZone("Europe/Kiev");

        // Definir item de calendário para buscar e obter a resposta da consulta contendo
        query.getItems().add(calendarId);
        FreebusyResponse resp = client.getFreebusyInfo(query);

        client.deleteAppointment(calendarId, newAppointment.getUniqueId());
    } finally {
        client.deleteCalendar(calendarId);
    }
} finally {
    client.dispose();
}
```
## **Criando projeto no Google Developer Console**
Um projeto deve ser criado no Google Developer Console para um usuário com uma conta Gmail. Na página API & auth -> Credentials do projeto Google, informações como Client ID e Client Secret devem ser anotadas. Essa informação, juntamente com o nome de usuário e a senha da conta do Gmail, será necessária para executar o código, por exemplo, google calendar, listas de controle de acesso, compromissos, contatos, configurações, etc. nesta seção.
### **Passos para criar um projeto no Google Developer Console**
A seguir, um tutorial passo a passo para criar um projeto no Google Developer Console.

1. Acesse o link <https://console.cloud.google.com> e faça login usando suas credenciais do Gmail

2. Selecione a caixa de seleção "Li e concordo com todos os Termos de Serviço para os produtos da Google Cloud Platform." e pressione o botão **NOVO PROJETO**

![todo:image_alt_text](gmail-utility-features_1.png)

3. **Criar** e **Selecionar** novo projeto

![todo:image_alt_text](gmail-utility-features_2.png)

4. Selecione **Biblioteca** e ative a API de Contatos e Calendário

![todo:image_alt_text](gmail-utility-features_6.png)

5. Abra a **tela de consentimento do OAuth**

![todo:image_alt_text](gmail-utility-features_3.png)

6. Selecione a caixa de seleção **Externo** e pressione o botão **CRIAR**

![todo:image_alt_text](gmail-utility-features_4.png)

7. Edite o registro do aplicativo e pressione o botão **SALVAR E CONTINUAR**

![todo:image_alt_text](gmail-utility-features_5.png)

8. Adicione escopos e pressione o botão **ATUALIZAR**

![todo:image_alt_text](gmail-utility-features_7.png)

9. Crie credenciais OAuth

![todo:image_alt_text](gmail-utility-features_8.png)

10. Aqui estão o Client ID e o Client Secret que serão usados nos exemplos de código nesta seção.

![todo:image_alt_text](gmail-utility-features_9.png)

## **Classes Auxiliares**
As seguintes classes auxiliares são necessárias para executar os exemplos de código nesta seção. Essas classes `GoogleOAuthHelper` e `OAuthUser` são apenas para simplificação da demonstração. Os métodos nessas classes usam uma estrutura não pública de páginas da web que pode mudar a qualquer momento.
### **Classe GoogleOAuthHelper**
O seguinte trecho de código mostra como implementar a classe `GoogleOAuthHelper`.

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
import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;
import java.util.HashMap;
import java.util.Map;
import java.util.UUID;

import javax.xml.bind.DatatypeConverter;

/**
 * <p>
 * Console para desenvolvedores https://console.developers.google.com/projectselector/apis/credentials?pli=1 
 * Documentação https://developers.google.com/identity/protocols/OAuth2InstalledApp
 * </p>
 */
class GoogleOAuthHelper {
    public static final String AUTHORIZATION_URL = "https://accounts.google.com/o/oauth2/v2/auth";
    public static final String TOKEN_REQUEST_URL = "https://oauth2.googleapis.com/token";
    public static final String REDIRECT_URI = "urn:ietf:wg:oauth:2.0:oob";
    public static final String REDIRECT_TYPE = "code";
    public static final String SCOPE = "https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcalendar" // Calendário
            + "+https%3A%2F%2Fwww.google.com%2Fm8%2Ffeeds%2F" // Contatos
            + "+https%3A%2F%2Fmail.google.com%2F"; // IMAP & SMTP

    static class OAuthUser {
        String email;
        String clientId;
        String clientSecret;
        String refreshToken;
    }

    static String createCodeChalange() {
        String verifierStr = UUID.randomUUID().toString() + "-" + UUID.randomUUID().toString();
        System.out.println("Code Verifier: " + verifierStr);

        MessageDigest digest;
        try {
            digest = MessageDigest.getInstance("SHA-256");
        } catch (NoSuchAlgorithmException e) {
            throw new IllegalAccessError(e.getMessage());
        }
        byte[] hash = digest.digest(verifierStr.getBytes(StandardCharsets.UTF_8));
        String base64Hash = DatatypeConverter.printBase64Binary(hash);

        base64Hash = base64Hash.split("=")[0];
        base64Hash = base64Hash.replace('+', '-').replace('/', '_');
        return base64Hash;
    }

    static String getAuthorizationCodeUrl(OAuthUser acc) {
        return getAuthorizationCodeUrl(acc, SCOPE, REDIRECT_URI, REDIRECT_TYPE);
    }

    static String getAuthorizationCodeUrl(OAuthUser acc, String scope, String redirectUri, String responseType) {
        System.out.println("---------------------------------------------------------");
        System.out.println("------------- OAuth 2.0 AuthorizationCodeUrl -------------");
        System.out.println("---------------------------------------------------------");
        System.out.println("Login: " + acc.email);
        String codeChallenge = createCodeChalange();

        String state = urlEncode(UUID.randomUUID().toString());
        String approveUrl = AUTHORIZATION_URL + "?client_id=" + acc.clientId + "&redirect_uri=" + redirectUri + "&response_type=" + responseType + "&scope=" + scope
                + "&code_challenge=" + codeChallenge + "&code_challenge_method=S256&state=" + state;

        System.out.println("Approve Url: " + approveUrl);
        return approveUrl;
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

    static String getAccessTokenByAuthCode(String authorizationCode, String codeVerifier, OAuthUser user) {
        String encodedParameters = "client_id=" + urlEncode(user.clientId) + "&client_secret=" + urlEncode(user.clientSecret) + "&code=" + urlEncode(authorizationCode)
                + "&code_verifier=" + codeVerifier + "&redirect_uri=" + urlEncode(REDIRECT_URI) + "&grant_type=authorization_code";
        System.out.println("---------------------------------------------------------");
        System.out.println("------------- OAuth 2.0 AccessTokenByAuthCode -------------");
        System.out.println("---------------------------------------------------------");
        System.out.println("Authorization code: " + authorizationCode);

        String result = "";
        Map<String, String> token = geToken(encodedParameters);
        for (String key : token.keySet()) {
            System.out.println(key + ": " + token.get(key));
            if (key.equals("refresh_token")) {
                result = token.get(key);
            }
        }

        System.out.println("---------------------------------------------------------");

        return result;
    }

    static String getAccessTokenByRefreshToken(OAuthUser user) {
        String encodedParameters = "client_id=" + urlEncode(user.clientId) + "&client_secret=" + urlEncode(user.clientSecret) + "&refresh_token=" + urlEncode(user.refreshToken)
                + "&grant_type=refresh_token";
        System.out.println("---------------------------------------------------------");
        System.out.println("----------- OAuth 2.0 AccessTokenByRefreshToken -----------");
        System.out.println("---------------------------------------------------------");
        System.out.println("Login: " + user.email);

        String result = "";
        Map<String, String> token = geToken(encodedParameters);
        for (String key : token.keySet()) {
            System.out.println(key + ": " + token.get(key));
            if (key.equals("access_token")) {
                result = token.get(key);
            }
        }

        System.out.println("---------------------------------------------------------");

        return result;
    }

    static Map<String, String> geToken(String encodedParameters) {
        try {
            HttpURLConnection connection = (HttpURLConnection) new URL(TOKEN_REQUEST_URL).openConnection();
            connection.setRequestMethod("POST");

            byte[] requestData = encodedParameters.getBytes(StandardCharsets.UTF_8);

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
                throw new IllegalAccessError("Operação falhou: " + connection.getResponseCode() + "/" + connection.getResponseMessage() + "\r\nDetalhes:\r\n{2}"
                        + readInputStream(connection.getErrorStream()));
            }

            String responseText = readInputStream(connection.getInputStream());

            Map<String, String> result = new HashMap<String, String>();
            System.out.println(responseText);
            String[] strs = responseText.replace("{", "").replace("}", "").replace("\"", "").replace("\r", "").replace("\n", "").split(",");
            for (String sPair : strs) {
                String[] pair = sPair.split(":");
                String name = pair[0].trim().toLowerCase();
                String value = urlDecode(pair[1].trim());
                result.put(name, value);
            }

            return result;
        } catch (IOException e) {
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
}
```

**Google OAuth Helper** deve ser utilizado da seguinte forma:
1. Uma URL de código de autorização deve ser gerada primeiro.
1. Abra a URL em um navegador e complete todas as operações. Como resultado, você receberá um código de autorização.
1. Use o código de autorização para receber um token de atualização.
1. Quando o token de atualização existir, você poderá usá-lo para recuperar tokens de acesso.

```java
static class OAuthUser {
    String email;
    String clientId;
    String clientSecret;
    String refreshToken;
}

static void getRefreshToken() {
    Scanner inputReader = new Scanner(System.in);
    OAuthUser user = new OAuthUser();

    // Defina clientId, clientSecret e email
    System.out.println("Defina clientId: ");
    user.clientId = inputReader.nextLine();
    System.out.println("Defina clientSecret: ");
    user.clientSecret = inputReader.nextLine();
    System.out.println("Defina email: ");
    user.email = inputReader.nextLine();

    // Gere AuthorizationCodeUrl
    String authorizationCodeUrl = GoogleOAuthHelper.getAuthorizationCodeUrl(user);

    System.out.println("Você deve recuperar AuthorizationCode manualmente com a AuthorizationCodeUrl gerada");
    System.out.println("Defina authorizationCode: ");
    String authorizationCode = inputReader.nextLine();
    System.out.println("Copie o Code Verifier da saída do passo anterior");
    System.out.println("Defina codeVerifier: ");
    String codeVerifier = inputReader.nextLine();

    // Obtenha "Token de Atualização"
    String refreshToken = GoogleOAuthHelper.getAccessTokenByAuthCode(authorizationCode, codeVerifier, user);
    user.refreshToken = refreshToken;

    // Obtenha "Token de Acesso"
    String accessToken = GoogleOAuthHelper.getAccessTokenByRefreshToken(user);
    
    // Use "Token de Acesso" na API
    IGmailClient client = GmailClient.getInstance(accessToken, user.email);
}
```