---
title: "Trabajar con archivos adjuntos de mensajes"
url: /es/net/working-with-message-attachments/
weight: 80
type: docs
---


## **Administración de archivos adjuntos con Aspose Outlook**

[Creación y almacenamiento de archivos de mensajes de Outlook (MSG)](https://docs.aspose.com/email/es/net/creating-and-saving-msg-files/) explica cómo crear y guardar mensajes y cómo crear archivos MSG con archivos adjuntos. En este artículo se explica cómo administrar los archivos adjuntos de Microsoft Outlook con Aspose.Email. Se puede acceder a los archivos adjuntos de un archivo de mensajes y guardarlos en el disco mediante [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) propiedad. El [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) la propiedad es una colección de tipos [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) class.

### **Comprueba si el archivo adjunto está en línea o es normal**

Los archivos adjuntos en línea y regulares tienen diferentes propósitos. Los archivos adjuntos en línea se integran visualmente en el mensaje de correo electrónico y suelen ser imágenes o archivos multimedia. Mientras tanto, los archivos adjuntos normales son archivos independientes que se adjuntan al correo electrónico y pueden incluir varios tipos de archivos. El [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) propiedad del [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) la clase obtiene un valor que indica si el adjunto está en línea o es normal.

El siguiente ejemplo de código extrae y muestra información sobre cada adjunto del MAPIMessage cargado, incluidos sus nombres para mostrar y si son archivos adjuntos en línea o no.

```cs
var message = MapiMessage.Load(fileName);

foreach (var attach in message.Attachments)
{
    Console.WriteLine($"{attach.DisplayName0} : {attach.IsInline)}");
}
```

### **Guardar archivos adjuntos del archivo de mensajes de Outlook (MSG)**

Para guardar los archivos adjuntos de un archivo MSG:

1. Recorra en iteración el [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) recoja y obtenga los archivos adjuntos individuales.
1. Para guardar los archivos adjuntos, llame al método Save () de la clase MapiAttachment.

El siguiente fragmento de código muestra cómo guardar los archivos adjuntos en el disco local.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}

### **Obtener archivos adjuntos de mensajes de correo anidados**

Los archivos adjuntos OLE incrustados también aparecen en [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) colección de archivos adjuntos de clase. El siguiente ejemplo de código analiza un archivo de mensajes en busca de archivos adjuntos incrustados y lo guarda en el disco. El [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) El método estático class fromProperties () puede crear un nuevo mensaje a partir de un archivo adjunto incrustado. El siguiente fragmento de código muestra cómo obtener archivos adjuntos de mensajes de correo anidados.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}

### **Eliminar archivos adjuntos**

La biblioteca Aspose Outlook proporciona la funcionalidad para eliminar los archivos adjuntos de los archivos de mensajes de Microsoft Outlook (.msg):

- Llama al método removeAttachments (). Toma la ruta del archivo de mensajes como parámetro. Se implementa como un método estático público, por lo que no es necesario crear una instancia del objeto.

El siguiente fragmento de código muestra cómo eliminar los archivos adjuntos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}

También puede llamar al [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) método estático de clase [DestoryAttachment()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/destroyattachments/). Funciona más rápido que removeAttachment (), porque el método removeAttachment () analiza el archivo de mensajes.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}

### **Agregar archivos adjuntos de MSG**

Un mensaje de Outlook puede contener otros mensajes de Microsoft Outlook en archivos adjuntos, ya sea como mensajes normales o incrustados. El [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) permite a los miembros sobrecargados del método Add crear mensajes de Outlook con ambos tipos de datos adjuntos.

{{% alert %}}
**¡Pruébalo!**

