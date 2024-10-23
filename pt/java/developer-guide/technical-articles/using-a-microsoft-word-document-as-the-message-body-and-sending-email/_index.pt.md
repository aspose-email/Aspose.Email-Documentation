---
title: "Usando um Documento do Microsoft Word como Corpo da Mensagem e Enviando Email"
url: /pt/java/usando-um-documento-do-microsoft-word-como-corpo-da-mensagem-e-enviando-email/
weight: 140
type: docs
---


Este artigo mostra como usar um documento do Microsoft Word como o corpo do email e enviá-lo para os destinatários. O documento de exemplo é uma fatura de vendas do banco de dados Northwind, exportado para o formato Microsoft Word. Aspose.Email para Java lida com protocolos de rede e recursos do Microsoft Outlook e não pode manipular documentos do Microsoft Word. Para contornar isso, os exemplos neste artigo usam [Aspose.Words para Java](https://products.aspose.com/words/java/) para carregar o documento Word e convertê-lo para o formato MHTML. Aspose.Email para Java usa o documento MHTML no corpo do email.
## **Usando Documentos do Microsoft Word como Corpo do Email**
Os exemplos de programação abaixo ilustram como enviar um documento Word como corpo de email usando Aspose.Words para Java e Aspose.Email para Java:

1. Carregue um documento do Microsoft Word usando a classe [Document](https://apireference.aspose.com/words/java/com.aspose.words/Document) do Aspose.Words para Java.
1. Salve-o no formato MHTML.
1. Carregue o documento MHTML usando a classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) do Aspose.Email para Java para definir o corpo do email.
1. Defina outras propriedades da mensagem usando diferentes propriedades e métodos da classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).
1. Envie o email usando a classe [SMTPClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) do Aspose.Email para Java.

O documento fonte, uma fatura de vendas exportada para o Microsoft Word do exemplo Microsoft Northwind, pode ser visto abaixo. 

![todo:image_alt_text](usando-um-documento-do-microsoft-word-como-corpo-da-mensagem-e-enviando-email_1.png)

Quando a mensagem foi enviada e recebida no Microsoft Outlook, ela aparece como a mensagem abaixo. 

![todo:image_alt_text](usando-um-documento-do-microsoft-word-como-corpo-da-mensagem-e-enviando-email_2.png)

A formatação HTML e as imagens são preservadas conforme o documento fonte original quando visualizadas tanto no Outlook quanto em um cliente de email web como Gmail ou Hotmail. Abaixo está uma captura de tela da mensagem quando aberta com Gmail em um navegador Chrome. 

![todo:image_alt_text](usando-um-documento-do-microsoft-word-como-corpo-da-mensagem-e-enviando-email_3.png)

O seguinte trecho de código mostra como usar um documento do Microsoft Word como o corpo da mensagem e enviar um email usando uma instância da classe [SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient).

~~~Java
// O caminho para o diretório de arquivos
String dataDir = "data/";

// Carrega um documento Word do disco e salva como MHTML
Document wordDocument = new Document(dataDir + "Test.doc");
ByteArrayOutputStream mhtmlStream = new ByteArrayOutputStream();
wordDocument.save(mhtmlStream, SaveFormat.MHTML);

// Carrega o MHTML em um objeto MailMessage
MailMessage message = MailMessage.load(new ByteArrayInputStream(mhtmlStream.toByteArray()), new MhtmlLoadOptions());
message.setSubject("Enviando Fatura por Email");
message.setFrom(new MailAddress("sender@gmail.com"));
message.setTo(MailAddressCollection.to_MailAddressCollection("recipient@gmail.com"));

// Salva a mensagem no formato MSG no disco
message.save(dataDir + "WordDocAsEmailBody_out.msg", SaveOptions.getDefaultMsgUnicode());

    // Envia a mensagem de email
try (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "pwd")) {
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    client.send(message);
}
~~~