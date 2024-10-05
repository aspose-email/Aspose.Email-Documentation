---
title: "Работа с элементами календаря Outlook"
url: /ru/java/working-with-outlook-calendar-items/
weight: 120
type: docs
---

## **Работа с MapiCalendar**

Класс Aspose.Email's [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) предоставляет методы и атрибуты для установки различных свойств элемента календаря. Эта статья содержит примеры кода для:

- [**Работа с MapiCalendar**](#working-with-mapicalendar)
  - [**Создание и сохранение элементов календаря**](#creating-and-saving-calendar-items)
  - [**Сохранение элемента календаря в формате MSG**](#saving-the-calendar-item-as-msg)
  - [**Добавление напоминания о показе в календарь**](#adding-display-reminder-to-a-calendar)
  - [**Добавление звукового напоминания в календарь**](#adding-audio-reminder-to-a-calendar)
  - [**Добавление/Извлечение вложений из файлов календаря**](#addretrieve-attachments-from-calendar-files)
  - [**Статус получателей в запросе на встречу**](#status-of-recipients-from-a-meeting-request)
  - [**Создание MapiCalendarTimeZone из стандартного часового пояса**](#create-mapicalendartimezone-from-standard-timezone)
- [**Установка напоминания с созданным назначением**](#setting-reminder-with-the-created-appointment)
  - [**Установка напоминания путем добавления тегов**](#setting-a-reminder-by-adding-tags)
- [**Преобразование EML назначения в MSG с HTML содержимым**](#convert-appointment-eml-to-msg-with-html-body)

### **Создание и сохранение элементов календаря**

Следующий фрагмент кода показывает, как создать и сохранить элемент календаря в формате ICS.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

Calendar cal = Calendar.getInstance();
cal.set(2012, Calendar.OCTOBER, 2, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2012, Calendar.OCTOBER, 2, 14, 0, 0);
Date endDate = cal.getTime();

MapiCalendar calendar = new MapiCalendar("LAKE ARGYLE WA 6743", 
                                         "Appointment", 
                                         "This is a very important meeting :)", 
                                         startDate, 
                                         endDate);

calendar.save(dataDir + "CalendarItem_out.ics", AppointmentSaveFormat.Ics);
~~~ 

### **Сохранение элемента календаря в формате MSG**

Следующий фрагмент кода показывает, как сохранить элемент календаря в формате MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
calendar.save(dataDir + "CalendarItemAsMSG_out.Msg", AppointmentSaveFormat.Msg);
~~~ 

### **Установка идентификатора продукта при сохранении элемента календаря в ICS**

Свойство [ProductIdentifier](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#getProductIdentifier--) класса [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) используется для сохранения элемента календаря MAPI в файл iCalendar (ICS), сохраняя при этом оригинальную информацию о дате и времени, а также пользовательский идентификатор продукта. Это свойство указывает идентификатор продукта, который создал объект iCalendar.

Следующий пример показывает, как работать с данными iCalendar (ICS) в объекте календаря MAPI:

```java
MapiCalendarIcsSaveOptions icsSaveOptions = new MapiCalendarIcsSaveOptions();
icsSaveOptions.setKeepOriginalDateTimeStamp(true);
icsSaveOptions.setProductIdentifier("Foo Ltd");

mapiCalendar.save("my.ics", icsSaveOptions);
``` 

### **Добавление напоминания о показе в календарь**

Следующий фрагмент кода показывает, как добавить напоминание о показе в календарь.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Attendee"));
// Создание назначения
Appointment app = new Appointment("Home", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizer"), 
                                  attendees);
MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar calendar = (MapiCalendar) mapi.toMapiMessageItem();

// Установка свойств календаря
calendar.setReminderSet(true);
calendar.setReminderDelta(5); // 45 мин до начала события

String savedFile = (dataDir + "calendarWithDisplayReminder.ics");
calendar.save(savedFile, AppointmentSaveFormat.Ics);
~~~ 

### **Добавление звукового напоминания в календарь**

Следующий фрагмент кода показывает, как добавить звуковое напоминание в календарь.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Attendee"));

Appointment app = new Appointment("Home", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizer"), 
                                  attendees);

MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar cal = (MapiCalendar) mapi.toMapiMessageItem();

cal.setReminderSet(true);
cal.setReminderDelta(58); // 58 мин до начала события
cal.setReminderFileParameter(dataDir + "Alarm01.wav");

String savedFile = dataDir + "calendarWithAudioReminder_out.ics";
cal.save(savedFile, AppointmentSaveFormat.Ics);
~~~ 

### **Добавление/Извлечение вложений из файлов календаря**

Следующий фрагмент кода показывает, как добавлять/извлекать вложения из файлов календаря.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

String[] files = new String[3];
files[0] = "attachment_1.doc";
files[1] = "download.png";
files[2] = "Desert.jpg";

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Attendee"));

Appointment app1 = new Appointment("Home", 
                                   startDate, 
                                   endDate, 
                                   new MailAddress("organizer@domain.com", "Organizer"), 
                                   attendees);
for (String file : files) {
    app1.getAttachments().addItem(new Attachment(dataDir + file));
}

app1.save(dataDir + "appWithAttachments_out.ics", AppointmentSaveFormat.Ics);

Appointment app2 = Appointment.load(dataDir + "appWithAttachments_out.ics");
System.out.println(app2.getAttachments().size());
for (Attachment att : app2.getAttachments())
    System.out.println(att.getName());
~~~ 

### **Статус получателей в запросе на встречу**

Следующий фрагмент кода показывает, как получить статус получателей из запроса на встречу.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
for (MapiRecipient recipient : message.getRecipients()) {
    System.out.println(recipient.getRecipientTrackStatus());
}
~~~ 

### **Создание MapiCalendarTimeZone из стандартного часового пояса**

Следующий фрагмент кода показывает, как создать [MapiCalendarTimeZone](https://reference.aspose.com/email/java/com.aspose.email/mapicalendartimezone/) из стандартного часового пояса.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarTimeZone timeZone = new MapiCalendarTimeZone("Eastern Standard Time");
~~~ 

## **Установка напоминания с созданным назначением**

Напоминание может быть добавлено при создании назначения. Эти сигналы могут срабатывать на основе различных критериев, таких как n минут до начала расписания, повторение n раз с интервалом n. Разные теги могут использоваться для создания этих триггеров в скрипте, заключенном между BEGIN:VALARM и END:VALARM внутри назначения. Существует множество вариантов, по которым напоминание может быть установлено в назначении.

### **Установка напоминания путем добавления тегов**

Следующий фрагмент кода показывает, как установить напоминание, добавив теги.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();
long MIN_MS = 60 * 1000;
long HR_MS = 60 * MIN_MS;
long DAY_MS = 24 * HR_MS;

String location = "Meeting Location: Room 5";
Date startDate = getDate(1997, 3, 18, 18, 30, 00);
Date endDate = getDate(1997, 3, 18, 19, 30, 00);
MailAddress organizer = new MailAddress("aaa@amail.com", "Organizer");
MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("bbb@bmail.com", "First attendee"));

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

// Звуковой сигнал, который прозвучит в определенное время и
// повторится 4 раза с интервалами в 15 минут:
AppointmentReminder audioReminder = new AppointmentReminder();
audioReminder.setTrigger(new ReminderTrigger(getDate(1997, 3, 17, 13, 30, 0)));
audioReminder.setRepeat(4);
audioReminder.setDuration(new ReminderDuration(15 * MIN_MS));
audioReminder.setAction(ReminderAction.Audio);
ReminderAttachment attach = new ReminderAttachment(new URI("ftp://Host.com/pub/sounds/bell-01.aud"));
audioReminder.getAttachments().addItem(attach);
target.getReminders().addItem(audioReminder);

// Дисплейный сигнал, который сработает за 30 минут до
// запланированного начала мероприятия, с
// повторением 2 раза с интервалами в 15 минут:
AppointmentReminder displayReminder = new AppointmentReminder();
ReminderDuration dur = new ReminderDuration(-30 * MIN_MS);
displayReminder.setTrigger(new ReminderTrigger(dur, ReminderRelated.Start));
displayReminder.setRepeat(2);
displayReminder.setDuration(new ReminderDuration(15 * MIN_MS));
displayReminder.setAction(ReminderAction.Display);
displayReminder.setDescription("Breakfast meeting with executive team at 8:30 AM EST");
target.getReminders().addItem(displayReminder);

// Электронное напоминание, которое сработает за 2 дня до
// запланированного срока. Оно не
// повторяется. Электронное письмо содержит тему, текст и ссылку на вложение.
AppointmentReminder emailReminder = new AppointmentReminder();
ReminderDuration dur1 = new ReminderDuration(-2 * DAY_MS);
emailReminder.setTrigger(new ReminderTrigger(dur1, ReminderRelated.Start));
ReminderAttendee attendee = new ReminderAttendee("john_doe@host.com");
emailReminder.getAttendees().addItem(attendee);
emailReminder.setAction(ReminderAction.Email);
emailReminder.setSummary("REMINDER: SEND AGENDA FOR WEEKLY STAFF MEETING");
emailReminder.setDescription("A draft agenda needs to be sent out to the attendees to the weekly managers meeting (MGR-LIST). Attached is a pointer the document template for the agenda file.");
ReminderAttachment attach1 = new ReminderAttachment(new URI("http://Host.com/templates/agenda.doc"));
emailReminder.getAttachments().addItem(attach1);
target.getReminders().addItem(emailReminder);

// Процедурный сигнал, который сработает в определенную дату/время
// и повторится еще 23 раза с интервалами в один час. Сигнал
// вызовет файл процедуры.
AppointmentReminder procReminder = new AppointmentReminder();
procReminder.setTrigger(new ReminderTrigger(getDate(1998, 1, 1, 5, 0, 0)));
procReminder.setRepeat(23);
procReminder.setDuration(new ReminderDuration(1 * DAY_MS));
procReminder.setAction(ReminderAction.Procedure);
ReminderAttachment attach2 = new ReminderAttachment(new URI("ftp://Host.com/novo-procs/felizano.exe"));
procReminder.getAttachments().addItem(attach2);
target.getReminders().addItem(procReminder);
target.save(dataDir + "savedFile_out.ics");
~~~ 

## **Преобразование EML назначения в MSG с HTML содержимым**

С версии 19.3 Aspose.Email предоставляет возможность преобразования назначения EML в MSG с сохранением HTML содержимого назначения. Aspose.Email предоставляет свойство [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) с умолчательным значением **true.** Когда значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) установлено в **true**, тело назначения преобразуется в формат RTF. Чтобы сохранить формат тела назначения в формате HTML, установите значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) в **false.**

Следующий пример демонстрирует использование свойства [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) для сохранения формата тела назначения в формате HTML.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage mailMessage = MailMessage.load(dataDir + "TestAppointment.eml");

MapiConversionOptions conversionOptions = new MapiConversionOptions();
conversionOptions.setFormat(OutlookMessageFormat.Unicode);

// default value for ForcedRtfBodyForAppointment is true
conversionOptions.setForcedRtfBodyForAppointment(false);

MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, conversionOptions);

if (mapiMessage.getBodyType() == BodyContentType.Html) {
    System.out.println("Body Type: Html");
} else if (mapiMessage.getBodyType() == BodyContentType.Rtf) {
    System.out.println("Body Type: Rtf");
}

mapiMessage.save(dataDir + "TestAppointment_out.msg");
~~~