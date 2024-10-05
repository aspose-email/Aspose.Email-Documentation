---
title: "Утилиты Microsoft Graph"
url: /ru/java/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Создание проекта в Центре администрирования Azure Active Directory**

Проект необходимо создать в Центре администрирования Azure Active Directory для пользователя с учетной записью MS Office.
### **Шаги для создания проекта в Центре администрирования Azure Active Directory**

Ниже приведено пошаговое руководство по созданию проекта в Центре администрирования Azure Active Directory.

#### 1. Перейдите в Azure Active Directory и войдите, используя свои учетные данные MS Office.

**Ссылка на Azure Active Directory** - <https://aad.portal.azure.com/>

#### 2. Создайте приложение Azure AD в своем арендаторе.

В левой панели нажмите на ярлык **Azure Active Directory**. Это откроет панель Azure Active Directory. На этом экране должно быть видно ярлык **Регистрация приложений**. Это начальная точка для регистрации приложения Azure AD. Эта панель позволит вам создать новое приложение для Azure AD.

Нажмите на кнопку **Новая регистрация**, чтобы создать новое приложение.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Теперь вы увидите панель новой регистрации приложения.

- **Имя** Это будет имя вашего приложения.
- **Типы поддерживаемых аккаунтов** Этот раздел ограничит доступ.

Нажмите кнопку **Зарегистрировать**.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Вы должны увидеть панель недавно зарегистрированных приложений.

- **Идентификатор приложения (клиента)** Идентификатор вашего приложения.
- **Идентификатор каталога (арендатора)** Идентификатор арендатора Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Разрешение доступа для Microsoft Graph API.

Нажмите на ярлык **Разрешения API**.

Azure уже предоставил вам делегированные разрешения **User.Read** для вашего приложения. Это разрешение позволит нам читать информацию о пользователе для вошедшего пользователя. Это разрешения Microsoft Graph API, в свою очередь, мы можем называть их **Области**.

Полный список областей для Microsoft Graph API - <https://docs.microsoft.com/en-us/graph/permissions-reference>.

Нажмите на кнопку **+ Добавить разрешение** и выберите **Microsoft Graph**.

Нажмите на **Делегированные разрешения**. Теперь вы увидите список разрешений, доступных для Microsoft Graph API.

Выберите необходимые разрешения и нажмите кнопку **Добавить разрешения**.

Нажмите кнопку **Предоставить согласие администратора**.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Разрешите публичные клиентские потоки.

Указывает, является ли приложение публичным клиентом. Подходит для приложений, использующих потоки предоставления токенов, которые не используют перенаправление URI.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Создайте ключ для приложения

![todo:image_alt_text](microsoft-graph-utility-features_5.png)

## **Вспомогательные классы**

Следующие вспомогательные классы необходимы для выполнения кода в этом разделе. Эти классы предназначены только для упрощения демонстрации.

### **Класс AzureROPCTokenProvider**

Экземпляр класса [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) обрабатывает построение запросов, их отправку в Microsoft Graph API и обработку ответов. Чтобы создать новый экземпляр этого класса, вам необходимо предоставить экземпляр [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), который может аутентифицировать запросы к Microsoft Graph.

~~~Java
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
 * Провайдер токенов с использованием учетных данных владельца ресурса Azure (ROPC)
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
                throw new IllegalAccessError("Операция завершилась ошибкой: " + connection.getResponseCode() + "/" +
                        connection.getResponseMessage() + "\r\nПодробности:\r\n{2}"
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
~~~