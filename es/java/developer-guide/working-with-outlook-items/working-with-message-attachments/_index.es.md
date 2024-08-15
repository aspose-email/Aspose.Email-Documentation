---
title: "Trabajar con archivos adjuntos de mensajes"
url: /es/java/working-with-message-attachments/
weight: 70
type: docs
---

## **Análisis y almacenamiento de archivos adjuntos**

Los archivos de mensajes de Outlook pueden contener uno o más archivos adjuntos. Aspose.Email permite a los desarrolladores revisar los archivos adjuntos de un archivo MSG y guardarlos en el disco. En este tema se describe el proceso. También describe cómo incrustar un archivo adjunto.

Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) la clase se usa para cargar un archivo MSG desde el disco y expone el [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) método que hace referencia al [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) colección de objetos asociada al archivo MSG. La [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) El objeto expone además los métodos que realizan acciones en el archivo adjunto.

Para guardar los archivos adjuntos de un archivo MSG en un disco con el nombre y la extensión originales:

1. Crea una instancia del [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase para cargar un archivo MSG usando el [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) método estático.
2. Llame al [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) class [getAttachments()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getAttachments--) método para obtener una referencia a la colección de [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) objetos asociados al archivo MSG.
3. Recorre el [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/) para mostrar el contenido de cada [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) objetar a través de sus métodos públicos.
4. Llame al [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) class [save()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#save-java.lang.String-) método para guardar el archivo adjunto en el disco.
 
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ParseAndSaveAttachment.java" >}}

Incrustar mensajes como archivos adjuntos

Un mensaje de Microsoft Outlook puede contener otros mensajes de Microsoft Outlook en archivos adjuntos, ya sea como mensajes normales, descritos anteriormente, o como mensajes incrustados. El [MapiAttachmentCollection](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/)  proporciona miembros sobrecargados del método add para crear mensajes de Outlook con ambos tipos de datos adjuntos. Los archivos MSG de Outlook incrustados en un archivo MSG contienen un PR_ATTACH_METHOD con el valor 5.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-EmbeddingMessageAsAttachment.java" >}}

### **Lectura de un mensaje incrustado desde un archivo adjunto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ParseAndSaveAttachment-ReadingEmbeddedMessageFromAttachment.java" >}}

## **Inserción y reemplazo de archivos adjuntos MSG**

La API Aspose.Email ofrece la capacidad de insertar archivos adjuntos en un índice específico en el mensaje principal. También ofrece la posibilidad de reemplazar el contenido de un adjunto por otro adjunto de mensaje.

### **Inserte el archivo adjunto MSG en una ubicación específica**

La API Aspose.Email ofrece la capacidad de insertar un archivo adjunto de MSG en un MSG principal mediante el [MapiAttachmentCollection.Insert()](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#insert-int-java.lang.String-com.aspose.email.MapiMessage-) method.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-InsertMSGAttachmentAtSpecificLocation.java" >}}

### **Reemplazar el contenido del archivo adjunto MSG incrustado**

Esto se puede usar para reemplazar el contenido de los archivos adjuntos incrustados por otros nuevos mediante el [Replace](https://reference.aspose.com/email/java/com.aspose.email/mapiattachmentcollection/#replace-int-java.lang.String-com.aspose.email.MapiMessage-) método. Sin embargo, no se puede usar para insertar datos adjuntos con PR_ATTACH_NUM = 4 (por ejemplo) en la colección con Collection.count = 2.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-InsertAndReplaceMSGAttachment-ReplaceEmbeddedMSGAttachmentContents.java" >}}

## **Guardar archivos adjuntos de un mensaje firmado digitalmente**

La API Aspose.Email ofrece la capacidad de obtener o establecer un valor que indique si se decodificará un mensaje con firma clara. 

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-DecodeClearSignedContent-DecodeClearSignedContent.java" >}}

## **Cambiar el nombre de un archivo adjunto en un MAPIMessage**

Aspose.Email permite editar el [DisplayName](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#setDisplayName-java.lang.String-) valor de la propiedad en [Adjuntos de MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/).

El siguiente ejemplo de código muestra cómo actualizar los nombres para mostrar del primer y segundo archivo adjunto del mensaje Mapi cargado:

```java
MapiMessage msg = MapiMessage.load(fileName);
msg.getAttachments().get_Item(0).setDisplayName("New display name 1");
msg.getAttachments().get_Item(1).setDisplayName("New display name 2");
```
## **Comprueba si un archivo adjunto está en línea o es normal**

La diferencia entre los archivos adjuntos en línea y los archivos adjuntos normales es la forma en que se presentan en un correo electrónico. Los archivos adjuntos en línea están incrustados en el cuerpo del correo electrónico y se pueden ver sin tener que abrir un archivo separado ni descargar nada. Los archivos adjuntos normales, por otro lado, son archivos independientes que se adjuntan al correo electrónico, pero no se muestran directamente en el cuerpo del mensaje y deben descargarse y abrirse externamente. El [MapiAttachment.IsInline](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/#isInline--) propiedad del [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/mapiattachment/) la clase obtiene un valor que indica si el adjunto está en línea o es normal.

En el siguiente ejemplo de código, se carga un mensaje de correo electrónico desde un archivo y, a continuación, se recupera la información sobre los archivos adjuntos. En concreto, se imprime el nombre para mostrar de cada archivo adjunto y si está en línea en el mensaje o no:

```java
MapiMessage message = MapiMessage.load("fileName");

for (MapiAttachment attach : message.getAttachments()) {
    System.out.println(attach.getDisplayName() + ": " + attach.isInline());
}
```