Agregue o elimine archivos adjuntos de correo electrónico con la versión gratuita [**Aplicación Aspose.Email Editor**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregar un ReferenceAttachment en un MapiMessage**

The [MapiAttachmentCollection.Add (nombre de cadena, cadena SharedLink, cadena url, cadena ProviderName)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) método del [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) La clase permite agregar un adjunto de referencia en un mapiMessage. Cuando los destinatarios del correo electrónico hagan clic en el archivo adjunto de referencia, podrán acceder al archivo vinculado si tienen los permisos adecuados para hacerlo. Al usar un archivo adjunto de referencia, puede enviar un mensaje de correo electrónico más pequeño y asegurarse de que todos tengan acceso a la versión más actualizada del archivo o elemento.

El método tiene los siguientes parámetros:

- *name* - el nombre del adjunto
- *sharedLink* - un enlace compartido totalmente cualificado al archivo adjunto proporcionado por el servicio web que manipula el archivo adjunto
- *url* - una ubicación de archivo
- *providerName* - el nombre del proveedor de archivos adjuntos de referencia

El ejemplo de código siguiente muestra cómo agregar un adjunto de referencia a un mensaje:

```cs
// Let's say you want to send an email message that includes a link to a Document.pdf file stored on a Google Drive.
// Instead of attaching the document directly to the email message,
// you can create a reference attachment that links to the file on the Google Drive.

// Create a message
var msg = new MapiMessage("from@domain.com", "to@domain.com", "Outlook message file",
    "This message is created by Aspose.Email", OutlookMessageFormat.Unicode);

// Add reference attachment
msg.Attachments.Add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive");
//Also, you can set additional attachment properties
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPermissionType, AttachmentPermissionType.AnyoneCanEdit);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentOriginalPermissionType, 0);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentIsFolder, false);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentProviderEndpointUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPreviewUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentThumbnailUrl, "");
// Finally save the message
msg.Save(@"my.msg");
```

### **Incrustar un mensaje como archivo adjunto**

El siguiente fragmento de código muestra cómo incrustar un archivo MSG adjunto en un mensaje.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}

### **Lectura de mensajes incrustados desde archivos adjuntos**

El siguiente fragmento de código muestra cómo leer los mensajes incrustados de los archivos adjuntos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}

## **Inserción y reemplazo de archivos adjuntos**

La API Aspose.Email ofrece la capacidad de insertar archivos adjuntos en un índice específico en el mensaje principal. También ofrece la posibilidad de reemplazar el contenido de un adjunto por otro adjunto de mensaje.

{{% alert %}}
**¡Pruébalo!**

Ejecute el [ReplaceAttach](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ReplaceAttach/ReplaceAttach) proyecto de aplicación simple y pruebe las capacidades de Aspose.Email para reemplazar los archivos adjuntos en acción.
{{% /alert %}}

### **Insertar en una ubicación específica**

La API Aspose.Email ofrece la capacidad de insertar un archivo adjunto de MSG en un mensaje principal mediante el método de inserción MapiAttachmentCollection Insert de MapiAttachmentCollection Insert (int index, string name, mapiMessage msg). En el siguiente fragmento de código, se muestra cómo insertar un archivo adjunto en una ubicación específica.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}

### **Reemplazar el contenido del archivo adjunto**

Esto se puede usar para reemplazar el contenido de los archivos adjuntos incrustados por otros nuevos mediante el método Replace. Sin embargo, no se puede usar para insertar datos adjuntos con PR_ATTACH_NUM = 4 (por ejemplo) en la colección con Collection.count = 2. El siguiente fragmento de código muestra cómo reemplazar el contenido de los archivos adjuntos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}

### **Cambiar el nombre de un archivo adjunto en MapiMessage**

Es posible editar el valor de la propiedad DisplayName en los archivos adjuntos de MapiMessage.

```cs
var msg = MapiMessage.Load(fileName);
msg.Attachments[0].DisplayName = "New display name 1";
msg.Attachments[1].DisplayName = "New display name 2";
```

## **Guardar archivos adjuntos de mensajes firmados digitalmente**

La API Aspose.Email ofrece la capacidad de obtener o establecer un valor que indique si se decodificará un mensaje con firma clara. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}
