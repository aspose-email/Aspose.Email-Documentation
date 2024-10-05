---
title: "Использование OAuth для доступа к почтовым службам"
url: /ru/java/using-oauth-to-access-mail-services/
weight: 192
type: docs
---


Поддержка OAuth 2.0 была добавлена в Aspose.Email и может быть использована для доступа к **SMTP**, **POP3**, **IMAP** и **EWS** серверам. В общем, все серверы, поддерживающие **OAuth 2.0** токены, могут быть использованы с Aspose.Email, но наши почтовые клиенты были протестированы с серверами Gmail и Microsoft Office 365. Доступ к серверу из [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient), [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/Pop3Client), [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/ImapClient) и [EWSClient](https://reference.aspose.com/email/java/com.aspose.email/EWSClient) с помощью OAuth может быть реализован двумя способами.

1. Предоставить токен доступа непосредственно в конструкторе почтового клиента. В этом случае пользователю необходимо понимать, что срок действия токенов доступа ограничен. Когда токен истекает, почтовый клиент не может использоваться для доступа к серверу.
2. Предоставить свою реализацию провайдера токенов на основе интерфейса [ITokenProvider](https://reference.aspose.com/email/java/com.aspose.email/itokenprovider) в конструкторе почтового клиента. В этом случае клиент проверяет время истечения токена и запрашивает у [ITokenProvider](https://reference.aspose.com/email/java/com.aspose.email/itokenprovider) новый токен доступа, когда старый истекает. Таким образом, клиент периодически обновляет токены и может работать с сервером неограниченное время. Часто службы поддерживают простой способ обновления токенов доступа. Например, можно использовать refresh токены в службах Google или поток аутентификации ROPC на платформе идентификации Microsoft для реализации провайдера токенов.

## **Настройка учетной записи на соответствующем сервере**

Следующие статьи помогут вам настроить учетные записи для доступа к почтовым службам.

- Для [Office 365](https://docs.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth)
- Для [Gmail](https://developers.google.com/gmail/imap/imap-smtp)

## **Доступ к почтовым службам с помощью токенов доступа**

Следующие примеры кода покажут вам, как подключиться к почтовым службам, используя токены доступа.

```java
// Подключение к SMTP серверу
try (SmtpClient client = new SmtpClient(
        "smtp.gmail.com",
        587,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.SSLExplicit)) {

}

// Подключение к IMAP серверу
try (ImapClient client = new ImapClient(
        "imap.gmail.com",
        993,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.SSLImplicit)) {

}

// Подключение к POP3 серверу
try (Pop3Client client = new Pop3Client(
        "pop.gmail.com",
        995,
        "user1@gmail.com",
        "accessToken",
        true,
        SecurityOptions.Auto)) {

}
```

## **Доступ к почтовым службам с помощью провайдеров токенов**

Следующие примеры кода покажут вам, как подключиться к почтовым службам, используя провайдера токенов.

```java
ITokenProvider tokenProvider = TokenProvider.Google.getInstance(
        "ClientId",
        "ClientSecret",
        "RefreshToken");

// Подключение к SMTP серверу
try (SmtpClient client = new SmtpClient(
        "smtp.gmail.com",
        587,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.SSLExplicit)) {

}

// Подключение к IMAP серверу
try (ImapClient client = new ImapClient(
        "imap.gmail.com",
        993,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.SSLImplicit)) {

}

// Подключение к POP3 серверу
try (Pop3Client client = new Pop3Client(
        "pop.gmail.com",
        995,
        "user1@gmail.com",
        tokenProvider,
        SecurityOptions.Auto)) {

}
```

## **Реализация пользовательского ITokenProvider для Office 365**

Вы можете использовать реализацию провайдера токена ниже для доступа к почтовым службам Office 365.

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
 * Провайдер токенов с учетными данными владельца ресурса Azure (ROPC)
 * https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
 * https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth
 * https://portal.azure.com
 * https://developer.microsoft.com/en-us/graph/graph-explorer/# 
 * парсер токенов https://jwt.io
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
                throw new IllegalAccessError("Операция не удалась: " + connection.getResponseCode() + "/" +
                        connection.getResponseMessage() + "\r\nДетали:\r\n{2}"
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
            // игнорировать
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

Следующие примеры кода покажут вам, как подключиться к службам Office 365 с использованием пользовательского провайдера токенов. 

```java
ITokenProvider tokenProvider = new AzureROPCTokenProvider(
        "Tenant",
        "ClientId",
        "ClientSecret",
        "EMail",
        "Password",
        scopes);

// Подключение к SMTP серверу
try (SmtpClient client = new SmtpClient(
        "smtp.office365.com",
        587,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.SSLExplicit)) {

}

// Подключение к IMAP серверу
try (ImapClient client = new ImapClient(
        "outlook.office365.com",
        993,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.SSLImplicit)) {

}

// Подключение к POP3 серверу
try (Pop3Client client = new Pop3Client(
        "outlook.office365.com",
        995,
        "Test1@test.onmicrosoft.com",
        tokenProvider,
        SecurityOptions.Auto)) {

}

// Подключение к EWS серверу
final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
ICredentials credentials = new OAuthNetworkCredential(tokenProvider);
try (IEWSClient ewsClient = EWSClient.getEWSClient(mailboxUri, credentials)) {

}
```

## **Разрешения для доступа к Office 365 через IMAP, POP3 или SMTP**

Мы должны применить правильные разрешения API и предоставить согласие администратора для доступа к почтовым службам Office 365:

![todo:image_alt_text](perm_conf.png)

В мастере разрешений API / Добавить разрешение выберите Microsoft Graph, а затем Делегированные разрешения, чтобы найти следующие разрешения:

```
offline_access
IMAP.AccessAsUser.All
POP.AccessAsUser.All
SMTP.Send
```

Пример провайдера токенов:

```java
ITokenProvider tokenProvider = new AzureROPCTokenProvider(OAuth.Tenant, OAuth.ClientId, OAuth.ClientSecret, User.EMail, User.Password,
        new String[] {
                "offline_access",
                "https://outlook.office.com/IMAP.AccessAsUser.All", // IMAP scope
                "https://outlook.office.com/POP.AccessAsUser.All",  // POP3 scope
                "https://outlook.office.com/SMTP.Send"              // SMTP scope
        });
```