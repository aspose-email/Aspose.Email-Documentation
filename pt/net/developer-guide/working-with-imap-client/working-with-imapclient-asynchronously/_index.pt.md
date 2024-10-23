---
title: "Trabalhando com ImapClient de forma assíncrona"
url: /pt/net/trabalhando-com-imapclient-de-forma-assincrona/
weight: 70
type: docs
---


Trabalhar com mensagens pode ser realizado de forma assíncrona usando o Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Este artigo mostra como recuperar mensagens de uma caixa de entrada de forma assíncrona. Este artigo também mostra como listar mensagens fornecendo critérios de pesquisa usando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Será mostrado separadamente como interromper uma operação com mensagens de e-mail iniciada por um padrão assíncrono baseado em tarefas ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)).

## **Recuperar Mensagens de forma assíncrona**

O seguinte trecho de código mostra como recuperar mensagens de forma assíncrona.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrievingMessagesasynchronously-RetrievingMessagesasynchronously.cs" >}}

## **Listar Mensagens de forma assíncrona com MailQuery**

A classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) pode ser usada para especificar critérios de pesquisa para recuperar uma lista específica de mensagens de forma assíncrona, como mostrado no seguinte exemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListMessagesasynchronously-ListMessagesasynchronouslyWithMailQuery.cs" >}}

## **Como Interromper um Método TAP**

A partir do .NET Framework 4.5, você pode usar métodos assíncronos implementados de acordo com o modelo TAP. O trecho de código abaixo mostra como anexar muitas mensagens usando o método de padrão assíncrono baseado em tarefas chamado `AppendMessagesAsync` e, em seguida, interromper esse processo após um tempo.

```csharp
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-.NET

List<MailMessage> mailMessages = new List<MailMessage>();

// criar mensagens de e-mail
for (int i = 0; i < 100; i++)
    mailMessages.Add(new MailMessage(senderEmail, receiverEmail, $"Mensagem #{i}", "Texto"));

using (ImapClient client = new ImapClient(host, 993, senderEmail, password, SecurityOptions.SSLImplicit))
{
    CancellationTokenSource cancellationTokenSource = new CancellationTokenSource();
    AutoResetEvent autoResetEvent = new AutoResetEvent(false);
    Exception exception = null;

    ThreadPool.QueueUserWorkItem(delegate
    {
        try
        {
            // começar a anexar as mensagens
            var task = client.AppendMessagesAsync(mailMessages, cancellationTokenSource.Token);
            AppendMessagesResult appendMessagesResult = task.GetAwaiter().GetResult();
            Console.WriteLine("Todas as mensagens foram anexadas.");
        }
        catch (Exception e)
        {
            exception = e;
        }
        finally
        {
            autoResetEvent.Set();
        }
    });

    Thread.Sleep(5000);

    // parar de anexar as mensagens
    cancellationTokenSource.Cancel();
    autoResetEvent.WaitOne();

    foreach (MailMessage mailMessage in mailMessages)
        mailMessage.Dispose();

    if (exception is OperationCanceledException)
        Console.WriteLine("A operação foi interrompida: " + exception.Message);
}
```
## **Enviando Mensagens de forma assíncrona**

Enviar e-mails de forma assíncrona é muito conveniente, pois o processo não bloqueia a execução do programa ou da thread. Em vez de esperar que o e-mail seja enviado antes de prosseguir com outras tarefas, o programa pode continuar sendo executado enquanto o e-mail está sendo enviado em segundo plano.

Os seguintes recursos ajudarão você a implementar o envio assíncrono em seu projeto:

