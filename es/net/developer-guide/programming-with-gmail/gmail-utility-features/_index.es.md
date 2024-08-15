---
title: "Funciones de la utilidad Gmail"
url: /es/net/gmail-utility-features/
weight: 10
type: docs
---


## **Trabajando con FreeBusy Query**

Aspose.Email proporciona un mecanismo de consulta para comprobar si alguna cita vence o no según los criterios. La clase FreeBusyQuery se proporciona para este propósito, que permite preparar una consulta para un calendario en particular.

### **Consulta de un calendario**

En este ejemplo de código se muestra la función de consultar un calendario. En este ejemplo se realizan las siguientes tareas:

1. Crear e insertar un calendario
1. Crea una cita
1. Insertar cita
1. Prepare un BusyQuery gratuito
1. Obtenga la respuesta gratuita de BusyResponse

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

## **Creación de un proyecto en Google Developer Console**

Se va a crear un proyecto en Google Developer Console para un usuario que tenga una cuenta de Gmail. En la página API y autenticación -> Credenciales del proyecto de Google, debe indicarse información como el ID del cliente y el secreto del cliente. Esta información, junto con el nombre de usuario y la contraseña de la cuenta de Gmail, serán necesarios para ejecutar el código, por ejemplo, el calendario de Google, las listas de control de acceso, las citas, los contactos, la configuración, etc. de esta sección.

### **Pasos para crear un proyecto en Google Developer Console**

A continuación se muestra un tutorial paso a paso para crear un proyecto en Google Developer Console.

1. Ir al enlace <https://cloud.google.com/console/project> e inicie sesión con sus credenciales de Gmail

|![todo:image_alt_text](gmail-utility-features_1.png)|
|: - |
2. Selecciona la casilla «He leído y acepto todas las condiciones de servicio de los productos de Google Cloud Platform» y pulsa el botón Crear

|![todo:image_alt_text](gmail-utility-features_2.png)|
|: - |
3. Se solicitará la «verificación por SMS». Pulsa el botón de continuar:

|![todo:image_alt_text](gmail-utility-features_3.png)|
|: - |
4. Introduzca el nombre de su país e introduzca el número de teléfono móvil. Presiona el botón: Enviar código de verificación

|![todo:image_alt_text](gmail-utility-features_4.png)|
|: - |
5. Introduce el código de verificación recibido en tu móvil.

|![todo:image_alt_text](gmail-utility-features_5.png)|
|: - |
6. En la lista API & auth\ APIs, active el estado de la API de calendario y la API de contactos. Desactiva todos los demás.

|![todo:image_alt_text](gmail-utility-features_6.png)|
|: - |
7. En las API y la autenticación -> Credenciales, pulse el botón «CREAR UN NUEVO ID DE CLIENTE» en la sección «OAuth». Selecciona «Aplicación instalada» y «Otra» entre las opciones disponibles y pulsa el botón «Crear ID de cliente». Anote aquí el ID de cliente y el secreto del cliente que se utilizarán en los códigos de muestra de esta sección.

|![todo:image_alt_text](gmail-utility-features_7.png)|
|: - |

## **Clases de ayuda**

Se requieren las siguientes clases auxiliares para ejecutar los ejemplos de código de esta sección. Estas clases `GoogleOAuthHelper` and `GoogleUser` son solo para simplificar la demostración. Los métodos de estas clases utilizan una estructura no pública de páginas web que puede cambiar en cualquier momento.

### **Clase GoogleOAuthHelper**

El siguiente fragmento de código muestra cómo implementar `GoogleOAuthHelper` class.

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

**Ayudante de Google OAuth** debe usarse de la siguiente manera:

1. Primero se debe generar una URL de código de autorización.
1. Abre la URL en un navegador y completa todas las operaciones. Como resultado, recibirá un código de autorización.
1. Usa el código de autorización para recibir un token de actualización.
1. Cuando exista el token de actualización, puede usarlo para recuperar los tokens de acceso.

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

### **Clase GoogleUser**
El siguiente fragmento de código muestra cómo implementar `GoogleUser` class.

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

### **Clase TokenResponse**

El siguiente fragmento de código muestra cómo implementar `TokenResponse` class.

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
