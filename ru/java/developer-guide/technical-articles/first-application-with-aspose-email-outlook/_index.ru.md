---
title: "Первое приложение с Aspose.Email Outlook"
url: /ru/java/first-application-with-aspose-email-outlook/
weight: 280
type: docs
---


В этом разделе показано, как использовать Aspose.Email Mapi. Мы создаем небольшое приложение, которое загружает файл сообщений Outlook (TestMessage.msg) и отображает тему сообщения, адрес отправки и адрес, а также основной контент. Выполните следующие действия, чтобы создать свое первое приложение с помощью Aspose.Email Outlook.

1. Создайте экземпляр [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) класс, указав путь к файлу сообщения.
1. Используйте общедоступные свойства для отображения объекта, от и до тела.

Реализация вышеуказанных шагов продемонстрирована ниже в следующем фрагменте кода.



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