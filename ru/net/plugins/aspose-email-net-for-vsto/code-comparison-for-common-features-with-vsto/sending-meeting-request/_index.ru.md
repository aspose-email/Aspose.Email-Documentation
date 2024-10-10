---
title: "Отправка запроса на встречу"
url: /ru/net/sending-meeting-request/
weight: 200
type: docs
---


## **VSTO**
Чтобы использовать классы Outlook, необходимо сослаться на Outlook.Interop в вашем .NET проекте. Приведенный ниже фрагмент кода:

1. Создает запрос на встречу.
1. Устанавливает такие свойства, как тема, текст, местоположение и время.
1. Отправляет запрос на встречу получателю.
1. Microsoft Outlook должен быть установлен на системе, где будет запущено это образец приложения.

``` cs

 // Создать экземпляр класса приложения Outlook

Outlook.Application outlookApp = new Outlook.Application();

// Создать экземпляр объекта AppointmentItem и установить свойства:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem)outlookApp.CreateItem(Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "тема встречи";

oAppointment.Body = "текст встречи";

oAppointment.Location = "Место встречи";

// Установить даты начала и окончания

oAppointment.Start = Convert.ToDateTime("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Сохранить встречу

oAppointment.Save();

// Отправить встречу

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal();

mailItem.To = "recipient@domain.com";

mailItem.Send();

```
## **Aspose.Email**
Приведенный ниже код использует Aspose.Email для .NET для отправки запроса на встречу. Сначала создайте запрос на встречу, используя класс Aspose.Email.Appointment. Затем отправьте электронное письмо, прикрепите запрос на встречу и отправьте письмо с помощью класса Aspose.Email.Mail.SmtpClient.

Преимущества использования Aspose.Email для .NET

Outlook Interop требует, чтобы Microsoft Outlook был установлен на системе, где он используется. Aspose.Email для .NET не требует установки Microsoft Outlook и подходит для серверных приложений.

``` cs

  // Создать участников встречи

MailAddressCollection attendees = new MailAddressCollection();

attendees.Add("recipient1@domain.com");

attendees.Add("recipient2@domain.com");

// Настроить встречу

Appointment app = new Appointment(

    "Место", // место встречи

    DateTime.Now, // дата начала

    DateTime.Now.AddHours(1), // дата окончания

    new MailAddress("organizer@domain.com"), // организатор

    attendees); // участники

// Настроить сообщение, которое должно быть отправлено

MailMessage msg = new MailMessage();

msg.From = "from@domain.com";

msg.To = "to@domain.com";

msg.Subject = "запрос на встречу";

msg.Body = "вы приглашены";

// Добавить запрос на встречу в сообщение

msg.AddAlternateView(app.RequestApointment());

// Настроить SMTP-клиент для отправки электронного письма с запросом на встречу

SmtpClient client = new SmtpClient("host", 25 ,"user", "password");

client.Send(msg);

```
##**Скачать пример кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772944)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Sending.Meeting.Request.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Sending%20Meeting%20Request%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Sending%20Meeting%20Request%20\(Aspose.Email\).zip)