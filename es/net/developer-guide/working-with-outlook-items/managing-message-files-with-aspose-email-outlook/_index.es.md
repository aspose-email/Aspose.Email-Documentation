---
title: "Gestión de Archivos de Mensajes con Aspose.Email.Outlook"
url: /es/net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Obteniendo un tipo de elemento MAPI**

La enumeración [MapiItemType](https://reference.aspose.com/email/net/aspose.email.mapi/mapiitemtype/) representa un tipo de elemento MAPI que puede convertirse explícitamente en un objeto de la clase correspondiente derivada de la interfaz [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/#imapimessageitem-interface). De esta manera, los usuarios pueden evitar comprobar el valor de la propiedad [MessageClass](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/messageclass/) antes de la conversión del mensaje.

El siguiente ejemplo de código muestra cómo definir un tipo para el elemento que se va a convertir:

```cs
foreach (var messageInfo in folder.EnumerateMessages())
{
    var msg = pst.ExtractMessage(messageInfo);

    switch (msg.SupportedType)
    {
        // Tipo no soportado. MapiMessage no puede ser convertido a un tipo de item apropiado.
        // Simplemente usar en formato MSG.
        case MapiItemType.None:
            break;
        // Un mensaje de correo electrónico. La conversión no es necesaria.
        case MapiItemType.Message:
            break;
        // Un elemento de contacto. Se puede convertir a MapiContact.
        case MapiItemType.Contact:
            var contact = (MapiContact)msg.ToMapiMessageItem();
            break;
        // Un elemento de calendario. Se puede convertir a MapiCalendar.
        case MapiItemType.Calendar:
            var calendar = (MapiCalendar)msg.ToMapiMessageItem();
            break;
        // Una lista de distribución. Se puede convertir a MapiDistributionList.
        case MapiItemType.DistList:
            var dl = (MapiDistributionList)msg.ToMapiMessageItem();
            break;
        // Una entrada de diario. Se puede convertir a MapiJournal.
        case MapiItemType.Journal:
            var journal = (MapiJournal)msg.ToMapiMessageItem();
            break;
        // Una Nota Adhesiva. Se puede convertir a MapiNote.
        case MapiItemType.Note:
            var note = (MapiNote)msg.ToMapiMessageItem();
            break;
        // Un elemento de tarea. Se puede convertir a MapiTask.
        case MapiItemType.Task:
            var task = (MapiTask)msg.ToMapiMessageItem();
            break;
    }
}
```
## **Guardando Correo Electrónico como HTML**

Aspose.Email permite guardar recursos de correo electrónico con rutas relativas al exportar mensajes al formato HTML. Esta característica proporciona más flexibilidad en cómo se vinculan los recursos en el archivo HTML de salida, facilitando compartir y mostrar correos electrónicos guardados en diferentes sistemas. Para guardar recursos con rutas relativas, use la propiedad [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/). El valor predeterminado de la propiedad es falso (los recursos se guardan con rutas absolutas). Cuando se establece en verdadero, los recursos se guardan con rutas relativas.

Los archivos HTML con rutas relativas son más portátiles y pueden ser visualizados correctamente sin importar la estructura de archivos del entorno de alojamiento. Puede elegir entre rutas absolutas y relativas según los requisitos. Puede definir rutas personalizadas para recursos utilizando el evento [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/).

El siguiente ejemplo de código demuestra cómo **guardar un correo electrónico con ruta relativa predeterminada a recursos**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
En este caso, los recursos se guardarán en la carpeta [nombre de archivo html]_files, en la misma ruta que el archivo .html y el HTML hará referencia a los recursos mediante rutas relativas.

El siguiente ejemplo de código demuestra cómo **guardar con ruta absoluta a recursos**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = false
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
Al igual que en el primer caso, los recursos se guardarán en la carpeta [nombre de archivo html]_files por defecto, pero el HTML hará referencia a los recursos utilizando rutas absolutas.

Al utilizar el evento [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/), puede establecer rutas relativas o absolutas personalizadas para los recursos. Al personalizar rutas con el manejador del evento [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/), y dado que [UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) está establecido en verdadero, debe asignar una ruta relativa a la propiedad [PathToResourceFile](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/pathtoresourcefile/) para asegurar una referencia correcta.

El siguiente ejemplo de código demuestra cómo **ruta relativa personalizada utilizando el Evento ResourceHtmlRendering**:

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
	    // Dado que UseRelativePathToResources = true, debe asignar una ruta relativa a la propiedad PathToResourceFile.
        args.PathToResourceFile = $@"images\{attachment.ContentType.Name}";
    }
};

