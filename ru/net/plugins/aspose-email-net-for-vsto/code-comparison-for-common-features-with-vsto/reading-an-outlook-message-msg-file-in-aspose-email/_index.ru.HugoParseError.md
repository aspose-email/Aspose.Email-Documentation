---
title: Чтение сообщения Outlook (файл MSG) в Aspose.Email
type: docs
weight: 190
url: /net/reading-an-outlook-message-msg-file-in-aspose-email/
---


Чтобы использовать объекты автоматизации Office для Microsoft Outlook, необходимо добавить ссылки на библиотеки Microsoft Office и Microsoft Office Interop для Outlook в ваш проект.
### **VSTO**
``` cs

 // Создать новый класс приложения

_Application outlook = new Outlook.Application();

// Создать объект MailItem

MailItem item = (MailItem)outlook.CreateItemFromTemplate("test.msg", Type.Missing);

// Получить доступ к различным полям сообщения

System.Console.WriteLine(string.Format("Тема:{0}", item.Subject));

System.Console.WriteLine(string.Format("Адрес электронной почты отправителя:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("Имя отправителя:{0}", item.SenderName));

System.Console.WriteLine(string.Format("Кому:{0}", item.To));

System.Console.WriteLine(string.Format("Копия:{0}", item.CC));

System.Console.WriteLine(string.Format("Скрытая копия:{0}", item.BCC));

System.Console.WriteLine(string.Format("HTML тело:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Текстовое тело:{0}", item.Body));

```
### **Aspose.Email**
Чтобы получить доступ к объектам Aspose.Email.Outlook, необходимо добавить ссылку на Aspose.Email в ваш проект.

``` cs

  // Создать участников встречи

MailAddressCollection attendees = new MailAddressCollection();

attendees.Add("recipient1@domain.com");

attendees.Add("recipient2@domain.com");

// Настроить встречу

Appointment app = new Appointment(

    "Место встречи", // место встречи

    DateTime.Now, // дата начала

    DateTime.Now.AddHours(1), // дата окончания

    new MailAddress("organizer@domain.com"), // организатор

    attendees); // участники

// Настроить сообщение, которое необходимо отправить

MailMessage msg = new MailMessage();

msg.From = "from@domain.com";

msg.To = "to@domain.com";

msg.Subject = "запрос на встречу";

msg.Body = "вы приглашены";

// Добавить запрос на встречу в сообщение

msg.AddAlternateView(app.RequestApointment());

// Настроить SMTP-клиент для отправки электронной почты с запросом на встречу

SmtpClient client = new SmtpClient("host", 25 ,"user", "password");

client.Send(msg);

```
## **Скачать образец кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772943)
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Reading.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Sourceforge](http://goo.gl/TpCQPp)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Reading%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)