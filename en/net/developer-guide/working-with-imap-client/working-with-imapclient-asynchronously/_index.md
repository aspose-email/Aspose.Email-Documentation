---
title: Working with ImapClient asynchronously
type: docs
weight: 70
url: /net/working-with-imapclient-asynchronously/
---


Working with messages can be performed asynchronously by using the Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). This article shows retrieving messages from a mailbox asynchronously. This article also shows how to list messages by providing search criteria using [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). It will be shown separately how to interrupt an operation with email messages started by a task-based asynchronous pattern ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)) method.

## **Retrieve Messages asynchronously**

The following code snippet shows you how to retrieve messages asynchronously.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrievingMessagesasynchronously-RetrievingMessagesasynchronously.cs" >}}

## **List Messages asynchronously with MailQuery**

The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class can be used to specify search criteria for retrieving a specified list of messages asynchronously as is shown in the following code sample.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListMessagesasynchronously-ListMessagesasynchronouslyWithMailQuery.cs" >}}

## **How to Interrupt a TAP Method**

Starting with .NET Framework 4.5, you can use asynchronous methods implemented according to TAP model. The code snippet below shows how to append many messages using the task-based asynchronous pattern method named `AppendMessagesAsync` and then interrupt this process after a while.

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
## **Sending Messages asynchronously**

Sending emails asynchronously is very convenient, as the process does not block the execution of the program or thread.Instead of waiting for the email to be sent before proceeding with other tasks, the program can continue running while the email is being sent in the background.

The following features will help you implement asynchronous sending into your project:

- [IAsyncImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Allows applications to access and manipulate messages by using the Internet Message Access Protocol (IMAP).

- [ImapClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Creates a new instance of the Aspose.Email.Clients.Imap.ImapClientclass

The code sample given below demonstrates how to list messages in the background:

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
## **Cancelation for asynchronous Operations**

Sometimes you may face the need to stop asynchronous operations. For this purpose our library offers cancellation of asynchronous operations through the use of the CancellationToken parameter. When invoking an asynchronous method that supports cancellation, you can pass a CancellationToken instance as a parameter. The CancellationToken is used to signal and control the cancellation of the operation.

To enable cancellation, you first need to create a CancellationTokenSource instance that provides the CancellationToken. Then, pass the CancellationToken to the asynchronous method, allowing it to check for cancellation requests during execution.

Here is an example that demonstrates cancellation using CancellationToken:

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