---
title: "Функции утилиты График Майкрософт"
url: /ru/java/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Создание проекта в Центре администрирования Активная директория Azure**

Проект должен быть создан в Центре администрирования Активная директория Azure для пользователя, имеющего учетную запись MS Office.
### **Шаги по созданию проекта в Центре администрирования Активная директория Azure**

Ниже приводится пошаговое руководство по созданию проекта в Центре администрирования Активная директория Azure.

#### 1. Перейдите в Активная директория Azure и войдите в систему, используя свои учетные данные MS Office.

**Активная директория Azure** Ссылка - <https://aad.portal.azure.com/>

#### 2. Создайте приложение Azure AD в своем арендаторе.

На левой боковой панели нажмите на метку **Активная директория Azure**. Это откроет блейд для Активная директория Azure. На этом экране должна появиться надпись **Регистрация приложений**. Это отправная точка регистрации приложения Azure AD. Этот блейд позволит вам создать новое приложение для Azure AD.

Нажмите на кнопку **Новая регистрация** для создания нового приложения.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Теперь вы увидите новое лезвие для регистрации приложений.

- **Name** Это будет название вашего приложения.
- **Поддерживаемые типы счетов** Этот раздел ограничит доступ.

Click **Register** button.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Вы должны увидеть лезвие недавно зарегистрированных приложений.

- **Идентификатор приложения (клиента)** Идентификатор вашего приложения.
- **Идентификатор каталога (арендатора)** Идентификатор клиента Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Предоставление разрешений для График Майкрософт API.

Нажмите на **Разрешения API** label.

Azure уже предоставила вам **User.Read** делегированные разрешения для вашего приложения. Это разрешение позволит нам читать информацию о вошедшем в систему пользователе. Это разрешения График Майкрософт API, с другой стороны, мы можем назвать их так **Scopes**.

Полный список областей применения График Майкрософт API - <https://docs.microsoft.com/en-us/graph/permissions-reference>.

Нажмите на **+ Добавить разрешение** кнопка и выберите **График Майкрософт**.

Нажмите на **Делегированные разрешения**. Теперь вы видите список разрешений, доступных для График Майкрософт API.

Выберите необходимые разрешения, нажмите **Добавить разрешения** button.

Click **Предоставьте согласие администратора** button.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Разрешите потоки государственных клиентов.

Указывает, является ли приложение публичным клиентом. Подходит для приложений, использующих потоки предоставления токенов и не использующих URI перенаправления.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Создайте ключ для приложения

![todo:image_alt_text](microsoft-graph-utility-features_5.png)

## **Вспомогательные классы**

Для запуска кодов, описанных в этом разделе, необходимы следующие вспомогательные классы. Эти классы предназначены только для упрощения демонстрации.

### **Класс поставщика токенов AzureROP**

Пример [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) класс обрабатывает запросы на сборку, отправляет их в График Майкрософт API и обрабатывает ответы. Чтобы создать новый экземпляр этого класса, вам необходимо предоставить экземпляр [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), который может аутентифицировать запросы к График Майкрософт.

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
 * Azure resource owner password credential (ROPC) token provider
 * https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
 * https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth
 * https://portal.azure.com
 * https://developer.microsoft.com/en-us/graph/graph-explorer/#
 * token parser https://jwt.io
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
                throw new IllegalAccessError("Operation failed: " + connection.getResponseCode() + "/" +
                        connection.getResponseMessage() + "\r\nDetails:\r\n{2}"
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
            // ignore
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
