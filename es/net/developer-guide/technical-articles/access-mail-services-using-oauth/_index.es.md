---
title: "Acceso a los Servicios de Correo utilizando OAuth"
url: /es/net/access-mail-services-using-oauth/
weight: 190
type: docs
---


El soporte para OAuth 2.0 se ha añadido a Aspose.Email y se puede utilizar para acceder a servidores **SMTP**, **POP3**, **IMAP** y **EWS**. 
En general, todos los servidores que admiten tokens portadores de **OAuth 2.0** se pueden utilizar con Aspose.Email, pero nuestros clientes de correo han sido probados con servidores de correo de Google y servidores de Microsoft Office 365. 
El acceso al servidor desde el [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient), [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client), [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) y [EWSClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) con OAuth puede implementarse de 2 maneras.

1. Proporcionar el token de acceso directamente al constructor del cliente de correo. En este caso, el usuario debe entender que la duración de los tokens de acceso es limitada. Cuando el token ha caducado, el cliente de correo no puede ser utilizado para acceder al servidor. 
2. Proporcionar una implementación personalizada del proveedor de tokens basada en la interfaz [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) en el constructor del cliente de correo. En este caso, el cliente verifica el tiempo de expiración del token y solicita un nuevo token de acceso a [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) cuando el anterior ha caducado. De esta manera, el cliente actualiza los tokens periódicamente y puede trabajar con el servidor por un tiempo ilimitado. A menudo, los servicios admiten una forma sencilla de actualizar los tokens de acceso. Por ejemplo, usar tokens de actualización en los servicios de Google o el flujo de autenticación ROPC en la plataforma de identidad de Microsoft se puede utilizar para implementar el proveedor de tokens.

## **Configurar una Cuenta en el Servidor Apropiado**

Los siguientes artículos le ayudan a configurar cuentas para acceder a los servicios de correo.

