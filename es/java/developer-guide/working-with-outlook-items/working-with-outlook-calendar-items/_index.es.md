---
title: "Trabajando con Elementos del Calendario de Outlook"
url: /es/java/working-with-outlook-calendar-items/
weight: 120
type: docs
---

## **Trabajando con MapiCalendar**

La clase [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) de Aspose.Email proporciona métodos y atributos para establecer diversas propiedades de un elemento del calendario. Este artículo proporciona ejemplos de código para:

- [**Trabajando con MapiCalendar**](#working-with-mapicalendar)
  - [**Creando y Guardando Elementos del Calendario**](#creating-and-saving-calendar-items)
  - [**Guardando el Elemento del Calendario como MSG**](#saving-the-calendar-item-as-msg)
  - [**Añadiendo Recordatorio Visual a un Calendario**](#adding-display-reminder-to-a-calendar)
  - [**Añadiendo Recordatorio de Audio a un Calendario**](#adding-audio-reminder-to-a-calendar)
  - [**Añadir/Recuperar Adjuntos de Archivos del Calendario**](#addretrieve-attachments-from-calendar-files)
  - [**Estado de los Destinatarios de una Solicitud de Reunión**](#status-of-recipients-from-a-meeting-request)
  - [**Crear MapiCalendarTimeZone desde la Zona Horaria Estándar**](#create-mapicalendartimezone-from-standard-timezone)
- [**Estableciendo Recordatorio con la Cita Creada**](#setting-reminder-with-the-created-appointment)
  - [**Estableciendo un Recordatorio Añadiendo Etiquetas**](#setting-a-reminder-by-adding-tags)
- [**Convertir Cita EML a MSG con Cuerpo HTML**](#convert-appointment-eml-to-msg-with-html-body)


### **Creando y Guardando Elementos del Calendario**

El siguiente fragmento de código muestra cómo crear y guardar un elemento del calendario en formato ICS.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
String dataDir = "outlook/";

Calendar cal = Calendar.getInstance();
cal.set(2012, Calendar.OCTOBER, 2, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2012, Calendar.OCTOBER, 2, 14, 0, 0);
Date endDate = cal.getTime();

MapiCalendar calendar = new MapiCalendar("LAKE ARGYLE WA 6743", 
                                         "Cita", 
                                         "Esta es una reunión muy importante :)", 
                                         startDate, 
                                         endDate);

calendar.save(dataDir + "CalendarItem_out.ics", AppointmentSaveFormat.Ics);
~~~

### **Guardando el Elemento del Calendario como MSG**

El siguiente fragmento de código muestra cómo guardar el elemento del calendario como MSG.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
calendar.save(dataDir + "CalendarItemAsMSG_out.Msg", AppointmentSaveFormat.Msg);
~~~

### **Estableciendo un ID de producto al guardar un Elemento del Calendario en ICS**

La propiedad [ProductIdentifier](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#getProductIdentifier--) de la clase [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) se utiliza para guardar un elemento del calendario MAPI en un archivo iCalendar (ICS) preservando la información de fecha y hora original así como un identificador de producto personalizado. La propiedad especifica el identificador del producto que creó el objeto iCalendar.

El siguiente ejemplo de código muestra cómo trabajar con datos de iCalendar (ICS) dentro de un objeto de calendario MAPI:

```java
MapiCalendarIcsSaveOptions icsSaveOptions = new MapiCalendarIcsSaveOptions();
icsSaveOptions.setKeepOriginalDateTimeStamp(true);
icsSaveOptions.setProductIdentifier("Foo Ltd");

mapiCalendar.save("my.ics", icsSaveOptions);
```

### **Añadiendo Recordatorio Visual a un Calendario**

El siguiente fragmento de código muestra cómo añadir un recordatorio visual a un calendario.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Asistente"));
// Crear Cita
Appointment app = new Appointment("Inicio", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizador"), 
                                  attendees);
MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar calendar = (MapiCalendar) mapi.toMapiMessageItem();

// Establecer Propiedades del calendario
calendar.setReminderSet(true);
calendar.setReminderDelta(5); // 45 min antes del inicio del evento

String savedFile = (dataDir + "calendarWithDisplayReminder.ics");
calendar.save(savedFile, AppointmentSaveFormat.Ics);
~~~

### **Añadiendo Recordatorio de Audio a un Calendario**

El siguiente fragmento de código muestra cómo añadir un recordatorio de audio a un calendario.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
String dataDir = "outlook/";
Calendar jCalendar = Calendar.getInstance();
jCalendar.add(Calendar.HOUR, 1);
Date startDate = jCalendar.getTime();
Date endDate = jCalendar.getTime();

MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("attendee@domain.com", "Asistente"));

Appointment app = new Appointment("Inicio", 
                                  startDate, 
                                  endDate, 
                                  new MailAddress("organizer@domain.com", "Organizador"), 
                                  attendees);

MailMessage msg = new MailMessage();
msg.addAlternateView(app.requestApointment());
MapiMessage mapi = MapiMessage.fromMailMessage(msg);
MapiCalendar cal = (MapiCalendar) mapi.toMapiMessageItem();

cal.setReminderSet(true);
cal.setReminderDelta(58); // 58 min antes del inicio del evento
cal.setReminderFileParameter(dataDir + "Alarm01.wav");

String savedFile = dataDir + "calendarWithAudioReminder_out.ics";
cal.save(savedFile, AppointmentSaveFormat.Ics);
~~~

### **Añadir/Recuperar Adjuntos de Archivos del Calendario**

El siguiente fragmento de código muestra cómo añadir/recuperar adjuntos de archivos del calendario.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
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
attendees.addItem(new MailAddress("attendee@domain.com", "Asistente"));

Appointment app1 = new Appointment("Inicio", 
                                   startDate, 
                                   endDate, 
                                   new MailAddress("organizer@domain.com", "Organizador"), 
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

### **Estado de los Destinatarios de una Solicitud de Reunión**

El siguiente fragmento de código muestra cómo obtener el estado de los destinatarios de una solicitud de reunión.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
for (MapiRecipient recipient : message.getRecipients()) {
    System.out.println(recipient.getRecipientTrackStatus());
}
~~~

### **Crear MapiCalendarTimeZone desde la Zona Horaria Estándar**

El siguiente fragmento de código muestra cómo crear [MapiCalendarTimeZone](https://reference.aspose.com/email/java/com.aspose.email/mapicalendartimezone/) desde la zona horaria estándar.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarTimeZone timeZone = new MapiCalendarTimeZone("Hora Estándar del Este");
~~~

## **Estableciendo Recordatorio con la Cita Creada**

Se puede añadir un recordatorio cuando se crea una cita. Estas alarmas pueden activarse en función de diferentes criterios, como n minutos antes de que comience el programa, repetir n veces a intervalos de n. Se pueden utilizar diferentes etiquetas para crear estos disparadores en el script encerrado entre BEGIN:VALARM y END:VALARM dentro de una cita. Hay varias variantes en las que se puede establecer el recordatorio en una cita.

### **Estableciendo un Recordatorio Añadiendo Etiquetas**

El siguiente fragmento de código muestra cómo establecer un recordatorio añadiendo etiquetas.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
String dataDir = RunExamples.getDataDir_Outlook();
long MIN_MS = 60 * 1000;
long HR_MS = 60 * MIN_MS;
long DAY_MS = 24 * HR_MS;

String location = "Ubicación de la Reunión: Sala 5";
Date startDate = getDate(1997, 3, 18, 18, 30, 00);
Date endDate = getDate(1997, 3, 18, 19, 30, 00);
MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");
MailAddressCollection attendees = new MailAddressCollection();
attendees.addItem(new MailAddress("bbb@bmail.com", "Primer asistente"));

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);

// Alarmas de audio que sonarán en un momento preciso y
// Repetir 4 veces más en intervalos de 15 minutos:
AppointmentReminder audioReminder = new AppointmentReminder();
audioReminder.setTrigger(new ReminderTrigger(getDate(1997, 3, 17, 13, 30, 0)));
audioReminder.setRepeat(4);
audioReminder.setDuration(new ReminderDuration(15 * MIN_MS));
audioReminder.setAction(ReminderAction.Audio);
ReminderAttachment attach = new ReminderAttachment(new URI("ftp://Host.com/pub/sounds/bell-01.aud"));
audioReminder.getAttachments().addItem(attach);
target.getReminders().addItem(audioReminder);


// Alarmas visuales que se activarán 30 minutos antes del
// Inicio programado del evento con el que están
// Asociadas y se repetirán 2 veces más a intervalos de 15 minutos:
AppointmentReminder displayReminder = new AppointmentReminder();
ReminderDuration dur = new ReminderDuration(-30 * MIN_MS);
displayReminder.setTrigger(new ReminderTrigger(dur, ReminderRelated.Start));
displayReminder.setRepeat(2);
displayReminder.setDuration(new ReminderDuration(15 * MIN_MS));
displayReminder.setAction(ReminderAction.Display);
displayReminder.setDescription("Reunión de desayuno con el equipo ejecutivo a las 8:30 AM EST");
target.getReminders().addItem(displayReminder);

// Alarmas por email que se activarán 2 días antes de la
// Fecha/hora límite programada. No se repite. El email tiene un asunto, cuerpo y enlace de adjunto.
AppointmentReminder emailReminder = new AppointmentReminder();
ReminderDuration dur1 = new ReminderDuration(-2 * DAY_MS);
emailReminder.setTrigger(new ReminderTrigger(dur1, ReminderRelated.Start));
ReminderAttendee attendee = new ReminderAttendee("john_doe@host.com");
emailReminder.getAttendees().addItem(attendee);
emailReminder.setAction(ReminderAction.Email);
emailReminder.setSummary("RECORDATORIO: ENVIAR AGENDA PARA LA REUNIÓN SEMANAL DEL PERSONAL");
emailReminder.setDescription("Se necesita enviar un borrador de agenda a los asistentes a la reunión semanal de gerentes (MGR-LIST). Adjunta está una referencia al documento plantilla para el archivo de agenda.");
ReminderAttachment attach1 = new ReminderAttachment(new URI("http://Host.com/templates/agenda.doc"));
emailReminder.getAttachments().addItem(attach1);
target.getReminders().addItem(emailReminder);

// Alarmas procesales que se activarán en una fecha/hora precisa
// Y se repetirán 23 veces más a intervalos de una hora. La alarma
// Invocará un archivo de procedimiento.
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

## **Convertir Cita EML a MSG con Cuerpo HTML**

Desde la versión 19.3, Aspose.Email proporciona la capacidad de convertir Cita EML a MSG mientras conserva el cuerpo HTML de la cita. Aspose.Email proporciona una [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) propiedad que tiene un valor por defecto de **true.** Cuando el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) se establece en **true**, el cuerpo de la cita se convierte al formato RTF. Para mantener el formato del cuerpo de la cita en formato HTML, establezca el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) en **false.**

El siguiente ejemplo demuestra el uso de la propiedad [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#getForcedRtfBodyForAppointment--) para mantener el formato del cuerpo de la cita en formato HTML.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
String dataDir = "outlook/";

MailMessage mailMessage = MailMessage.load(dataDir + "TestAppointment.eml");

MapiConversionOptions conversionOptions = new MapiConversionOptions();
conversionOptions.setFormat(OutlookMessageFormat.Unicode);

// valor por defecto para ForcedRtfBodyForAppointment es true
conversionOptions.setForcedRtfBodyForAppointment(false);

MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, conversionOptions);

if (mapiMessage.getBodyType() == BodyContentType.Html) {
    System.out.println("Tipo de Cuerpo: Html");
} else if (mapiMessage.getBodyType() == BodyContentType.Rtf) {
    System.out.println("Tipo de Cuerpo: Rtf");
}

mapiMessage.save(dataDir + "TestAppointment_out.msg");
~~~