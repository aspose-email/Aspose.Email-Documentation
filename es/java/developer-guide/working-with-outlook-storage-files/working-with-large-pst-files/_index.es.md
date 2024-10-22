---
title: "Trabajando con grandes archivos PST"
url: /es/java/working-with-large-pst-files/
weight: 130
type: docs
---

El rendimiento puede verse degradado al procesar grandes archivos PST.
Las siguientes sugerencias ayudarán a mejorar el rendimiento de su aplicación al procesar archivos grandes.

{{% alert color="primary" %}}
Considere métodos que devuelvan `Iterable` al recorrer carpetas o mensajes en un pst.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    for (FolderInfo folder : pst.getRootFolder().enumerateFolders())
        for (MessageInfo messageInfo : folder.enumerateMessages()) {
            // Hacer algo con el mensaje
        }
}
```

{{% alert color="primary" %}}
Prefiera [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/) para acceder a las propiedades básicas del mensaje.
{{% /alert %}}

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    System.out.println("Asunto: " + messageInfo.getSubject());
    System.out.println("Para: " + messageInfo.getDisplayTo());
    System.out.println("Importancia: " + messageInfo.getImportance());
    System.out.println("Clase de mensaje: " + messageInfo.getMessageClass());
}
```
{{% alert color="primary" %}}
Evite usar los métodos [ExtractMessage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) o [EnumerateMapiMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) para todos los mensajes a menos que necesite acceder a todas las propiedades.
{{% /alert %}}

{{% alert color="primary" %}}
Considere usar [EnumerateMessagesEntryId](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessagesEntryId--) para recuperar fácilmente todos los IDs de mensajes contenidos en una carpeta.
{{% /alert %}}

```java
for (String id : folder.enumerateMessagesEntryId())
{
    // Usar id para recuperar una propiedad (extractProperty),
    // extraer un MapiMessage (extractMessage),
    // extraer los archivos adjuntos del mensaje (extractAttachments),
    // guardar el mensaje en un flujo (saveMessageToStream).
}
```
{{% alert color="primary" %}}
Considere usar [ExtractProperty](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractProperty-byte---long-) para leer una única propiedad que falta en MessageInfo.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    String transportMessageHeaders =
            pst.extractProperty(org.apache.commons.codec.binary.Base64.decodeBase64(msgId),
                    KnownPropertyList.TRANSPORT_MESSAGE_HEADERS.getTag()).getString();
}
```
{{% alert color="primary" %}}
Considere usar [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) si solo se requieren los archivos adjuntos.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    MapiAttachmentCollection attachments = pst.extractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Utilice el filtrado basado en [criterios de búsqueda](https://docs.aspose.com/email/es/java/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst) para obtener los mensajes que necesita.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {

    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // Mensajes no leídos
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);

    for (FolderInfo folder : pst.getRootFolder().enumerateFolders()) {
        MessageInfoCollection unread = folder.getContents(builder.getQuery());
    }
}
```

{{% alert color="primary" %}}
Considere usar [SaveMessageToStream](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) si es necesario guardar mensajes del pst.
{{% /alert %}}

En lugar de usar:

```java
for (String id : folder.enumerateMessagesEntryId()) {
    MapiMessage msg = pst.extractMessage(id);
    msg.save("message.msg");
}
```

Use:

```java
for (String id : folder.enumerateMessagesEntryId()) {
    try (OutputStream fos  = new FileOutputStream("message.msg")) {
        pst.saveMessageToStream(id, fos);
    }
}
```
{{% alert color="primary" %}}
Prefiera métodos masivos para [agregar](https://docs.aspose.com/email/es/java/working-with-messages-in-a-pst-file/#adding-bulk-messages) o [eliminar](https://docs.aspose.com/email/es/java/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) múltiples elementos.
{{% /alert %}}