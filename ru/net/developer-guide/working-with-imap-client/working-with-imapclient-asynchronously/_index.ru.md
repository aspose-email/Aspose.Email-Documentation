---
title: "Асинхронная работа с IMapClient"
url: /ru/net/working-with-imapclient-asynchronously/
weight: 70
type: docs
---


Работа с сообщениями может выполняться асинхронно с помощью Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). В этой статье показано асинхронное получение сообщений из почтового ящика. В этой статье также показано, как составить список сообщений, указав критерии поиска, используя [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Отдельно будет показано, как прервать операцию с сообщениями электронной почты, запущенную по асинхронному шаблону, основанному на задаче ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)) метод.

## **Асинхронное получение сообщений**

В следующем фрагменте кода показано, как асинхронно извлекать сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrievingMessagesasynchronously-RetrievingMessagesasynchronously.cs" >}}

## **Асинхронный список сообщений с помощью MailQuery**

The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) класс можно использовать для указания критериев поиска для асинхронного получения указанного списка сообщений, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListMessagesasynchronously-ListMessagesasynchronouslyWithMailQuery.cs" >}}

## **Как прервать метод TAP**

Начиная с платформы.NET Framework 4.5 можно использовать асинхронные методы, реализованные по модели TAP. В приведенном ниже фрагменте кода показано, как добавлять много сообщений, используя метод асинхронных шаблонов на основе задач под названием `AppendMessagesAsync` а затем прервите этот процесс через некоторое время.

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
## **Асинхронная отправка сообщений**

Асинхронная отправка электронных писем очень удобна, так как этот процесс не блокирует выполнение программы или потока. Вместо ожидания отправки письма перед выполнением других задач программа может продолжать работать, пока электронное письмо отправляется в фоновом режиме.

Следующие функции помогут внедрить асинхронную отправку в проект:

- [IAsyncImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Позволяет приложениям получать доступ к сообщениям и управлять ими с помощью протокола доступа к сообщениям Интернета (IMAP).

- [ImapClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Создает новый экземпляр `Aspose.Email.Clients.Imap.ImapClient` class

В приведенном ниже примере кода показано, как отображать сообщения в фоновом режиме:

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
## **Отмена асинхронных операций**

Иногда вы можете столкнуться с необходимостью остановить асинхронные операции. Для этого наша библиотека предлагает отмену асинхронных операций с помощью параметра CancellationToken. При вызове асинхронного метода, поддерживающего отмену, вы можете передать экземпляр CancellationToken в качестве параметра. CancellationToken используется для сигнализации и управления отменой операции.

Чтобы включить отмену, сначала необходимо создать экземпляр CancellationTokenSource, предоставляющий CancellationToken. Затем передайте CancellationToken асинхронному методу, чтобы он мог проверять запросы на отмену во время выполнения.

Вот пример, демонстрирующий отмену с помощью CancellationToken:

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