- [IAsyncImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Permite que aplicações acessem e manipulem mensagens usando o Protocolo de Acesso a Mensagens pela Internet (IMAP).

- [ImapClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Cria uma nova instância da classe `Aspose.Email.Clients.Imap.ImapClient`.

O exemplo de código abaixo demonstra como listar mensagens em segundo plano:

```cs
// Autentica o cliente para obter as permissões necessárias
static readonly string tenantId = "SEU_ID_DE_TENANT";
static readonly string clientId = "SEU_ID_DE_CLIENTE";
static readonly string redirectUri = "http://localhost";
static readonly string username = "username";
static readonly string[] scopes = { "https://outlook.office.com/IMAP.AccessAsUser.All" };

// Use o método ImapAsync para operações assíncronas
static async Task Main(string[] args)
{
    await ImapAsync();
    Console.ReadLine();
}

// Estabeleça a conexão com o servidor
// Crie uma instância do ImapClient de forma assíncrona usando o método CreateAsync
// Selecione a pasta Caixa de Entrada usando o método SelectFolderAsync para completar e buscar a lista de mensagens de e-mail de forma assíncrona usando o método ListMessagesAsync.
static async Task ImapAsync()
{
    var tokenProvider = new TokenProvider(clientId, tenantId, redirectUri, scopes);
    var client = ImapClient.CreateAsync("outlook.office365.com", username, tokenProvider, 993).GetAwaiter().GetResult();
    await client.SelectFolderAsync(ImapFolderInfo.InBox);
    var messages = await client.ListMessagesAsync();
    Console.WriteLine("Mensagens :" + messages.Count);
}

// Implementação do provedor de token
public class TokenProvider : IAsyncTokenProvider
{
    private readonly PublicClientApplicationOptions _pcaOptions;
    private readonly string[] _scopes;

    public TokenProvider(string clientId, string tenantId, string redirectUri, string[] scopes)
    {
        _pcaOptions = new PublicClientApplicationOptions
        {
            ClientId = clientId,
            TenantId = tenantId,
            RedirectUri = redirectUri
        };

        _scopes = scopes;
    }

    public async Task<OAuthToken> GetAccessTokenAsync(bool ignoreExistingToken = false, CancellationToken cancellationToken = default)
    {

        var pca = PublicClientApplicationBuilder
            .CreateWithApplicationOptions(_pcaOptions).Build();

        try
        {
            var result = await pca.AcquireTokenInteractive(_scopes)
                .WithUseEmbeddedWebView(false)
                .ExecuteAsync(cancellationToken);

            return new OAuthToken(result.AccessToken);
        }
        catch (MsalException ex)
        {
            Console.WriteLine($"Erro ao adquirir token de acesso: {ex}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Erro: {ex}");
        }

        return null;
    }

    public void Dispose()
    {

    }
}
```
## **Cancelamento para Operações Assíncronas**

Às vezes, você pode enfrentar a necessidade de interromper operações assíncronas. Para isso, nossa biblioteca oferece o cancelamento de operações assíncronas através do uso do parâmetro CancellationToken. Ao invocar um método assíncrono que suporta cancelamento, você pode passar uma instância de CancellationToken como parâmetro. O CancellationToken é usado para sinalizar e controlar a interrupção da operação.

Para habilitar o cancelamento, você precisa primeiro criar uma instância de CancellationTokenSource que fornece o CancellationToken. Em seguida, passe o CancellationToken para o método assíncrono, permitindo que ele verifique solicitações de cancelamento durante a execução.

Aqui está um exemplo que demonstra o cancelamento usando CancellationToken:

```cs
CancellationTokenSource tokenSource = new CancellationTokenSource();
AppendMessagesResult appendMessagesResult = null;
AutoResetEvent autoResetEvent = new AutoResetEvent(false);
ThreadPool.QueueUserWorkItem(delegate(object state)
    {
        try
        {
            appendMessagesResult = imapClient.AppendMessagesAsync(mmList, tokenSource.Token).GetAwaiter().GetResult();
        }
        catch (Exception ex)
        {

        }
        finally
        {
            autoResetEvent.Set();
        }
    });

tokenSource.Cancel();
autoResetEvent.WaitOne();
```