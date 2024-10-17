---
title: "Trabajando con elementos del calendario de Outlook"
url: /es/net/working-with-outlook-calendar-items/
weight: 120
type: docs
---


## **Trabajando con MapiCalendar**

La clase MapiCalendar de Aspose.Email proporciona métodos y atributos para establecer varias propiedades de un elemento del calendario. Este artículo proporciona ejemplos de código para:

- [**Trabajando con MapiCalendar**](#working-with-mapicalendar)
  - [**Creando y guardando elementos del calendario**](#creating-and-saving-calendar-items)
  - [**Guardando el elemento del calendario como MSG**](#saving-the-calendar-item-as-msg)
  - [**Añadiendo recordatorio visual a un calendario**](#adding-display-reminder-to-a-calendar)
  - [**Añadiendo recordatorio de audio a un calendario**](#adding-audio-reminder-to-a-calendar)
  - [**Añadir/Recuperar archivos adjuntos de los archivos del calendario**](#addretrieve-attachments-from-calendar-files)
  - [**Estado de los destinatarios de una solicitud de reunión**](#status-of-recipients-from-a-meeting-request)
  - [**Crear MapiCalendarTimeZone de la zona horaria estándar**](#create-mapicalendartimezone-from-standard-timezone)
- [**Establecer recordatorio con la cita creada**](#setting-reminder-with-the-created-appointment)
  - [**Establecer un recordatorio añadiendo etiquetas**](#setting-a-reminder-by-adding-tags)
- [**Convertir cita EML a MSG con cuerpo HTML**](#convert-appointment-eml-to-msg-with-html-body)
  
### **Creando y guardando elementos del calendario**

El siguiente fragmento de código muestra cómo crear y guardar un elemento del calendario en formato ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cs" >}}

### **Guardando el elemento del calendario como MSG**

El siguiente fragmento de código muestra cómo guardar el elemento del calendario como MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cs" >}}

### **Establecer un ID de producto al guardar MapiCalendar a ICS**

La propiedad [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) de la clase [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) se usa para guardar un elemento del calendario MAPI en un archivo iCalendar (ICS) preservando la información original de fecha y hora, así como un identificador de producto personalizado. La propiedad especifica el identificador del producto que creó el objeto iCalendar.

El siguiente ejemplo de código muestra cómo trabajar con datos de iCalendar (ICS) dentro de un objeto de calendario MAPI:

```cs
var icsSaveOptions = new MapiCalendarIcsSaveOptions
{
    KeepOriginalDateTimeStamp = true,
    ProductIdentifier = "Foo Ltd"
};

mapiCalendar.Save("my.ics", icsSaveOptions);
```
### **Obteniendo el número total de eventos**

La clase CalendarReader permite manejar eventos de calendario sin esfuerzo. Las siguientes propiedades y un método te permiten trabajar con múltiples eventos:

- **CalendarReader.Count** - La propiedad Count de la clase CalendarReader te permite recuperar el número de componentes Vevent (eventos) presentes en el calendario, facilitando el seguimiento del número total de eventos.
- **CalendarReader.IsMultiEvents** - Esta propiedad determina si el calendario contiene múltiples eventos. Proporciona un valor booleano que indica si el calendario contiene más de un evento, ayudando a identificar calendarios con eventos únicos o múltiples.
- **CalendarReader.Method** - La propiedad Method obtiene el tipo de método de iCalendar asociado con el objeto del calendario. Devuelve el tipo de método, como "REQUEST", "PUBLISH" o "CANCEL", proporcionando información valiosa sobre el propósito del calendario.
- **CalendarReader.Version** - Obtiene la versión de iCalendar.
- **CalendarReader.LoadAsMultiple()** Este método permite cargar una lista de eventos de un calendario que contiene múltiples eventos. Devuelve una lista de objetos Appointment, lo que permite el acceso fácil y el procesamiento de cada evento individualmente.

El siguiente ejemplo de código demuestra cómo puedes implementar estas capacidades en tu proyecto:

```cs
var reader = new CalendarReader(fileName);
Console.WriteLine("El calendario contiene " + reader.Count + " eventos");
Console.WriteLine("La versión del calendario es " + reader.Version);
Console.WriteLine("El método del calendario es " + reader.Method);
Console.WriteLine("¿El calendario contiene múltiples eventos? - " + reader.IsMultiEvents);
List<Appointment> appointments = reader.LoadAsMultiple();
```

### **Añadiendo recordatorio visual a un calendario**

El siguiente fragmento de código muestra cómo añadir un recordatorio visual a un calendario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cs" >}}

### **Añadiendo recordatorio de audio a un calendario**

El siguiente fragmento de código muestra cómo añadir un recordatorio de audio a un calendario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cs" >}}

### **Añadir/Recuperar archivos adjuntos de los archivos del calendario**

El siguiente fragmento de código muestra cómo añadir/recuperar archivos adjuntos de los archivos del calendario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cs" >}}

### **Estado de los destinatarios de una solicitud de reunión**

El siguiente fragmento de código muestra cómo mostrar el estado de los destinatarios de una solicitud de reunión.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cs" >}}

### **Crear MapiCalendarTimeZone de la zona horaria estándar**

El siguiente fragmento de código muestra cómo crear MapiCalendarTimeZone de la zona horaria estándar.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cs" >}}

## **Establecer recordatorio con la cita creada**

Se puede añadir un recordatorio cuando se crea una cita. Estas alarmas pueden activarse en función de diferentes criterios, como n minutos antes de que comience el horario, repetir n veces a intervalos n. Se pueden usar diferentes etiquetas para crear estos disparadores en el script encerrado entre BEGIN:VALARM y END:VALARM dentro de una cita. Hay varias variantes en las que se puede establecer el recordatorio en una cita.

### **Establecer un recordatorio añadiendo etiquetas**

El siguiente fragmento de código muestra cómo establecer un recordatorio añadiendo etiquetas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cs" >}}

## **Convertir cita EML a MSG con cuerpo HTML**

Desde la versión 19.3, Aspose.Email proporciona la capacidad de convertir cita EML a MSG mientras se conserva el cuerpo HTML de la cita. Aspose.Email proporciona una [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) propiedad que tiene un valor predeterminado de **true.** Cuando el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) se establece en **true**, el cuerpo de la cita se convierte al formato RTF. Para mantener el formato del cuerpo de la cita en formato HTML, establece el valor de [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) en **false.**

El siguiente ejemplo demuestra el uso de la [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) propiedad para mantener el formato del cuerpo de la cita en formato HTML.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-ConvertAppointmentEMLToMSGWithHTMLBody-1.cs" >}}