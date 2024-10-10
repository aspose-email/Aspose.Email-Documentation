---
title: "Утилиты Gmail"
url: /ru/java/gmail-utility-features/
weight: 10
type: docs
---


## **Работа с запросом FreeBusy**
Aspose.Email предоставляет механизм запросов для проверки, запланирована ли встреча в соответствии с заданными критериями. Для этой цели предоставляется класс [FreebusyQuery](https://reference.aspose.com/email/java/com.aspose.email/FreebusyQuery), который позволяет подготовить запрос для определённого календаря.
### **Запрос календаря**
Этот пример кода демонстрирует возможность запроса календаря. В этом примере выполняются следующие задачи:

1. Создание и вставка календаря
1. Создание встречи
1. Вставка встречи
1. Подготовка [FreebusyQuery](https://reference.aspose.com/email/java/com.aspose.email/FreebusyQuery)
1. Получение [FreebusyResponse](https://reference.aspose.com/email/java/com.aspose.email/FreebusyResponse)

```java
// Используйте классы OAuthUser и GoogleOAuthHelper ниже для получения токена доступа
IGmailClient client = GmailClient.getInstance(accessToken, "user@domain.com");
try {
    Calendar newCalendar = new Calendar("summary", null, null, "Europe/Kiev");

    // Вставьте календарь и получите идентификатор вновь вставленного календаря, затем получите тот же календарь, используя идентификатор календаря
    String id = client.createCalendar(newCalendar);
    Calendar fetchedCalendar = client.fetchCalendar(id);
    String calendarId = fetchedCalendar.getId();
    try {
        // Получите список встреч в вновь вставленном календаре. Он должен быть равен нулю
        Appointment[] appointments = client.listAppointments(calendarId);

        // Создайте новую встречу и рассчитайте время начала и окончания встречи
        java.util.Calendar c = java.util.Calendar.getInstance();
        Date startDate = c.getTime();
        c.add(java.util.Calendar.HOUR_OF_DAY, 1);
        Date endDate = c.getTime();

        // Создайте список участников для встречи
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.add("user1@domain.com");
        attendees.add("user2@domain.com");

        // Создайте встречу
        Appointment app1 = new Appointment("Location", startDate, endDate, MailAddress.to_MailAddress("user2@domain.com"), attendees);
        app1.setSummary("Summary");
        app1.setDescription("Description");
        app1.setStartTimeZone("Europe/Kiev");
        app1.setEndTimeZone("Europe/Kiev");

        // Вставьте вновь созданную встречу и получите её при успешной вставке
        Appointment newAppointment = client.createAppointment(calendarId, app1);

        // Создайте запрос Freebusy, установив минимальное/максимальное время и временную зону
        FreebusyQuery query = new FreebusyQuery();
        c = java.util.Calendar.getInstance();
        c.add(java.util.Calendar.DATE, -1);
        query.setTimeMin(c.getTime());
        c.add(java.util.Calendar.DATE, 2);
        query.setTimeMax(c.getTime());
        query.setTimeZone("Europe/Kiev");

        // Установите элемент календаря для поиска и получите ответ на запрос
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
## **Создание проекта в Google Developer Console**
Проект должен быть создан в Google Developer Console для пользователя с Gmail-аккаунтом. На странице API и авторизация -> Учетные данные Google проекта нужно записать информацию, такую как идентификатор клиента и секрет клиента. Эта информация вместе с именем пользователя и паролем Gmail потребуется для выполнения кода, например, для работы с Google Calendar, списками контроля доступа, встречами, контактами, настройками и т.д. в этом разделе.
### **Шаги для создания проекта в Google Developer Console**
Ниже представлено пошаговое руководство по созданию проекта в Google Developer Console.

1. Перейдите по ссылке <https://console.cloud.google.com> и войдите с использованием данных своей учетной записи Gmail.

2. Установите флажок "Я прочитал и согласен со всеми условиями обслуживания продуктов Google Cloud Platform." и нажмите кнопку **НОВЫЙ ПРОЕКТ**.

![todo:image_alt_text](gmail-utility-features_1.png)

3. **Создайте** и **Выберите** новый проект.

![todo:image_alt_text](gmail-utility-features_2.png)

4. Выберите **Библиотека** и включите API контактов и календаря.

![todo:image_alt_text](gmail-utility-features_6.png)

5. Откройте **Экран согласия OAuth**.

![todo:image_alt_text](gmail-utility-features_3.png)

6. Установите флажок **Внешний** и нажмите кнопку **СОЗДАТЬ**.

![todo:image_alt_text](gmail-utility-features_4.png)

7. Отредактируйте регистрацию приложения и нажмите кнопку **СОХРАНИТЬ И ПРОДОЛЖИТЬ**.

![todo:image_alt_text](gmail-utility-features_5.png)

8. Добавьте области и нажмите кнопку **ОБНОВИТЬ**.

![todo:image_alt_text](gmail-utility-features_7.png)

9. Создайте учетные данные OAuth.

![todo:image_alt_text](gmail-utility-features_8.png)

10. Идентификатор клиента и секрет клиента здесь, которые будут использоваться в примерах кода в этом разделе.

![todo:image_alt_text](gmail-utility-features_9.png)

## **Вспомогательные классы**
Для выполнения примеров кода в этом разделе требуются следующие вспомогательные классы. Эти классы `GoogleOAuthHelper` и `OAuthUser` предназначены только для упрощения демонстрации. Методы в этих классах используют непубличную структуру веб-страниц, которая может изменяться в любое время.
### **Класс GoogleOAuthHelper**
Следующий фрагмент кода показывает, как реализовать класс `GoogleOAuthHelper`.

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
 * Консоль разработчика https://console.developers.google.com/projectselector/apis/credentials?pli=1 
 * Документация https://developers.google.com/identity/protocols/OAuth2InstalledApp
 * </p>
 */
class GoogleOAuthHelper {
    public static final String AUTHORIZATION_URL = "https://accounts.google.com/o/oauth2/v2/auth";
    public static final String TOKEN_REQUEST_URL = "https://oauth2.googleapis.com/token";
    public static final String REDIRECT_URI = "urn:ietf:wg:oauth:2.0:oob";
    public static final String REDIRECT_TYPE = "code";
    public static final String SCOPE = "https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcalendar" // Календарь
            + "+https%3A%2F%2Fwww.google.com%2Fm8%2Ffeeds%2F" // Контакты
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
        System.out.println("------------- URL авторизации OAuth 2.0 -------------");
        System.out.println("---------------------------------------------------------");
        System.out.println("Логин: " + acc.email);
        String codeChallenge = createCodeChalange();

        String state = urlEncode(UUID.randomUUID().toString());
        String approveUrl = AUTHORIZATION_URL + "?client_id=" + acc.clientId + "&redirect_uri=" + redirectUri + "&response_type=" + responseType + "&scope=" + scope
                + "&code_challenge=" + codeChallenge + "&code_challenge_method=S256&state=" + state;

        System.out.println("URL для подтверждения: " + approveUrl);
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
        System.out.println("Авторизационный код: " + authorizationCode);

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
        System.out.println("Логин: " + user.email);

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
                throw new IllegalAccessError("Операция не удалась: " + connection.getResponseCode() + "/" + connection.getResponseMessage() + "\r\nДетали:\r\n{2}"
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
            // игнорировать
        }
        return result.toString();
    }
}
```

**Google OAuth Helper** должен использоваться следующим образом:
1. Сначала необходимо сгенерировать URL авторизации.
1. Откройте URL в браузере и выполните все операции. В результате вы получите код авторизации.
1. Используйте код авторизации для получения токена обновления.
1. Когда токен обновления существует, вы можете использовать его для получения токенов доступа.

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

    // Установите clientId, clientSecret и email
    System.out.println("Установите clientId: ");
    user.clientId = inputReader.nextLine();
    System.out.println("Установите clientSecret: ");
    user.clientSecret = inputReader.nextLine();
    System.out.println("Установите email: ");
    user.email = inputReader.nextLine();

    // Генерация URL для AuthorizationCode
    String authorizationCodeUrl = GoogleOAuthHelper.getAuthorizationCodeUrl(user);

    System.out.println("Вы должны вручную получить AuthorizationCode с помощью сгенерированного AuthorizationCodeUrl");
    System.out.println("Установите authorizationCode: ");
    String authorizationCode = inputReader.nextLine();
    System.out.println("Скопируйте Code Verifier из предыдущего шага.");
    System.out.println("Установите codeVerifier: ");
    String codeVerifier = inputReader.nextLine();

    // Получите "Refresh Token"
    String refreshToken = GoogleOAuthHelper.getAccessTokenByAuthCode(authorizationCode, codeVerifier, user);
    user.refreshToken = refreshToken;

    // Получите "Access Token"
    String accessToken = GoogleOAuthHelper.getAccessTokenByRefreshToken(user);
    
    // Используйте "Access Token" в API
    IGmailClient client = GmailClient.getInstance(accessToken, user.email);
}
```