- Para [Office 365](https://docs.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth)
- Para [Gmail](https://developers.google.com/gmail/imap/imap-smtp)

## **Acceso a los Servicios de Correo con los Tokens de Acceso**

Los siguientes ejemplos de código le muestran cómo conectarse a los servicios de correo utilizando tokens de acceso.

```csharp
// Conectando al servidor SMTP
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    "accessToken",
    true,
    SecurityOptions.SSLExplicit))
{

}

// Conectando al servidor IMAP
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   "accessToken",
   true,
   SecurityOptions.SSLImplicit))
{

}

// Conectando al servidor POP3
using (Pop3Client client = new Pop3Client(
   "pop.gmail.com",
   995,
   "user1@gmail.com",
   "accessToken",
   true,
   SecurityOptions.Auto))
{

}
```

## **Acceso a los Servicios de Correo con los Proveedores de Tokens**

Los siguientes ejemplos de código le muestran cómo conectarse a los servicios de correo utilizando un proveedor de tokens.

```csharp
ITokenProvider tokenProvider = TokenProvider.Google.GetInstance(
    "ClientId",
    "ClientSecret",
    "RefreshToken");

// Conectando al servidor SMTP
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Conectando al servidor IMAP
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.SSLImplicit))
{

}

// Conectando al servidor POP3
using (Pop3Client client = new Pop3Client(
   "pop.gmail.com",
   995,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}
```

## **Implementación de ITokenProvider Personalizado para Office 365**

Puede utilizar la implementación del proveedor de tokens a continuación para acceder a los servicios de correo de Office 365.

```csharp
using JsonConvert = Newtonsoft.Json.JsonConvert;
using Aspose.Email.Clients;
using Aspose.Email.Common.Utils;
using Aspose.Email.Tests.TestUtils;
using Newtonsoft.Json;
using System;
using System.IO;
using System.Net;
using System.Text;

namespace TestNS
{
    /// <summary>
    /// Proveedor de tokens de credenciales de contraseña del propietario del recurso de Azure (ROPC)
    /// https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
    /// https://portal.azure.com
    /// https://developer.microsoft.com/en-us/graph/graph-explorer/#
    /// analizador de token https://jwt.io
    /// </summary>
    internal class AzureROPCTokenProvider : ITokenProvider
    {
        private const string uriFormat = "https://login.microsoftonline.com/{0}/oauth2/v2.0/token";
        private const string bodyFormat =
            "client_id={0}" +
            "&scope={1}" +
            "&username={2}" +
            "&password={3}" +
            "&grant_type={4}";

        private readonly string scope;
        private const string grant_type = "password";
        private readonly object tokenSyncObj = new object();
        private OAuthToken token;
        private readonly string tenant;
        private readonly string clientId;
        private readonly string clientSecret;
        private readonly string userName;
        private readonly string password;

        /// <summary>
        /// Inicializa una nueva instancia de la clase <see cref="AzureROPCTokenProvider"/>
        /// </summary>
        /// <param name="tenant"></param>
        /// <param name="clientId"></param>
        /// <param name="clientSecret"></param>
        /// <param name="scope"></param>
        /// <param name="userName"></param>
        /// <param name="password"></param>
        /// <param name="scopeAr"></param>
        public AzureROPCTokenProvider(
            string tenant, 
            string clientId, 
            string clientSecret, 
            string userName, 
            string password,
            string[] scopeAr)
        {
            this.tenant = tenant;
            this.clientId = clientId;
            this.clientSecret = clientSecret;
            this.userName = userName;
            this.password = password;
            this.scope = string.Join(" ", scopeAr);
        }

        /// <summary>
        /// Obtiene el token de acceso de oAuth. 
        /// </summary>
        /// <param name="ignoreExistingToken">
        /// Si ignoreExistingToken es verdadero, solicita un nuevo token a un servidor. De lo contrario, el comportamiento depende de si el token existe o no.
        /// Si el token existe y su fecha de expiración no ha caducado, devuelve el token actual; de lo contrario, solicita un nuevo token a un servidor.
        /// </param>
        /// <returns>Devuelve el token de acceso de oAuth</returns>
        public virtual OAuthToken GetAccessToken(bool ignoreExistingToken)
        {
            lock (tokenSyncObj)
            {
                if (this.token != null && !this.token.Expired && !ignoreExistingToken)
                    return this.token;
                token = null;
                string uri = string.Format(uriFormat, string.IsNullOrWhiteSpace(tenant) ? "common" : tenant);
                HttpWebRequest request = (HttpWebRequest)HttpWebRequest.Create(uri);
                string body = string.Format(bodyFormat,
                    HttpUtility.UrlEncode(clientId),
                    HttpUtility.UrlEncode(scope),
                    HttpUtility.UrlEncode(userName),
                    HttpUtility.UrlEncode(password),
                    HttpUtility.UrlEncode(grant_type));
                byte[] bytes = Encoding.ASCII.GetBytes(body);
                request.Method = "POST";
                request.ContentType = "application/x-www-form-urlencoded";
                request.ContentLength = bytes.Length;
                MemoryStream ms = new MemoryStream(bytes);
                using (Stream requestStream = request.GetRequestStream())
                    requestStream.Write(bytes, 0, bytes.Length);
                HttpWebResponse response = (HttpWebResponse)request.GetResponse();
                StringBuilder responseText = new StringBuilder();
                bytes = new byte[1024];
                int read = 0;
                using (Stream stream = response.GetResponseStream())
                {
                    while ((read = stream.Read(bytes, 0, bytes.Length)) > 0)
                        responseText.Append(Encoding.ASCII.GetString(bytes, 0, read));
                }
                string jsonString = responseText.ToString();
                AzureTokenResponse t = JsonConvert.DeserializeObject<AzureTokenResponse>(jsonString);
                token = new OAuthToken(
                    t.access_token,
                    TokenType.AccessToken,
                    DateTime.Now.AddSeconds(t.expires_in));
                return token;
            }
        }

        /// <summary>
        /// Obtiene el token de acceso de oAuth.
        /// Si el token existe y su fecha de expiración no ha caducado, devuelve el token actual; de lo contrario, solicita un nuevo token a un servidor.
        /// </summary>
        /// <returns>Devuelve el token de acceso de oAuth</returns>
        public OAuthToken GetAccessToken()
        {
            return GetAccessToken(false);
        }

        /// <summary>
        /// Realiza tareas definidas por la aplicación asociadas con liberar, liberar o restablecer recursos no administrados.
        /// </summary>
        public virtual void Dispose()
        {
        }
    }

    /// <summary>
    /// Una respuesta exitosa contiene una respuesta JSON de OAuth 2.0 con los siguientes parámetros.
    /// </summary>
    public class AzureTokenResponse
    {
        /// <summary>
        /// El token de acceso solicitado. El servicio web que llama puede usar este token para autenticarse en el servicio web receptor.
        /// </summary>
        public string access_token { get; set; }

        /// <summary>
        /// Indica el valor del tipo de token. El único tipo que admite Azure AD es Bearer. Para más información sobre los tokens portadores,
        /// consulte El marco de autorización de OAuth 2.0: Uso de tokens portadores (RFC 6750).
        /// </summary>
        public string token_type { get; set; }

        /// <summary>
        /// Cuánto tiempo es válido el token de acceso (en segundos).
        /// </summary>
        public int expires_in { get; set; }

        /// <summary>
        /// Cuánto tiempo es válido el token de acceso (en segundos).
        /// </summary>
        public int ext_expires_in { get; set; }

        /// <summary>
        /// El momento en que el token de acceso expira. 
        /// La fecha se representa como el número de segundos desde 1970-01-01T00:00:00Z UTC hasta el tiempo de expiración.
        /// Este valor se utiliza para determinar la duración de los tokens en caché.
        /// </summary>
        public int expires_on { get; set; }

        /// <summary>
        /// La URI del App ID del servicio web receptor.
        /// </summary>
        public string resource { get; set; }

        /// <summary>
        /// Si se devolvió un token de acceso, este parámetro enumera los ámbitos para los que el token de acceso es válido.
        /// </summary>
        public string scope { get; set; }

        /// <summary>
        /// Emitido si el parámetro de ámbito original incluía el ámbito openid.
        /// </summary>
        public string id_token { get; set; }

        /// <summary>
        /// Emitido si el parámetro de ámbito original incluía offline_access.
        /// </summary>
        public string refresh_token { get; set; }
    }
}

```

Los siguientes ejemplos de código le muestran cómo conectarse a los servicios de Office 365 utilizando el proveedor de tokens personalizado. 

```csharp
ITokenProvider tokenProvider = new AzureROPCTokenProvider(
    "Tenant",
    "ClientId",
    "ClientSecret",
    "EMail",
    "Password",
    scopes);

// Conectando al servidor SMTP
using (SmtpClient client = new SmtpClient(
    "smtp.office365.com",
    587,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Conectando al servidor IMAP
using (ImapClient client = new ImapClient(
    "outlook.office365.com",
    993,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLImplicit))
{

}

// Conectando al servidor POP3
using (Pop3Client client = new Pop3Client(
   "outlook.office365.com",
   995,
   "Test1@test.onmicrosoft.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}

// Conectando al servidor EWS
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
ICredentials credentials = new OAuthNetworkCredential(tokenProvider);
using (IEWSClient ewsClient = EWSClient.GetEWSClient(mailboxUri, credentials))
{

}
```