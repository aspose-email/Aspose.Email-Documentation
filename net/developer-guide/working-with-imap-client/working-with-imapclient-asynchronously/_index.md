---
title: Working with ImapClient Asynchronously
type: docs
weight: 70
url: /net/working-with-imapclient-asynchronously/
---


Working with messages can be performed asynchronously by using the Aspose.Email's [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient). This article shows retrieving messages from a mailbox asynchronously. This article also shows how to list messages by providing search criteria using [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery). It will be shown separately how to interrupt an operation with email messages started by a task-based asynchronous pattern ([TAP](https://docs.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)) method.

## **Retrieve Messages Asynchronously**
The following code snippet shows you how to retrieve messages asynchronously.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrievingMessagesAsynchronously-RetrievingMessagesAsynchronously.cs" >}}

## **List Messages Asynchronously with MailQuery**
The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery) class can be used to specify search criteria for retrieving a specified list of messages asynchronously as is shown in the following code sample.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListMessagesAsynchronously-ListMessagesAsynchronouslyWithMailQuery.cs" >}}

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
