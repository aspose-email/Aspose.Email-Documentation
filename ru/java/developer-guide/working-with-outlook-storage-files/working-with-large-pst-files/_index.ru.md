---
title: "Работа с большими файлами PST"
url: /ru/java/working-with-large-pst-files/
weight: 130
type: docs
---

При обработке больших файлов PST производительность может снизиться.
Следующие рекомендации помогут повысить производительность приложения при обработке больших файлов.

{{% alert color="primary" %}}
Рассмотрим методы, возвращающиеся `Iterable` при просмотре папок или сообщений в посте.
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
Prefer [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/) для доступа к основным свойствам сообщения.
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
Избегайте использования [ExtractMessage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) or [EnumerateMapiMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) методы для всех сообщений, если вам не нужен доступ ко всем свойствам.
{{% /alert %}}

{{% alert color="primary" %}}
Рассмотрите возможность использования [EnumerateMessagesEntryId](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessagesEntryId--) чтобы легко получить все идентификаторы сообщений, содержащихся в папке.
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
Рассмотрите возможность использования [ExtractProperty](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractProperty-byte---long-) для чтения одного свойства, отсутствующего в MessageInfo.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    String transportMessageHeaders =
            pst.extractProperty(org.apache.commons.codec.binary.Base64.decodeBase64(msgId),
                    KnownPropertyList.TRANSPORT_MESSAGE_HEADERS.getTag()).getString();
}
```
{{% alert color="primary" %}}
Рассмотрите возможность использования [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) если требуются только вложения.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    MapiAttachmentCollection attachments = pst.extractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Use [критерии поиска](https://docs.aspose.com/email/ru/java/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst)фильтрация на основе фильтрации для получения необходимых сообщений.
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
Рассмотрите возможность использования [SaveMessageToStream](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) если необходимо сохранить сообщения из pst.
{{% /alert %}}

Вместо использования:

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
Предпочитаю массовые методы [add](https://docs.aspose.com/email/ru/java/working-with-messages-in-a-pst-file/#adding-bulk-messages) or [delete](https://docs.aspose.com/email/ru/java/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) несколько предметов.
{{% /alert %}}
