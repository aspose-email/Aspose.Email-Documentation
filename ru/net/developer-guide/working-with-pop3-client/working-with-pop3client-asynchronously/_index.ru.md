---
title: "Работа с Pop3Client Асинхронно"
url: /ru/net/working-with-pop3client-asynchronously/
weight: 60
type: docs
---


Работа с сообщениями также может выполняться асинхронно с использованием Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). В этой статье показано, как асинхронно извлекать сообщения из почтового ящика. Также показано, как перечислять сообщения, предоставив критерии поиска с помощью [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Отдельно будет показано, как прервать операцию с почтовым ящиком, запущенную с помощью метода асинхронной модели на основе задач ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)).

## **Асинхронное извлечение сообщений**

Следующий фрагмент кода показывает, как асинхронно извлекать сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessagesAsynchronously-RetrieveMessagesAsynchronously.cs" >}}

## **Асинхронный список сообщений с MailQuery**

Класс [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) может использоваться для указания критериев поиска для асинхронного извлечения списка сообщений, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ListMessagesAsynchronouslyWithMailQuery-ListMessagesAsynchronouslyWithMailQuery.cs" >}}

## **Как прервать метод TAP**

Начиная с .NET Framework 4.5, вы можете использовать асинхронные методы, реализованные в соответствии с моделью TAP. Ниже представлен фрагмент кода, который показывает, как получить информацию о почтовом ящике с помощью метода асинхронной модели на основе задач с именем `GetMailboxInfoAsync`, а затем прервать этот процесс через некоторое время.

```csharp
// Для полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-.NET

using (Pop3Client client = new Pop3Client(host, 995, senderEmail, password, SecurityOptions.Auto))
{
    CancellationTokenSource cancellationTokenSource = new CancellationTokenSource();
    AutoResetEvent autoResetEvent = new AutoResetEvent(false);
    Exception exception = null;

    ThreadPool.QueueUserWorkItem(delegate
    {
        try
        {
            // начинаем получать информацию о почтовом ящике
            var task = client.GetMailboxInfoAsync(cancellationTokenSource.Token);
            Pop3MailboxInfo mailboxInfo = task.GetAwaiter().GetResult();
            Console.WriteLine("Количество сообщений: " + mailboxInfo.MessageCount);
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

    // останавливаем получение информации о почтовом ящике
    cancellationTokenSource.Cancel();
    autoResetEvent.WaitOne();

    if (exception is OperationCanceledException)
        Console.WriteLine("Операция была прервана: " + exception.Message);
}
```