---
title: "Trabajar con archivos PST de gran tamaño"
url: /es/java/working-with-large-pst-files/
weight: 130
type: docs
---

El rendimiento puede degradarse al procesar archivos PST de gran tamaño.
Las siguientes sugerencias te ayudarán a mejorar el rendimiento de tu aplicación al procesar archivos de gran tamaño.

{{% alert color="primary" %}}
Considere los métodos de devolución `Iterable` al recorrer carpetas o mensajes en una publicación.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    for (FolderInfo folder : pst.getRootFolder().enumerateFolders())
        for (MessageInfo messageInfo : folder.enumerateMessages()) {
            // Do something with message
        }
}
```

{{% alert color="primary" %}}
Prefer [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/) para acceder a las propiedades básicas de los mensajes.
{{% /alert %}}

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    System.out.println("Subject: " + messageInfo.getSubject());
    System.out.println("To: " + messageInfo.getDisplayTo());
    System.out.println("Importance: " + messageInfo.getImportance());
    System.out.println("Message Class: " + messageInfo.getMessageClass());
}
```
{{% alert color="primary" %}}
Evite usar el [ExtractMessage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) or [EnumerateMapiMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) métodos para todos los mensajes, a menos que necesite tener acceso a todas las propiedades.
{{% /alert %}}

{{% alert color="primary" %}}
Considera usar [EnumerateMessagesEntryId](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessagesEntryId--) para recuperar fácilmente todos los identificadores de mensajes contenidos en una carpeta.
{{% /alert %}}

```java
for (String id : folder.enumerateMessagesEntryId())
{
    // Use id to retrieve a property (extractProperty),
    // extract a MapiMessage (extractMessage),
    // extarct message attachments (extractAttachments),
    // save msg to a stream (saveMessageToStream).
}
```
{{% alert color="primary" %}}
Considera usar [ExtractProperty](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractProperty-byte---long-) para leer una sola propiedad que falta en MessageInfo.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    String transportMessageHeaders =
            pst.extractProperty(org.apache.commons.codec.binary.Base64.decodeBase64(msgId),
                    KnownPropertyList.TRANSPORT_MESSAGE_HEADERS.getTag()).getString();
}
```
{{% alert color="primary" %}}
Considera usar [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) si solo se requieren los archivos adjuntos.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    MapiAttachmentCollection attachments = pst.extractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Use [criterios de búsqueda](https://docs.aspose.com/email/es/java/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst)filtrado basado en el filtrado para obtener los mensajes que necesita.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {

    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);

    for (FolderInfo folder : pst.getRootFolder().enumerateFolders()) {
        MessageInfoCollection unread = folder.getContents(builder.getQuery());
    }
}
```

{{% alert color="primary" %}}
Considera usar [SaveMessageToStream](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) si es necesario guardar los mensajes de pst.
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
Prefiero los métodos masivos a [add](https://docs.aspose.com/email/es/java/working-with-messages-in-a-pst-file/#adding-bulk-messages) or [delete](https://docs.aspose.com/email/es/java/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) varios artículos.
{{% /alert %}}
