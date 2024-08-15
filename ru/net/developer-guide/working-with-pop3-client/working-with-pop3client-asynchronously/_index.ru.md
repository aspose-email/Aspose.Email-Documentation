---
title: "Асинхронная работа с Pop3Client"
url: /ru/net/working-with-pop3client-asynchronously/
weight: 60
type: docs
---


Работа с сообщениями также может выполняться асинхронно с помощью Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). В этой статье показано, как асинхронно извлекать сообщения из почтового ящика. В ней также показано, как составить список сообщений, указав критерии поиска, используя [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Отдельно будет показано, как прервать операцию с почтовым ящиком, запущенную по асинхронному шаблону, основанному на задаче ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)) метод.

## **Асинхронное получение сообщений**

В следующем фрагменте кода показано, как асинхронно извлекать сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessagesAsynchronously-RetrieveMessagesAsynchronously.cs" >}}

## **Асинхронный список сообщений с помощью MailQuery**

The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) класс можно использовать для указания критериев поиска для асинхронного получения списка сообщений, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ListMessagesAsynchronouslyWithMailQuery-ListMessagesAsynchronouslyWithMailQuery.cs" >}}

## **Как прервать метод TAP**

Начиная с платформы.NET Framework 4.5 можно использовать асинхронные методы, реализованные по модели TAP. В приведенном ниже фрагменте кода показано, как получать информацию о почтовом ящике с помощью метода асинхронных шаблонов на основе задач под названием `GetMailboxInfoAsync` а затем прервите этот процесс через некоторое время.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

using (Pop3Client client = new Pop3Client(host, 995, senderEmail, password, SecurityOptions.Auto))
{
    CancellationTokenSource cancellationTokenSource = new CancellationTokenSource();
    AutoResetEvent autoResetEvent = new AutoResetEvent(false);
    Exception exception = null;

    ThreadPool.QueueUserWorkItem(delegate
    {
        try
        {
            // start receiving mailbox information
            var task = client.GetMailboxInfoAsync(cancellationTokenSource.Token);
            Pop3MailboxInfo mailboxInfo = task.GetAwaiter().GetResult();
            Console.WriteLine("Message count: " + mailboxInfo.MessageCount);
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

    Thread.Sleep(2000);

    // stop receiving mailbox information
    cancellationTokenSource.Cancel();
    autoResetEvent.WaitOne();

    if (exception is OperationCanceledException)
        Console.WriteLine("Operation has been interrupted: " + exception.Message);
}
```
