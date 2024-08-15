---
title: "Convertir EML a HTML"
url: /es/net/converting-between-formats/
weight: 60
type: docs
---

## **Convertir EML a HTML**

Para integrar el contenido del correo electrónico en las aplicaciones web, la conversión de EML a HTML es la elección correcta, ya que facilita una presentación del correo electrónico visualmente atractiva.

Para convertir EML a HTML, necesitará las siguientes clases:

- [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase se usa para crear un objeto que representa un mensaje de correo electrónico. Permite acceder a las propiedades de los mensajes, como el asunto, el cuerpo, las direcciones del remitente y del destinatario, etc. Con sus métodos, puede crear, cargar y analizar, modificar, guardar correos electrónicos o realizar otras manipulaciones con ellos.
- [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) La clase proporciona opciones para guardar mensajes de correo electrónico en varios formatos. Permite a los usuarios personalizar la forma en que se guardan los mensajes de correo electrónico en diferentes formatos. Con esta clase, los usuarios pueden especificar las opciones para guardar los archivos adjuntos, los encabezados, los metadatos y las propiedades de los mensajes de correo electrónico, establecer las opciones de codificación o elegir si desean guardar los mensajes cifrados o no.

En el ejemplo de código siguiente, estas clases funcionan juntas para cargar un archivo EML existente y especificar el formato del mensaje como EML. Posteriormente, guardan el mensaje de correo electrónico cargado como un archivo HTML mediante las opciones de almacenamiento HTML predeterminadas especificadas:

1. Usa el [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) método para cargar el archivo existente en un objeto MailMessage especificando el formato del mensaje.
2. Guarde el objeto MailMessage cargado como un archivo HTML mediante el [save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método. Usa [SaveOptions.DefaultHtml()](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) para especificar las opciones de guardado para el formato HTML.

```cs
// Initialize and Load an existing EML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.eml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

### **Guarde los recursos de EML en un archivo separado**

Aspose.Email proporciona la [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) enumeración que permite a los desarrolladores manipular los recursos de un archivo HTML. En el ejemplo de código siguiente, esta enumeración se usa para guardar recursos en un archivo e insertar en HTML la etiqueta 'src' con la ruta a este archivo:

1. Cargue el mensaje de correo electrónico desde el archivo de origen mediante [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method.
2. Crea una instancia de [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) con opciones de representación y recursos especificadas.
3. Guarde el mensaje de correo electrónico cargado como un archivo HTML en la ubicación de destino mediante el [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) método con el parámetro HTMLSaveOptions.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
UseRelativePathToResources = true
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

### **Incrustar recursos en un archivo HTML**

En algunos casos, es necesario incrustar recursos, como imágenes, directamente en el archivo HTML para distribuirlos y presentarlos sin problemas. Con Aspose.Email para .NET, puede lograrlo fácilmente mediante el [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) enumeration:

1. Cargue el mensaje de correo electrónico desde el archivo de origen mediante [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method.
2. Crear un nuevo [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) objeta y establece la propiedad ResourceRenderingMode en EmbedInToHTML.
3. Guarde el mensaje de correo electrónico cargado como un archivo HTML mediante el [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) método, especificando la ruta del archivo de destino y pasando el objeto HTMLSaveOptions como parámetro para incrustar recursos en el archivo HTML.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.EmbedIntoHtml
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

## **Convertir EML a ICS**

El siguiente ejemplo de código muestra cómo extraer datos de eventos de calendario de un archivo EML y guardarlos en un archivo ICS independiente para su uso o manipulación posteriores.

```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// If an ICS view is found, save it to a file
if (icsView != null)
{
    File.WriteAllText("appointment.ics", icsView);
}
```
### **Customization**

Aspose.Email para.NET proporciona herramientas para personalizar el contenido de ICS (iCalendar) extraído de archivos EML (correo electrónico).

**Personaliza los detalles del evento**

El siguiente ejemplo de código muestra cómo configurar varios detalles de la cita, como el resumen, la ubicación y la descripción. El código utiliza el [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) clase que representa citas o eventos del calendario en formato ICS (iCalendar). La clase proporciona propiedades y métodos para crear, modificar y administrar los eventos del calendario mediante programación.

```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// If an ICS view is found, load it to Appointment class object
var appointment = Appointment.Load(new MemoryStream(Encoding.UTF8.GetBytes(icsView)));

// Personaliza los detalles del evento
appointment.Summary = "Customized Event Summary";
appointment.Location = "Customized Location";
appointment.Description = "Customized Event Description";

// Add or modify attendees as needed
appointment.Attendees.Clear();
appointment.Attendees.Add("custom@example.com");

// Save the customized ICS content to a file
appointment.Save("customized_appointment.ics");
```
**Crear un patrón de recurrencia**

El siguiente ejemplo de código muestra cómo crear un patrón de periodicidad semanal para una cita, en el que la cita tiene lugar cada 5 semanas los sábados. El código utiliza el [Recurrence](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/recurrence/#appointmentrecurrence-property) propiedad del [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) clase que obtiene o establece el patrón de recurrencia.

```cs
var pattern = new  WeeklyRecurrencePattern(5, 7);
pattern. EndDate = new DateTime(2023, 8, 7);

appointment.Recurrence = pattern;
```

## **Añadir EML a MBOX**

MBOX es un formato de uso común para almacenar varios mensajes de correo electrónico en un solo archivo, lo que lo hace adecuado para archivar y migrar correos electrónicos. Utilice el [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) clase para escribir mensajes de correo electrónico en un archivo MBOX. El siguiente ejemplo de código muestra cómo realizar esta tarea:

```cs
using (var message = MailMessage.Load("inputFile.eml")){
	using (var writer = new MboxrdStorageWriter("output.mbox", false)){
			writer.WriteMessage(message);
	}
}
```

## **Convertir EML a MHTML**

Con Aspose.Email para .NET, puede convertir fácilmente archivos EML a formato MHTML para diversos fines, como archivarlos, hacer compatibles, verlos sin conexión, etc. Cargue el mensaje de correo electrónico mediante el [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2), a continuación, utilice el [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) clase como parámetro para la [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método para especificar el formato del archivo de salida al guardar el mensaje como un archivo separado:

```cs
// Initialize and Load an existing EML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.eml");
var mhtSaveOptions = new MhtSaveOptions;
message.Save("output.mhtml", mhtSaveOptions);
```

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) class ofrece varias opciones para personalizar los archivos MHTML de salida para cumplir con sus requisitos específicos:

- Conserva el formato de fecha original. Puedes optar por conservar el formato original de los mensajes de correo electrónico durante el proceso de conversión:

  ```cs
  saveOptions.PreserveOriginalDate = true;
  ```

- Configure la codificación de salida. Puede especificar la codificación que se utilizará al escribir los archivos MHTML de salida:

  ```cs
  saveOptions.OutputEncoding = Encoding.UTF8;
  ```

- Incluya archivos adjuntos. Esto puede resultar útil si quieres conservar los archivos adjuntos al convertir correos electrónicos a formato MHTML:

  ```cs
  saveOptions.SaveAttachments = true;
  ```

## **Convertir EML a MSG**

Ya sea que necesite migrar datos de correo electrónico, archivar mensajes o integrarse con Microsoft Outlook, Aspose.Email ofrece soluciones para lograr sus objetivos. Los archivos MSG son ampliamente utilizados por Microsoft Outlook. Para la conversión de EML a MSG, utilice [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) método para cargar el archivo EML existente especificando cómo se cargará con [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class).

El siguiente ejemplo de código muestra cómo convertir archivos EML al formato MSG:

```cs
// Load mail message
using (var message = MailMessage.Load("sourceFile.eml", new EmlLoadOptions())){
// Save as MSG
var msgSaveOptions = new MsgSaveOptions;
message.Save("output.msg", MsgSaveOptions);
}
```

## **Convertir EML a OFT**

Para convertir archivos EML al formato de plantilla de Outlook (OFT), cargue el mensaje de correo electrónico existente mediante el [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) método y guárdalo con [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) especificar las opciones predeterminadas para guardar un mensaje en formato OFT:

```cs
// load the EML file to be converted
var message = MailMessage.Load("My File.eml");
// save EML as a OFT
message.Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Agregar EML a PST**

Para convertir archivos EML al formato de tabla de almacenamiento personal (PST), cargue el mensaje mediante el [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) método, cree el archivo de salida con el [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) y añada el correo electrónico a la carpeta Bandeja de entrada creada en el archivo de almacenamiento mediante [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/):

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

Los desarrolladores pueden convertir fácilmente archivos EML al formato de tabla de almacenamiento sin conexión (OST) de Outlook, lo que permite la integración con Microsoft Outlook. El siguiente ejemplo de código muestra cómo agregar un mensaje EML a un archivo OST:

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    // Load the EML file
    var msg = MapiMessage.Load("message.eml", new EmlLoadOptions());

    // Add the EML message to the OST file
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```
The [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class) el parámetro especifica opciones adicionales para cargar archivos EML, como conservar los formatos de mensajes incrustados, eliminar firmas y más.


## **Convertir EML a VCF**

Aspose.Email para.NET ofrece la funcionalidad de convertir archivos EML al formato vCard (VCF), lo que permite a los desarrolladores extraer la información de contacto de los mensajes de correo electrónico. Para ello, la biblioteca ofrece [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) método del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) clase que permite a los desarrolladores acceder a vistas alternativas en los mensajes de correo electrónico y extraer el contenido VCF incrustado en los archivos EML para su uso posterior:


```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/vcard" (VCF)
var vcfView = eml.GetAlternateViewContent("text/vcard");
// If an VCF view is found, save it to a file
if (vcfView != null)
{
    File.WriteAllText("contact.vcf", vcfView);
}
```
