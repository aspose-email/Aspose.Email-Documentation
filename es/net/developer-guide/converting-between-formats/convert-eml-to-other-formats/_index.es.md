---
title: "Convertir EML a HTML"
url: /es/net/converting-between-formats/
weight: 60
type: docs
---

## **Convertir EML a HTML**

Para integrar contenido de correo electrónico en aplicaciones web, la conversión de EML a HTML es la opción correcta, facilitando una presentación de correo electrónico visualmente atractiva.

Para convertir EML a HTML, necesitarás las siguientes clases:

- La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) se utiliza para crear un objeto que representa un mensaje de correo electrónico. Permite acceder a las propiedades del mensaje, como asunto, cuerpo, direcciones del remitente y de los destinatarios, etc. Con sus métodos, puedes crear, cargar y analizar, modificar, guardar correos electrónicos, o realizar otras manipulaciones con ellos.
- La clase [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) proporciona opciones para guardar mensajes de correo electrónico en varios formatos. Permite a los usuarios personalizar la forma en que se guardan los mensajes de correo electrónico en diferentes formatos. Con esta clase, los usuarios pueden especificar opciones para guardar adjuntos, encabezados, metadatos y propiedades de los mensajes de correo electrónico, establecer opciones de codificación o elegir si guardar mensajes con o sin cifrado.

En el siguiente ejemplo de código, estas clases trabajan juntas para cargar un archivo EML existente y especificar el formato del mensaje como EML. Posteriormente, guardan el mensaje de correo electrónico cargado como un archivo HTML utilizando las opciones predeterminadas de guardado en HTML especificadas:

1. Usa el método [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) para cargar el archivo existente en un objeto MailMessage especificando el formato del mensaje.
2. Guarda el objeto MailMessage cargado como un archivo HTML utilizando el método [save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3). Usa [SaveOptions.DefaultHtml()](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) para especificar las opciones de guardado para el formato HTML.

```cs
// Inicializa y carga un archivo EML existente especificando el MessageFormat
var message = MailMessage.Load("myMessage.eml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

### **Guardar Recursos EML en un Archivo Separado**

Aspose.Email proporciona la enumeración [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) que permite a los desarrolladores manipular recursos en un archivo HTML. En el siguiente ejemplo de código, esta enumeración se utiliza para guardar recursos en un archivo e insertar en HTML la etiqueta 'src' con la ruta a este archivo:

1. Carga el mensaje de correo electrónico desde el archivo fuente usando el método [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2).
2. Crea una instancia de [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) con las opciones de renderizado y recursos especificadas.
3. Guarda el mensaje de correo electrónico cargado como un archivo HTML en la ubicación de destino utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) con el parámetro HtmlSaveOptions.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
UseRelativePathToResources = true
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

### **Incrustar Recursos en un Archivo HTML**

En algunos casos, es necesario incrustar recursos, como imágenes, directamente en el archivo HTML para una distribución y presentación sin problemas. Con Aspose.Email para .NET, puedes lograr esto fácilmente utilizando la enumeración [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration):

1. Carga el mensaje de correo electrónico desde el archivo fuente usando el método [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2).
2. Crea un nuevo objeto [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) y establece la propiedad ResourceRenderingMode en EmbedIntoHtml.
3. Guarda el mensaje de correo electrónico cargado como un archivo HTML utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3), especificando la ruta del archivo de destino y pasando el objeto HtmlSaveOptions como un parámetro para incrustar recursos en el archivo HTML.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.EmbedIntoHtml
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

## **Convertir EML a ICS**

El siguiente ejemplo de código demuestra cómo extraer datos de eventos de calendario de un archivo EML y guardarlos en un archivo ICS separado para su posterior uso o manipulación.

```cs
// Cargar el archivo EML
var eml = MailMessage.Load("message.eml");
// Encontrar la vista alternativa con MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// Si se encuentra una vista ICS, guardarla en un archivo
if (icsView != null)
{
    File.WriteAllText("appointment.ics", icsView);
}
```
### **Personalización**

Aspose.Email para .NET proporciona herramientas para personalizar el contenido de ICS (iCalendar) extraído de archivos EML (Correo Electrónico).

**Personaliza los detalles del evento**

El siguiente ejemplo de código demuestra cómo establecer varios detalles de la cita, como el resumen, la ubicación y la descripción. El código utiliza la clase [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) que representa citas o eventos de calendario en formato ICS (iCalendar). La clase proporciona propiedades y métodos para crear, modificar y gestionar eventos de calendario programáticamente.

```cs
// Cargar el archivo EML
var eml = MailMessage.Load("message.eml");
// Encontrar la vista alternativa con MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// Si se encuentra una vista ICS, cargarla en un objeto de la clase Appointment
var appointment = Appointment.Load(new MemoryStream(Encoding.UTF8.GetBytes(icsView)));

// Personaliza los detalles del evento
appointment.Summary = "Resumen del Evento Personalizado";
appointment.Location = "Ubicación Personalizada";
appointment.Description = "Descripción del Evento Personalizado";

// Agregar o modificar asistentes según sea necesario
appointment.Attendees.Clear();
appointment.Attendees.Add("custom@example.com");

// Guardar el contenido ICS personalizado en un archivo
appointment.Save("customized_appointment.ics");
```
**Crear un patrón de recurrencia**

El siguiente ejemplo de código demuestra cómo crear un patrón de recurrencia semanal para una cita, donde la cita ocurre cada 5 semanas los sábados. El código utiliza la propiedad [Recurrence](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/recurrence/#appointmentrecurrence-property) de la clase [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) que obtiene o establece el patrón de recurrencia.

```cs
var pattern = new WeeklyRecurrencePattern(5, 7);
pattern.EndDate = new DateTime(2023, 8, 7);

