---
title: "Работа с большими файлами PST"
url: /ru/net/working-with-large-pst-files/
weight: 130
type: docs
---

При обработке больших файлов PST производительность может снизиться.
Следующие рекомендации помогут вам повысить производительность приложения при обработке больших файлов.

{{% alert color="primary" %}}
Рассмотрим методы, возвращающиеся `IEnumerable` при просмотре папок или сообщений в посте.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

foreach (var folder in pst.RootFolder.EnumerateFolders())
foreach (var messageInfo in folder.EnumerateMessages())
{
    // Do something with message
}
```

{{% alert color="primary" %}}
Prefer [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) для доступа к основным свойствам сообщения.
{{% /alert %}}

```csharp
foreach (var messageInfo in folder.EnumerateMessages())
{
    Console.WriteLine($"Subject: {messageInfo.Subject}");
    Console.WriteLine($"To: {messageInfo.DisplayTo}");
    Console.WriteLine($"Importance: {messageInfo.Importance}");
    Console.WriteLine($"Message Class: {messageInfo.MessageClass}");
}
```

{{% alert color="primary" %}}
Избегайте использования [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) or [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) методы для всех сообщений, если вам не нужен доступ ко всем свойствам.
{{% /alert %}}

{{% alert color="primary" %}}
Рассмотрите возможность использования [EnumerateMessagesEntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessagesentryid/) чтобы легко получить все идентификаторы сообщений, содержащихся в папке.
{{% /alert %}}

 ```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
   // Use id to retrieve a property (ExtractProperty),
	 // extract a MapiMessage (ExtractMessage),
	 // extarct message attachments (ExtractAttachments),
	 // save msg to a stream(SaveMessageToStream).
}
 ```

{{% alert color="primary" %}}
Рассмотрите возможность использования [ExtractProperty](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractproperty/) для чтения одного свойства, отсутствующего в MessageInfo.
{{% /alert %}}

 ```csharp
foreach (var msgId in folder.EnumerateMessagesEntryId())
{
    var transportMessageHeaders =
        pst.ExtractProperty(Convert.FromBase64String(msgId), KnownPropertyList.TransportMessageHeaders.Tag)
            .GetString();
}
 ```

{{% alert color="primary" %}}
Рассмотрите возможность использования [ExtractAttachments](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractattachments/) если требуются только вложения.
{{% /alert %}}

```csharp
foreach (var msgId in folder.EnumerateMessagesEntryId())
{
   var attachments = pst.ExtractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Use [критерии поиска](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst)фильтрация на основе фильтрации для получения необходимых сообщений.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

var builder = new PersonalStorageQueryBuilder();
// Unread messages
builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);

foreach (var folder in pst.RootFolder.EnumerateFolders())
{
    var unread = folder.GetContents(builder.GetQuery());
}
```

{{% alert color="primary" %}}
Рассмотрите возможность использования [SaveMessageToStream](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/savemessagetostream/) если необходимо сохранить сообщения из pst.
{{% /alert %}}

Вместо использования:

```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
    var msg = pst.ExtractMessage(id);
    msg.Save(@"message.msg");
}
```

Use:

```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
    pst.SaveMessageToStream(id, File.OpenWrite(@"message.msg"));
}
```

{{% alert color="primary" %}}
Предпочитаю массовые методы [add](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#adding-bulk-messages) or [delete](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) несколько предметов.
{{% /alert %}}