msg.Save(Path.Combine(targetPath, "A Day in the Park.html"), htmlSaveOptions);
```


## **Convirtiendo MSG a mensaje MIME**

La API de Aspose.Email proporciona la capacidad de convertir archivos MSG a mensajes MIME utilizando el método [ToMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomailmessage/#tomailmessage).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMSGToMIMEMessage-ConvertMSGToMIMEMessage.cs" >}}


## **Estableciendo un Tiempo de Espera para el Proceso de Conversión y Carga de Mensajes**

Las siguientes características le permitirán establecer el tiempo de espera en milisegundos para el proceso de conversión y carga:

- Propiedad [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/#mailconversionoptionstimeout-property) - Limita el tiempo en milisegundos mientras se convierte un mensaje.

- [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Se genera si el tiempo se agota al convertir a MailMessage.

- [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limita el tiempo en milisegundos mientras se convierte un mensaje.

- [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Se genera si el tiempo se agota al convertir a MailMessage.

El siguiente ejemplo de código le mostrará cómo establecer un tiempo de espera al convertir un mensaje:

```cs
var options = new MailConversionOptions();
// Establecer el tiempo de espera a 5 segundos
options.Timeout = 5000;

options.TimeoutReached += (object sender, EventArgs args) =>
{
    string subj = (sender as MailMessage).Subject;
	 // Establecer una bandera indicando que se alcanzó el tiempo de espera
    isTimedOut = true;
};

var mailMessage = mapiMessage.ToMailMessage(options);
```

## **Lectura y Escritura de Archivo de Plantilla de Outlook (.OFT)**

Las plantillas de Outlook son muy útiles cuando desea enviar un mensaje de correo electrónico similar una y otra vez. En lugar de preparar el mensaje desde cero cada vez, primero prepare el mensaje en Outlook y guárdelo como una Plantilla de Outlook (OFT). Después de eso, cada vez que necesite enviar el mensaje, puede crearlo a partir de la plantilla, ahorrando tiempo escribiendo el mismo texto en el cuerpo o en la línea de asunto, configurando formato, etc. La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) de Aspose.Email puede ser utilizada para cargar y leer un archivo de plantilla de Outlook (OFT). Una vez que la plantilla de Outlook esté cargada en una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), puede actualizar el remitente, destinatario, cuerpo, asunto y otras propiedades. Después de actualizar las propiedades:

- Envíe el correo electrónico utilizando la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) o
- Guarde el mensaje en formato MSG y realice más actualizaciones/validaciones utilizando Microsoft Outlook.

En los ejemplos de código a continuación,:

1. Cargamos la plantilla utilizando la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Actualizamos algunas de las propiedades.
1. Guardamos el mensaje en formato MSG.

El siguiente fragmento de código le muestra cómo cargar el archivo OFT, actualizar el mensaje y guardarlo en formato MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cs" >}}

### **Guardando el archivo MSG de Outlook como Plantilla**

El siguiente fragmento de código le muestra cómo guardar el archivo MSG de Outlook como una plantilla.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveMsgAsTemplate-SaveMsgAsTemplate.cs" >}}

### **Determinar si un MapiMessage es OFT o MSG**

Al cargar un objeto MapiMessage desde un archivo, puede que necesite determinar si el mensaje cargado es un archivo de plantilla o un archivo de correo electrónico regular. Utilizando la propiedad [IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class), puede detectar con precisión si un correo electrónico es una plantilla o no. Esta funcionalidad puede ser valiosa al manejar y procesar varios tipos de archivos de correo electrónico dentro de aplicaciones y sistemas.

El siguiente ejemplo de código demuestra cómo determinar si un MapiMessage es OFT o MSG: 

```cs
var msg = MapiMessage.Load("message.msg");
var isOft = msg.IsTemplate; // devuelve false

var msg = MapiMessage.Load("message.oft");
var isOft = msg.IsTemplate; // devuelve true
```

### **Guardando MapiMessage o MailMessage en formato OFT**

La clase [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) permite especificar opciones adicionales al guardar un MailMessage o MapiMessage en un formato particular.

El siguiente ejemplo de código demuestra cómo guardar un mensaje en formato OFT:

```cs
// Guardar el MailMessage en formato OFT
using (var eml = MailMessage.Load("message.eml"))
{
    eml.Save("message.oft", SaveOptions.DefaultOft);
	
	// o manera alternativa #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);
	
	// o manera alternativa #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);

}