appointment.Recurrence = pattern;
```

## **Agregar EML a MBOX**

MBOX es un formato comúnmente utilizado para almacenar múltiples mensajes de correo electrónico en un solo archivo, lo que lo hace adecuado para fines de archivo y migración de correos electrónicos. Utiliza la clase [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) para escribir mensajes de correo electrónico en un archivo MBOX. El siguiente ejemplo de código demuestra cómo realizar esta tarea:

```cs
using (var message = MailMessage.Load("inputFile.eml")){
	using (var writer = new MboxrdStorageWriter("output.mbox", false)){
			writer.WriteMessage(message);
	}
} 
```

## **Convertir EML a MHTML**

Con Aspose.Email para .NET, puedes convertir fácilmente archivos EML a formato MHTML para varios propósitos como archivo, compatibilidad, visualización offline, etc. Carga el mensaje de correo electrónico usando el método [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2), luego usa la clase [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) como un parámetro para el método [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) para especificar el formato del archivo de salida al guardar el mensaje como un archivo separado:

```cs
// Inicializa y carga un archivo EML existente especificando el MessageFormat
var message = MailMessage.Load("myMessage.eml");
var mhtSaveOptions = new MhtSaveOptions();
message.Save("output.mhtml", mhtSaveOptions);
```

La clase [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) proporciona varias opciones para personalizar archivos MHTML de salida para cumplir con tus requisitos específicos:

- Preservar el formato de fecha original. Puedes elegir conservar el formato original de los mensajes de correo electrónico durante el proceso de conversión:

  ```cs
  saveOptions.PreserveOriginalDate = true;
  ```

- Establecer codificación de salida. Puedes especificar la codificación que se utilizará al escribir los archivos MHTML de salida:

  ```cs
  saveOptions.OutputEncoding = Encoding.UTF8; 
  ```

- Incluir adjuntos. Esto puede ser útil si deseas preservar los adjuntos al convertir correos electrónicos a formato MHTML:

  ```cs
  saveOptions.SaveAttachments = true;
  ```

## **Convertir EML a MSG**

Ya sea que necesites migrar datos de correos electrónicos, archivar mensajes, o integrarte con Microsoft Outlook, Aspose.Email proporciona soluciones para lograr tus objetivos. Los archivos MSG son ampliamente utilizados por Microsoft Outlook. Para la conversión de EML a MSG, usa el método [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) para cargar el archivo EML existente especificando cómo se cargará con [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class).

El siguiente ejemplo de código demuestra cómo convertir archivos EML a formato MSG:

```cs
// Cargar el mensaje de correo
using (var message = MailMessage.Load("sourceFile.eml", new EmlLoadOptions())){
// Guardar como MSG
var msgSaveOptions = new MsgSaveOptions();
message.Save("output.msg", msgSaveOptions);
} 
```

## **Convertir EML a OFT**

Para convertir archivos EML a formato de Plantilla de Outlook (OFT), carga el mensaje de correo electrónico existente usando el método [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) y guárdalo con [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) especificando las opciones predeterminadas para guardar un mensaje en formato OFT:

```cs
// cargar el archivo EML a convertir
var message = MailMessage.Load("My File.eml"); 
// guardar EML como un OFT 
message.Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Agregar EML a PST**

Para convertir archivos EML a formato de Tabla de Almacenamiento Personal (PST), carga el mensaje usando el método [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3), crea el archivo de salida con [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) y agrega el correo electrónico a la carpeta Bandeja de entrada creada en el archivo de almacenamiento usando [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/):

```cs
using (var msg = MapiMessage.Load("sourceFile.eml", new EmlLoadOptions()))
{
    using (var personalStorage = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
  {
        var inbox = personalStorage.RootFolder.AddSubFolder("Inbox");
        inbox.AddMessage(msg);
  }
}
```

## **Agregar EML a OST**

Los desarrolladores pueden convertir fácilmente archivos EML a formato de Tabla de Almacenamiento Offline de Outlook (OST), lo que permite la integración con Microsoft Outlook. El siguiente ejemplo de código demuestra cómo agregar un mensaje EML a un archivo OST:

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    // Cargar el archivo EML
    var msg = MapiMessage.Load("message.eml", new EmlLoadOptions());

    // Agregar el mensaje EML al archivo OST
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```
El parámetro [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class) especifica opciones adicionales para cargar archivos EML, como preservar formatos de mensaje incrustados, eliminar firmas, y más.

## **Convertir EML a VCF**

Aspose.Email para .NET ofrece funcionalidad para convertir archivos EML a formato vCard (VCF), permitiendo a los desarrolladores extraer información de contacto de mensajes de correo electrónico. Para este propósito, la biblioteca ofrece el método [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) que permite a los desarrolladores acceder a vistas alternativas dentro de mensajes de correo electrónico y extraer el contenido VCF incrustado dentro de archivos EML para su uso posterior:

```cs
// Cargar el archivo EML
var eml = MailMessage.Load("message.eml");
// Encontrar la vista alternativa con MediaType "text/vcard" (VCF)
var vcfView = eml.GetAlternateViewContent("text/vcard");
// Si se encuentra una vista VCF, guardarla en un archivo
if (vcfView != null)
{
    File.WriteAllText("contact.vcf", vcfView);
}
```