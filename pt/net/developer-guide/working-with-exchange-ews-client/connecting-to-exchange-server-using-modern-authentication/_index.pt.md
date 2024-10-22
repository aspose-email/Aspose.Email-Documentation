---
title: "Conectando ao Exchange Server usando Autenticação Moderna"
url: /pt/net/conectando-ao-exchange-server-usando-autenticacao-moderna/
weight: 5
type: docs
---

A Autenticação Moderna agora está habilitada por padrão para todos os novos locatários do Microsoft 365/Azure, pois esse protocolo é mais seguro do que a Autenticação Básica, que foi descontinuada. 
A Autenticação Moderna é baseada na Biblioteca de Autenticação do Active Directory e no OAuth 2.0. Ela utiliza tokens com tempo limitado, e os aplicativos não armazenam as credenciais do usuário.

## **Configurações pré-requisitos**

Para usar a Autenticação Moderna, certifique-se de que ela está habilitada. No entanto, para locatários criados antes de 1º de agosto de 2017, a autenticação moderna está desativada por padrão. 
No [centro de administração do Microsoft 365](https://admin.microsoft.com/), vá em **Configurações > Configurações da Organização > Autenticação Moderna**. No **painel de autenticação moderna** que aparece, você pode identificar os protocolos que não exigem mais a autenticação básica. 
Para novos locatários do Microsoft 365 no Azure, a Autenticação Básica está desabilitada por padrão para todos os aplicativos. Portanto, o texto será exibido nesta seção.

> Sua organização tem os padrões de segurança habilitados, o que significa que a autenticação moderna ao Exchange Online é obrigatória, e as conexões de autenticação básica estão bloqueadas. Você deve desativar os padrões de segurança no portal do Azure antes de alterar qualquer configuração aqui.

Você pode habilitar o suporte à Autenticação Básica para o locatário no portal do [Azure](https://aad.portal.azure.com/), vá em **Azure Active Directory > Propriedades > Gerenciar padrões de segurança > Habilitar padrões de segurança > Não**. 
Para mais informações, consulte o [Artigo da Documentação da Microsoft](https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## **Registro de aplicativo com o Azure Active Directory**

É necessário realizar o registro do aplicativo com o Azure Active Directory. 
Existem dois tipos de permissões que podem ser usadas para acessar as caixas de correio com seu aplicativo. Escolha um tipo específico de permissão, dependendo do aplicativo que você está criando:

- Aplicativos que usam **permissões Delegadas** têm um usuário autenticado presente. Em outras palavras, quando você se conecta ao serviço, uma janela de diálogo aparece para um nome de usuário e uma senha. O aplicativo nunca pode ter mais privilégios do que um usuário autenticado.
- Aplicativos que usam **permissões de Aplicativo** funcionam sem um usuário autenticado presente. Por exemplo, esses são aplicativos que funcionam como serviços em segundo plano ou daemons. Somente um administrador pode consentir as permissões de aplicativo.

Além disso, consulte o [Artigo da Documentação da Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth) para mais informações.

O procedimento de registro depende do tipo de permissão selecionado. Para registrar seu aplicativo, consulte o [Artigo da Documentação da Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth#register-your-application).

## **Usar autenticação moderna com EwsClient**

Depois de registrar o aplicativo, podemos nos concentrar em escrever o código, que consistirá nas seguintes partes:

 - Obter o token de autorização.
 - Usar o token para autenticar.

### Obtendo o token de autorização

Para obter o token, usaremos a [Microsoft Authentication Library (MSAL) for .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Os seguintes são os passos para obter o token de autorização.

 - Adicione o [pacote nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contém os binários do MSAL.NET.
 - Crie uma classe AccessParameters para armazenar as credenciais.
 - Crie um método aceitando os parâmetros de acesso e usando o MSAL.NET para obter um token de acesso.

Os seguintes exemplos de código dependerão do tipo de autenticação escolhida.

**Obter um token com autenticação delegada**

```csharp
public class AccessParameters
{
    public string TenantId { get; set; }
    public string ClientId { get; set; }
    public string RedirectUri { get; set; } = "http://localhost";
    public string[] Scopes { get; set; } = { "https://outlook.office365.com/EWS.AccessAsUser.All" };
}

public static async Task<string> GetAccessToken(AccessParameters accessParameters)
{
    var pca = PublicClientApplicationBuilder
                            .Create(accessParameters.ClientId)
                            .WithTenantId(accessParameters.TenantId)
                            .WithRedirectUri(ccessParameters.RedirectUri)
                            .Build();

    var result = await pca.AcquireTokenInteractive(accessParameters.Scopes)
        .WithUseEmbeddedWebView(false)
        .ExecuteAsync();

    return result.AccessToken;
}

```
**Obter um token com autenticação de aplicativo**

```csharp
public class AccessParameters
{
    public string TenantId { get; set; }
    public string ClientId { get; set; }
    public string ClientSecret { get; set; }
    public string[] Scopes { get; set; } = { "https://outlook.office365.com/.default" };
}

public static async Task<string> GetAccessToken(AccessParameters accessParameters)
{
    var cca = ConfidentialClientApplicationBuilder
        .Create(accessParameters.ClientId)
        .WithClientSecret(accessParameters.ClientSecret)
        .WithTenantId(accessParameters.TenantId)
        .Build();

    var result = await cca.AcquireTokenForClient(accessParameters.Scopes).ExecuteAsync();

    return result.AccessToken;
}

```

### Usando o token para autenticar

Depois disso, quando tivermos obtido um token com sucesso, vamos inicializar o [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

**Usando o token com autenticação delegada**

```csharp
NetworkCredential credentials = new OAuthNetworkCredential(accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Experimente!**
Execute o projeto simples [EWSModernAuthenticationDelegated](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationDelegated), conecte-se ao Microsoft 365 com autenticação delegada e leia sua Caixa de Entrada.
{{% /alert %}}

**Usando o token com autenticação de aplicativo**

```csharp
// Use o nome de usuário do Microsoft365 e o token de acesso
NetworkCredential credentials = new OAuthNetworkCredential(username, accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Experimente!**
Execute o projeto simples [EWSModernAuthenticationApp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationApp), conecte-se ao Microsoft 365 com autenticação de aplicativo e leia sua Caixa de Entrada.
{{% /alert %}}

## **Usar Autenticação Moderna com clientes IMAP, POP ou SMTP**

O acesso IMAP, POP, SMTP via permissões de aplicativo não é suportado. Em outras palavras, a autenticação delegada é a única suportada.

O procedimento de registro do aplicativo com o Azure Active Directory está definido [acima](https://blog.aspose.com/email/connect-to-microsoft365-mailbox-using-modern-authentication-in-c-.net/#App-registration-with-Azure-Active-Directory).

### Usar o centro de administração do Microsoft 365 para habilitar ou desabilitar IMAP, POP, SMTP AUTH em caixas de correio específicas

 - Abra o [centro de administração do Microsoft 365](https://admin.microsoft.com/) e vá para **Usuários > Usuários ativos**.
 - Selecione o usuário e, no painel que aparece, clique em **Email**.
 - Na seção **Aplicativos de Email**, clique em **Gerenciar aplicativos de email**.
 - Verifique a configuração **IMAP, POP, SMTP Autenticado**: desmarcado = desativado, marcado = ativado.
 - Clique em **Salvar alterações**.

### Adicionando código para obter um token de autenticação de um servidor de tokens

Certifique-se de especificar os escopos completos, incluindo URLs de recursos do Outlook.

IMAP: https://outlook.office.com/IMAP.AccessAsUser.All
POP: https://outlook.office.com/POP.AccessAsUser.All
SMTP: https://outlook.office.com/SMTP.Send

Para obter o token, usaremos a [Microsoft Authentication Library (MSAL) for .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Os seguintes são os passos para obter o token de autorização.

- Adicione o [pacote nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contém os binários do MSAL.NET.
- Crie uma classe AccessParameters para armazenar as credenciais.
- Crie um método aceitando os parâmetros de acesso e usando o MSAL.NET para obter um token de acesso.

```csharp
public class AccessParameters
{
    public string TenantId { get; set; }
    public string ClientId { get; set; }
    public string RedirectUri { get; set; } = "http://localhost";
    public string[] Scopes { get; set; } = { 
        "https://outlook.office.com/IMAP.AccessAsUser.All", 
        "https://outlook.office.com/SMTP.Send" };
}

public static async Task<string> GetAccessToken(AccessParameters accessParameters)
{
    var pca = PublicClientApplicationBuilder
                            .Create(accessParameters.ClientId)
                            .WithTenantId(accessParameters.TenantId)
                            .WithRedirectUri(ccessParameters.RedirectUri)
                            .Build();

    var result = await pca.AcquireTokenInteractive(accessParameters.Scopes)
        .WithUseEmbeddedWebView(false)
        .ExecuteAsync();

    return result.AccessToken;
}

```

### Usando o token para autenticar

Depois disso, quando tivermos obtido um token com sucesso, vamos inicializar o [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
var imapClient = new ImapClient(
    "outlook.office365.com", 
    993, 
    username, 
    accessToken, 
    true);

```
Da mesma forma, a inicialização do [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) será a seguinte.

```csharp
var smtpClient = new SmtpClient(
    "smtp.office365.com",
    587, 
    username,
    accessToken, 
    true);

```

{{% alert %}}
**Experimente!**
Execute o projeto simples [EWSModernAuthenticationImapSmtp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationImapSmtp), conecte-se ao Microsoft 365 via IMAP e SMTP e leia sua Caixa de Entrada.
{{% /alert %}}

## **Retornar o ID da Solicitação do Cliente**

A propriedade [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) foi adicionada ao EWSClient para sua conveniência, a fim de especificar se o ID da solicitação do cliente deve ser retornado na resposta das chamadas dos Serviços Web do Exchange (EWS). O ID da solicitação do cliente é um identificador único que você pode definir para cada solicitação EWS enviada pelo seu aplicativo. Ao definir a propriedade [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) como *true*, você indica que deseja que o ID da solicitação do cliente seja incluído na resposta do servidor EWS. Isso pode ser útil para rastrear e correlacionar solicitações e respostas em cenários onde múltiplas solicitações são feitas e processadas de forma assíncrona.

O seguinte trecho de código mostra como a propriedade pode ser utilizada:

```cs
using (IEWSClient client = TestUtil.CreateEWSClient(user))
{
    // O cliente irá criar um ID aleatório e passá-lo para o servidor.
	// O servidor deve incluir esse ID no cabeçalho request-id de todas as respostas.
    client.ReturnClientRequestId = true;
    
	client.LogFileName = "ews.log";
    client.GetMailboxInfo();
}
```