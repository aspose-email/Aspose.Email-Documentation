---
title: "Отправка запроса на встречу с использованием Outlook Interop и Aspose.Email для Java"
url: /ru/java/sending-meeting-request-using-outlook-interop-and-aspose-email-for-java/
weight: 40
type: docs
---


{{% alert color="primary" %}} 

Наши советы по миграции показывают, как продукты Aspose могут быть использованы для улучшения ваших приложений и освобождения от зависимости от традиционной автоматизации.

Этот совет по миграции отправляет запрос на встречу получателю. Он демонстрирует, как отправить запрос на встречу двумя способами:

- [Используя Outlook Interop](#sending-meeting-request-with-outlook-interop).
- [Используя Aspose.Email для Java](#advantages-of-using-asposeemail-for-java).

Мы также обсудим преимущества последнего подхода.

{{% /alert %}} 
## **Отправка запроса на встречу с использованием Outlook Interop**
Чтобы использовать классы Outlook, необходимо ссылаться на Outlook.Interop в вашем .NET проекте. Приведенный ниже код:

1. Создает запрос на встречу.
1. Устанавливает свойства, такие как тема, текст и время.
1. Отправляет запрос на встречу получателю.

Microsoft Outlook должен быть установлен на системе, где будет работать это демонстрационное приложение.
### **Программные примеры**
**C#**

~~~cs

// Создание экземпляра класса Outlook Application

Outlook.Application outlookApp = new Outlook.Application ();

// Создание экземпляра объекта AppointmentItem и установка свойств:

Outlook.AppointmentItem oAppointment = (Outlook.AppointmentItem) outlookApp.CreateItem (Outlook.OlItemType.olAppointmentItem);

oAppointment.Subject = "тема встречи";

oAppointment.Body = "текст встречи";

oAppointment.Location = "Место проведения встречи";

// Установка даты начала и окончания

oAppointment.Start = Convert.ToDateTime ("01/22/2010 10:00:00 AM");

oAppointment.End = Convert.ToDateTime("01/22/2010 2:00:00 PM");

// Сохранение встречи

oAppointment.Save ();

// Отправка встречи

Outlook.MailItem mailItem = oAppointment.ForwardAsVcal ();

mailItem.To = "recipient@domain.com";

mailItem.Send();


~~~
## **Отправка запроса на встречу с использованием Aspose.Email для Java**
Код ниже использует Aspose.Email для Java для отправки запроса на встречу. Сначала создайте запрос на встречу, используя класс [Aspose.Email Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment). Затем отправьте электронное письмо, прикрепите запрос на встречу и отправьте электронное письмо с использованием класса [Aspose.Email SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/SmtpClient).
### **Преимущества использования Aspose.Email для Java**
Outlook Interop требует установки Microsoft Outlook на системе, где он используется. Aspose.Email для Java не требует установки Microsoft Outlook и подходит для серверных приложений.
### **Программные примеры**

~~~Java

// Создание участников встречи
MailAddressCollection attendees = new MailAddressCollection();
attendees.add("recipient1@domain.com");
attendees.add("recipient2@domain.com");

java.util.Calendar c = java.util.Calendar.getInstance();
Date startDate = c.getTime();
c.add(java.util.Calendar.HOUR_OF_DAY, 1);
Date endDate = c.getTime();

// Настройка встречи
Appointment app = new Appointment(
    "Место", // место встречи
    startDate, // дата начала
    endDate, // дата окончания
    new MailAddress("organizer@domain.com"), // организатор
    attendees); // участники

// Настройка сообщения, которое нужно отправить
MailMessage msg = new MailMessage();
msg.setFrom(new MailAddress("from@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setSubject("запрос на встречу");
msg.setBody("вы приглашены");

// Добавление запроса на встречу в сообщение
msg.addAlternateView(app.requestApointment());

// Настройка SMTP-клиента для отправки электронного письма с запросом на встречу
try (SmtpClient client = new SmtpClient("host", 25, "user", "password")) {
    client.send(msg);
}

~~~