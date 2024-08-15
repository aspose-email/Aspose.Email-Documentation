---
title: "Trabajando con IMAPClient de forma asincrónica"
url: /es/net/working-with-imapclient-asynchronously/
weight: 70
type: docs
---


El trabajo con los mensajes se puede realizar de forma asincrónica mediante Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). En este artículo se muestra la recuperación de mensajes de un buzón de forma asincrónica. En este artículo también se muestra cómo enumerar los mensajes proporcionando criterios de búsqueda mediante [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Se mostrará por separado cómo interrumpir una operación con mensajes de correo electrónico iniciados mediante un patrón asincrónico basado en tareas ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)) método.

## **Recuperar mensajes de forma asincrónica**

El siguiente fragmento de código muestra cómo recuperar mensajes de forma asincrónica.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrievingMessagesasynchronously-RetrievingMessagesasynchronously.cs" >}}

## **Listar mensajes de forma asincrónica con MailQuery**

The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) La clase se puede usar para especificar los criterios de búsqueda para recuperar una lista específica de mensajes de forma asincrónica, como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListMessagesasynchronously-ListMessagesasynchronouslyWithMailQuery.cs" >}}

## **Cómo interrumpir un método TAP**

A partir de .NET Framework 4.5, puede usar métodos asincrónicos implementados de acuerdo con el modelo TAP. El siguiente fragmento de código muestra cómo agregar muchos mensajes mediante el método de patrón asincrónico basado en tareas denominado `AppendMessagesAsync` y luego interrumpir este proceso después de un tiempo.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

List<MailMessage> mailMessages = new List<MailMessage>();

// create mail messages
for (int i = 0; i < 100; i++)
    mailMessages.Add(new MailMessage(senderEmail, receiverEmail, $"Message #{i}", "Text"));

using (ImapClient client = new ImapClient(host, 993, senderEmail, password, SecurityOptions.SSLImplicit))
{
    CancellationTokenSource cancellationTokenSource = new CancellationTokenSource();
    AutoResetEvent autoResetEvent = new AutoResetEvent(false);
    Exception exception = null;

    ThreadPool.QueueUserWorkItem(delegate
    {
        try
        {
            // start uploading the messages
            var task = client.AppendMessagesAsync(mailMessages, cancellationTokenSource.Token);
            AppendMessagesResult appendMessagesResult = task.GetAwaiter().GetResult();
            Console.WriteLine("All messages have been appended.");
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

    // stop uploading the messages
    cancellationTokenSource.Cancel();
    autoResetEvent.WaitOne();

    foreach (MailMessage mailMessage in mailMessages)
        mailMessage.Dispose();

    if (exception is OperationCanceledException)
        Console.WriteLine("Operation has been interrupted: " + exception.Message);
}
```
## **Envío de mensajes de forma asincrónica**

Enviar correos electrónicos de forma asincrónica es muy cómodo, ya que el proceso no bloquea la ejecución del programa o hilo. En lugar de esperar a que se envíe el correo electrónico antes de continuar con otras tareas, el programa puede seguir ejecutándose mientras el correo electrónico se envía en segundo plano.

Las siguientes funciones te ayudarán a implementar el envío asincrónico en tu proyecto:

- [IAsyncImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Permite a las aplicaciones acceder a los mensajes y manipularlos mediante el Protocolo de acceso a mensajes de Internet (IMAP).

- [ImapClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Crea una nueva instancia del `Aspose.Email.Clients.Imap.ImapClient` class

El ejemplo de código que se muestra a continuación muestra cómo enumerar los mensajes en segundo plano:

```cs
// Authenticate the client to obtain necessary permissions
static readonly string tenantId = "YOU_TENANT_ID";
static readonly string clientId = "YOU_CLIENT_ID";
static readonly string redirectUri = "http://localhost";
static readonly string username = "username";
static readonly string[] scopes = { "https://outlook.office.com/IMAP.AccessAsUser.All" };

// Use the ImapAsync method for asynchronous operations
static async Task Main(string[] args)
{
    await ImapAsync();
    Console.ReadLine();
}

// Establish the connection with the server
// Create an instance of the ImapClient asynchronously using the CreateAsync method
// Select the Inbox folder using SelectFolderAsync method to complete and fetch the list of email messages asynchronously using the ListMessagesAsync method.
static async Task ImapAsync()
{
    var tokenProvider = new TokenProvider(clientId, tenantId, redirectUri, scopes);
    var client = ImapClient.CreateAsync("outlook.office365.com", username, tokenProvider, 993).GetAwaiter().GetResult();
    await client.SelectFolderAsync(ImapFolderInfo.InBox);
    var messages = await client.ListMessagesAsync();
    Console.WriteLine("Messages :" + messages.Count);
}

// Token provider implementation
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
            Console.WriteLine($"Error acquiring access token: {ex}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex}");
        }

        return null;
    }

    public void Dispose()
    {

    }
}
```
## **Cancelación de operaciones asincrónicas**

En ocasiones, es posible que tenga que detener las operaciones asincrónicas. Para ello, nuestra biblioteca ofrece la cancelación de operaciones asincrónicas mediante el uso del parámetro cancellationToken. Al invocar un método asincrónico que admite la cancelación, puedes pasar una instancia de CancellationToken como parámetro. El cancellationToken se usa para señalar y controlar la cancelación de la operación.

Para habilitar la cancelación, primero debes crear una instancia de CancellationTokenSource que proporcione el CancellationToken. A continuación, pasa el cancellationToken al método asíncrono, lo que le permitirá comprobar si hay solicitudes de cancelación durante la ejecución.

Este es un ejemplo que demuestra la cancelación con CancellationToken:

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
