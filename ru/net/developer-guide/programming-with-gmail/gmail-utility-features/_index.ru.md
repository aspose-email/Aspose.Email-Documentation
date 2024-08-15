---
title: "Функции утилиты Gmail"
url: /ru/net/gmail-utility-features/
weight: 10
type: docs
---


## **Работа с запросом FreeBusy**

Aspose.Email предоставляет механизм запросов, позволяющий проверить, назначена ли встреча в соответствии с критериями. Для этого предусмотрен класс FreeBusyQuery, который позволяет подготовить запрос к определенному календарю.

### **Запрос календаря**

В этом примере кода показана возможность запроса календаря. В этом примере выполняются следующие задачи:

1. Создание и вставка календаря
1. Назначьте встречу
1. Укажите встречу
1. Подготовьте бесплатный запрос Busy
1. Получите бесплатный ответ Busy

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Use the GoogleUser and GoogleOAuthHelper classes below to receive an access token
using (IGmailClient client = GmailClient.GetInstance(accessToken, user.Email))
{
    // Initialize calendar item
    Aspose.Email.Clients.Google.Calendar calendar1 = new Aspose.Email.Clients.Google.Calendar("summary - " + Guid.NewGuid().ToString(), null, null, "Europe/Kiev");

    // Insert calendar and get back id of newly inserted calendar and Fetch the same calendar using calendar id
    string id = client.CreateCalendar(calendar1);
    Aspose.Email.Clients.Google.Calendar cal1 = client.FetchCalendar(id);
    string calendarId1 = cal1.Id;
    try
    {
        // Get list of appointments in newly inserted calendar. It should be zero
        Appointment[] appointments = client.ListAppointments(calendarId1);
        if (appointments.Length != 0)
        {
            Console.WriteLine("Wrong number of appointments");
            return;
        }

        // Create a new appointment and Calculate appointment start and finish time
        DateTime startDate = DateTime.Now;
        DateTime endDate = startDate.AddHours(1);

        // Create attendees list for appointment
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.Add("user1@domain.com");
        attendees.Add("user2@domain.com");

        // Create appointment
        Appointment app1 = new Appointment("Location - " + Guid.NewGuid().ToString(), startDate, endDate, "user2@domain.com", attendees);
        app1.Summary = "Summary - " + Guid.NewGuid().ToString();
        app1.Description = "Description - " + Guid.NewGuid().ToString();
        app1.StartTimeZone = "Europe/Kiev";
        app1.EndTimeZone = "Europe/Kiev";

        // Insert the newly created appointment and get back the same in case of successful insertion
        Appointment app2 = client.CreateAppointment(calendarId1, app1);

        // Create Freebusy query by setting min/max timeand time zone
        FreebusyQuery query = new FreebusyQuery();
        query.TimeMin = DateTime.Now.AddDays(-1);
        query.TimeMax = DateTime.Now.AddDays(1);
        query.TimeZone = "Europe/Kiev";

        // Set calendar item to search and Get the reponse of query containing
        query.Items.Add(cal1.Id);
        FreebusyResponse resp = client.GetFreebusyInfo(query);
        // Delete the appointment
        client.DeleteAppointment(calendarId1, app2.UniqueId);
    }
    finally
    {
        // Delete the calendar
        client.DeleteCalendar(cal1.Id);
    }
}
```

## **Создание проекта в консоли разработчика Google**

Проект должен быть создан в консоли разработчика Google для пользователя, имеющего учетную запись Gmail. На странице API & auth -> Учетные данные проекта Google необходимо указать такую информацию, как идентификатор клиента и секрет клиента. Эта информация, а также имя пользователя и пароль учетной записи Gmail потребуются для выполнения кода, например, календарь Google, списки контроля доступа, встречи, контакты, настройки и т. д. в этом разделе.

### **Шаги по созданию проекта в консоли разработчика Google**

Ниже приведено пошаговое руководство по созданию проекта в консоли разработчика Google.

1. Перейти по ссылке <https://cloud.google.com/console/project> и войдите в систему, используя свои учетные данные gmail

|![todo:image_alt_text](gmail-utility-features_1.png)|
|: - |
2. Установите флажок «Я прочитал и согласен со всеми Условиями обслуживания продуктов Google Cloud Platform» и нажмите кнопку «Создать»

|![todo:image_alt_text](gmail-utility-features_2.png)|
|: - |
3. Будет запрошена «Подтверждение по SMS». Нажмите кнопку «Продолжить»:

|![todo:image_alt_text](gmail-utility-features_3.png)|
|: - |
4. Введите название страны и номер мобильного телефона. Нажмите кнопку: Отправить проверочный код

|![todo:image_alt_text](gmail-utility-features_4.png)|
|: - |
5. Введите проверочный код, полученный на вашем мобильном телефоне.

|![todo:image_alt_text](gmail-utility-features_5.png)|
|: - |
6. В списке API и auth\ API включите статус API календаря и API контактов. Выключите все остальные.

|![todo:image_alt_text](gmail-utility-features_6.png)|
|: - |
7. В разделе «API и аутентификация» -> «Учетные данные» нажмите кнопку «СОЗДАТЬ НОВЫЙ ИДЕНТИФИКАТОР КЛИЕНТА» в разделе «OAuth». Выберите «Установленное приложение» и «Другое» из предложенных вариантов и нажмите кнопку «Создать идентификатор клиента». Запишите здесь идентификатор клиента и секрет клиента, которые будут использованы в примерах кодов в этом разделе.

|![todo:image_alt_text](gmail-utility-features_7.png)|
|: - |

## **Вспомогательные классы**

Для запуска примеров кода, приведенных в этом разделе, необходимы следующие вспомогательные классы. Эти классы `GoogleOAuthHelper` and `GoogleUser` предназначены только для упрощения демонстрации. Методы этих классов используют закрытую структуру веб-страниц, которая может измениться в любое время.

### **Вспомогательный класс Google OAuth**

В следующем фрагменте кода показано, как реализовать `GoogleOAuthHelper` class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

using Newtonsoft.Json;
using System;
using System.Collections.Generic;
using System.IO;
using System.Net;
using System.Security.Cryptography;
using System.Text;

/// <summary>
/// Developer console:
/// https://console.cloud.google.com/projectselector2
/// Documentation:
/// https://developers.google.com/identity/protocols/oauth2/native-app
/// </summary>
internal class GoogleOAuthHelper
{
    public const string AUTHORIZATION_URL = "https://accounts.google.com/o/oauth2/v2/auth";
    public const string TOKEN_REQUEST_URL = "https://oauth2.googleapis.com/token";

    public const string REDIRECT_URI = "urn:ietf:wg:oauth:2.0:oob";
    public const string REDIRECT_TYPE = "code";

    public static string codeVerifier;
    public static string codeChallenge;

    public static CodeChallengeMethod codeChallengeMethod = CodeChallengeMethod.S256;

    public const string SCOPE =
        "https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcalendar" + // Calendar
        "+" +
        "https%3A%2F%2Fwww.google.com%2Fm8%2Ffeeds%2F" + // Contacts
        "+" +
        "https%3A%2F%2Fmail.google.com%2F"; // IMAP & SMTP

    static GoogleOAuthHelper()
    {
        CreateCodeVerifier();
        CreateCodeChallenge();
    }

    internal static string CreateCodeVerifier()
    {
        string allowedChars = "0123456789AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz-._~";

        const int minLength = 43;
        const int maxLength = 128;

        Random random = new Random();
        int length = minLength + random.Next(maxLength - minLength);
        List<char> codeVerifierChars = new List<char>();

        for (int i = 0; i < length; i++)
        {
            int index = random.Next(allowedChars.Length);
            codeVerifierChars.Add(allowedChars[index]);
        }

        return codeVerifier = string.Join("", codeVerifierChars.ToArray());
    }

    internal static string CreateCodeChallenge()
    {
        if (codeChallengeMethod == CodeChallengeMethod.Plain)
            return codeChallenge = codeVerifier;

        byte[] hashValue = null;
        using (SHA256 sha256 = SHA256.Create())
            hashValue = sha256.ComputeHash(Encoding.ASCII.GetBytes(codeVerifier));

        string b64 = Convert.ToBase64String(hashValue);
        b64 = b64.Split('=')[0];
        b64 = b64.Replace('+', '-');
        b64 = b64.Replace('/', '_');

        return codeChallenge = b64;
    }

    internal static string GetAuthorizationCodeUrl(GoogleUser user)
    {
        return GetAuthorizationCodeUrl(user, SCOPE, REDIRECT_URI, REDIRECT_TYPE);
    }

    internal static string GetAuthorizationCodeUrl(
        GoogleUser user, string scope, string redirectUri, string responseType)
    {
        string state = System.Web.HttpUtility.UrlEncode(Guid.NewGuid().ToString());

        string approveUrl = AUTHORIZATION_URL +
            $"?client_id={user.ClientId}&redirect_uri={redirectUri}&response_type={responseType}&scope={scope}&" +
            $"code_challenge={codeChallenge}&code_challenge_method={codeChallengeMethod.ToString()}&" +
            $"state={state}";

        return approveUrl;
    }

    internal static TokenResponse GetAccessTokenByRefreshToken(GoogleUser user)
    {
        HttpWebRequest request = (HttpWebRequest)WebRequest.Create(TOKEN_REQUEST_URL);
        request.CookieContainer = new CookieContainer();
        request.Method = "POST";
        request.ContentType = "application/x-www-form-urlencoded";

        string clientId = System.Web.HttpUtility.UrlEncode(user.ClientId);
        string clientSecret = System.Web.HttpUtility.UrlEncode(user.ClientSecret);
        string refreshToken = System.Web.HttpUtility.UrlEncode(user.RefreshToken);
        string grantType = System.Web.HttpUtility.UrlEncode("refresh_token");

        string encodedParameters = $"client_id={clientId}&client_secret={clientSecret}&refresh_token={refreshToken}&grant_type={grantType}";

        byte[] requestData = Encoding.UTF8.GetBytes(encodedParameters);
        request.ContentLength = requestData.Length;
        if (requestData.Length > 0)
            using (Stream stream = request.GetRequestStream())
                stream.Write(requestData, 0, requestData.Length);

        HttpWebResponse response = (HttpWebResponse)request.GetResponse();
        string responseText = null;
        using (TextReader reader = new StreamReader(response.GetResponseStream(), Encoding.ASCII))
            responseText = reader.ReadToEnd();

        TokenResponse tokensResponse = JsonConvert.DeserializeObject<TokenResponse>(responseText);

        return tokensResponse;
    }

    internal static TokenResponse GetAccessTokenByAuthCode(string authorizationCode, GoogleUser user)
    {
        HttpWebRequest request = (HttpWebRequest)WebRequest.Create(TOKEN_REQUEST_URL);
        request.CookieContainer = new CookieContainer();
        request.Method = "POST";
        request.ContentType = "application/x-www-form-urlencoded";

        string clientId = System.Web.HttpUtility.UrlEncode(user.ClientId);
        string clientSecret = System.Web.HttpUtility.UrlEncode(user.ClientSecret);
        string authCode = System.Web.HttpUtility.UrlEncode(authorizationCode);
        string redirectUri = System.Web.HttpUtility.UrlEncode(REDIRECT_URI);
        string grantType = System.Web.HttpUtility.UrlEncode("authorization_code");

        string encodedParameters = $"client_id={clientId}&client_secret={clientSecret}&code={authCode}&code_verifier={codeVerifier}&redirect_uri={redirectUri}&grant_type={grantType}";

        byte[] requestData = Encoding.UTF8.GetBytes(encodedParameters);
        request.ContentLength = requestData.Length;
        if (requestData.Length > 0)
            using (Stream stream = request.GetRequestStream())
                stream.Write(requestData, 0, requestData.Length);

        HttpWebResponse response = (HttpWebResponse)request.GetResponse();
        string responseText = null;
        using (TextReader reader = new StreamReader(response.GetResponseStream(), Encoding.ASCII))
            responseText = reader.ReadToEnd();

        TokenResponse tokensResponse = JsonConvert.DeserializeObject<TokenResponse>(responseText);

        return tokensResponse;
    }

    public enum CodeChallengeMethod
    {
        S256,
        Plain
    }
}
```

