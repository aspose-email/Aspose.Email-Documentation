---
title: "Доступ к почтовым службам с использованием OAuth"
url: /ru/net/access-mail-services-using-oauth/
weight: 190
type: docs
---

Поддержка OAuth 2.0 была добавлена в Aspose.Email и может использоваться для доступа к **SMTP**, **POP3**, **IMAP** и **EWS** серверам. В общем, все серверы, поддерживающие **OAuth 2.0** токены доступа, могут использоваться с Aspose.Email, но наши почтовые клиенты были протестированы с почтовыми серверами Google и серверами Microsoft Office 365. Доступ к серверу из [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient), [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client), [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) и [EWSClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) с OAuth может быть реализован двумя способами.

1. Предоставить токен доступа прямо в конструкторе почтового клиента. В этом случае пользователю необходимо понимать, что срок действия токенов доступа ограничен. Когда токен истекает, почтовый клиент не может быть использован для доступа к серверу.
2. Предоставить собственную реализацию провайдера токенов на основе интерфейса [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) в конструктор почтового клиента. В этом случае клиент проверяет время истечения токена и запрашивает [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) для получения нового токена доступа, когда предыдущий истекает. Таким образом, клиент периодически обновляет токены и может работать с сервером неограниченное время. Часто службы поддерживают простой способ обновления токенов доступа. Например, можно использовать refresh-токены в службах Google или поток аутентификации ROPC в платформе идентификации Microsoft для реализации провайдера токенов.

## **Настройка учетной записи на соответствующем сервере**

Следующие статьи помогут вам настроить учетные записи для доступа к почтовым услугам.

- Для [Office 365](https://docs.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth)
- Для [Gmail](https://developers.google.com/gmail/imap/imap-smtp)

## **Доступ к почтовым службам с токенами доступа**

Следующие примеры кода показывают, как подключиться к почтовым службам, используя токены доступа.

```csharp
// Подключение к SMTP серверу
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    "accessToken",
    true,
    SecurityOptions.SSLExplicit))
{

}

// Подключение к IMAP серверу
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   "accessToken",
   true,
   SecurityOptions.SSLImplicit))
{

}

// Подключение к POP3 серверу
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

## **Доступ к почтовым службам с провайдерами токенов**

Следующие примеры кода показывают, как подключиться к почтовым службам, используя провайдера токенов.

```csharp
ITokenProvider tokenProvider = TokenProvider.Google.GetInstance(
    "ClientId",
    "ClientSecret",
    "RefreshToken");

// Подключение к SMTP серверу
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Подключение к IMAP серверу
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.SSLImplicit))
{

}

// Подключение к POP3 серверу
using (Pop3Client client = new Pop3Client(
   "pop.gmail.com",
   995,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}
```

## **Реализация собственного ITokenProvider для Office 365**

Вы можете использовать реализацию провайдера токенов ниже для доступа к почтовым службам Office 365.

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
    /// Провайдер токенов учетных данных владельца ресурса Azure (ROPC)
    /// https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
    /// https://portal.azure.com
    /// https://developer.microsoft.com/en-us/graph/graph-explorer/#
    /// парсер токенов https://jwt.io
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
        /// Инициализирует новый экземпляр класса <see cref="AzureROPCTokenProvider"/>
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
        /// Получает oAuth токен доступа. 
        /// </summary>
        /// <param name="ignoreExistingToken">
        /// Если ignoreExistingToken равно true, запрашивает новый токен у сервера. В противном случае поведение зависит от того, существует ли токен.
        /// Если токен существует и его дата истечения не истекла, возвращает текущий токен, в противном случае запрашивает новый токен у сервера.
        /// </param>
        /// <returns>Возвращает oAuth токен доступа</returns>
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
        /// Получает oAuth токен доступа.
        /// Если токен существует и его дата истечения не истекла, возвращает текущий токен, в противном случае запрашивает новый токен у сервера.
        /// </summary>
        /// <returns>Возвращает oAuth токен доступа</returns>
        public OAuthToken GetAccessToken()
        {
            return GetAccessToken(false);
        }

        /// <summary>
        /// Выполняет задачи, определенные приложением, связанные с освобождением, удалением или сбросом неуправляемых ресурсов.
        /// </summary>
        public virtual void Dispose()
        {
        }
    }

    /// <summary>
    /// Успешный ответ содержит JSON OAuth 2.0 ответ со следующими параметрами.
    /// </summary>
    public class AzureTokenResponse
    {
        /// <summary>
        /// Запрашиваемый токен доступа. Вызываемая веб-служба может использовать этот токен для аутентификации в получающей веб-службе.
        /// </summary>
        public string access_token { get; set; }

        /// <summary>
        /// Указывает значение типа токена. Единственный тип, который поддерживает Azure AD - Bearer. Для получения дополнительной информации о токенах-п носителях 
        /// см. Рамки авторизации OAuth 2.0: Использование токена-п носителя (RFC 6750).
        /// </summary>
        public string token_type { get; set; }

        /// <summary>
        /// Как долго действителен токен доступа (в секундах).
        /// </summary>
        public int expires_in { get; set; }

        /// <summary>
        /// Как долго действителен токен доступа (в секундах).
        /// </summary>
        public int ext_expires_in { get; set; }

        /// <summary>
        /// Время, когда токен доступа истекает. 
        /// Дата представлена в виде числа секунд с 1970-01-01T00:00:00Z UTC до времени истечения.
        /// Это значение используется для определения срока действия кэшированных токенов.
        /// </summary>
        public int expires_on { get; set; }

        /// <summary>
        /// URI App ID получающей веб-службы.
        /// </summary>
        public string resource { get; set; }

        /// <summary>
        /// Если был возвращен токен доступа, этот параметр перечисляет области, для которых токен доступа действителен.
        /// </summary>
        public string scope { get; set; }

        /// <summary>
        /// Выдается, если оригинальный параметр области включал область openid.
        /// </summary>
        public string id_token { get; set; }

        /// <summary>
        /// Выдается, если оригинальный параметр области включал offline_access.
        /// </summary>
        public string refresh_token { get; set; }
    }
}

```

Следующие примеры кода показывают, как подключиться к службам Office 365, используя пользовательский провайдер токенов.

```csharp
ITokenProvider tokenProvider = new AzureROPCTokenProvider(
    "Tenant",
    "ClientId",
    "ClientSecret",
    "EMail",
    "Password",
    scopes);

// Подключение к SMTP серверу
using (SmtpClient client = new SmtpClient(
    "smtp.office365.com",
    587,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Подключение к IMAP серверу
using (ImapClient client = new ImapClient(
    "outlook.office365.com",
    993,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLImplicit))
{

}

// Подключение к POP3 серверу
using (Pop3Client client = new Pop3Client(
   "outlook.office365.com",
   995,
   "Test1@test.onmicrosoft.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}

// Подключение к EWS серверу
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
ICredentials credentials = new OAuthNetworkCredential(tokenProvider);
using (IEWSClient ewsClient = EWSClient.GetEWSClient(mailboxUri, credentials))
{

}
```