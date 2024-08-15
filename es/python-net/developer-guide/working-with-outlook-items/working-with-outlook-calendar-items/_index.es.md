---
title: "Trabajar con los elementos del calendario de Outlook"
url: /es/python-net/working-with-outlook-calendar-items/
weight: 80
type: docs
---


## **Trabajando con MapiCalendar**
La clase MapiCalendar de Aspose.Email proporciona métodos y atributos para establecer varias propiedades de un elemento del calendario.

### **Creación y almacenamiento de elementos del calendario**
El siguiente fragmento de código muestra cómo crear y guardar un elemento del calendario en formato ICS.

```cs
import aspose.email as ae
from datetime import datetime

data_dir = "path/to/data/directory"

# Create the appointment
calendar = ae.mapi.MapiCalendar(
    "LAKE ARGYLE WA 6743",
    "Appointment",
    "This is a very important meeting :)",
    datetime(2012, 4, 1),
    datetime(2012, 5, 1))

calendar.save(data_dir + "CalendarItem_out.ics", ae.calendar.AppointmentSaveFormat.ICS)
```
### **Guardar el elemento del calendario como MSG**
El siguiente fragmento de código muestra cómo guardar el elemento del calendario como MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveCalendarItems-CreateAndSaveCalendarItems.py" >}}

### **Configuración de un identificador de producto al guardar MapiCalendar en ICS**

La biblioteca Aspose.Email le permite guardar un MapiCalendar (un elemento del calendario) en un archivo ICS (iCalendar) con opciones específicas. Con *ics_save_options.keep_original_date_time_stamp* and *ics_save_options.product_identifier* propiedades: puede conservar las marcas de fecha y hora originales asociadas al elemento del calendario y establecer el identificador del producto en el archivo ICS, por ejemplo, en «Foo Ltd», respectivamente. El identificador del producto es un campo que identifica el software o el servicio que generó el archivo ICS.

Este es un ejemplo de código que te permite establecer un identificador de producto al guardar MapiCalendar en ICS:

```python
import aspose.email as ae

ics_save_options = ae.mapi.MapiCalendarIcsSaveOptions()
ics_save_options.keep_original_date_time_stamp = True
ics_save_options.product_identifier = "Foo Ltd"

mapiCalendar.save("my.ics", ics_save_options)
```
### **Obtener el número total de eventos**

La funcionalidad del [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) La clase le permite leer los datos del calendario de un archivo específico. Al crear un objeto CalendarReader, podemos extraer información importante, como el número total de eventos, la versión del calendario, el método utilizado y si el calendario contiene varios eventos. El siguiente fragmento de código muestra cómo trabajar con los datos del calendario y, además, cargar las citas del calendario como una lista de varios eventos.

```python
import aspose.email as ae

reader = ae.calendar.CalendarReader(fileName)
print(f"Calendar contains {reader.count} events")
print(f"The Version of the calendar is {reader.version}")
print(f"The Method of the calendar is {reader.method}")
print(f"Is calendar contains contains multiple events? - {reader.is_multi_events}")
appointments = reader.load_as_multiple()
```

### **Añadir un recordatorio de pantalla a un calendario**
En el siguiente fragmento de código, se muestra cómo añadir un recordatorio de pantalla a un calendario.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddDisplayReminderToCalendar-AddDisplayReminderToCalendar.py" >}}
### **Añadir un recordatorio de audio a un calendario**
El siguiente fragmento de código muestra cómo añadir un recordatorio de audio a un calendario.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddAudioReminderToCalendar-AddAudioReminderToCalendar.py" >}}

### **Añadir/recuperar archivos adjuntos de archivos de calendario**

El módulo Aspose.Email Calendar («ae.calendar») también proporciona la funcionalidad de agregar y recuperar información adjunta.

- Para incluir un adjunto en la cita, se crea un objeto «Attachment» que proporciona la ruta del archivo. A continuación, este archivo adjunto se añade a la lista de archivos adjuntos de la cita. La cita se guarda en una ruta de archivo específica en formato iCalendar mediante el [save](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) método y el formato de archivo apropiado.

- Para recuperar los archivos adjuntos de una cita, primero se cargan desde el archivo guardado mediante el [load](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) método, se muestra el número de archivos adjuntos presentes en «cita2\" y, al iterar sobre los archivos adjuntos, se imprimen sus nombres.

El siguiente fragmento de código muestra cómo crear citas con archivos adjuntos, guardarlas y recuperar la información de los archivos adjuntos mediante el módulo «ae.calendar». Destaca la funcionalidad y las capacidades de trabajar con citas y archivos adjuntos en una aplicación de calendario.

```python
import aspose.email as ae
import datetime as dt

# Add an attachment to an appointment
attendees = ae.MailAddressCollection()
attendees.append(ae.MailAddress("attendee@domain.com", "Recipient 1"))

appointment = ae.calendar.Appointment("Room 112", dt.datetime(2023, 5, 27), dt.date(2023, 5, 28),  ae.MailAddress("organizer@domain.com"), attendees)

attachment = ae.Attachment("D:\\Aspose\\Files\\Attachment.txt")
appointment.attachments.append(attachment)

appointment.save("D:\\Aspose\\Files\\appWithAttachments_out.ics", ae.calendar.AppointmentSaveFormat.ICS)

# Retrieve attachments from an appointment
appointment2 = ae.calendar.Appointment.load("D:\\Aspose\\Files\\appWithAttachments_out.ics")
print(appointment2.attachments.length)
for att in appointment2.attachments:
    print(att.name)
```
### **Estado de los destinatarios de una convocatoria de reunión**
El siguiente fragmento de código muestra cómo determinar el estado de los destinatarios de una convocatoria de reunión.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DisplayReceipientsStatusFromMeetingReqeust-DisplayReceipientsStatusFromMeetingReqeust.py" >}}

## **Convierte EML Appointment en MSG conservando el cuerpo en formato HTML**

Aspose.Email permite convertir una cita EML en MSG y conservar el cuerpo HTML. La propiedad «forced_rtf_body_for_appointment» del [MapiConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#mapiconversionoptions-class) la clase se utiliza para manipular el tipo de órgano de nombramiento. Cuando se establece en *True*, el cuerpo se convierte al formato RTF por defecto. Para conservar el cuerpo en formato HTML, debe configurarse en *False*. El siguiente ejemplo de código muestra cómo conservar el cuerpo HTML de la cita al convertirla de EML a MSG:

```python
import aspose.email as ae

eml = ae.MailMessage.load("appointment.eml")

conversionOptions = ae.mapi.MapiConversionOptions()
conversionOptions.format = ae.mapi.OutlookMessageFormat.UNICODE
# default value for ForcedRtfBodyForAppointment is true
conversionOptions.forced_rtf_body_for_appointment = False

msg = ae.mapi.MapiMessage.from_mail_message(eml, conversionOptions)

print(f"Body Type: {msg.body_type}")

msg.save("appointment.msg")
```