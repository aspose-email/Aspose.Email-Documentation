---
title: "Парсинг файлов сообщений Microsoft Outlook"
url: /ru/java/parsing-microsoft-outlook-message-files/
weight: 80
type: docs
---

С помощью Aspose.Email вы можете парсить сообщения Microsoft Outlook всего несколькими строками кода. Эта статья демонстрирует, как это сделать. Aspose.Email имеет классы для выполнения множества программных задач с сообщениями Outlook. Пример кода ниже показывает, как:

1. Загрузить электронное сообщение.
1. Получить тему письма.
1. Узнать имя отправителя.
1. Получить полный текст сообщения.
1. Узнать, есть ли вложения.
1. Получить имена файлов вложений и сохранить их.

Следующий фрагмент кода показывает, как парсить файлы сообщений Microsoft Outlook.

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