---
title: "Trabajar con los elementos del calendario de Outlook"
url: /es/net/working-with-outlook-calendar-items/
weight: 120
type: docs
---


## **Trabajando con MapiCalendar**

La clase MapiCalendar de Aspose.Email proporciona métodos y atributos para establecer varias propiedades de un elemento del calendario. En este artículo se proporcionan ejemplos de código para:

- [**Trabajando con MapiCalendar**](#working-with-mapicalendar)
  - [**Creación y almacenamiento de elementos del calendario**](#creating-and-saving-calendar-items)
  - [**Guardar el elemento del calendario como MSG**](#saving-the-calendar-item-as-msg)
  - [**Añadir un recordatorio de pantalla a un calendario**](#adding-display-reminder-to-a-calendar)
  - [**Añadir un recordatorio de audio a un calendario**](#adding-audio-reminder-to-a-calendar)
  - [**Añadir/recuperar archivos adjuntos de archivos de calendario**](#addretrieve-attachments-from-calendar-files)
  - [**Estado de los destinatarios de una convocatoria de reunión**](#status-of-recipients-from-a-meeting-request)
  - [**Crear MapiCalendarTimezone a partir de una zona horaria estándar**](#create-mapicalendartimezone-from-standard-timezone)
- [**Configurar un recordatorio con la cita creada**](#setting-reminder-with-the-created-appointment)
  - [**Establecer un recordatorio añadiendo etiquetas**](#setting-a-reminder-by-adding-tags)
- [**Convierta Appointment EML a MSG con HTML Body**](#convert-appointment-eml-to-msg-with-html-body)
 
### **Creación y almacenamiento de elementos del calendario**

El siguiente fragmento de código muestra cómo crear y guardar un elemento del calendario en formato ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cs" >}}

### **Guardar el elemento del calendario como MSG**

El siguiente fragmento de código muestra cómo guardar el elemento del calendario como MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cs" >}}

### **Configuración de un identificador de producto al guardar MapiCalendar en ICS**

The [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) propiedad del [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) La clase se usa para guardar un elemento del calendario MAPI en un archivo iCalendar (ICS) que conserva la información original de fecha y hora, así como un identificador de producto personalizado. La propiedad especifica el identificador del producto que creó el objeto iCalendar.

El siguiente ejemplo de código muestra cómo trabajar con datos de iCalendar (ICS) en un objeto de calendario MAPI:

```cs
var icsSaveOptions = new MapiCalendarIcsSaveOptions
{
    KeepOriginalDateTimeStamp = true,
    ProductIdentifier = "Foo Ltd"
};

mapiCalendar.Save("my.ics", icsSaveOptions);
```
### **Obtener el número total de eventos**

La clase CalendarReader permite gestionar los eventos del calendario sin esfuerzo. Las siguientes propiedades y un método permiten trabajar con varios eventos:

- **CalendarReader.Count** - La propiedad Count de la clase CalendarReader permite recuperar el número de componentes (eventos) de Vevent presentes en el calendario, lo que facilita el seguimiento del número total de eventos.
- **CalendarReader.IsMultiEvents** - Esta propiedad determina si el calendario contiene varios eventos. Proporciona un valor booleano que indica si el calendario contiene más de un evento, lo que ayuda a identificar los calendarios con uno o varios eventos.
- **CalendarReader.Method** - La propiedad Method obtiene el tipo de método iCalendar asociado al objeto de calendario. Devuelve el tipo de método, como «REQUEST», «PUBLISH» o «CANCEL», lo que proporciona información valiosa sobre el propósito del calendario.
- **CalendarReader.Version** - Obtiene la versión de iCalendar.
- **CalendarReader.LoadAsMultiple()** Este método permite cargar una lista de eventos de un calendario que contiene varios eventos. Devuelve una lista de objetos de citas, lo que permite acceder fácilmente a cada evento y procesarlo de forma individual.

El siguiente ejemplo de código demuestra cómo puedes implementar estas capacidades en tu proyecto:

```cs
var reader = new CalendarReader(fileName);
Console.WriteLine("Calendar contains " + reader.Count + " events");
Console.WriteLine("The Version of the calendar is " + reader.Version);
Console.WriteLine("The Method of the calendar is " + reader.Method);
Console.WriteLine("Is calendar contains contains multiple events? - " + reader.IsMultiEvents);
List<Appointment> appointments = reader.LoadAsMultiple();
```

### **Añadir un recordatorio de pantalla a un calendario**

En el siguiente fragmento de código, se muestra cómo añadir un recordatorio de visualización a un calendario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cs" >}}

### **Añadir un recordatorio de audio a un calendario**

En el siguiente fragmento de código, se muestra cómo añadir un recordatorio de audio a un calendario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cs" >}}

### **Añadir/recuperar archivos adjuntos de archivos de calendario**

El siguiente fragmento de código muestra cómo añadir o recuperar archivos adjuntos de los archivos de calendario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cs" >}}

### **Estado de los destinatarios de una convocatoria de reunión**

El siguiente fragmento de código muestra cómo mostrar el estado de los destinatarios de una convocatoria de reunión.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cs" >}}

### **Crear MapiCalendarTimezone a partir de una zona horaria estándar**

El siguiente fragmento de código muestra cómo crear MapiCalendarTimezone a partir de una zona horaria estándar.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cs" >}}

## **Configurar un recordatorio con la cita creada**

Se puede agregar un recordatorio cuando se crea una cita. Estas alarmas pueden activarse en función de diferentes criterios, como n minutos antes de que comience la programación o repetirse n veces a intervalos de n. Se pueden usar diferentes etiquetas para crear estos activadores en el script incluido entre BEGIN:VALARM y END:VALARM dentro de una cita. Hay varias variantes en las que se puede configurar el recordatorio en una cita.

### **Establecer un recordatorio añadiendo etiquetas**

En el siguiente fragmento de código, se muestra cómo configurar un recordatorio añadiendo etiquetas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cs" >}}

## **Convierta Appointment EML a MSG con HTML Body**

Desde la versión 19.3, Aspose.Email ofrece la posibilidad de convertir Appointment EML en MSG conservando el cuerpo HTML de la cita. Aspose.Email proporciona un [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) propiedad que tiene un valor predeterminado de **true.** Cuando el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) está configurado en **true**, el organismo de la designación se convierte al formato RTF. Para mantener el formato del cuerpo de la cita en formato HTML, defina el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) to **false.**

El siguiente ejemplo demuestra el uso de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) propiedad para mantener el formato del cuerpo de la cita en formato HTML.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-ConvertAppointmentEMLToMSGWithHTMLBody-1.cs" >}}
