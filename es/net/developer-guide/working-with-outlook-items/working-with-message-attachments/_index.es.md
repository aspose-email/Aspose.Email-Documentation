---
title: "Trabajando con Archivos Adjuntos de Mensajes"
url: /es/net/working-with-message-attachments/
weight: 80
type: docs
---


## **Gestionando Adjuntos con Aspose Outlook**

[Crear y guardar archivos de mensaje de Outlook (MSG)](https://docs.aspose.com/email/es/net/creating-and-saving-msg-files/) explica cómo crear y guardar mensajes, y cómo crear archivos MSG con adjuntos. Este artículo explica cómo gestionar los adjuntos de Microsoft Outlook con Aspose.Email. Los adjuntos de un archivo de mensaje se acceden y guardan en disco utilizando la propiedad [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). La propiedad [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) es una colección del tipo de la clase [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/).

### **Verificar si el Adjunto es Inline o Regular**

Los adjuntos inline y regulares cumplen diferentes propósitos. Los adjuntos inline están integrados visualmente en el mensaje de correo electrónico y suelen ser imágenes o archivos multimedia. Mientras tanto, los adjuntos regulares son archivos separados que se adjuntan al correo electrónico y pueden incluir varios tipos de archivos. La propiedad [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) de la clase [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) obtiene un valor que indica si el adjunto es inline o regular.

El siguiente ejemplo de código extrae y muestra información sobre cada adjunto en el MapiMessage cargado, incluyendo sus nombres para mostrar y si son adjuntos inline o no.

```cs
var message = MapiMessage.Load(fileName);

foreach (var attach in message.Attachments)
{
    Console.WriteLine($"{attach.DisplayName0} : {attach.IsInline)}");
}
```

### **Guardar Adjuntos desde el Archivo de Mensaje de Outlook (MSG)**

Para guardar adjuntos de un archivo MSG:

1. Iterar a través de la colección [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) y obtener los adjuntos individuales.
1. Para guardar los adjuntos, llamar al método Save() de la clase MapiAttachment.

El siguiente fragmento de código te muestra cómo guardar adjuntos en el disco local.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}

### **Obteniendo Adjuntos de Mensajes de Correo Anidados**

Los adjuntos OLE incrustados también aparecen en la colección de adjuntos de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). El siguiente ejemplo de código analiza un archivo de mensaje en busca de adjuntos de mensajes incrustados y los guarda en el disco. El método estático FromProperties() de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) puede crear un nuevo mensaje a partir de un adjunto incrustado. El siguiente fragmento de código te muestra cómo obtener adjuntos de mensajes de correo anidados.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}

### **Eliminar Adjuntos**

La biblioteca Aspose Outlook proporciona la funcionalidad para eliminar adjuntos de archivos de Microsoft Outlook Message (.msg):

- Llama al método RemoveAttachments(). Toma la ruta del archivo de mensaje como parámetro. Está implementado como un método estático público, por lo que no necesitas instanciar el objeto.

El siguiente fragmento de código te muestra cómo eliminar adjuntos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}

También puedes llamar al método estático [DestoryAttachment()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/destroyattachments/) de la clase [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). Funciona más rápido que RemoveAttachment(), porque el método RemoveAttachment() analiza el archivo de mensaje.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}

### **Agregar Adjuntos MSG**

Un mensaje de Outlook puede contener otros mensajes de Microsoft Outlook en adjuntos ya sea como mensajes regulares o incrustados. La [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) proporciona miembros sobrecargados del método Add para crear mensajes de Outlook con ambos tipos de adjuntos.

{{% alert %}}
**¡Pruébalo!**