**Помощник Google по аутентификации** следует использовать следующим образом:

1. Сначала необходимо сгенерировать URL-адрес кода авторизации.
1. Откройте URL-адрес в браузере и выполните все операции. В результате вы получите код авторизации.
1. Используйте код авторизации для получения токена обновления.
1. Если токен обновления существует, вы можете использовать его для получения токенов доступа.

```csharp
GoogleUser user = new GoogleUser(email, password, clientId, clientSecret);

string authUrl = GoogleOAuthHelper.GetAuthorizationCodeUrl(user);

Console.WriteLine("Go to the following URL and get your authorization code:");
Console.WriteLine(authUrl);
Console.WriteLine();

Console.WriteLine("Enter the authorization code:");
string authorizationCode = Console.ReadLine();
Console.WriteLine();

TokenResponse tokenInfo = GoogleOAuthHelper.GetAccessTokenByAuthCode(authorizationCode, user);
Console.WriteLine("The refresh token has been received:");
Console.WriteLine(tokenInfo.RefreshToken);
Console.WriteLine();

user.RefreshToken = tokenInfo.RefreshToken;
tokenInfo = GoogleOAuthHelper.GetAccessTokenByRefreshToken(user);
Console.WriteLine("The new access token has been received:");
Console.WriteLine(tokenInfo.AccessToken);
Console.WriteLine();
```

