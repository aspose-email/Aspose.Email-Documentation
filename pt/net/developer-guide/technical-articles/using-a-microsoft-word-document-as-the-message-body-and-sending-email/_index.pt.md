---
title: "Usando um Documento do Microsoft Word como Corpo da Mensagem e Enviando Email"
url: /pt/net/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
weight: 140
type: docs
---


Este artigo mostra como usar um documento do Microsoft Word como corpo do email e enviá-lo para os destinatários. O documento de exemplo é uma fatura de venda do banco de dados Northwind, exportada para o formato Microsoft Word. Aspose.Email para .NET lida com protocolos de rede e funcionalidades do Microsoft Outlook, mas não pode manipular documentos do Microsoft Word. Para contornar isso, os exemplos neste artigo usam [Aspose.Words for .NET](https://products.aspose.com/words/net/) para carregar o documento do Word e convertê-lo para o formato MHTML. Aspose.Email para .NET usa o documento MHTML no corpo do email.
## **Usando Documentos do Microsoft Word como Corpo do Email**
Os exemplos de programação abaixo ilustram como enviar um documento do Word como corpo do email usando Aspose.Words para .NET e Aspose.Email para .NET:

1. Carregue um documento do Microsoft Word usando a classe [Document](https://apireference.aspose.com/words/net/aspose.words/document) do Aspose.Words para .NET.
1. Salve-o no formato MHTML.
1. Carregue o documento MHTML usando a classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) do Aspose.Email para .NET para definir o corpo do email.
1. Defina outras propriedades da mensagem usando diferentes propriedades e métodos da classe [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Envie o email usando a classe [SMTPClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) do Aspose.Email para .NET.

O documento fonte, uma fatura de venda exportada para o Microsoft Word do exemplo Microsoft Northwind, pode ser visto abaixo. 

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

Quando a mensagem foi enviada e recebida no Microsoft Outlook, ela parece com a mensagem abaixo. 

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

A formatação HTML e as imagens são preservadas como no documento fonte original quando visualizadas no Outlook ou em um cliente de email web como Gmail ou Hotmail. Abaixo está uma captura de tela da mensagem quando aberta no Gmail em um navegador Chrome. 

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

O seguinte trecho de código mostra como usar um documento do Microsoft Word como o corpo da mensagem e enviar um email usando a instância da classe [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient).

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET

// Carregue um documento do Word do disco e salve-o em stream como MHTML
Document wordDocument = new Document(folderPath + "invoice.docx");
MemoryStream mhtmlStream = new MemoryStream();
wordDocument.Save(mhtmlStream, SaveFormat.Mhtml);

// Carregue o MHTML em um objeto MailMessage
mhtmlStream.Position = 0;
using (MailMessage message = MailMessage.Load(mhtmlStream, new MhtmlLoadOptions()))
{
    message.Subject = "Enviando Fatura por Email";
    message.From = "sender@gmail.com";
    message.To = "recipient@gmail.com";

    // Salve a mensagem no formato MSG no disco
    message.Save(folderPath + "WordDocAsEmailBody_out.msg", SaveOptions.DefaultMsgUnicode);

    // Envie a mensagem de email
    using (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "password"))
    {
        client.SecurityOptions = SecurityOptions.SSLExplicit;
        client.Send(message);
    }
}
```