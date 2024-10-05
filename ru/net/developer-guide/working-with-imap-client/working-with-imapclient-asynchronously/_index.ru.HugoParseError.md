---
title: Работа с ImapClient асинхронно
type: docs
weight: 70
url: /net/working-with-imapclient-asynchronously/
---


Работа с сообщениями может выполняться асинхронно с использованием Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). В этой статье показано, как асинхронно получать сообщения из почтового ящика. Также в статье показано, как перечислять сообщения, предоставляя критерии поиска с помощью [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Отдельно будет показано, как прервать операцию с электронными сообщениями, инициированную методом асинхронного шаблона на основе задач ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)).

## **Получение сообщений асинхронно**

Следующий фрагмент кода показывает, как асинхронно получать сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrievingMessagesasynchronously-RetrievingMessagesasynchronously.cs" >}}

## **Перечисление сообщений асинхронно с MailQuery**

Класс [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) может использоваться для указания критериев поиска для асинхронного получения заданного списка сообщений, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListMessagesasynchronously-ListMessagesasynchronouslyWithMailQuery.cs" >}}

## **Как прервать метод TAP**

Начиная с .NET Framework 4.5, вы можете использовать асинхронные методы, реализованные в соответствии с моделью TAP. Ниже приведен фрагмент кода, который показывает, как добавлять многие сообщения с использованием метода асинхронного шаблона на основе задач, названного `AppendMessagesAsync`, а затем прервать этот процесс через некоторое время.

```csharp
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-.NET

List<MailMessage> mailMessages = new List<MailMessage>();

// создайте почтовые сообщения
for (int i = 0; i < 100; i++)
    mailMessages.Add(new MailMessage(senderEmail, receiverEmail, $"Сообщение #{i}", "Текст"));

using (ImapClient client = new ImapClient(host, 993, senderEmail, password, SecurityOptions.SSLImplicit))
{
    CancellationTokenSource cancellationTokenSource = new CancellationTokenSource();
    AutoResetEvent autoResetEvent = new AutoResetEvent(false);
    Exception exception = null;

    ThreadPool.QueueUserWorkItem(delegate
    {
        try
        {
            // начните загрузку сообщений
            var task = client.AppendMessagesAsync(mailMessages, cancellationTokenSource.Token);
            AppendMessagesResult appendMessagesResult = task.GetAwaiter().GetResult();
            Console.WriteLine("Все сообщения были добавлены.");
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

    // остановите загрузку сообщений
    cancellationTokenSource.Cancel();
    autoResetEvent.WaitOne();

    foreach (MailMessage mailMessage in mailMessages)
        mailMessage.Dispose();

    if (exception is OperationCanceledException)
        Console.WriteLine("Операция была прервана: " + exception.Message);
}
```
## **Отправка сообщений асинхронно**

Отправка электронных писем асинхронно очень удобна, так как процесс не блокирует выполнение программы или потока. Вместо того чтобы ждать, пока электронная почта будет отправлена, прежде чем продолжить выполнение других задач, программа может продолжать работать, пока электронная почта отправляется в фоновом режиме.

Следующие функции помогут вам реализовать асинхронную отправку в ваш проект:

- [IAsyncImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Позволяет приложениям получать доступ и манипулировать сообщениями, используя Протокол для доступа к интернет-сообщениям (IMAP).

- [ImapClient.CreateAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Создает новый экземпляр класса `Aspose.Email.Clients.Imap.ImapClient`.

Пример кода, приведенный ниже, демонстрирует, как перечислять сообщения в фоновом режиме:

```cs
// Аутентификация клиента для получения необходимых разрешений
static readonly string tenantId = "ВАШ_TENANT_ID";
static readonly string clientId = "ВАШ_CLIENT_ID";
static readonly string redirectUri = "http://localhost";
static readonly string username = "имя пользователя";
static readonly string[] scopes = { "https://outlook.office.com/IMAP.AccessAsUser.All" };

// Используйте метод ImapAsync для асинхронных операций
static async Task Main(string[] args)
{
    await ImapAsync();
    Console.ReadLine();
}

// Установите соединение с сервером
// Создайте экземпляр ImapClient асинхронно, используя метод CreateAsync
// Выберите папку Входящие, используя метод SelectFolderAsync, чтобы завершить и получить список электронных сообщений асинхронно с использованием метода ListMessagesAsync.
static async Task ImapAsync()
{
    var tokenProvider = new TokenProvider(clientId, tenantId, redirectUri, scopes);
    var client = ImapClient.CreateAsync("outlook.office365.com", username, tokenProvider, 993).GetAwaiter().GetResult();
    await client.SelectFolderAsync(ImapFolderInfo.InBox);
    var messages = await client.ListMessagesAsync();
    Console.WriteLine("Сообщения :" + messages.Count);
}

// Реализация поставщика токенов
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
            Console.WriteLine($"Ошибка при получении токена доступа: {ex}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Ошибка: {ex}");
        }

        return null;
    }

    public void Dispose()
    {

    }
}
```
## **Отмена асинхронных операций**

Иногда вам может понадобиться остановить асинхронные операции. Для этой цели наша библиотека предлагает отмену асинхронных операций с помощью параметра CancellationToken. При вызове асинхронного метода, который поддерживает отмену, вы можете передать экземпляр CancellationToken в качестве параметра. CancellationToken используется для сигнализации и контроля отмены операции.

Чтобы включить отмену, вам сначала нужно создать экземпляр CancellationTokenSource, который предоставляет CancellationToken. Затем передайте CancellationToken в асинхронный метод, что позволяет ему проверять запросы на отмену во время выполнения.

Вот пример, который демонстрирует отмену с использованием CancellationToken:

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