### **Класс пользователя Google**
В следующем фрагменте кода показано, как реализовать `GoogleUser` class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

public class GoogleUser
{
    public GoogleUser(string email, string password, string clientId, string clientSecret)
        : this(email, password, clientId, clientSecret, null)
    {
    }

    public GoogleUser(string email, string password, string clientId, string clientSecret, string refreshToken)
    {
        Email = email;
        Password = password;
        ClientId = clientId;
        ClientSecret = clientSecret;
        RefreshToken = refreshToken;
    }

    public readonly string Email;
    public readonly string Password;
    public readonly string ClientId;
    public readonly string ClientSecret;

    public string RefreshToken;
}
```

### **Класс ответа токена**

В следующем фрагменте кода показано, как реализовать `TokenResponse` class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

using Newtonsoft.Json;

public class TokenResponse
{
    [JsonProperty(NullValueHandling = NullValueHandling.Ignore, PropertyName = "access_token", Required = Required.Default)]
    public string AccessToken { get; set; }

    [JsonProperty(NullValueHandling = NullValueHandling.Ignore, PropertyName = "token_type", Required = Required.Default)]
    public string TokenType { get; set; }

    [JsonProperty(NullValueHandling = NullValueHandling.Ignore, PropertyName = "expires_in", Required = Required.Default)]
    public int ExpiresIn { get; set; }

    [JsonProperty(NullValueHandling = NullValueHandling.Ignore, PropertyName = "refresh_token", Required = Required.Default)]
    public string RefreshToken { get; set; }

    [JsonProperty(NullValueHandling = NullValueHandling.Ignore, PropertyName = "scope", Required = Required.Default)]
    public string Scope { get; set; }
}
```
