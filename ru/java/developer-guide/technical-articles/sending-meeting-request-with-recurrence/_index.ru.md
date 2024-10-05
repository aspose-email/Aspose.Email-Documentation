---
title: "Отправка запроса на встречу с повторением"
url: /ru/java/sending-meeting-request-with-recurrence/
weight: 240
type: docs
---

С помощью Aspose.Email возможно генерировать запрос на встречу с повторением. В этой статье объясняется, как можно сгенерировать запрос на встречу с определенным повторением. Уникальный идентификатор назначения может быть сохранен для дальнейшего использования при отправке любого обновления к встрече.
## **Генерация запроса на встречу с повторением**
Следующий образец кода показывает, как это достичь.

~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
String szUniqueId;

// Создание сообщения электронной почты
MailMessage msg1 = new MailMessage();
msg1.getTo().add("to@domain.com");
msg1.setFrom(new MailAddress("from@gmail.com"));

// Заполнение объекта назначения
Date startDate = sdf.parse("2013-12-01 17:00:00");
Date endDate = sdf.parse("2013-12-31 17:30:00");

// Создание объекта назначения
Appointment agendaAppointment = new Appointment("то же место", startDate, endDate, msg1.getFrom(), msg1.getTo());

// Создание уникального идентификатора, так как это поможет получить доступ к этому назначению позже
szUniqueId = UUID.randomUUID().toString();
agendaAppointment.setUniqueId(szUniqueId);
agendaAppointment.setDescription("----------------");

// Создание объекта шаблона повторения для недели
WeeklyRecurrencePattern pattern1 = new WeeklyRecurrencePattern(14);

// Установка свойств недельного шаблона, таких как дни: Пн, Вт и Чт
pattern1.setStartDays(new int[3]);
pattern1.getStartDays()[0] = CalendarDay.Monday;
pattern1.getStartDays()[1] = CalendarDay.Tuesday;
pattern1.getStartDays()[2] = CalendarDay.Thursday;
pattern1.setInterval(1);

// Установка шаблона повторения для назначения
agendaAppointment.setRecurrence(pattern1);

// Привязка этого назначения к почте
msg1.getAlternateViews().addItem(agendaAppointment.requestApointment());

// Создание SmtpCleint
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
client.setSecurityOptions(SecurityOptions.Auto);

// Отправка почты с запросом на назначение
client.send(msg1);

// Возврат уникального идентификатора для дальнейшего использования
// return szUniqueId;
~~~
## **Отправка запроса на обновление назначения**
Для отправки обновления предыдущего назначения необходим уникальный идентификатор. Следующий пример кода показывает, как можно отправить запрос на обновление этого назначения.

~~~Java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
Date startDate = sdf.parse("2013-12-12 17:00:00");
Date endDate = sdf.parse("2013-12-12 17:30:00");
Appointment appUpdate = new Appointment("Другое место", startDate, endDate, new MailAddress("newcustomeronnet@gmail.com"),
        MailAddressCollection.to_MailAddressCollection("kashif.iqbal@aspose.com"));
appUpdate.setUniqueId(szUniqueId);
WeeklyRecurrencePattern pattern3 = (WeeklyRecurrencePattern) appUpdate.getRecurrence();
appUpdate.setSummary("обновленное резюме запроса на встречу");
appUpdate.setDescription("обновление");
MailMessage msgUpdate = new MailMessage("newcustomeronnet@gmail.com", "kashif.iqbal@aspose.com", "06 - тестовое письмо - обновление запроса на встречу", "тестовое письмо");
msgUpdate.addAlternateView(appUpdate.updateAppointment());
SmtpClient smtp = new SmtpClient("server.domain.com", 587, "username", "password");
smtp.send(msgUpdate);
~~~