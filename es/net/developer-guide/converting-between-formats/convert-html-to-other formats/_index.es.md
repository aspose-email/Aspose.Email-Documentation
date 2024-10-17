---
title: "Convertir HTML a Otros Formatos"
url: /es/net/converting-between-formats/convert-html-to-other-formats
weight: 60
type: docs
---

## **Convertir HTML a EML**

Aspose.Email para .NET proporciona un método para convertir archivos HTML a formato EML utilizando los métodos [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) y [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) para cargar el archivo HTML existente y guardarlo en formato EML respectivamente:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.eml", SaveOptions.DefaultEml);
```

En el ejemplo de código, la clase [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) permite especificar opciones adicionales al cargar un MailMessage desde formato HTML. El siguiente ejemplo de código demuestra el uso de esta clase. En el ejemplo, se especifica una representación de texto del cuerpo del mensaje:

```cs
// Crear una instancia de HtmlLoadOptions
var loadOptions = new HtmlLoadOptions();

// Establecer la propiedad ShouldAddPlainTextView en true para generar una vista de texto plano junto con HTML
loadOptions.ShouldAddPlainTextView = true;

// Cargar un archivo HTML
var mailMessage = MailMessage.Load("input.html", loadOptions);

// Acceder a la vista de texto plano del mensaje de correo electrónico
var plainTextView = mailMessage.GetAlternateViewContent("text/plain");

// Imprimir o procesar further la vista de texto plano
Console.WriteLine("Vista de Texto Plano:");
Console.WriteLine(plainTextView);
```

## **Convertir HTML a EMLX**

Puedes convertir fácilmente archivos HTML a EMLX. Todas las propiedades y clases proporcionadas por la API para la conversión de HTML a EML están disponibles para este tipo de conversión también:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.emlx", SaveOptions.DefaultEmlx);
```
Para configuraciones adicionales, consulta el párrafo [Convertir HTML a EML](#convert-html-to-eml).

## **Convertir HTML a ICS**

Para realizar la tarea, la biblioteca ofrece la clase [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) para representar y gestionar eventos del calendario. El siguiente ejemplo de código demuestra cómo crear una cita a partir del contenido HTML y guardarla en un archivo de formato ICS (iCalendar):

```cs
// Contenido HTML de ejemplo
var htmlContent = File.ReadAllText("content.html");

// Crear e inicializar una instancia de la clase Appointment
var appointment = new Appointment(
    "Sala de Reuniones 3 en la Sede de la Oficina", // Ubicación
    "Reunión Mensual",                               // Resumen
    "Por favor confirma tu disponibilidad.",         // Descripción
    new DateTime(2015, 2, 8, 13, 0, 0),             // Fecha de inicio
    new DateTime(2015, 2, 8, 14, 0, 0),             // Fecha de finalización
    "from@domain.com",                               // Organizador
    "attendees@domain.com")
{
    HtmlDescription = htmlContent
};

// Guardar el evento en un archivo ICS
appointment.Save("output.ics", AppointmentSaveFormat.Ics);
```

## **Generar MBOX desde contenido HTML**

Para realizar la conversión de HTML a MBOX, utiliza el método [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class), especificando la ruta del archivo de contenido HTML y una instancia de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Este método analiza el contenido HTML y genera un objeto MailMessage correspondiente, preservando la estructura y formato del HTML original. Después de cargar el contenido HTML en un objeto MailMessage, escribe el mensaje en un archivo MBOX utilizando la clase [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class):

```cs
using (var eml = MailMessage.Load("content.html", new HtmlLoadOptions()))
{
    using (var writer = new MboxrdStorageWriter("output.mbox", false))
    {
        writer.WriteMessage(eml);
    }
}
```

## **Convertir HTML a MHTML**

Utiliza el método [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para cargar el archivo existente, especificando una ruta hacia él y una instancia de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Este método analiza el contenido HTML y genera un objeto MailMessage correspondiente, preservando la estructura y formato del HTML original. Después de cargar el contenido HTML en un objeto MailMessage, los desarrolladores pueden guardarlo como un archivo MHTML utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), especificando la ruta de archivo de salida deseada y utilizando la opción [SaveOptions.DefaultMhtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmhtml/):

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.mhtml", SaveOptions.DefaultMhtml);
```

La clase [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) proporciona una variedad de opciones para configurar el comportamiento y configuraciones del archivo de salida MHTML en lugar de SaveOptions.DefaultMhtml. Con sus [propiedades](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#properties), puedes especificar opciones adicionales al guardar MailMessage en formato MHTML.
Las más populares son:

- [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/mhtformatoptions/) - Te permite personalizar cómo se guarda el mensaje de correo electrónico en formato MHT para adaptarse mejor a tus necesidades.
- [SaveAttachments](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveattachments/) - Obtiene o establece un valor que indica si se deben guardar los archivos adjuntos.
- [SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Define si se necesita guardar todos los encabezados en el MHTML de salida o no. El valor predeterminado es falso.
- [PreserveOriginalDate](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/preserveoriginaldate/) - Define si se debe mantener la fecha original en el mensaje de correo al guardar o no. El valor predeterminado es verdadero.

El siguiente ejemplo de código demuestra cómo se pueden usar estas propiedades:

```cs
var mhtSaveOptions = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader,
    SaveAttachments = true,
    SaveAllHeaders = true,
    PreserveOriginalDate = true
}
```

## **Convertir HTML a MSG**

Después de cargar el contenido HTML en un objeto MailMessage, guárdalo como un archivo MSG utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), especificando la ruta de archivo de salida deseada y utilizando la opción [SaveOptions.DefaultMsgUnicode](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmsgunicode/) opción. Esta opción asegura que el archivo de salida se guarde en formato MSG con codificación Unicode.

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.msg", SaveOptions.DefaultMsgUnicode);
```
Además, Aspose.Email para .NET ofrece una gama de características y opciones avanzadas para la conversión de HTML a MSG:

