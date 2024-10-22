---
title: "Trabalhando com Pop3Client Assincronamente"
url: /pt/net/trabalhando-com-pop3client-assincronamente/
weight: 60
type: docs
---

Trabalhar com mensagens também pode ser realizado de forma assíncrona usando o Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). Este artigo mostra como recuperar mensagens de uma caixa de entrada de forma assíncrona. Ele também mostra como listar mensagens fornecendo critérios de pesquisa usando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Será mostrado separadamente como interromper uma operação com uma caixa de entrada iniciada por um método baseado em padrão assíncrono com tarefas ([TAP](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)).

## **Recuperar Mensagens Assincronamente**

O seguinte trecho de código mostra como recuperar mensagens de forma assíncrona.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessagesAsynchronously-RetrieveMessagesAsynchronously.cs" >}}

## **Listar Mensagens Assincronamente com MailQuery**

A classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) pode ser usada para especificar critérios de pesquisa para recuperar uma lista de mensagens de forma assíncrona, como é mostrado no seguinte exemplo de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ListMessagesAsynchronouslyWithMailQuery-ListMessagesAsynchronouslyWithMailQuery.cs" >}}

## **Como Interromper um Método TAP**

A partir do .NET Framework 4.5, você pode usar métodos assíncronos implementados de acordo com o modelo TAP. O trecho de código abaixo mostra como receber informações sobre uma caixa de entrada usando o método do padrão assíncrono baseado em tarefas chamado `GetMailboxInfoAsync` e, em seguida, interromper este processo após um tempo.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET

using (Pop3Client client = new Pop3Client(host, 995, senderEmail, password, SecurityOptions.Auto))
{
    CancellationTokenSource cancellationTokenSource = new CancellationTokenSource();
    AutoResetEvent autoResetEvent = new AutoResetEvent(false);
    Exception exception = null;

    ThreadPool.QueueUserWorkItem(delegate
    {
        try
        {
            // começar a receber informações da caixa de entrada
            var task = client.GetMailboxInfoAsync(cancellationTokenSource.Token);
            Pop3MailboxInfo mailboxInfo = task.GetAwaiter().GetResult();
            Console.WriteLine("Contagem de mensagens: " + mailboxInfo.MessageCount);
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

    // parar de receber informações da caixa de entrada
    cancellationTokenSource.Cancel();
    autoResetEvent.WaitOne();

    if (exception is OperationCanceledException)
        Console.WriteLine("A operação foi interrompida: " + exception.Message);
}
```