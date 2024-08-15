---
title: "Trabajar con los elementos del calendario de Outlook"
url: /es/java/working-with-outlook-calendar-items/
weight: 120
type: docs
---

## **Trabajando con MapiCalendar**

Aspose.Email's [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) La clase proporciona métodos y atributos para establecer varias propiedades de un elemento del calendario. Este artículo proporciona ejemplos de código para:

- [**Trabajando con MapiCalendar**](#working-with-mapicalendar)
  - [**Creación y almacenamiento de elementos del calendario**](#creating-and-saving-calendar-items)
  - [**Guardar el elemento del calendario como MSG**](#saving-the-calendar-item-as-msg)
  - [**Agregar un recordatorio de pantalla a un calendario**](#adding-display-reminder-to-a-calendar)
  - [**Añadir un recordatorio de audio a un calendario**](#adding-audio-reminder-to-a-calendar)
  - [**Añadir/recuperar archivos adjuntos de archivos de calendario**](#addretrieve-attachments-from-calendar-files)
  - [**Estado de los destinatarios de una convocatoria de reunión**](#status-of-recipients-from-a-meeting-request)
  - [**Crear MapiCalendarTimezone a partir de una zona horaria estándar**](#create-mapicalendartimezone-from-standard-timezone)
- [**Configurar un recordatorio con la cita creada**](#setting-reminder-with-the-created-appointment)
  - [**Establecer un recordatorio añadiendo etiquetas**](#setting-a-reminder-by-adding-tags)
- [**Convierta Appointment EML a MSG con HTML Body**](#convert-appointment-eml-to-msg-with-html-body)


### **Creación y almacenamiento de elementos del calendario**

El siguiente fragmento de código muestra cómo crear y guardar un elemento del calendario en formato ICS.

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

### **Guardar el elemento del calendario como MSG**

El siguiente fragmento de código muestra cómo guardar el elemento del calendario como MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
calendar.save(dataDir + "CalendarItemAsMSG_out.Msg", AppointmentSaveFormat.Msg);
~~~

### **Configuración de un identificador de producto al guardar un elemento del calendario en ICS**

The [ProductIdentifier](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#getProductIdentifier--) propiedad del [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) La clase se usa para guardar un elemento del calendario MAPI en un archivo iCalendar (ICS) que conserva la información original de fecha y hora, así como un identificador de producto personalizado. La propiedad especifica el identificador del producto que creó el objeto iCalendar.

El siguiente ejemplo de código muestra cómo trabajar con datos de iCalendar (ICS) en un objeto de calendario MAPI:

```java
MapiCalendarIcsSaveOptions icsSaveOptions = new MapiCalendarIcsSaveOptions();
icsSaveOptions.setKeepOriginalDateTimeStamp(true);
icsSaveOptions.setProductIdentifier("Foo Ltd");

mapiCalendar.save("my.ics", icsSaveOptions);
```

### **Agregar un recordatorio de pantalla a un calendario**

En el siguiente fragmento de código, se muestra cómo añadir un recordatorio de pantalla a un calendario.

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

### **Añadir un recordatorio de audio a un calendario**

En el siguiente fragmento de código, se muestra cómo añadir un recordatorio de audio a un calendario.

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

### **Añadir/recuperar archivos adjuntos de archivos de calendario**

El siguiente fragmento de código muestra cómo añadir o recuperar archivos adjuntos de los archivos de calendario.

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

### **Estado de los destinatarios de una convocatoria de reunión**

El siguiente fragmento de código muestra cómo obtener el estado de los destinatarios de una convocatoria de reunión.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
for (MapiRecipient recipient : message.getRecipients()) {
    System.out.println(recipient.getRecipientTrackStatus());
}
~~~

### **Crear MapiCalendarTimezone a partir de una zona horaria estándar**

El siguiente fragmento de código muestra cómo crear [MapiCalendarTimeZone](https://reference.aspose.com/email/java/com.aspose.email/mapicalendartimezone/) desde la zona horaria estándar.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarTimeZone timeZone = new MapiCalendarTimeZone("Eastern Standard Time");
~~~

## **Configurar un recordatorio con la cita creada**

Se puede agregar un recordatorio cuando se crea una cita. Estas alarmas pueden activarse en función de diferentes criterios, como n minutos antes de que comience la programación o repetirse n veces a intervalos de n. Se pueden usar diferentes etiquetas para crear estos activadores en el script incluido entre BEGIN:VALARM y END:VALARM dentro de una cita. Hay varias variantes en las que se puede configurar el recordatorio en una cita.

### **Establecer un recordatorio añadiendo etiquetas**

En el siguiente fragmento de código, se muestra cómo configurar un recordatorio añadiendo etiquetas.

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

## **Convierta Appointment EML a MSG con HTML Body**

Desde la versión 19.3, Aspose.Email ofrece la posibilidad de convertir Appointment EML en MSG conservando el cuerpo HTML de la cita. Aspose.Email proporciona un [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) propiedad que tiene un valor predeterminado de **true.** Cuando el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) está configurado en **true**, el organismo de la designación se convierte al formato RTF. Para mantener el formato del cuerpo de la cita en formato HTML, defina el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) to **false.**

El siguiente ejemplo demuestra el uso de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) propiedad para mantener el formato del cuerpo de la cita en formato HTML.

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
