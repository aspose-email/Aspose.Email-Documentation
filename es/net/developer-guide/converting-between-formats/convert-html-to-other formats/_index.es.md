---
title: "Convertir HTML a otros formatos"
url: /es/net/converting-between-formats/convert-html-to-other-formats
weight: 60
type: docs
---

## **Convertir HTML a EML**

Aspose.Email para.NET proporciona un método para convertir archivos HTML al formato EML mediante el [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) and [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) métodos para cargar el archivo HTML existente y guardarlo en formato EML respectivamente:


```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.eml", SaveOptions.DefaultEml);
```

En el ejemplo de código, el [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) La clase le permite especificar opciones adicionales al cargar un MailMessage en formato HTML. El siguiente ejemplo de código demuestra el uso de esta clase. En el ejemplo, especifica una representación textual del cuerpo del mensaje:

```cs
// Create an instance of HtmlLoadOptions
var loadOptions = new HtmlLoadOptions();

// Set the ShouldAddPlainTextView property to true to generate a plain text view along with HTML
loadOptions.ShouldAddPlainTextView = true;

// Load an HTML file
var mailMessage = MailMessage.Load("input.html", loadOptions);

// Access the plain text view of the email message
var plainTextView = mailMessage.GetAlternateViewContent("text/plain");

// Print or further process the plain text view
Console.WriteLine("Plain Text View:");
Console.WriteLine(plainTextView);
```

## **Convertir HTML a EMLX**

Puede convertir fácilmente archivos HTML a EMLX. Todas las propiedades y clases que proporciona la API para la conversión de HTML a EML también están disponibles para este tipo de conversión:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.emlx", SaveOptions.DefaultEmlx);
```
Para ver ajustes adicionales, consulte [Convertir HTML a EML](#convert-html-to-eml) paragraph.

## **Convertir HTML a ICS**

Para realizar la tarea, la biblioteca ofrece [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) clase para representar y gestionar los eventos del calendario. El siguiente ejemplo de código muestra cómo crear el contenido HTML de un formulario de cita y guardarlo en un formato de archivo ICS (iCalendar):

```cs
// Sample HTML content
var htmlContent = File.ReadAllText("content.html");

// Create and initialize an instance of the Appointment class
var appointment = new Appointment(
    "Meeting Room 3 at Office Headquarters",// Location
    "Monthly Meeting",                      // Summary
    "Please confirm your availability.",    // Description
    new DateTime(2015, 2, 8, 13, 0, 0),     // Start date
    new DateTime(2015, 2, 8, 14, 0, 0),     // End date
    "from@domain.com",                      // Organizer
    "attendees@domain.com")
{
    HtmlDescription = htmlContent
};