Agrega o elimina adjuntos de correo electrónico con la gratuita [**Aplicación Editor de Aspose.Email**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregar un Adjunto de Referencia en un MapiMessage**

El método [MapiAttachmentCollection.Add(string name, string sharedLink, string url, string providerName)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) de la clase [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) permite agregar un adjunto de referencia en un MapiMessage. Cuando los destinatarios del correo electrónico hacen clic en el adjunto de referencia, podrán acceder al archivo vinculado si tienen los permisos apropiados para hacerlo. Al usar un adjunto de referencia, puedes enviar un mensaje de correo electrónico más pequeño y asegurarte de que todos tengan acceso a la versión más actualizada del archivo o elemento.

El método tiene los siguientes parámetros:

- *name* - el nombre del adjunto
- *sharedLink* - un enlace compartido completamente calificado al adjunto proporcionado por el servicio web que manipula el adjunto
- *url* - una ubicación de archivo
- *providerName* - un nombre del proveedor del adjunto de referencia

El siguiente ejemplo de código demuestra cómo agregar un adjunto de referencia a un mensaje:

```cs
// Supongamos que deseas enviar un mensaje de correo electrónico que incluya un enlace a un archivo Document.pdf almacenado en Google Drive.
// En lugar de adjuntar directamente el documento al mensaje de correo electrónico,
// puedes crear un adjunto de referencia que vincule al archivo en Google Drive.

// Crear un mensaje
var msg = new MapiMessage("from@domain.com", "to@domain.com", "Archivo de mensaje de Outlook",
    "Este mensaje ha sido creado por Aspose.Email", OutlookMessageFormat.Unicode);

// Agregar adjunto de referencia
msg.Attachments.Add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive");
//Además, puedes establecer propiedades adicionales del adjunto
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPermissionType, AttachmentPermissionType.AnyoneCanEdit);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentOriginalPermissionType, 0);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentIsFolder, false);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentProviderEndpointUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPreviewUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentThumbnailUrl, "");
// Finalmente guarda el mensaje
msg.Save(@"my.msg");
```

### **Incrustando un Mensaje como Adjunto**

El siguiente fragmento de código te muestra cómo incrustar un archivo MSG como adjunto a un mensaje.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}

### **Leyendo Mensajes Incrustados desde Adjuntos**

El siguiente fragmento de código te muestra cómo leer mensajes incrustados desde adjuntos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}

## **Inserción y Reemplazo de Adjuntos**

La API de Aspose.Email proporciona la capacidad de insertar adjuntos en un índice específico en el mensaje principal. También proporciona la facilidad de reemplazar el contenido de un adjunto con otro adjunto de mensaje.

{{% alert %}}
**¡Pruébalo!**

Ejecuta el proyecto de aplicación simple [ReplaceAttach](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ReplaceAttach/ReplaceAttach) y prueba las capacidades de Aspose.Email para reemplazar adjuntos en acción.
{{% /alert %}} 

### **Insertar en una Ubicación Específica**

La API de Aspose.Email proporciona la capacidad de insertar un adjunto MSG en un MSG principal usando el método Insert de MapiAttachmentCollection MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). El siguiente fragmento de código te muestra cómo insertar un adjunto en una ubicación específica.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}

### **Reemplazar Contenidos del Adjunto**

Esto se puede usar para reemplazar el contenido de un adjunto incrustado con los nuevos usando el método Replace. Sin embargo, no se puede usar para insertar un adjunto con PR_ATTACH_NUM = 4 (por ejemplo) en la colección con collection.Count = 2. El siguiente fragmento de código te muestra cómo reemplazar los contenidos de un adjunto.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}

### **Renombrar un Adjunto en MapiMessage**

Es posible editar el valor de la propiedad DisplayName en los adjuntos de MapiMessage.

```cs
var msg = MapiMessage.Load(fileName);
msg.Attachments[0].DisplayName = "Nuevo nombre para mostrar 1";
msg.Attachments[1].DisplayName = "Nuevo nombre para mostrar 2";
```

## **Guardar Adjuntos desde Mensajes Firmados Digitalmente**

La API de Aspose.Email proporciona la capacidad de obtener o establecer un valor que indique si un mensaje firmado en claro será decodificado.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}