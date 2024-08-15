---
title: "Acceder a los servicios de correo mediante OAuth"
url: /es/net/access-mail-services-using-oauth/
weight: 190
type: docs
---


Se ha agregado la compatibilidad con OAuth 2.0 a Aspose.Email y se puede usar para acceder **SMTP**, **POP3**, **IMAP** and **EWS** servidores.
En general, todos los servidores compatibles **OAuth 2.0** Los tokens portadores se pueden usar con Aspose.Email, pero nuestros clientes de correo electrónico se han probado con los servidores de correo de Google y Microsoft Office 365.
Acceso al servidor desde [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient), [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client), [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) and [EWSClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) con OAuth se puede implementar de 2 maneras.

1. Proporcione el token de acceso directamente al constructor del cliente de correo electrónico. En este caso, el usuario debe entender que la vida útil de los tokens de acceso es limitada. Cuando el token caduca, el cliente de correo electrónico no se puede usar para acceder al servidor.
2. Proporcione una implementación personalizada del proveedor de tokens basada en [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) interfaz en el constructor del cliente de correo electrónico. En este caso, el cliente comprueba la fecha de caducidad del token y las solicitudes [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) para un nuevo token de acceso cuando el anterior haya caducado. De esta forma, el cliente actualiza los tokens periódicamente y puede trabajar con el servidor durante un tiempo ilimitado. A menudo, los servicios admiten una forma sencilla de actualizar los tokens de acceso. Por ejemplo, el uso de tokens de actualización en los servicios de Google o el flujo de autenticación ROPC en la plataforma de identidad de Microsoft se puede usar para implementar el proveedor de tokens.

## **Configurar una cuenta en el servidor apropiado**

Los siguientes artículos le ayudan a configurar cuentas para acceder a los servicios de correo.

- For [Office 365](https://docs.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth)
- For [Gmail](https://developers.google.com/gmail/imap/imap-smtp)

## **Acceda a los servicios de correo con los tokens de acceso**

Los siguientes ejemplos de código muestran cómo conectarse a los servicios de correo mediante tokens de acceso.

```csharp
// Connecting to SMTP server
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    "accessToken",
    true,
    SecurityOptions.SSLExplicit))
{

}

// Connecting to IMAP server
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   "accessToken",
   true,
   SecurityOptions.SSLImplicit))
{

}

// Connecting to POP3 server
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

## **Acceda a los servicios de correo con los proveedores de tokens**

Los siguientes ejemplos de código muestran cómo conectarse a los servicios de correo mediante un proveedor de tokens.

```csharp
ITokenProvider tokenProvider = TokenProvider.Google.GetInstance(
    "ClientId",
    "ClientSecret",
    "RefreshToken");

// Connecting to SMTP server
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Connecting to IMAP server
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.SSLImplicit))
{

}

// Connecting to POP3 server
using (Pop3Client client = new Pop3Client(
   "pop.gmail.com",
   995,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}
```

## **Implementación de iTokenProvider personalizado para Office 365**

Puede usar la implementación del proveedor de tokens que aparece a continuación para acceder a los servicios de correo de Office 365.

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
    /// Azure resource owner password credential (ROPC) token provider
    /// https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
    /// https://portal.azure.com
    /// https://developer.microsoft.com/en-us/graph/graph-explorer/#
    /// token parser https://jwt.io
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
        /// Initializes a new instance of the <see cref="AzureROPCTokenProvider"/> class
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
        /// Gets oAuth access token.
        /// </summary>
        /// <param name="ignoreExistingToken">
        /// If ignoreExistingToken is true, requests new token from a server. Otherwise behaviour is depended on whether token exists or not.
        /// If token exists and its expiration date is not expired returns current token, otherwise requests new token from a server.
        /// </param>
        /// <returns>Returns oAuth access token</returns>
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
        /// Gets oAuth access token.
        /// If token exists and its expiration date is not expired returns current token, otherwise requests new token from a server.
        /// </summary>
        /// <returns>Returns oAuth access token</returns>
        public OAuthToken GetAccessToken()
        {
            return GetAccessToken(false);
        }

        /// <summary>
        /// Performs application-defined tasks associated with freeing, releasing, or resetting unmanaged resources.
        /// </summary>
        public virtual void Dispose()
        {
        }
    }

    /// <summary>
    /// A success response contains a JSON OAuth 2.0 response with the following parameters.
    /// </summary>
    public class AzureTokenResponse
    {
        /// <summary>
        /// The requested access token. The calling web service can use this token to authenticate to the receiving web service.
        /// </summary>
        public string access_token { get; set; }

        /// <summary>
        /// Indicates the token type value. The only type that Azure AD supports is Bearer For more information about bearer tokens,
        /// see The OAuth 2.0 Authorization Framework: Bearer Token Usage (RFC 6750).
        /// </summary>
        public string token_type { get; set; }

        /// <summary>
        /// How long the access token is valid (in seconds).
        /// </summary>
        public int expires_in { get; set; }

        /// <summary>
        /// How long the access token is valid (in seconds).
        /// </summary>
        public int ext_expires_in { get; set; }

        /// <summary>
        /// The time when the access token expires.
        /// The date is represented as the number of seconds from 1970-01-01T00:00:00Z UTC until the expiration time.
        /// This value is used to determine the lifetime of cached tokens.
        /// </summary>
        public int expires_on { get; set; }

        /// <summary>
        /// The App ID URI of the receiving web service.
        /// </summary>
        public string resource { get; set; }

        /// <summary>
        /// If an access token was returned, this parameter lists the scopes the access token is valid for.
        /// </summary>
        public string scope { get; set; }

        /// <summary>
        /// Issued if the original scope parameter included the openid scope.
        /// </summary>
        public string id_token { get; set; }

        /// <summary>
        /// Issued if the original scope parameter included offline_access.
        /// </summary>
        public string refresh_token { get; set; }
    }
}

```

Los siguientes ejemplos de código muestran cómo conectarse a los servicios de Office 365 mediante el proveedor de token personalizado.

```csharp
ITokenProvider tokenProvider = new AzureROPCTokenProvider(
    "Tenant",
    "ClientId",
    "ClientSecret",
    "EMail",
    "Password",
    scopes);

// Connecting to SMTP server
using (SmtpClient client = new SmtpClient(
    "smtp.office365.com",
    587,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Connecting to IMAP server
using (ImapClient client = new ImapClient(
    "outlook.office365.com",
    993,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLImplicit))
{

}

// Connecting to POP3 server
using (Pop3Client client = new Pop3Client(
   "outlook.office365.com",
   995,
   "Test1@test.onmicrosoft.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}

// Connecting to EWS server
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
ICredentials credentials = new OAuthNetworkCredential(tokenProvider);
using (IEWSClient ewsClient = EWSClient.GetEWSClient(mailboxUri, credentials))
{

}
```
