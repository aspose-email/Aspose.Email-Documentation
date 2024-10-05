---
title: "Работа с большими PST файлами"
url: /ru/java/working-with-large-pst-files/
weight: 130
type: docs
---

Производительность может снижаться при обработке больших PST файлов. 
Следующие рекомендации помогут улучшить производительность вашего приложения при обработке больших файлов.

{{% alert color="primary" %}}
Рассматривайте методы, возвращающие `Iterable`, при переборе папок или сообщений в pst.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    for (FolderInfo folder : pst.getRootFolder().enumerateFolders())
        for (MessageInfo messageInfo : folder.enumerateMessages()) {
            // Выполните что-то с сообщением
        }
}
```

{{% alert color="primary" %}}
Предпочитайте [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/) для доступа к основным свойствам сообщения.
{{% /alert %}}

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    System.out.println("Тема: " + messageInfo.getSubject());
    System.out.println("Кому: " + messageInfo.getDisplayTo());
    System.out.println("Важно: " + messageInfo.getImportance());
    System.out.println("Класс сообщения: " + messageInfo.getMessageClass());
}
```
{{% alert color="primary" %}}
Избегайте использования методов [ExtractMessage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) или [EnumerateMapiMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) для всех сообщений, если вам не нужен доступ ко всем свойствам.
{{% /alert %}}

{{% alert color="primary" %}}
Рассмотрите возможность использования [EnumerateMessagesEntryId](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessagesEntryId--), чтобы легко получить все идентификаторы сообщений, содержащиеся в папке.
{{% /alert %}}

```java
for (String id : folder.enumerateMessagesEntryId())
{
    // Используйте id для получения свойства (extractProperty),
    // извлечения MapiMessage (extractMessage),
    // извлечения вложений сообщения (extractAttachments),
    // сохранения сообщения в поток (saveMessageToStream).
}
```
{{% alert color="primary" %}}
Рассмотрите возможность использования [ExtractProperty](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractProperty-byte---long-), чтобы прочитать одно свойство, которое отсутствует в MessageInfo.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    String transportMessageHeaders =
            pst.extractProperty(org.apache.commons.codec.binary.Base64.decodeBase64(msgId),
                    KnownPropertyList.TRANSPORT_MESSAGE_HEADERS.getTag()).getString();
}
```
{{% alert color="primary" %}}
Рассмотрите возможность использования [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-), если нужны только вложения.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    MapiAttachmentCollection attachments = pst.extractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Используйте фильтрацию на основе [критериев поиска](https://docs.aspose.com/email/ru/java/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst), чтобы получить необходимые сообщения.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {

    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // Непрочитанные сообщения
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);

    for (FolderInfo folder : pst.getRootFolder().enumerateFolders()) {
        MessageInfoCollection unread = folder.getContents(builder.getQuery());
    }
}
```

{{% alert color="primary" %}}
Рассмотрите возможность использования [SaveMessageToStream](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-), если необходимо сохранять сообщения из pst.
{{% /alert %}}

Вместо использования:

```java
for (String id : folder.enumerateMessagesEntryId()) {
    MapiMessage msg = pst.extractMessage(id);
    msg.save("message.msg");
}
```

Используйте:

```java
for (String id : folder.enumerateMessagesEntryId()) {
    try (OutputStream fos  = new FileOutputStream("message.msg")) {
        pst.saveMessageToStream(id, fos);
    }
}
```
{{% alert color="primary" %}}
Предпочитайте массовые методы для [добавления](https://docs.aspose.com/email/ru/java/working-with-messages-in-a-pst-file/#adding-bulk-messages) или [удаления](https://docs.aspose.com/email/ru/java/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) нескольких элементов.
{{% /alert %}}