---
title: "Trabajando con Pop3Client Asincrónicamente"
url: /es/net/working-with-pop3client-asynchronously/
weight: 60
type: docs
---


Trabajar con mensajes también se puede realizar de manera asincrónica utilizando el [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) de Aspose.Email. Este artículo muestra cómo recuperar mensajes de un buzón de manera asincrónica. También muestra cómo listar mensajes proporcionando criterios de búsqueda utilizando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Se mostrará por separado cómo interrumpir una operación con un buzón iniciada por un método de patrón asincrónico basado en tareas ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)).

## **Recuperar Mensajes Asincrónicamente**

El siguiente fragmento de código muestra cómo recuperar mensajes de manera asincrónica.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessagesAsynchronously-RetrieveMessagesAsynchronously.cs" >}}

## **Listar Mensajes Asincrónicamente con MailQuery**

La clase [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) se puede utilizar para especificar criterios de búsqueda para recuperar una lista de mensajes de manera asincrónica, como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ListMessagesAsynchronouslyWithMailQuery-ListMessagesAsynchronouslyWithMailQuery.cs" >}}

## **Cómo Interrumpir un Método TAP**

A partir de .NET Framework 4.5, puede utilizar métodos asincrónicos implementados de acuerdo con el modelo TAP. El siguiente fragmento de código muestra cómo recibir información sobre un buzón utilizando el método de patrón asincrónico basado en tareas llamado `GetMailboxInfoAsync` y luego interrumpir este proceso después de un tiempo.

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