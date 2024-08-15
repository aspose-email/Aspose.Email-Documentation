---
title: "Trabajando con Pop3Client de forma asincrónica"
url: /es/net/working-with-pop3client-asynchronously/
weight: 60
type: docs
---


El trabajo con mensajes también se puede realizar de forma asincrónica mediante Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). En este artículo se muestra cómo recuperar mensajes de un buzón de forma asincrónica. También muestra cómo enumerar los mensajes proporcionando criterios de búsqueda mediante [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Se mostrará por separado cómo interrumpir una operación con un buzón iniciado por un patrón asincrónico basado en tareas ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)) método.

## **Recuperar mensajes de forma asincrónica**

El siguiente fragmento de código muestra cómo recuperar mensajes de forma asincrónica.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessagesAsynchronously-RetrieveMessagesAsynchronously.cs" >}}

## **Listar mensajes de forma asincrónica con MailQuery**

The [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) La clase se puede usar para especificar criterios de búsqueda para recuperar una lista de mensajes de forma asincrónica, como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ListMessagesAsynchronouslyWithMailQuery-ListMessagesAsynchronouslyWithMailQuery.cs" >}}

## **Cómo interrumpir un método TAP**

A partir de .NET Framework 4.5, puede usar métodos asincrónicos implementados de acuerdo con el modelo TAP. El siguiente fragmento de código muestra cómo recibir información sobre un buzón mediante el método de patrón asincrónico basado en tareas denominado `GetMailboxInfoAsync` y luego interrumpir este proceso después de un tiempo.

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
