---
title: "Administración de archivos de mensajes con Aspose.Email.Outlook"
url: /es/net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Obtener un tipo de elemento MAPI**

The [MapiItemType](https://reference.aspose.com/email/net/aspose.email.mapi/mapiitemtype/) enum representa un tipo de elemento MAPI que se puede convertir explícitamente en un objeto de la clase correspondiente derivada del [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/#imapimessageitem-interface)interfaz. De esta forma, los usuarios pueden evitar comprobar la [MessageClass](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/messageclass/) valor de la propiedad antes de la conversión del mensaje.

El siguiente ejemplo de código muestra cómo definir un tipo para el artículo que se va a convertir:

```cs
foreach (var messageInfo in folder.EnumerateMessages())
{
    var msg = pst.ExtractMessage(messageInfo);

    switch (msg.SupportedType)
    {
        // Non-supported type. MapiMessage cannot be converted to an appropriate item type.
        // Just use in MSG format.
        case MapiItemType.None:
            break;
        // An email message. Conversion isn't required.
        case MapiItemType.Message:
            break;
        // A contact item. Can be converted to MapiContact.
        case MapiItemType.Contact:
            var contact = (MapiContact)msg.ToMapiMessageItem();
            break;
        // A calendar item. Can be converted to MapiCalendar.
        case MapiItemType.Calendar:
            var calendar = (MapiCalendar)msg.ToMapiMessageItem();
            break;
        // A distribution list. Can be converted to MapiDistributionList.
        case MapiItemType.DistList:
            var dl = (MapiDistributionList)msg.ToMapiMessageItem();
            break;
        // A Journal entry. Can be converted to MapiJournal.
        case MapiItemType.Journal:
            var journal = (MapiJournal)msg.ToMapiMessageItem();
            break;
        // A StickyNote. Can be converted to MapiNote.
        case MapiItemType.Note:
            var note = (MapiNote)msg.ToMapiMessageItem();
            break;
        // A Task item. Can be converted to MapiTask.
        case MapiItemType.Task:
            var task = (MapiTask)msg.ToMapiMessageItem();
            break;
    }
}
```
## **Guardar el correo electrónico como HTML**

Aspose.Email permite guardar recursos de correo electrónico con rutas relativas al exportar mensajes a formato HTML. Esta función proporciona más flexibilidad en la forma en que se vinculan los recursos en el archivo HTML de salida, lo que facilita compartir y mostrar los correos electrónicos guardados en diferentes sistemas. Para guardar recursos con rutas relativas, utilice [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) propiedad. El valor predeterminado de la propiedad es falso (los recursos se guardan con rutas absolutas). Cuando se establece en verdadero, los recursos se guardan con rutas relativas.

Los archivos HTML con rutas relativas son más portátiles y se pueden ver correctamente independientemente de la estructura de archivos del entorno de alojamiento. Puede elegir entre rutas absolutas y relativas en función de los requisitos. Puede definir rutas personalizadas para los recursos mediante el [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) event.

El siguiente ejemplo de código muestra cómo **guardar un correo electrónico con la ruta relativa predeterminada a los recursos**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
En este caso, los recursos se guardarán en la carpeta [nombre del archivo html] _files, en la misma ruta que el archivo.html, y el HTML hará referencia a los recursos mediante rutas relativas.

El ejemplo de código que aparece a continuación demuestra cómo **ahorre con una ruta absoluta a los recursos**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = false
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
Como en el primer caso, los recursos se guardarán en la carpeta [nombre del archivo html] _files de forma predeterminada, pero el HTML hará referencia a los recursos mediante rutas absolutas.

Mediante el uso del [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) evento, puede establecer rutas absolutas o relativas personalizadas para los recursos. Al personalizar las rutas con el [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) controlador de eventos, y desde [UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) está establecido en verdadero, debe asignar una ruta relativa al [PathToResourceFile](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/pathtoresourcefile/) propiedad para garantizar una referencia correcta.

El siguiente ejemplo de código muestra cómo **ruta relativa personalizada mediante el evento ResourceHtmlRendering**

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

htmlSaveOptions.ResourceHtmlRendering += (o, args) =>
{
    if (o is AttachmentBase attachment)
    {
	    // Since UseRelativePathToResources = true, you should assign a relative path to the PathToResourceFile property.
        args.PathToResourceFile = $@"images\{attachment.ContentType.Name}";
    }
};

msg.Save(Path.Combine(targetPath, "A Day in the Park.html"), htmlSaveOptions);
```


## **Conversión de MSG a mensaje MIME**

La API Aspose.Email ofrece la capacidad de convertir archivos MSG en mensajes MIME mediante el [ToMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomailmessage/#tomailmessage) method.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMSGToMIMEMessage-ConvertMSGToMIMEMessage.cs" >}}


## **Configuración del tiempo de espera para el proceso de conversión y carga de mensajes**

Las siguientes funciones le permitirán establecer el tiempo de espera en milisegundos para el proceso de conversión y carga:

- [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/#mailconversionoptionstimeout-property) propiedad: limita el tiempo en milisegundos durante la conversión de un mensaje.

- [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Se aumenta si se acaba el tiempo durante la conversión a MailMessage.

- [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limita el tiempo en milisegundos durante la conversión de un mensaje.

- [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Se aumenta si se acaba el tiempo durante la conversión a MailMessage.

El ejemplo de código que aparece a continuación te mostrará cómo configurar el tiempo de espera al convertir un mensaje:

```cs
var options = new MailConversionOptions();
// Set the timeout to 5 seconds
options.Timeout = 5000;

options.TimeoutReached += (object sender, EventArgs args) =>
{
    string subj = (sender as MailMessage).Subject;
	 // Set a flag indicating the timeout was reached
    isTimedOut = true;
};

var mailMessage = mapiMessage.ToMailMessage(options);
```

## **Archivo de plantilla de Outlook para lectura y escritura (.OFT)**

Las plantillas de Outlook son muy útiles cuando quieres enviar un mensaje de correo similar una y otra vez. En lugar de preparar el mensaje desde cero cada vez, primero prepare el mensaje en Outlook y guárdelo como plantilla de Outlook (OFT). Después de eso, siempre que necesite enviar el mensaje, puede crearlo a partir de la plantilla, ahorrando tiempo al escribir el mismo texto en el cuerpo o en la línea de asunto, configurar el formato, etc. Aspose. Correos electrónicos [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase se puede usar para cargar y leer un archivo de plantilla de Outlook (OFT). Una vez cargada la plantilla de Outlook en una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase, puede actualizar el remitente, el destinatario, el cuerpo, el asunto y otras propiedades. Tras actualizar las propiedades:

- Envía el correo electrónico mediante [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase o
- Guarde el mensaje como MSG y realice más actualizaciones/validaciones con Microsoft Outlook.

En los ejemplos de código que aparecen a continuación, nosotros:

1. Cargue la plantilla mediante el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Actualice algunas de las propiedades.
1. Guarda el mensaje en formato MSG.

El siguiente fragmento de código muestra cómo cargar el archivo OFT, actualizar el mensaje y guardarlo en formato MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cs" >}}

### **Guardar el archivo MSG de Outlook como plantilla**

El siguiente fragmento de código muestra cómo guardar el archivo MSG de Outlook como plantilla.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveMsgAsTemplate-SaveMsgAsTemplate.cs" >}}

### **Determine si un MapiMessage es OFT o MSG**

Al cargar un objeto MapiMessage desde un archivo, es posible que deba determinar si el mensaje cargado es un archivo de plantilla o un archivo de correo electrónico normal. Mediante el uso del [IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) propiedad del [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) clase, puedes detectar con precisión si un correo electrónico es una plantilla o no. Esta funcionalidad puede resultar valiosa a la hora de gestionar y procesar varios tipos de archivos de correo electrónico en aplicaciones y sistemas.

El siguiente ejemplo de código demuestra cómo determinar si un MAPIMessage es OFT o MSG:

```cs
var msg = MapiMessage.Load("message.msg");
var isOft = msg.IsTemplate; // returns false

var msg = MapiMessage.Load("message.oft");
var isOft = msg.IsTemplate; // returns true
```

### **Guardar MapiMessage o MailMessage en formato OFT**

The [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) La clase le permite especificar opciones adicionales al guardar un MailMessage o MapiMessage en un formato determinado.

El siguiente ejemplo de código muestra cómo guardar un mensaje en formato OFT:

```cs
// Save the MailMessage to OFT format
using (var eml = MailMessage.Load("message.eml"))
{
    eml.Save("message.oft", SaveOptions.DefaultOft);
	
	// or alternative way #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);
	
	// or alternative  way #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);

}

// Save the MapiMessage to OFT format
using (var msg = MapiMessage.Load("message.msg"))
{
    msg.Save("message.oft", SaveOptions.DefaultOft);
	
	// or alternative way #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
	
	// or alternative  way #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
}
```

## **Administración de mensajes firmados digitalmente**

Aspose.Email implementa el algoritmo completo de objetos de correo electrónico S/MIME. Esto le da a la API el poder total para preservar las firmas digitales mientras convierte los mensajes entre formatos.

### **Preservar la firma al convertir de EML a MSG**

Aspose.Email conserva la firma digital al convertir de EML a MSG. El siguiente fragmento de código muestra cómo convertir de EML a MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cs" >}}

### **Conversión de mensajes S/MIME de MSG a EML**

Aspose.Email conserva la firma digital al convertir de MSG a EML, como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cs" >}}

### **Comprobar la firma de correos electrónicos seguros**

Están disponibles las siguientes funciones para comprobar la firma de los objetos MapiMessage.

- [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) clase para comprobar la firma de correos electrónicos seguros.
- [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) clase para almacenar los resultados de la comprobación.
- [SecureEmailManager.checkSignature (mensaje de MAPIMessage)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3) method.
- [SecureEmailManager.CheckSignature (mensaje de MAPIMessage, certificado X509 Certificate2 para descifrar)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4) method.
- [SecureEmailManager.CheckSignature (mensaje de MapiMessage, certificado X509 Certificate 2 para desencriptar, X509 Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5) method.

El siguiente ejemplo de código muestra cómo implementar las funciones en tu proyecto:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions());
var result = new SecureEmailManager().CheckSignature(msg);

var certFileName = "cert.pfx";
var cert = new X509Certificate2(certFileName, "pass");
var eml = MapiMessage.Load(fileName);
var store = new X509Store();
store.Open(OpenFlags.ReadWrite);
store.Add(cert);
store.Close();

var result = new SecureEmailManager().CheckSignature(eml, cert, store);
```

### **Eliminar una firma de un MAPIMessage**

Para una mejor compatibilidad, el [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) método y [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) Las propiedades se utilizan para eliminar una firma digital de un mensaje.

El siguiente fragmento de código muestra cómo implementar estas funciones en tu proyecto:

```cs
var msg = MapiMessage.Load(fileName);

if (msg.IsSigned)
{
    var unsignedMsg = msg.RemoveSignature();
}
```
## **Descifrar un MAPIMessage con certificado**

Si tiene mensajes MAPI cifrados y necesita descifrarlos con la clave privada almacenada en un certificado, las siguientes funciones de Aspose.Email pueden resultar útiles:

- [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/#mapimessageisencrypted-property) - Obtiene un valor que indica si el mensaje está cifrado.
- [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Descifra este mensaje (el método busca en el usuario y la computadora actuales de My stores el certificado y la clave privada apropiados).
- [MapiMessage.decrypt (certificado X509 Certificate2)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Descifra este mensaje con un certificado.

El siguiente fragmento de código muestra cómo trabajar con mensajes MAPI cifrados:

```cs
var privateCert = new X509Certificate2(privateCertFile, "password");
var msg = MapiMessage.Load("encrypted.msg");

if (msg.IsEncrypted);
{
    var decryptedMsg = msg.Decrypt(privateCert);
}
```

## **Configuración de la categoría de color para los archivos MSG de Outlook**

Una categoría de color marca un mensaje de correo electrónico con algún tipo de importancia o categoría. Microsoft Outlook permite a los usuarios asignar categorías de colores para diferenciar los correos electrónicos. Para gestionar la categoría de color, utilice el [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/). Contiene funciones como [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory), [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory), [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) and [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories).

- [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) y la cadena de categoría de color, por ejemplo, «Categoría púrpura» o «Categoría roja» como argumentos.
- [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) y la cadena de categoría de color que se va a eliminar del mensaje.
- [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) se usa para eliminar todas las categorías de colores del mensaje.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories) se usa para recuperar todas las categorías de colores de un mensaje en particular.

El siguiente ejemplo realiza las tareas que se indican a continuación:

1. Añade una categoría de color.
1. Añade otra categoría de color.
1. Recupera la lista de todas las categorías.
1. Eliminar todas las categorías.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetColorCategories-SetColorCategories.cs" >}}

## **Acceso a la información de seguimiento desde el archivo MSG**

La API Aspose.Email ofrece la capacidad de acceder a la información de seguimiento de un mensaje enviado o recibido. Puede recuperar la información sobre la lectura, la entrega, la lectura, el recibo y los resultados de la votación de un archivo de mensajes.

### **Recuperación de la información de lectura y recibo de entrega**

El siguiente fragmento de código muestra cómo recuperar la información de los recibos de entrega y lectura.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cs" >}}

## **Creación de mensajes de reenvío y respuesta**

La API Aspose.Email proporciona la capacidad de crear y formatear los mensajes de reenvío y respuesta. La [ReplyMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/replymessagebuilder/) and [ForwardMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/forwardmessagebuilder/) las clases de la API se utilizan para crear los mensajes de respuesta y reenviar, respectivamente. Se puede especificar la creación de un mensaje de respuesta o reenvío mediante cualquiera de los modos de [OriginalMessageAdditionMode](https://reference.aspose.com/email/net/aspose.email.tools/originalmessageadditionmode/) enumeración. Esta enumeración tiene los valores siguientes:

- **OriginalMessageAdditionMode.None** - El mensaje original no se incluye en el mensaje de respuesta.
- **OriginalMessageAdditionMode.Attachment** - El mensaje original se incluye como adjunto en el mensaje de respuesta
- **OriginalMessageAdditionMode.Textpart** - El mensaje original se incluye como texto en el cuerpo del mensaje de respuesta

### **Creación de un mensaje de respuesta**

El siguiente fragmento de código muestra cómo crear un mensaje de respuesta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatReplyMessage-CreatReplyMessage.cs" >}}

### **Creación de un mensaje de reenvío**

El siguiente fragmento de código muestra cómo crear un mensaje de reenvío.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateForwardMessage-CreatForwardMessage.cs" >}}
