---
title: "Trabajando con elementos del calendario de Outlook"
url: /es/python-net/working-with-outlook-calendar-items/
weight: 80
type: docs
---

## **Trabajando con MapiCalendar**
La clase MapiCalendar de Aspose.Email proporciona métodos y atributos para establecer varias propiedades de un elemento del calendario.

### **Creando y guardando elementos del calendario**
El siguiente fragmento de código muestra cómo crear y guardar un elemento del calendario en formato ICS.

```cs
import aspose.email as ae
from datetime import datetime

data_dir = "path/to/data/directory"

# Crear la cita
calendar = ae.mapi.MapiCalendar(
    "LAKE ARGYLE WA 6743",
    "Cita",
    "Esta es una reunión muy importante :)",
    datetime(2012, 4, 1),
    datetime(2012, 5, 1))

calendar.save(data_dir + "CalendarItem_out.ics", ae.calendar.AppointmentSaveFormat.ICS)
```
### **Guardando el elemento del calendario como MSG**
El siguiente fragmento de código muestra cómo guardar el elemento del calendario como MSG.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveCalendarItems-CreateAndSaveCalendarItems.py" >}}

### **Estableciendo un ID de producto al guardar MapiCalendar en ICS**

La biblioteca Aspose.Email permite guardar un MapiCalendar (un elemento del calendario) en un archivo ICS (iCalendar) con opciones específicas. Con las propiedades *ics_save_options.keep_original_date_time_stamp* y *ics_save_options.product_identifier* puedes conservar las marcas de tiempo originales asociadas con el elemento del calendario y establecer el identificador del producto en el archivo ICS, por ejemplo, "Foo Ltd". El identificador del producto es un campo que identifica el software o servicio que generó el archivo ICS.

Aquí tienes un ejemplo de código que te permite establecer un ID de producto al guardar MapiCalendar en ICS:

```python
import aspose.email as ae

ics_save_options = ae.mapi.MapiCalendarIcsSaveOptions()
ics_save_options.keep_original_date_time_stamp = True
ics_save_options.product_identifier = "Foo Ltd"

mapiCalendar.save("my.ics", ics_save_options)
```
### **Obteniendo el número total de eventos**

La funcionalidad de la clase [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) te permite leer datos del calendario desde un archivo especificado. Al crear un objeto CalendarReader, podemos extraer información importante como el número total de eventos, la versión del calendario, el método utilizado y si el calendario contiene múltiples eventos. El siguiente fragmento de código demuestra cómo trabajar con datos de calendario y, adicionalmente, cargar las citas del calendario como una lista de múltiples eventos.

```python
import aspose.email as ae

reader = ae.calendar.CalendarReader(fileName)
print(f"El calendario contiene {reader.count} eventos")
print(f"La versión del calendario es {reader.version}")
print(f"El método del calendario es {reader.method}")
print(f"¿El calendario contiene múltiples eventos? - {reader.is_multi_events}")
appointments = reader.load_as_multiple()
```

### **Agregando un recordatorio de pantalla a un calendario**
El siguiente fragmento de código muestra cómo agregar un recordatorio de pantalla a un calendario.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddDisplayReminderToCalendar-AddDisplayReminderToCalendar.py" >}}
### **Agregando un recordatorio de audio a un calendario**
El siguiente fragmento de código muestra cómo agregar un recordatorio de audio a un calendario.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddAudioReminderToCalendar-AddAudioReminderToCalendar.py" >}}

### **Agregar/Recuperar adjuntos de archivos del calendario**

El módulo de Aspose.Email Calendar ("ae.calendar") también proporciona la funcionalidad para agregar y recuperar información de adjuntos. 

- Para incluir un adjunto con la cita, se crea un objeto "Attachment", proporcionando la ruta del archivo. Este adjunto se agrega a la lista de adjuntos de la cita. La cita se guarda en una ruta de archivo específica en formato iCalendar utilizando el [save](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) método y el formato de archivo apropiado.

- Para recuperar adjuntos de una cita, primero se carga desde el archivo guardado utilizando el [load](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) método, se muestra el número de adjuntos presentes en "appointment2", y al iterar sobre los adjuntos se imprimen sus nombres.

El siguiente fragmento de código demuestra cómo crear citas con adjuntos, guardarlas y recuperar información de adjuntos utilizando el módulo "ae.calendar". Destaca la funcionalidad y capacidades de trabajar con citas y adjuntos en una aplicación de calendario.

```python
import aspose.email as ae
import datetime as dt

# Agregar un adjunto a una cita
attendees = ae.MailAddressCollection()
attendees.append(ae.MailAddress("attendee@domain.com", "Destinatario 1"))

appointment = ae.calendar.Appointment("Sala 112", dt.datetime(2023, 5, 27), dt.date(2023, 5, 28),  ae.MailAddress("organizer@domain.com"), attendees)

attachment = ae.Attachment("D:\\Aspose\\Files\\Attachment.txt")
appointment.attachments.append(attachment)

appointment.save("D:\\Aspose\\Files\\appWithAttachments_out.ics", ae.calendar.AppointmentSaveFormat.ICS)

# Recuperar adjuntos de una cita 
appointment2 = ae.calendar.Appointment.load("D:\\Aspose\\Files\\appWithAttachments_out.ics")
print(appointment2.attachments.length)
for att in appointment2.attachments:
    print(att.name)
```
### **Estado de los destinatarios de una solicitud de reunión**
El siguiente fragmento de código muestra cómo obtener el estado de los destinatarios de una solicitud de reunión.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DisplayReceipientsStatusFromMeetingReqeust-DisplayReceipientsStatusFromMeetingReqeust.py" >}}

## **Convertir cita EML a MSG preservando el cuerpo en formato HTML**

Aspose.Email hace posible convertir una cita EML a MSG y preservar el cuerpo en HTML. La propiedad "forced_rtf_body_for_appointment" de la clase [MapiConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#mapiconversionoptions-class) se utiliza para manipular el tipo del cuerpo de la cita. Cuando se establece en *True*, el cuerpo se convierte al formato RTF por defecto. Para conservar el cuerpo en formato HTML, debe establecerse en *False*. El siguiente ejemplo de código muestra cómo preservar el cuerpo en HTML de la cita al convertirla de EML a MSG:

```python
import aspose.email as ae

eml = ae.MailMessage.load("appointment.eml")

conversionOptions = ae.mapi.MapiConversionOptions()
conversionOptions.format = ae.mapi.OutlookMessageFormat.UNICODE
# el valor predeterminado para ForcedRtfBodyForAppointment es verdadero
conversionOptions.forced_rtf_body_for_appointment = False

msg = ae.mapi.MapiMessage.from_mail_message(eml, conversionOptions)

print(f"Tipo de cuerpo: {msg.body_type}")

msg.save("appointment.msg")
```