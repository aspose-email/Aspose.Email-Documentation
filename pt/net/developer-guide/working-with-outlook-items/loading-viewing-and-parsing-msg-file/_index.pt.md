---
title: "Carregando, Exibindo e Analisando Arquivo MSG"
url: /pt/net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


Este tópico explica como carregar um arquivo de Mensagem do Microsoft Outlook (*.msg). A classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) é usada para carregar arquivos MSG e fornece várias funções de carregamento estático para diferentes cenários. O seguinte trecho de código mostra como carregar arquivos MSG de um arquivo ou de um stream.

## **Carregando Arquivos MSG**

O seguinte trecho de código mostra como carregar arquivos MSG.

```cs
// O caminho para o diretório do arquivo.
string dataDir = RunExamples.GetDataDir_Outlook();

// Cria uma instância de MapiMessage a partir do arquivo
MapiMessage msg = MapiMessage.Load(dataDir + @"message.msg");

// Obtém o assunto
Console.WriteLine("Assunto:" + msg.Subject);

// Obtém o endereço do remetente
Console.WriteLine("De:" + msg.SenderEmailAddress);

// Obtém o corpo
Console.WriteLine("Corpo" + msg.Body);

// Obtém informações dos destinatários
Console.WriteLine("Destinatário: " + msg.Recipients);

// Obtém anexos
foreach (MapiAttachment att in msg.Attachments)
{
    Console.Write("Nome do Anexo: " + att.FileName);
    Console.Write("Nome de Exibição do Anexo: " + att.DisplayName);
}
```

O seguinte exemplo de código mostra como usar MailMessage para carregar uma mensagem no formato MSG.

```csharp

MailMessage eml = MailMessage.Load("message.msg");

```

Deve-se notar que uma mensagem resultante é convertida para o formato EML, incluindo anexos de mensagens incorporadas. Não use este método de carregamento se você deseja preservar algumas propriedades específicas do formato msg da mensagem original.

Para preservar o formato original dos anexos de mensagem incorporados, use a propriedade [msgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/).

```csharp

MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.PreserveEmbeddedMessageFormat = true;
var msg = MailMessage.Load(stream, msgLoadOptions);

```

## **Carregando de Stream**

O seguinte trecho de código mostra como carregar um arquivo de um stream.

```cs
// Cria uma instância de MapiMessage a partir do arquivo
byte[] bytes = File.ReadAllBytes(dataDir + @"message.msg");

using (MemoryStream stream = new MemoryStream(bytes))
{
    stream.Seek(0, SeekOrigin.Begin);
    // Cria uma instância de MapiMessage a partir do arquivo
    MapiMessage msg = MapiMessage.Load(stream);

    // Obtém o assunto
    Console.WriteLine("Assunto:" + msg.Subject);

    // Obtém o endereço do remetente
    Console.WriteLine("De:" + msg.SenderEmailAddress);

    // Obtém o corpo
    Console.WriteLine("Corpo" + msg.Body);

}
```

Convertendo EML para MSG preservando o formato EML incorporado

Arquivos EML podem ser carregados na classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) instanciando um objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) e passando-o para o método [MapiMessage.FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/). Se o arquivo EML contiver arquivos EML incorporados, use [MapiConversionOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveembeddedmessageformat/) para reter o formato dos arquivos EML incorporados. O trecho de código abaixo mostra como carregar arquivos EML na classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) enquanto preserva o formato dos arquivos EML incorporados.

{{% alert %}}
**Experimente!**

Converta e-mails e arquivos de mensagens online com o gratuito [**Aplicativo de Conversão Aspose.Email**](https://products.aspose.app/email/pt/Conversion).
{{% /alert %}}

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}