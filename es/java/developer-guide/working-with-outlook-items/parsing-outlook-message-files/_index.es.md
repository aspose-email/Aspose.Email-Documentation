---
title: "Analizando Archivos de Mensaje de Outlook"
url: /es/java/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

Usando Aspose.Email para Java, los desarrolladores no solo pueden cargar sino también analizar el contenido de los archivos de mensaje de Outlook.

- Para cargar archivos MSG desde el disco, use el método estático [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) de la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
- Para analizar el contenido del archivo MSG, la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) expone varios métodos.

Este tema muestra cómo cargar y luego analizar un archivo MSG para mostrar su contenido.

{{% /alert %}} 

Aspose.Email para Java proporciona la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) que se utiliza para abrir y analizar un archivo MSG. Dado que puede haber muchos destinatarios en un archivo MSG, la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) expone el método [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) que devuelve una [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) que representa una colección de objetos [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/). El objeto [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) expone además métodos para trabajar con atributos del destinatario.

La siguiente secuencia de pasos sirve a este propósito:

1. Cree una instancia de la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) para cargar un archivo MSG desde el método estático [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-).
2. Muestre el nombre del remitente, el asunto y el cuerpo del archivo MSG utilizando los métodos [getSenderName()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSenderName--), [getSubject()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSubject--) y [getBody()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getBody--).
3. Llame al método [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) expuesto por la clase [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) para obtener una referencia a la colección de objetos [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) asociados con el archivo MSG.
4. Recorra la colección [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) para mostrar el contenido de cada objeto [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) a través de sus métodos públicos.

```java
// La ruta al directorio de recursos.
String dataDir = Utils.getSharedDataDir(ParsingOutlookMessageFiles.class) + "outlook/";
//Instanciar un archivo MSG para cargar un archivo MSG del disco
MapiMessage outlookMessageFile = MapiMessage.fromFile(dataDir + "message.msg");
//Mostrar el nombre del remitente
System.out.println("Sender Name : " + outlookMessageFile.getSenderName());
//Mostrar Asunto
System.out.println("Subject : " + outlookMessageFile.getSubject());
//Mostrar Cuerpo
System.out.println("Body : " + outlookMessageFile.getBody());
//Mostrar información del Destinatario
System.out.println("Recipients : \n");
//Recorrer la colección de destinatarios asociada con el objeto MapiMessage
for (int i = 0; i < outlookMessageFile.getRecipients().size(); i++) {
	//Establecer una referencia al objeto MapiRecipient
	MapiRecipient rcp = (MapiRecipient) outlookMessageFile.getRecipients().get_Item(i);
	//Mostrar la dirección de correo electrónico del destinatario
	System.out.println("Email : " + rcp.getEmailAddress());
	//Mostrar el nombre del destinatario
	System.out.println("Name : " + rcp.getDisplayName());
	//Mostrar el tipo de destinatario
	System.out.println("Recipient Type : " + rcp.getRecipientType());
}
```

{{% alert %}}
**¡Pruébalo!**

Analiza archivos de correo electrónico en línea con el **[Aplicación Aspose.Email Parser](https://products.aspose.app/email/es/parser)** gratuita.
{{% /alert %}}

## **Obtener un Tipo de Elemento de un Mensaje MAPI**

Aspose.Email ofrece un enum [MapiItemType](https://reference.aspose.com/email/java/com.aspose.email/mapiitemtype/) que representa un tipo de elemento. Se puede usar para la conversión de un mensaje en un objeto de una clase correspondiente derivada de la interfaz [IMapiMessageItem](https://reference.aspose.com/email/java/com.aspose.email/imapimessageitem). Esto evita que los usuarios verifiquen el valor de la propiedad MessageClass antes de la conversión del mensaje.

El siguiente ejemplo de código demuestra cómo iterar a través de los mensajes en una carpeta y convertir cada mensaje MAPI en un tipo de elemento MAPI correspondiente, dependiendo del tipo del mensaje:

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    MapiMessage msg = pst.extractMessage(messageInfo);

    switch (msg.getSupportedType()) {
        // Tipo no soportado. MapiMessage no se puede convertir en un tipo de elemento apropiado.
        // Solo usar en formato MSG.
        case MapiItemType.None:
            break;
        // Un mensaje de correo electrónico. No se requiere conversión.
        case MapiItemType.Message:
            break;
        // Un elemento de contacto. Se puede convertir a MapiContact.
        case MapiItemType.Contact:
            MapiContact contact = (MapiContact) msg.toMapiMessageItem();
            break;
        // Un elemento de calendario. Se puede convertir a MapiCalendar.
        case MapiItemType.Calendar:
            MapiCalendar calendar = (MapiCalendar) msg.toMapiMessageItem();
            break;
        // Una lista de distribución. Se puede convertir a MapiDistributionList.
        case MapiItemType.DistList:
            MapiDistributionList dl = (MapiDistributionList) msg.toMapiMessageItem();
            break;
        // Una entrada de diario. Se puede convertir a MapiJournal.
        case MapiItemType.Journal:
            MapiJournal journal = (MapiJournal) msg.toMapiMessageItem();
            break;
        // Una nota adhesiva. Se puede convertir a MapiNote.
        case MapiItemType.Note:
            MapiNote note = (MapiNote) msg.toMapiMessageItem();
            break;
        // Un elemento de tarea. Se puede convertir a MapiTask.
        case MapiItemType.Task:
            MapiTask task = (MapiTask) msg.toMapiMessageItem();
            break;
    }
}
```