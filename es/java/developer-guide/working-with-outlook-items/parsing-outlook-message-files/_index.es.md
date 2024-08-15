---
title: "Análisis de archivos de mensajes de Outlook"
url: /es/java/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}}

Con Aspose.Email para Java, los desarrolladores no solo pueden cargar sino también analizar el contenido de los archivos de mensajes de Outlook.

- Para cargar archivos MSG desde el disco, utilice el [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase estática [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) method.
- Para analizar el contenido del archivo MSG, [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) expone una serie de métodos.

En este tema se muestra cómo cargar y, a continuación, analizar un archivo MSG para mostrar su contenido.

{{% /alert %}}

Aspose.Email para Java proporciona la [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase que se usa para abrir y analizar un archivo MSG. Como puede haber muchos destinatarios en un archivo MSG, [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) la clase expone el [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) método que devuelve un [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) que representa una colección de [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) objetos. El [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) El objeto expone además los métodos para trabajar con los atributos del destinatario.

La siguiente secuencia de pasos cumple este propósito:

1. Crea una instancia del [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) clase para cargar un archivo MSG desde [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) método estático.
2. Muestre el nombre, el asunto y el cuerpo del remitente del archivo MSG mediante [getSenderName()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSenderName--), [getSubject()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSubject--) and [getBody()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getBody--) methods.
3. Llame al [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) método expuesto por el [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) clase para obtener una referencia a la colección de [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) objetos asociados al archivo MSG.
4. Recorre el [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) colección para mostrar el contenido de cada [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) objetar a través de sus métodos públicos.

```java
// The path to the resource directory.
String dataDir = Utils.getSharedDataDir(ParsingOutlookMessageFiles.class) + "outlook/";

//Instantiate an MSG file to load an MSG file from disk
MapiMessage outlookMessageFile = MapiMessage.fromFile(dataDir + "message.msg");
//Display sender's name
System.out.println("Sender Name : " + outlookMessageFile.getSenderName());
//Display Subject
System.out.println("Subject : " + outlookMessageFile.getSubject());
//Display Body
System.out.println("Body : " + outlookMessageFile.getBody());
//Display Recipient's info
System.out.println("Recipients : \n");

//Recorre el recipients collection associated with the MapiMessage object
for (int i = 0; i < outlookMessageFile.getRecipients().size(); i++) {
	//Set a reference to the MapiRecipient object
	MapiRecipient rcp = (MapiRecipient) outlookMessageFile.getRecipients().get_Item(i);
	//Display recipient email address
	System.out.println("Email : " + rcp.getEmailAddress());
	//Display recipient name
	System.out.println("Name : " + rcp.getDisplayName());
	//Display recipient type
	System.out.println("Recipient Type : " + rcp.getRecipientType());
}
```

{{% alert %}}
**¡Pruébalo!**

Analice archivos de correo electrónico en línea con la versión gratuita [**Aplicación de análisis Aspose.Email**](https://products.aspose.app/email/es/parser).
{{% /alert %}}

## **Obtener un tipo de elemento de un mensaje MAPI**

Aspose.Email ofrece una [MapiItemType](https://reference.aspose.com/email/java/com.aspose.email/mapiitemtype/) enumeración que representa un tipo de elemento. Se puede usar para convertir mensajes en un objeto de una clase correspondiente derivada del [IMapiMessageItem](https://reference.aspose.com/email/java/com.aspose.email/imapimessageitem) interfaz. Esto evita que los usuarios comprueben el valor de la propiedad MessageClass antes de la conversión del mensaje.

El siguiente ejemplo de código muestra cómo recorrer en iteración los mensajes de una carpeta y convertir cada mensaje MAPI en el tipo de elemento MAPI correspondiente, según el tipo de mensaje:

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    MapiMessage msg = pst.extractMessage(messageInfo);

    switch (msg.getSupportedType()) {
        // Non-supported type. MapiMessage cannot be converted to an appropriate item type.
        // Just use in MSG format.
        case MapiItemType.None:
            break;
        // An email message. Conversion isn't required.
        case MapiItemType.Message:
            break;
        // A contact item. Can be converted to MapiContact.
        case MapiItemType.Contact:
            MapiContact contact = (MapiContact) msg.toMapiMessageItem();
            break;
        // A calendar item. Can be converted to MapiCalendar.
        case MapiItemType.Calendar:
            MapiCalendar calendar = (MapiCalendar) msg.toMapiMessageItem();
            break;
        // A distribution list. Can be converted to MapiDistributionList.
        case MapiItemType.DistList:
            MapiDistributionList dl = (MapiDistributionList) msg.toMapiMessageItem();
            break;
        // A Journal entry. Can be converted to MapiJournal.
        case MapiItemType.Journal:
            MapiJournal journal = (MapiJournal) msg.toMapiMessageItem();
            break;
        // A StickyNote. Can be converted to MapiNote.
        case MapiItemType.Note:
            MapiNote note = (MapiNote) msg.toMapiMessageItem();
            break;
        // A Task item. Can be converted to MapiTask.
        case MapiItemType.Task:
            MapiTask task = (MapiTask) msg.toMapiMessageItem();
            break;
    }
}
```