// Save the event to an ICS file
appointment.Save("output.ics", AppointmentSaveFormat.Ics);
```


## **Generar MBOX a partir de contenido HTML**

Para realizar la conversión de HTML a MBOX, utilice [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) método del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) clase, especificando la ruta del archivo de contenido HTML y una instancia de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Este método analiza el contenido HTML y genera el objeto MailMessage correspondiente, conservando la estructura y el formato del HTML original. Tras cargar el contenido HTML en un objeto MailMessage, escriba el mensaje en un archivo MBOX mediante el [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) class:


```cs
using (var eml = MailMessage.Load("content.html", new HtmlLoadOptions())){
    using (var writer = new MboxrdStorageWriter("output.mbox", false)){
        writer.WriteMessage(eml);
    }
}
```

## **Convertir HTML a MHTML**

Usa el [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) método del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) clase para cargar el archivo existente, especificando una ruta al mismo y una instancia de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Este método analiza el contenido HTML y genera el objeto MailMessage correspondiente, conservando la estructura y el formato del HTML original. Tras cargar el contenido HTML en un objeto MailMessage, los desarrolladores pueden guardarlo como un archivo MHTML mediante el [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método, especificando la ruta deseada del archivo de salida y utilizando el [SaveOptions.DefaultMhtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmhtml/) option:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.mhtml", SaveOptions.DefaultMhtml);
```

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) La clase proporciona una variedad de opciones para configurar el comportamiento y los ajustes del archivo MHTML de salida en lugar de SaveOptions.defaultMHTML. Con su [properties](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#properties), puede especificar opciones adicionales al guardar MailMessage en formato MHTML.
Los más populares son:

- [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/mhtformatoptions/) - Le permite personalizar la forma en que se guarda el mensaje de correo electrónico en formato MHT para que se adapte mejor a sus necesidades.
- [SaveAttachments](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveattachments/) - Obtiene o establece un valor que indica si se deben guardar los archivos adjuntos.
- [SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Define si es necesario guardar todos los encabezados en la salida mhtml o no. El valor predeterminado es falso.
- [PreserveOriginalDate](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/preserveoriginaldate/) - Define si es necesario mantener la fecha original en el mensaje de correo al guardar o no. El valor predeterminado es verdadero.

El siguiente ejemplo de código muestra cómo se pueden usar estas propiedades:

```cs
var mhtSaveOprtions = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader,
    SaveAttachments = true,
    SaveAllHeaders = true,
    PreserveOriginalDate = true
}
```

## **Convertir HTML a MSG**

Tras cargar el contenido HTML en un objeto MailMessage, guárdelo como un archivo MSG mediante el [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método, especificando la ruta deseada del archivo de salida y utilizando el [SaveOptions.DefaultMsgUnicode](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmsgunicode/) opción. Esta opción garantiza que el archivo de salida se guarde en formato MSG con codificación Unicode.

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.msg", SaveOptions.DefaultMsgUnicode);
```
Además, Aspose.Email para.NET ofrece una gama de funciones y opciones avanzadas para la conversión de HTML a MSG:

## **Convertir HTML a OFT**

Tras cargar el contenido HTML en un objeto MailMessage, guárdelo como un archivo OFT mediante el [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método, especificando la ruta deseada del archivo de salida y utilizando el [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/) option:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("template.oft", SaveOptions.DefaultOft);
```

## **Agregar un mensaje con contenido HTML de origen a PST**

La conversión de HTML a PST implica crear un nuevo archivo PST (tabla de almacenamiento personal) con una nueva carpeta, cargar un archivo HTML y agregarlo a la nueva carpeta:

1. Cree una instancia de un objeto PersonalStorage que represente un nuevo archivo PST mediante el [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) método del [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.
2. Acceda a la carpeta raíz del archivo PST y añada una subcarpeta mediante el [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder) método del [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class.
3. Cargue el contenido de un archivo HTML en un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) objeto que usa el [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) método con una instancia de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) para especificar que el contenido está en formato HTML.
4. Añada el objeto MAPIMessage cargado (que representa el contenido HTML) a la carpeta del archivo PST mediante el [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method.

```cs
using (var pst = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
{
    var inbox = pst.RootFolder.AddSubFolder("Inbox");
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    inbox.AddMessage(msg);
}
```

## **Agregar mensaje con contenido HTML de origen a OST**

El siguiente ejemplo de código con pasos le mostrará cómo estos componentes funcionan juntos para agregar contenido HTML al archivo OST:

1. Cargue un archivo OST existente con [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) método del [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) clase utilizada para representar el archivo de almacenamiento que almacenará los mensajes de correo electrónico.
2. Cargue el archivo HTML con el [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) método del [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) clase que representa un mensaje de correo electrónico en formato Microsoft Outlook.
3. Specify [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) para habilitar opciones adicionales al cargar MailMessage en formato HTML.
4. Recupere la carpeta raíz del archivo OST mediante el [RootFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/rootfolder/) propiedad del [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) object.
5. Obtenga la carpeta Bandeja de entrada dentro del archivo OST mediante el [GetSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder) método en la carpeta raíz.
6. Añada el objeto MAPIMessage cargado (que representa el contenido HTML) a la carpeta Bandeja de entrada mediante [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) método en la carpeta.

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```

## **Convertir HTML a VCF**

El siguiente ejemplo de código muestra cómo crear un elemento de contacto, rellenarlo con contenido HTML y guardarlo en un archivo VCF:

1. Lea el contenido de un archivo HTML en una variable de cadena mediante el método File.readAllText.
2. Cree un nuevo objeto MapiContact creando una instancia del [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/#mapicontact-class) class.
3. Configure las propiedades del contacto: nombre para mostrar, dirección de correo electrónico.
4. Establezca el contenido del cuerpo del contacto en HTML usando [SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/setbodycontent/#setbodycontent).
5. Guarde el contacto como un archivo VCF mediante el [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_4) method.

```cs
var content = File.ReadAllText("content.html");
           
// Create a new MapiContact
var contact = new MapiContact();
contact.NameInfo.DisplayName = "John Doe";
contact.ElectronicAddresses.Email1.EmailAddress = "john.doe@example.com";
contact.SetBodyContent(content, BodyContentType.Html);

// Save the contact to a VCF file
contact.Save("contact.vcf", ContactSaveFormat.VCard)
```
