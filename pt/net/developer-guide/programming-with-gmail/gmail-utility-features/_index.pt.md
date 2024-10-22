---
title: "Recursos Utilitários do Gmail"
url: /pt/net/gmail-utility-features/
weight: 10
type: docs
---

## **Trabalhando com Consulta FreeBusy**

Aspose.Email fornece um mecanismo de consulta para verificar se um compromisso está agendado de acordo com os critérios. A classe FreebusyQuery é fornecida para esse propósito e permite preparar uma consulta para um calendário específico.

### **Consultando um calendário**

Este exemplo de código demonstra a funcionalidade de consultar um calendário. As seguintes tarefas são executadas neste exemplo:

1. Criar e inserir um calendário
1. Criar um compromisso
1. Inserir o compromisso
1. Preparar uma FreeBusyQuery
1. Obter a FreebusyResponse

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET

// Use as classes GoogleUser e GoogleOAuthHelper abaixo para receber um token de acesso
using (IGmailClient client = GmailClient.GetInstance(accessToken, user.Email))
{
    // Inicializar item de calendário
    Aspose.Email.Clients.Google.Calendar calendar1 = new Aspose.Email.Clients.Google.Calendar("resumo - " + Guid.NewGuid().ToString(), null, null, "Europe/Kiev");

    // Inserir calendário e obter o id do calendário recém-inserido e buscar o mesmo calendário usando o id do calendário
    string id = client.CreateCalendar(calendar1);
    Aspose.Email.Clients.Google.Calendar cal1 = client.FetchCalendar(id);
    string calendarId1 = cal1.Id;
    try
    {
        // Obter lista de compromissos no calendário recém-inserido. Deve ser zero
        Appointment[] appointments = client.ListAppointments(calendarId1);
        if (appointments.Length != 0)
        {
            Console.WriteLine("Número incorreto de compromissos");
            return;
        }

        // Criar um novo compromisso e calcular o horário de início e término do compromisso
        DateTime startDate = DateTime.Now;
        DateTime endDate = startDate.AddHours(1);

        // Criar lista de participantes para o compromisso
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.Add("user1@domain.com");
        attendees.Add("user2@domain.com");

        // Criar compromisso
        Appointment app1 = new Appointment("Localização - " + Guid.NewGuid().ToString(), startDate, endDate, "user2@domain.com", attendees);
        app1.Summary = "Resumo - " + Guid.NewGuid().ToString();
        app1.Description = "Descrição - " + Guid.NewGuid().ToString();
        app1.StartTimeZone = "Europe/Kiev";
        app1.EndTimeZone = "Europe/Kiev";

        // Inserir o compromisso recém-criado e obter o mesmo em caso de inserção bem-sucedida
        Appointment app2 = client.CreateAppointment(calendarId1, app1);

        // Criar consulta Freebusy definindo min/max tempo e fuso horário
        FreebusyQuery query = new FreebusyQuery();
        query.TimeMin = DateTime.Now.AddDays(-1);
        query.TimeMax = DateTime.Now.AddDays(1);
        query.TimeZone = "Europe/Kiev";

        // Definir item de calendário para busca e obter a resposta da consulta contendo
        query.Items.Add(cal1.Id);
        FreebusyResponse resp = client.GetFreebusyInfo(query);
        // Deletar o compromisso
        client.DeleteAppointment(calendarId1, app2.UniqueId);
    }
    finally
    {
        // Deletar o calendário
        client.DeleteCalendar(cal1.Id);
    }
}
```

## **Criando um projeto no Google Developer Console**

Um projeto deve ser criado no Google Developer Console para um usuário com conta Gmail. Na página API e autenticação -> Credenciais do projeto Google, informações como Client ID e Client Secret devem ser anotadas. Essa informação, junto com o nome de usuário e a senha da conta Gmail, será necessária para executar o código, por exemplo, Google Calendar, listas de controle de acesso, compromissos, contatos, configurações etc. nesta seção.

### **Passos para criar um projeto no Google Developer Console**

Abaixo está um tutorial passo a passo para criar um projeto no Google Developer Console.

1. Vá para o link <https://cloud.google.com/console/project> e faça login usando suas credenciais do Gmail

|![todo:image_alt_text](gmail-utility-features_1.png)|
| :- |
2. Marque a caixa de seleção "Eu li e concordo com todos os Termos de Serviço dos produtos do Google Cloud Platform." e pressione o botão Criar

|![todo:image_alt_text](gmail-utility-features_2.png)|
| :- |
3. "Verificação por SMS" será solicitado. Pressione o botão continuar:

|![todo:image_alt_text](gmail-utility-features_3.png)|
| :- |
4. Digite o nome do seu país e insira o número do celular. Pressione o botão: Enviar Código de Verificação

|![todo:image_alt_text](gmail-utility-features_4.png)|
| :- |
5. Insira o código de verificação recebido no seu celular.

|![todo:image_alt_text](gmail-utility-features_5.png)|
| :- |
6. Na lista de APIs e autenticação \ APIs, ative o status da API do Calendário e da API de Contatos. Desative todas as outras.

|![todo:image_alt_text](gmail-utility-features_6.png)|
| :- |
7. Na API e autenticação -> Credenciais, pressione o botão "CRIAR NOVO CLIENTE ID" na seção "OAuth". Selecione "Aplicativo instalado" e "Outro" nas opções dadas, e pressione o botão "Criar Client ID". Anote o Client ID e o Client Secret aqui, que serão utilizados nos códigos de exemplo nesta seção.

|![todo:image_alt_text](gmail-utility-features_7.png)|
| :- |

## **Classes Auxiliares**

As seguintes classes auxiliares são necessárias para executar os exemplos de código nesta seção. Essas classes `GoogleOAuthHelper` e `GoogleUser` são apenas para simplificação da demonstração. Os métodos nessas classes usam uma estrutura não pública de páginas da web que pode mudar a qualquer momento.

### **Classe GoogleOAuthHelper**

O seguinte trecho de código mostra como implementar a classe `GoogleOAuthHelper`.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET

using Newtonsoft.Json;
using System;
using System.Collections.Generic;
using System.IO;
using System.Net;
using System.Security.Cryptography;
using System.Text;

/// <summary>
/// Console do desenvolvedor:
/// https://console.cloud.google.com/projectselector2
/// Documentação:
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
        "https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcalendar" + // Calendário
        "+" +
        "https%3A%2F%2Fwww.google.com%2Fm8%2Ffeeds%2F" + // Contatos
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

**Google OAuth Helper** deve ser usado da seguinte maneira:

1. Uma URL de código de autorização deve ser gerada primeiro.
1. Abra a URL em um navegador e complete todas as operações. Como resultado, você receberá um código de autorização.
1. Use o código de autorização para receber um token de atualização.
1. Quando o token de atualização existir, você pode usá-lo para recuperar tokens de acesso.

```csharp
GoogleUser user = new GoogleUser(email, password, clientId, clientSecret);

string authUrl = GoogleOAuthHelper.GetAuthorizationCodeUrl(user);

Console.WriteLine("Vá para a seguinte URL e obtenha seu código de autorização:");
Console.WriteLine(authUrl);
Console.WriteLine();

Console.WriteLine("Insira o código de autorização:");
string authorizationCode = Console.ReadLine();
Console.WriteLine();

TokenResponse tokenInfo = GoogleOAuthHelper.GetAccessTokenByAuthCode(authorizationCode, user);
Console.WriteLine("O token de atualização foi recebido:");
Console.WriteLine(tokenInfo.RefreshToken);
Console.WriteLine();

user.RefreshToken = tokenInfo.RefreshToken;
tokenInfo = GoogleOAuthHelper.GetAccessTokenByRefreshToken(user);
Console.WriteLine("O novo token de acesso foi recebido:");
Console.WriteLine(tokenInfo.AccessToken);
Console.WriteLine();
```

### **Classe GoogleUser**

O seguinte trecho de código mostra como implementar a classe `GoogleUser`.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET

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

### **Classe TokenResponse**

O seguinte trecho de código mostra como implementar a classe `TokenResponse`.

```csharp
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-.NET

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