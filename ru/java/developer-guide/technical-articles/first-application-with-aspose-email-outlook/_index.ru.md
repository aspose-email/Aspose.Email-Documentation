---
title: "Первое приложение с Aspose.Email Outlook"
url: /ru/java/first-application-with-aspose-email-outlook/
weight: 280
type: docs
---


В этом разделе показано, как использовать Aspose.Email Mapi. Мы создадим небольшое приложение, которое загружает файл сообщения Outlook (TestMessage.msg) и отображает тему, адреса отправителя и получателя, а также содержимое тела сообщения. Выполните следующие шаги, чтобы создать свое первое приложение с использованием Aspose.Email Outlook.

1. Создайте экземпляр класса [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage), указав путь к файлу сообщения.
1. Используйте открытые свойства для отображения темы, отправителя, получателя и тела.

Реализация вышеуказанных шагов демонстрируется ниже в следующем фрагменте кода.



~~~Java
// Load the outlook message file
MapiMessage msg = MapiMessage.fromFile("outlookmessage.msg");

// Use the public properties
//read subject
System.out.print("Subject:" + msg.getSubject());

//sender name
System.out.print("From:" + msg.getSenderName());

//message body
System.out.print("Body:" + msg.getBody());

//Attachments
for(MapiAttachment att : msg.getAttachments())
{
    System.out.print("Attachment Name:"+att.getFileName());
    att.save(att.getFileName());
}
~~~