## **Convertir HTML a OFT**

Después de cargar el contenido HTML en un objeto MailMessage, guárdalo como un archivo OFT utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), especificando la ruta de archivo de salida deseada y utilizando la opción [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/) opción:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("template.oft", SaveOptions.DefaultOft);
```

## **Agregar un mensaje con contenido HTML de origen a PST**

La conversión de HTML a PST implica crear un nuevo archivo PST (Tabla de Almacenamiento Personal) con una nueva carpeta, cargar un archivo HTML y agregarlo a la nueva carpeta:

1. Crea una instancia de un objeto PersonalStorage que represente un nuevo archivo PST utilizando el método [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) de la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
2. Accede a la carpeta raíz del archivo PST y agrega una subcarpeta usando el método [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder) de la clase [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class).
3. Carga el contenido de un archivo HTML en un objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) utilizando el método [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) con una instancia de [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) para especificar que el contenido está en formato HTML.
4. Agrega el objeto MapiMessage cargado (que representa el contenido HTML) a la carpeta dentro del archivo PST utilizando el método [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/).

```cs
using (var pst = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
{ 
    var inbox = pst.RootFolder.AddSubFolder("Inbox");
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    inbox.AddMessage(msg);
}
```

## **Agregar un mensaje con contenido HTML de origen a OST**

El siguiente ejemplo de código con pasos te mostrará cómo estos componentes trabajan juntos para agregar contenido HTML a un archivo OST:

1. Carga un archivo OST existente utilizando el método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) de la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) que se utiliza para representar el archivo de almacenamiento que contendrá los mensajes de correo electrónico. 
2. Carga el archivo HTML usando el método [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) que representa un mensaje de correo electrónico en formato Microsoft Outlook. 
3. Especifica [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) para habilitar opciones adicionales al cargar MailMessage desde formato HTML.
4. Recupera la carpeta raíz del archivo OST utilizando la propiedad [RootFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/rootfolder/) del objeto [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
5. Obtén la carpeta de la Bandeja de entrada dentro del archivo OST utilizando el método [GetSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder) en la carpeta raíz.
6. Agrega el objeto MapiMessage cargado (que representa el contenido HTML) a la carpeta de la Bandeja de entrada utilizando el método [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) en la carpeta.

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
``` 

## **Convertir HTML a VCF**

El siguiente ejemplo de código demuestra cómo crear un elemento de contacto, poblarlo con contenido HTML y guardarlo en un archivo VCF:

1. Lee el contenido de un archivo HTML en una variable de cadena utilizando el método File.ReadAllText.
2. Crea un nuevo objeto MapiContact instanciando la clase [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/#mapicontact-class).
3. Establece las propiedades del contacto: nombre a mostrar, dirección de correo electrónico.
4. Establece el contenido del cuerpo del contacto en HTML usando [SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/setbodycontent/#setbodycontent).
5. Guarda el contacto como un archivo VCF utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_4).

```cs
var content = File.ReadAllText("content.html");
            
// Crear un nuevo MapiContact
var contact = new MapiContact();
contact.NameInfo.DisplayName = "John Doe";
contact.ElectronicAddresses.Email1.EmailAddress = "john.doe@example.com";
contact.SetBodyContent(content, BodyContentType.Html);

// Guardar el contacto en un archivo VCF
contact.Save("contact.vcf", ContactSaveFormat.VCard)
```