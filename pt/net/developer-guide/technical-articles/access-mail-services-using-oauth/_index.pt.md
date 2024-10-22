---
title: "Acessar Serviços de Email usando OAuth"
url: /pt/net/access-mail-services-using-oauth/
weight: 190
type: docs
---

O suporte ao OAuth 2.0 foi adicionado ao Aspose.Email e pode ser usado para acessar servidores **SMTP**, **POP3**, **IMAP** e **EWS**. Em geral, todos os servidores que suportam tokens de portador **OAuth 2.0** podem ser usados com Aspose.Email, mas nossos clientes de email foram testados com servidores de email do Google e servidores do Microsoft Office 365. O acesso ao servidor a partir do [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient), [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client), [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) e [EWSClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient) com OAuth pode ser implementado de 2 maneiras.

1. Fornecer o token de acesso diretamente no construtor do cliente de email. Nesse caso, o usuário deve entender que a vida útil dos tokens de acesso é limitada. Quando o token expira, o cliente de email não pode ser usado para acessar o servidor.  
2. Fornecer uma implementação personalizada do provedor de token com base na interface [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) no construtor do cliente de email. Nesse caso, o cliente verifica o tempo de expiração do token e solicita ao [ITokenProvider](https://apireference.aspose.com/email/net/aspose.email.clients/itokenprovider) um novo token de acesso quando o anterior expira. Dessa forma, o cliente atualiza os tokens periodicamente e pode trabalhar com o servidor por tempo ilimitado. Muitas vezes, os serviços suportam uma maneira simples de atualizar os tokens de acesso. Por exemplo, usando tokens de atualização nos serviços do Google ou o fluxo de autenticação ROPC na plataforma de identidade da Microsoft pode ser usado para implementar o provedor de token.

## **Configurar uma Conta no Servidor Apropriado**

Os seguintes artigos ajudam você a configurar contas para acessar serviços de email.

- Para [Office 365](https://docs.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth)
- Para [Gmail](https://developers.google.com/gmail/imap/imap-smtp)

## **Acessar Serviços de Email com os Tokens de Acesso**

Os seguintes exemplos de código mostram como se conectar a serviços de email usando tokens de acesso.

```csharp
// Conectando ao servidor SMTP
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    "accessToken",
    true,
    SecurityOptions.SSLExplicit))
{

}

// Conectando ao servidor IMAP
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   "accessToken",
   true,
   SecurityOptions.SSLImplicit))
{

}

// Conectando ao servidor POP3
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

## **Acessar Serviços de Email com os Provedores de Token**

Os seguintes exemplos de código mostram como se conectar a serviços de email usando um provedor de token.

```csharp
ITokenProvider tokenProvider = TokenProvider.Google.GetInstance(
    "ClientId",
    "ClientSecret",
    "RefreshToken");

// Conectando ao servidor SMTP
using (SmtpClient client = new SmtpClient(
    "smtp.gmail.com",
    587,
    "user1@gmail.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Conectando ao servidor IMAP
using (ImapClient client = new ImapClient(
   "imap.gmail.com",
   993,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.SSLImplicit))
{

}

// Conectando ao servidor POP3
using (Pop3Client client = new Pop3Client(
   "pop.gmail.com",
   995,
   "user1@gmail.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}
```

## **Implementação de Custom ITokenProvider para Office 365**

Você pode usar a implementação do provedor de token abaixo para acessar os serviços de email do Office 365.

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
    /// Provedor de token de credencial de senha de proprietário de recurso Azure (ROPC)
    /// https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
    /// https://portal.azure.com
    /// https://developer.microsoft.com/en-us/graph/graph-explorer/#
    /// analisador de token https://jwt.io
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
        /// Inicializa uma nova instância da classe <see cref="AzureROPCTokenProvider"/>
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
        /// Obtém o token de acesso oAuth. 
        /// </summary>
        /// <param name="ignoreExistingToken">
        /// Se ignoreExistingToken for verdadeiro, solicita um novo token de um servidor. Caso contrário, o comportamento depende
        /// de existir ou não o token. Se o token existir e sua data de expiração não tiver expirado, retorna o token atual, 
        /// caso contrário, solicita um novo token de um servidor.
        /// </param>
        /// <returns>Retorna o token de acesso oAuth</returns>
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
        /// Obtém o token de acesso oAuth.
        /// Se o token existir e sua data de expiração não tiver expirado, retorna o token atual, caso contrário, solicita um novo token de um servidor.
        /// </summary>
        /// <returns>Retorna o token de acesso oAuth</returns>
        public OAuthToken GetAccessToken()
        {
            return GetAccessToken(false);
        }

        /// <summary>
        /// Realiza tarefas definidas pela aplicação associadas à liberação, liberação ou redefinição de recursos não gerenciados.
        /// </summary>
        public virtual void Dispose()
        {
        }
    }

    /// <summary>
    /// Uma resposta de sucesso contém uma resposta JSON OAuth 2.0 com os seguintes parâmetros.
    /// </summary>
    public class AzureTokenResponse
    {
        /// <summary>
        /// O token de acesso solicitado. O serviço web que chama pode usar este token para se autenticar no serviço web receptor.
        /// </summary>
        public string access_token { get; set; }

        /// <summary>
        /// Indica o valor do tipo de token. O único tipo que o Azure AD suporta é Bearer. Para mais informações sobre tokens de portador, 
        /// consulte O Quadro de Autorização OAuth 2.0: Uso de Token Bearer (RFC 6750).
        /// </summary>
        public string token_type { get; set; }

        /// <summary>
        /// Quanto tempo o token de acesso é válido (em segundos).
        /// </summary>
        public int expires_in { get; set; }

        /// <summary>
        /// Quanto tempo o token de acesso é válido (em segundos).
        /// </summary>
        public int ext_expires_in { get; set; }

        /// <summary>
        /// O momento em que o token de acesso expira. 
        /// A data é representada como o número de segundos desde 1970-01-01T00:00:00Z UTC até o horário de expiração.
        /// Este valor é usado para determinar a vida útil dos tokens em cache.
        /// </summary>
        public int expires_on { get; set; }

        /// <summary>
        /// O URI do ID do aplicativo do serviço web receptor.
        /// </summary>
        public string resource { get; set; }

        /// <summary>
        /// Se um token de acesso foi retornado, este parâmetro lista os escopos para os quais o token de acesso é válido.
        /// </summary>
        public string scope { get; set; }

        /// <summary>
        /// Emitido se o parâmetro de escopo original incluiu o escopo openid.
        /// </summary>
        public string id_token { get; set; }

        /// <summary>
        /// Emitido se o parâmetro de escopo original incluiu o offline_access.
        /// </summary>
        public string refresh_token { get; set; }
    }
}
```

Os próximos exemplos de código mostram como se conectar aos serviços Office 365 usando o provedor de token personalizado.

```csharp
ITokenProvider tokenProvider = new AzureROPCTokenProvider(
    "Tenant",
    "ClientId",
    "ClientSecret",
    "EMail",
    "Password",
    scopes);

// Conectando ao servidor SMTP
using (SmtpClient client = new SmtpClient(
    "smtp.office365.com",
    587,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLExplicit))
{

}

// Conectando ao servidor IMAP
using (ImapClient client = new ImapClient(
    "outlook.office365.com",
    993,
    "Test1@test.onmicrosoft.com",
    tokenProvider,
    SecurityOptions.SSLImplicit))
{

}

// Conectando ao servidor POP3
using (Pop3Client client = new Pop3Client(
   "outlook.office365.com",
   995,
   "Test1@test.onmicrosoft.com",
   tokenProvider,
   SecurityOptions.Auto))
{

}

// Conectando ao servidor EWS
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
ICredentials credentials = new OAuthNetworkCredential(tokenProvider);
using (IEWSClient ewsClient = EWSClient.GetEWSClient(mailboxUri, credentials))
{

}
```