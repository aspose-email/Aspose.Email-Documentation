---
title: "Trabajando con Adjunto de Mensajes"
url: /es/java/trabajando-con-adjuntos-de-mensajes/
weight: 70
type: docs
---

## **Analizando y Guardando Adjuntos**

Los archivos de mensaje de Outlook pueden contener uno o más adjuntos. Aspose.Email permite a los desarrolladores recorrer los adjuntos en un archivo MSG y guardarlos en el disco. Este tema describe el proceso. También describe cómo incrustar un adjunto.

La clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) de Aspose.Email se utiliza para cargar un archivo MSG desde el disco y expone el método [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) que hace referencia a la colección de objetos [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) asociada con el archivo MSG. El objeto [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) expone además métodos que realizan acciones sobre el adjunto.

Para guardar los adjuntos en un archivo MSG en el disco con el nombre y la extensión originales:

1. Crea una instancia de la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) para cargar un archivo MSG utilizando el método estático [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-).
2. Llama al método [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) de la clase [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) para obtener una referencia a la colección de objetos [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) asociada con el archivo MSG.
3. Recorre la [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) para mostrar contenidos respecto a cada objeto [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) a través de sus métodos públicos.
4. Llama al método [save()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#save-java.lang.String-) de la clase [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) para guardar el adjunto en el disco.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ParseAndSaveAttachment.java" >}}

Incrustando Mensajes como Adjuntos

Un mensaje de Microsoft Outlook puede contener otros mensajes de Microsoft Outlook en adjuntos, ya sea como mensajes regulares, descritos anteriormente, o como mensajes incrustados. La [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) proporciona miembros sobrecargados del método add para crear mensajes de Outlook con ambos tipos de adjuntos. Los archivos MSG de Outlook incrustados en un archivo MSG contienen un PR_ATTACH_METHOD con el valor 5.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-EmbeddingMessageAsAttachment.java" >}}

### **Leer un Mensaje Incrustado de un Adjunto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ReadingEmbeddedMessageFromAttachment.java" >}}

## **Inserción y Reemplazo de Adjuntos MSG**

La API de Aspose.Email proporciona la capacidad de insertar adjuntos en un índice específico en el mensaje padre. También proporciona la opción de reemplazar el contenido de un adjunto con otro adjunto de mensaje.

### **Insertar Adjunto MSG en una Ubicación Específica**

La API de Aspose.Email proporciona la capacidad de insertar un adjunto MSG a un MSG padre utilizando el método [MapiAttachmentCollection.Insert()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#insert-int-java.lang.String-com.aspose.email.MapiMessage-).

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-InsertMSGAttachmentAtSpecificLocation.java" >}}

### **Reemplazar Contenidos de Adjunto MSG Incrustado**

Esto se puede usar para reemplazar los contenidos de un adjunto incrustado con los nuevos utilizando el método [Replace](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#replace-int-java.lang.String-com.aspose.email.MapiMessage-). Sin embargo, no se puede usar para insertar un adjunto con PR_ATTACH_NUM = 4 (por ejemplo) en la colección con collection.Count = 2.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-ReplaceEmbeddedMSGAttachmentContents.java" >}}

## **Guardar Adjuntos de un Mensaje Firmado Digitalmente**

La API de Aspose.Email proporciona la capacidad de obtener o establecer un valor que indica si el mensaje firmado claro será decodificado.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-DecodeClearSignedContent-DecodeClearSignedContent.java" >}}

## **Renombrar un Adjunto en un MapiMessage**

Aspose.Email hace posible editar el valor de la propiedad [DisplayName](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#setDisplayName-java.lang.String-) en los adjuntos de [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/).

El siguiente ejemplo de código demuestra cómo actualizar los nombres de visualización del primer y segundo adjunto dentro del mensaje Mapi cargado:

```java
MapiMessage msg = MapiMessage.load(fileName);
msg.getAttachments().get_Item(0).setDisplayName("Nuevo nombre de visualización 1");
msg.getAttachments().get_Item(1).setDisplayName("Nuevo nombre de visualización 2");
```

## **Comprobar si un Adjunto es Inline o Regular**

La diferencia entre adjuntos inline y regulares es cómo se presentan dentro de un correo electrónico. Los adjuntos inline están incrustados dentro del cuerpo del correo electrónico y se pueden ver sin tener que abrir un archivo separado o descargar nada. Los adjuntos regulares, por otro lado, son archivos separados que se adjuntan al correo electrónico pero no se muestran directamente dentro del cuerpo del mensaje y deben ser descargados y abiertos externamente. La propiedad [MapiAttachment.IsInline](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#isInline--) de la clase [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) obtiene un valor que indica si el adjunto es inline o regular.

El siguiente ejemplo de código carga un mensaje de correo electrónico desde un archivo y luego recupera información sobre los adjuntos, imprimiendo específicamente el nombre de visualización de cada adjunto y si está inline dentro del mensaje o no:

```java
MapiMessage message = MapiMessage.load("fileName");

for (MapiAttachment attach : message.getAttachments()) {
    System.out.println(attach.getDisplayName() + ": " + attach.isInline());
}
```