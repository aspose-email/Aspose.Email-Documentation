---
title: "Trabajando con ImapClient de forma asincrónica"
url: /es/net/working-with-imapclient-asynchronously/
weight: 70
type: docs
---

Trabajar con mensajes se puede realizar de forma asincrónica utilizando el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) de Aspose.Email. Este artículo muestra cómo recuperar mensajes de un buzón de forma asincrónica. Este artículo también muestra cómo listar mensajes proporcionando criterios de búsqueda utilizando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Se mostrará por separado cómo interrumpir una operación con mensajes de correo electrónico iniciada por un método basado en patrones asincrónicos ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)).

## **Recuperar mensajes de forma asincrónica**

El siguiente fragmento de código muestra cómo recuperar mensajes de forma asincrónica.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrievingMessagesasynchronously-RetrievingMessagesasynchronously.cs" >}}

## **Listar mensajes de forma asincrónica con MailQuery**

La clase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) se puede usar para especificar criterios de búsqueda para recuperar una lista específica de mensajes de forma asincrónica, como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListMessagesasynchronously-ListMessagesasynchronouslyWithMailQuery.cs" >}}

## **Cómo interrumpir un método TAP**

A partir de .NET Framework 4.5, puede utilizar métodos asincrónicos implementados de acuerdo con el modelo TAP. El siguiente fragmento de código muestra cómo agregar muchos mensajes utilizando el método de patrón asincrónico basado en tareas llamado `AppendMessagesAsync` y luego interrumpir este proceso después de un tiempo.

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

Enviar correos electrónicos de forma asincrónica es muy conveniente, ya que el proceso no bloquea la ejecución del programa o del hilo. En lugar de esperar a que se envíe el correo electrónico antes de continuar con otras tareas, el programa puede seguir ejecutándose mientras se envía el correo electrónico en segundo plano.

Las siguientes características te ayudarán a implementar el envío asincrónico en tu proyecto:

- [IAsyncImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Permite a las aplicaciones acceder y manipular mensajes utilizando el Protocolo de Acceso a Mensajes de Internet (IMAP).

- [ImapClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Crea una nueva instancia de la clase `Aspose.Email.Clients.Imap.ImapClient`.

El siguiente ejemplo de código demuestra cómo listar mensajes en segundo plano:

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

A veces puedes enfrentar la necesidad de detener operaciones asincrónicas. Para este propósito, nuestra biblioteca ofrece la cancelación de operaciones asincrónicas a través del uso del parámetro CancellationToken. Al invocar un método asincrónico que soporta la cancelación, puedes pasar una instancia de CancellationToken como parámetro. El CancellationToken se utiliza para señalizar y controlar la cancelación de la operación.

Para habilitar la cancelación, primero necesitas crear una instancia de CancellationTokenSource que proporciona el CancellationToken. Luego, pasa el CancellationToken al método asincrónico, permitiendo que verifique las solicitudes de cancelación durante la ejecución.

Aquí hay un ejemplo que demuestra la cancelación utilizando CancellationToken:

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