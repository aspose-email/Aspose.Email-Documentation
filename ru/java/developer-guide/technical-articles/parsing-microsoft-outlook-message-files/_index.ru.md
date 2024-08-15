---
title: "Разбор файлов сообщений Microsoft Outlook"
url: /ru/java/parsing-microsoft-outlook-message-files/
weight: 80
type: docs
---


С помощью Aspose.Email вы можете анализировать сообщения Microsoft Outlook всего за несколько строк кода. В этой статье показано, как это сделать. В Aspose.Email есть классы для выполнения многих задач программирования с сообщениями Outlook. В приведенном ниже примере кода показано, как:

1. Загрузите сообщение электронной почты.
1. Укажите тему письма.
1. Узнайте имя отправителя.
1. Получите полный текст сообщения.
1. Узнайте, есть ли вложения.
1. Получите имена файлов любых вложений и сохраните их.

В следующем фрагменте кода показано, как анализировать файлы сообщений Microsoft Outlook.



~~~Java
// The path to the File directory and Load Microsoft Outlook email message file
String dataDir = "data/";
MapiMessage msg = MapiMessage.fromFile(dataDir + "message3.msg");

// Obtain subject of the email message, sender, body and Attachment count
System.out.println("Subject:" + msg.getSubject());
System.out.println("From:" + msg.getSenderName());
System.out.println("Body:" + msg.getBody());
System.out.println("Attachment Count:" + msg.getAttachments().size());

// Iterate through the attachments
for (MapiAttachment attachment : msg.getAttachments()) {
    // Access the attachment's file name and Save attachment
    System.out.println("Attachment:" + attachment.getFileName());
    attachment.save(dataDir + attachment.getLongFileName());
}
~~~