// Guardar el MapiMessage en formato OFT
using (var msg = MapiMessage.Load("message.msg"))
{
    msg.Save("message.oft", SaveOptions.DefaultOft);
	
	// o manera alternativa #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
	
	// o manera alternativa #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
}
```

## **Gestionando Mensajes Firmados Digitalmente**

Aspose.Email implementa el algoritmo completo de objeto de correo electrónico S/MIME. Esto le da a la API el poder completo para preservar las firmas digitales mientras se convierten mensajes entre formatos.

### **Preservando la Firma al Convertir de EML a MSG**

Aspose.Email preserva la firma digital al convertir de EML a MSG. El siguiente fragmento de código le muestra cómo convertir de EML a MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cs" >}}

### **Convirtiendo Mensajes S/MIME de MSG a EML**

Aspose.Email preserva la firma digital al convertir de MSG a EML como se muestra en el siguiente fragmento de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cs" >}}

### **Comprobando la Firma de Correos Electrónicos Seguros**

Las siguientes características están disponibles para comprobar la firma de objetos MapiMessage.

- Clase [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) para comprobar la firma de correos electrónicos seguros.
- Clase [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) para almacenar los resultados de la verificación.
- Método [SecureEmailManager.CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3).
- Método [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4).
- Método [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5).

El siguiente ejemplo de código muestra cómo implementar estas características en su proyecto:

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

### **Eliminando una Firma de un MapiMessage**

Para una mejor compatibilidad, se utilizan los métodos [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) y la propiedad [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) para eliminar una firma digital de un mensaje.

El siguiente fragmento de código muestra cómo implementar estas características en su proyecto:

```cs
var msg = MapiMessage.Load(fileName);

if (msg.IsSigned)
{
    var unsignedMsg = msg.RemoveSignature();
}
```
## **Descifrar un MapiMessage con Certificado**

Si tiene mensajes MAPI cifrados y necesita descifrarlos utilizando la clave privada almacenada en un certificado, las siguientes características de Aspose.Email pueden ser útiles:

- [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/#mapimessageisencrypted-property) - Obtiene un valor que indica si el mensaje está cifrado.
- [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Descifra este mensaje (el método busca el certificado y la clave privada apropiados en las tiendas del usuario y del ordenador actuales).
- [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Descifra este mensaje con el certificado.

El siguiente fragmento de código muestra cómo trabajar con mensajes MAPI cifrados: 

```cs
var privateCert = new X509Certificate2(privateCertFile, "password");
var msg = MapiMessage.Load("encrypted.msg");

if (msg.IsEncrypted);
{
    var decryptedMsg = msg.Decrypt(privateCert);
}
```

## **Estableciendo Categoría de Color para Archivos MSG de Outlook**

Una categoría de color marca un mensaje de correo electrónico para algún tipo de importancia o categoría. Microsoft Outlook permite a los usuarios asignar categorías de color para diferenciar correos electrónicos. Para manejar la categoría de color, use el [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/). Contiene funciones como [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory), [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory), [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) y [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories).

- [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory) toma un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) y la cadena de categoría de color, por ejemplo, "Categoría Púrpura" o "Categoría Roja" como argumentos.
- [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory) toma un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) y la cadena de categoría de color a ser eliminada del mensaje.
- [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) se utiliza para eliminar todas las categorías de color del mensaje.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories) se utiliza para recuperar todas las categorías de color de un mensaje particular.

El siguiente ejemplo realiza las tareas como se indica a continuación:

1. Agregar una categoría de color.
1. Agregar otra categoría de color.
1. Recuperar la lista de todas las categorías.
1. Eliminar todas las categorías.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetColorCategories-SetColorCategories.cs" >}}

## **Accediendo a la Información de Seguimiento desde el archivo MSG**

La API de Aspose.Email proporciona la capacidad de acceder a la información de seguimiento desde un mensaje enviado o recibido. Puede recuperar la información de Recibo de Lectura, Recibo de Entrega y resultados de votación de un archivo de mensaje.

### **Recuperando Información de Recibo de Lectura y Entrega**

El siguiente fragmento de código le muestra cómo recuperar información de recibo de lectura y entrega.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cs" >}}

## **Creando Mensajes de Reenvío y Respuesta**

La API de Aspose.Email proporciona la capacidad de crear y formatear mensajes de reenvío y respuesta. Las clases [ReplyMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/replymessagebuilder/) y [ForwardMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/forwardmessagebuilder/) de la API se utilizan para crear los mensajes de Respuesta y Reenvío respectivamente. Un mensaje de Respuesta o Reenvío puede ser especificado para ser creado utilizando cualquiera de los modos de la enumeración [OriginalMessageAdditionMode](https://reference.aspose.com/email/net/aspose.email.tools/originalmessageadditionmode/). Esta enumeración tiene los siguientes valores:

- **OriginalMessageAdditionMode.None** - El mensaje original no se incluye en el mensaje de respuesta.
- **OriginalMessageAdditionMode.Attachment** - El mensaje original se incluye como un archivo adjunto en el mensaje de respuesta.
- **OriginalMessageAdditionMode.Textpart** - El mensaje original se incluye como texto en el cuerpo del mensaje de respuesta.

### **Creando un Mensaje de Respuesta**

El siguiente fragmento de código le muestra cómo crear un mensaje de respuesta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatReplyMessage-CreatReplyMessage.cs" >}}

### **Creando un Mensaje de Reenvío**

El siguiente fragmento de código le muestra cómo crear un mensaje de reenvío.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateForwardMessage-CreatForwardMessage.cs" >}}