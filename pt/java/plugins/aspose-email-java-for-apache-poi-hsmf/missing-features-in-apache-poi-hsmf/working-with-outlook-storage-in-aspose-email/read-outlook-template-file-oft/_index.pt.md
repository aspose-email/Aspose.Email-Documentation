---
title: "Ler Arquivo de Modelo do Outlook OFT"
url: /pt/java/read-outlook-template-file-oft/
weight: 40
type: docs
---

## **Aspose.Email - Ler Modelo do Outlook OFT**
A classe [Aspose.Email.MailMessage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) pode ser usada para carregar um arquivo de modelo do Microsoft Outlook (OFT). Uma vez que o modelo do Outlook é carregado em uma instância da classe MailMessage, você pode atualizar o remetente, o destinatário, o corpo, o assunto e outras propriedades.

**Java**

``` java

 // Carregar o arquivo de modelo do Outlook (OFT) na instância do MailMessage

MailMessage message = MailMessage.load(dataDir + "sample.oft");

// Definir as informações do remetente e dos destinatários

String senderDisplayName = "John";

String senderEmailAddress = "john@abc.com";

String recipientDisplayName = "William";

String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));

message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));

message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Definir o nome, local e hora no corpo do e-mail

String meetingLocation = "<u>" + "Hall 1, Convention Center, New York, USA" + "</u>";

String meetingTime = "<u>" + "Monday, June 28, 2010" + "</u>";

message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));

message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Salvar a mensagem no formato MSG e abrir no Office Outlook

MapiMessage mapimessage = new MapiMessage().fromMailMessage(message);

mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);

mapimessage.save(dataDir + "AsposeInvitation.msg");

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Ler Arquivo de Modelo do Outlook (OFT)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}