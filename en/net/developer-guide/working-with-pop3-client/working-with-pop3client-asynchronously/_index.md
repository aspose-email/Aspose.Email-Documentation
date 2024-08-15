---
title: Working with Pop3Client Asynchronously
type: docs
weight: 60
url: /net/working-with-pop3client-asynchronously/
---


Working with messages can also be performed asynchronously using the Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). This article shows how to retrieve messages from a mailbox asynchronously. It also shows how to list messages by providing search criteria using [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). It will be shown separately how to interrupt an operation with a mailbox started by a task-based asynchronous pattern ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)) method.

## **Retrieve Messages Asynchronously**

The following code snippet shows you how to retrieve messages asynchronously.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessagesAsynchronously-RetrieveMessagesAsynchronously.cs" >}}

## **List Messages Asynchronously with MailQuery**

The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class can be used to specify search criteria for retrieving a list of messages asynchronously as is shown in the following code sample.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ListMessagesAsynchronouslyWithMailQuery-ListMessagesAsynchronouslyWithMailQuery.cs" >}}

## **How to Interrupt a TAP Method**

Starting with .NET Framework 4.5, you can use asynchronous methods implemented according to TAP model. The code snippet below shows how to receive information about a mailbox using the task-based asynchronous pattern method named `GetMailboxInfoAsync` and then interrupt this process after a while.

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
