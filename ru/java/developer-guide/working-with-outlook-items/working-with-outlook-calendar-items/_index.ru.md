---
title: "Работа с элементами календаря Outlook"
url: /ru/java/working-with-outlook-calendar-items/
weight: 120
type: docs
---

## **Работа с MapiCalendar**

Aspose.Email's [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) класс предоставляет методы и атрибуты для установки различных свойств элемента календаря. В этой статье представлены примеры кода для:

- [**Работа с MapiCalendar**](#working-with-mapicalendar)
  - [**Создание и сохранение элементов календаря**](#creating-and-saving-calendar-items)
  - [**Сохранение элемента календаря в формате MSG**](#saving-the-calendar-item-as-msg)
  - [**Добавление экранного напоминания в календарь**](#adding-display-reminder-to-a-calendar)
  - [**Добавление звукового напоминания в календарь**](#adding-audio-reminder-to-a-calendar)
  - [**Добавление/извлечение вложений из файлов календаря**](#addretrieve-attachments-from-calendar-files)
  - [**Статус получателей приглашения на собрание**](#status-of-recipients-from-a-meeting-request)
  - [**Создание часового пояса Mapicalend из стандартного часового пояса**](#create-mapicalendartimezone-from-standard-timezone)
- [**Настройка напоминания с созданной встречей**](#setting-reminder-with-the-created-appointment)
  - [**Настройка напоминания путем добавления тегов**](#setting-a-reminder-by-adding-tags)
- [**Преобразуйте EML встречи в MSG с помощью HTML-текста**](#convert-appointment-eml-to-msg-with-html-body)


### **Создание и сохранение элементов календаря**

В следующем фрагменте кода показано, как создать и сохранить элемент календаря в формате ICS.

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

В следующем фрагменте кода показано, как сохранить элемент календаря в формате MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
calendar.save(dataDir + "CalendarItemAsMSG_out.Msg", AppointmentSaveFormat.Msg);
~~~

### **Настройка идентификатора продукта при сохранении элемента календаря в ICS**

The [ProductIdentifier](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#getProductIdentifier--) собственность [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) класс используется для сохранения элемента календаря MAPI в файл iCalendar (ICS) с сохранением исходной информации о дате и времени, а также пользовательского идентификатора продукта. Свойство указывает идентификатор продукта, создавшего объект iCalendar.

В следующем примере кода показано, как работать с данными iCalendar (ICS) в объекте календаря MAPI:

```java
MapiCalendarIcsSaveOptions icsSaveOptions = new MapiCalendarIcsSaveOptions();
icsSaveOptions.setKeepOriginalDateTimeStamp(true);
icsSaveOptions.setProductIdentifier("Foo Ltd");

mapiCalendar.save("my.ics", icsSaveOptions);
```

### **Добавление экранного напоминания в календарь**

В следующем фрагменте кода показано, как добавить напоминание о отображении в календарь.

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
// Create Appointment
Appointment app = new Appointment("Home",
                                  startDate,
                                  endDate,
                                  new MailAddress("organizer@domain.com", "Organizer"),
                                  attendees);
MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar calendar = (MapiCalendar) mapi.toMapiMessageItem();

// Set calendar Properties
calendar.setReminderSet(true);
calendar.setReminderDelta(5); // 45 min before start of event

String savedFile = (dataDir + "calendarWithDisplayReminder.ics");
calendar.save(savedFile, AppointmentSaveFormat.Ics);
~~~

### **Добавление звукового напоминания в календарь**

В следующем фрагменте кода показано, как добавить звуковое напоминание в календарь.

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
cal.setReminderDelta(58); // 58 min before start of event
cal.setReminderFileParameter(dataDir + "Alarm01.wav");

String savedFile = dataDir + "calendarWithAudioReminder_out.ics";
cal.save(savedFile, AppointmentSaveFormat.Ics);
~~~

### **Добавление/извлечение вложений из файлов календаря**

В следующем фрагменте кода показано, как добавлять/извлекать вложения из файлов календаря.

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

### **Статус получателей приглашения на собрание**

В следующем фрагменте кода показано, как узнать статус получателей приглашения на собрание.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
for (MapiRecipient recipient : message.getRecipients()) {
    System.out.println(recipient.getRecipientTrackStatus());
}
~~~

### **Создание часового пояса Mapicalend из стандартного часового пояса**

В следующем фрагменте кода показано, как создать [MapiCalendarTimeZone](https://reference.aspose.com/email/java/com.aspose.email/mapicalendartimezone/) из стандартного часового пояса.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarTimeZone timeZone = new MapiCalendarTimeZone("Eastern Standard Time");
~~~

## **Настройка напоминания с созданной встречей**

Напоминание можно добавить при создании встречи. Эти сигналы могут срабатывать по разным критериям, например, за n минут до начала расписания и повторяться n раз с интервалом n раз. Для создания этих триггеров можно использовать разные теги в скрипте, прилагаемом к командам BEGIN:VALARM и END:VALARM во время встречи. Существует несколько вариантов, в которых напоминание можно установить во время встречи.

### **Настройка напоминания путем добавления тегов**

В следующем фрагменте кода показано, как настроить напоминание, добавляя теги.

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

// Audio alarm that will sound at a precise time and
// Repeat 4 more times at 15 minute intervals:
AppointmentReminder audioReminder = new AppointmentReminder();
audioReminder.setTrigger(new ReminderTrigger(getDate(1997, 3, 17, 13, 30, 0)));
audioReminder.setRepeat(4);
audioReminder.setDuration(new ReminderDuration(15 * MIN_MS));
audioReminder.setAction(ReminderAction.Audio);
ReminderAttachment attach = new ReminderAttachment(new URI("ftp://Host.com/pub/sounds/bell-01.aud"));
audioReminder.getAttachments().addItem(attach);
target.getReminders().addItem(audioReminder);


// Display alarm that will trigger 30 minutes before the
// Scheduled start of the event it is
// Associated with and will repeat 2 more times at 15 minute intervals:
AppointmentReminder displayReminder = new AppointmentReminder();
ReminderDuration dur = new ReminderDuration(-30 * MIN_MS);
displayReminder.setTrigger(new ReminderTrigger(dur, ReminderRelated.Start));
displayReminder.setRepeat(2);
displayReminder.setDuration(new ReminderDuration(15 * MIN_MS));
displayReminder.setAction(ReminderAction.Display);
displayReminder.setDescription("Breakfast meeting with executive team at 8:30 AM EST");
target.getReminders().addItem(displayReminder);

// Email alarm that will trigger 2 days before the
// Scheduled due date/time. It does not
// Repeat. The email has a subject, body and attachment link.
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

// Procedural alarm that will trigger at a precise date/time
// And will repeat 23 more times at one hour intervals. The alarm will
// Invoke a procedure file.
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

## **Преобразуйте EML встречи в MSG с помощью HTML-текста**

Начиная с версии 19.3, Aspose.Email предоставляет возможность конвертировать EML встречи в MSG, сохраняя при этом текст встречи в формате HTML. Aspose.Email предоставляет [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) свойство, значение которого по умолчанию равно **true.** Когда значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) настроен на **true**, текст записи преобразуется в формат RTF. Чтобы сохранить формат текста встречи в формате HTML, задайте значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) to **false.**

В следующем примере показано использование [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) свойство сохранять формат тела встречи в формате HTML.

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
