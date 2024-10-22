---
title: "Características de la utilería de Gmail"
url: /es/net/gmail-utility-features/
weight: 10
type: docs
---


## **Trabajando con la consulta FreeBusy**

Aspose.Email proporciona un mecanismo de consulta para verificar si alguna cita está pendiente o no de acuerdo con los criterios. Se proporciona la clase FreebusyQuery para este propósito, que permite preparar una consulta para un calendario particular.

### **Consultando un calendario**

Este ejemplo de código demuestra la función de consultar un calendario. Las siguientes tareas se realizan en este ejemplo:

1. Crear e insertar un calendario
1. Crear una cita
1. Insertar la cita
1. Preparar una FreeBusyQuery
1. Obtener la FreebusyResponse

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

// Usa las clases GoogleUser y GoogleOAuthHelper a continuación para recibir un token de acceso
using (IGmailClient client = GmailClient.GetInstance(accessToken, user.Email))
{
    // Inicializar el ítem del calendario
    Aspose.Email.Clients.Google.Calendar calendar1 = new Aspose.Email.Clients.Google.Calendar("resumen - " + Guid.NewGuid().ToString(), null, null, "Europe/Kiev");

    // Insertar el calendario y recuperar el id del calendario recién insertado y obtener el mismo calendario usando el id del calendario
    string id = client.CreateCalendar(calendar1);
    Aspose.Email.Clients.Google.Calendar cal1 = client.FetchCalendar(id);
    string calendarId1 = cal1.Id;
    try
    {
        // Obtener la lista de citas en el calendario recién insertado. Debería ser cero
        Appointment[] appointments = client.ListAppointments(calendarId1);
        if (appointments.Length != 0)
        {
            Console.WriteLine("Número incorrecto de citas");
            return;
        }

        // Crear una nueva cita y calcular la hora de inicio y fin de la cita
        DateTime startDate = DateTime.Now;
        DateTime endDate = startDate.AddHours(1);

        // Crear lista de asistentes para la cita
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.Add("user1@domain.com");
        attendees.Add("user2@domain.com");

        // Crear cita
        Appointment app1 = new Appointment("Ubicación - " + Guid.NewGuid().ToString(), startDate, endDate, "user2@domain.com", attendees);
        app1.Summary = "Resumen - " + Guid.NewGuid().ToString();
        app1.Description = "Descripción - " + Guid.NewGuid().ToString();
        app1.StartTimeZone = "Europe/Kiev";
        app1.EndTimeZone = "Europe/Kiev";

        // Insertar la cita recién creada y obtener la misma en caso de inserción exitosa
        Appointment app2 = client.CreateAppointment(calendarId1, app1);

        // Crear consulta Freebusy configurando tiempo mínimo/máximo y zona horaria
        FreebusyQuery query = new FreebusyQuery();
        query.TimeMin = DateTime.Now.AddDays(-1);
        query.TimeMax = DateTime.Now.AddDays(1);
        query.TimeZone = "Europe/Kiev";

        // Establecer el ítem del calendario a buscar y obtener la respuesta de la consulta conteniendo 
        query.Items.Add(cal1.Id);
        FreebusyResponse resp = client.GetFreebusyInfo(query);
        // Eliminar la cita
        client.DeleteAppointment(calendarId1, app2.UniqueId);
    }
    finally
    {
        // Eliminar el calendario
        client.DeleteCalendar(cal1.Id);
    }
}
```

## **Creando un proyecto en Google Developer Console**

Se debe crear un proyecto en Google Developer Console para un usuario que tenga cuenta de Gmail. En la página API & auth -> Credenciales del proyecto de Google, se debe anotar información como el ID de cliente y el secreto de cliente. Esta información junto con el nombre de usuario y la contraseña de la cuenta de Gmail será necesaria para ejecutar el código, por ejemplo, calendario de Google, listas de control de acceso, citas, contactos, configuraciones, etc. en esta sección.

### **Pasos para crear un proyecto en Google Developer Console**

A continuación se presenta un tutorial paso a paso para crear un proyecto en Google Developer Console.

1. Ve al enlace <https://cloud.google.com/console/project> e inicia sesión utilizando tus credenciales de Gmail

|![todo:image_alt_text](gmail-utility-features_1.png)|
| :- |
2. Selecciona la casilla "He leído y acepto todos los Términos de Servicio de los productos de Google Cloud Platform." y presiona el botón Crear

|![todo:image_alt_text](gmail-utility-features_2.png)|
| :- |
3. Se solicitará "Verificación por SMS". Presiona el botón continuar:

|![todo:image_alt_text](gmail-utility-features_3.png)|
| :- |
4. Ingresa el nombre de tu país y tu número de móvil. Presiona el botón: Enviar Código de Verificación

|![todo:image_alt_text](gmail-utility-features_4.png)|
| :- |
5. Ingresa el código de verificación recibido en tu móvil.

|![todo:image_alt_text](gmail-utility-features_5.png)|
| :- |
6. En la lista de APIs & auth \ APIs, activa el estado del Calendar API y Contacts API. Apaga todas las demás.

|![todo:image_alt_text](gmail-utility-features_6.png)|
| :- |
7. En APIs & auth -> Credenciales, presiona el botón "CREAR NUEVO ID DE CLIENTE" en la sección "OAuth". Selecciona "Aplicación instalada" y "Otro" de las opciones dadas, y presiona el botón "Crear ID de cliente". Anota el ID de cliente y el secreto de cliente aquí que se usarán en los códigos de muestra en esta sección.

|![todo:image_alt_text](gmail-utility-features_7.png)|
| :- |

## **Clases de Ayuda**

Las siguientes clases de ayuda son necesarias para ejecutar los ejemplos de código en esta sección. Estas clases `GoogleOAuthHelper` y `GoogleUser` son solo para simplificar la demostración. Los métodos en estas clases utilizan estructuras no públicas de las páginas web que pueden cambiar en cualquier momento.

### **Clase GoogleOAuthHelper**

El siguiente fragmento de código te muestra cómo implementar la clase `GoogleOAuthHelper`.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

using Newtonsoft.Json;
using System;
using System.Collections.Generic;
using System.IO;
using System.Net;
using System.Security.Cryptography;
using System.Text;

/// <summary>
/// Consola del desarrollador:
/// https://console.cloud.google.com/projectselector2
/// Documentación:
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
        "https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcalendar" + // Calendario
        "+" +
        "https%3A%2F%2Fwww.google.com%2Fm8%2Ffeeds%2F" + // Contactos
        "+" +
        "https%3A%2F%2Fmail.google.com%2F"; // IMAP y SMTP

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

**Ayudante de Google OAuth** debe utilizarse de la siguiente manera:

1. Primero se debe generar una URL de código de autorización.
1. Abre la URL en un navegador y completa todas las operaciones. Como resultado, recibirás un código de autorización.
1. Usa el código de autorización para recibir un token de actualización.
1. Cuando el token de actualización existe, puedes usarlo para recuperar tokens de acceso.

```csharp
GoogleUser user = new GoogleUser(email, password, clientId, clientSecret);

string authUrl = GoogleOAuthHelper.GetAuthorizationCodeUrl(user);

Console.WriteLine("Ve a la siguiente URL y obtén tu código de autorización:");
Console.WriteLine(authUrl);
Console.WriteLine();

Console.WriteLine("Ingresa el código de autorización:");
string authorizationCode = Console.ReadLine();
Console.WriteLine();

TokenResponse tokenInfo = GoogleOAuthHelper.GetAccessTokenByAuthCode(authorizationCode, user);
Console.WriteLine("El token de actualización ha sido recibido:");
Console.WriteLine(tokenInfo.RefreshToken);
Console.WriteLine();

user.RefreshToken = tokenInfo.RefreshToken;
tokenInfo = GoogleOAuthHelper.GetAccessTokenByRefreshToken(user);
Console.WriteLine("El nuevo token de acceso ha sido recibido:");
Console.WriteLine(tokenInfo.AccessToken);
Console.WriteLine();
```

### **Clase GoogleUser**
El siguiente fragmento de código muestra cómo implementar la clase `GoogleUser`.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

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

El siguiente fragmento de código muestra cómo implementar la clase `TokenResponse`.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET

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