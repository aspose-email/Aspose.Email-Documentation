---
title: "Работа с большими PST файлами"
url: /ru/net/working-with-large-pst-files/
weight: 130
type: docs
---

Производительность может ухудшаться при обработке больших PST файлов. 
Следующие рекомендации помогут вам улучшить производительность вашего приложения при обработке больших файлов.

{{% alert color="primary" %}}
Рассмотрите методы, возвращающие `IEnumerable`, при обходе папок или сообщений в PST.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

foreach (var folder in pst.RootFolder.EnumerateFolders())
foreach (var messageInfo in folder.EnumerateMessages())
{
    // Выполните какое-либо действие с сообщением
}
```

{{% alert color="primary" %}}
Предпочитайте [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) для доступа к основным свойствам сообщения.
{{% /alert %}}

```csharp
foreach (var messageInfo in folder.EnumerateMessages())
{
    Console.WriteLine($"Тема: {messageInfo.Subject}");
    Console.WriteLine($"Кому: {messageInfo.DisplayTo}");
    Console.WriteLine($"Важность: {messageInfo.Importance}");
    Console.WriteLine($"Класс сообщения: {messageInfo.MessageClass}");
}
```

{{% alert color="primary" %}}
Избегайте использования методов [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) или [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) для всех сообщений, если вам не нужен доступ ко всем свойствам.
{{% /alert %}}

{{% alert color="primary" %}}
Рассмотрите возможность использования [EnumerateMessagesEntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessagesentryid/) для легкого извлечения всех идентификаторов сообщений, содержащихся в папке.
{{% /alert %}}

```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
   // Используйте id, чтобы получить свойство (ExtractProperty),
   // извлечь MapiMessage (ExtractMessage),
   // извлечь вложения сообщения (ExtractAttachments),
   // сохранить сообщение в поток (SaveMessageToStream).
}
```

{{% alert color="primary" %}}
Рассмотрите возможность использования [ExtractProperty](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractproperty/) для чтения отдельного свойства, отсутствующего в MessageInfo.
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
Рассмотрите возможность использования [ExtractAttachments](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractattachments/), если нужны только вложения.
{{% /alert %}}

```csharp
foreach (var msgId in folder.EnumerateMessagesEntryId())
{
   var attachments = pst.ExtractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Используйте фильтрацию на основе [критериев поиска](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst) для получения нужных сообщений.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

var builder = new PersonalStorageQueryBuilder();
// Непрочитанные сообщения
builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);

foreach (var folder in pst.RootFolder.EnumerateFolders())
{
    var unread = folder.GetContents(builder.GetQuery());
}
```

{{% alert color="primary" %}}
Рассмотрите возможность использования [SaveMessageToStream](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/savemessagetostream/), если необходимо сохранить сообщения из PST.
{{% /alert %}}

Вместо использования:

```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
    var msg = pst.ExtractMessage(id);
    msg.Save(@"message.msg");
}
```

Используйте:

```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
    pst.SaveMessageToStream(id, File.OpenWrite(@"message.msg"));
}
```

{{% alert color="primary" %}}
Предпочитайте массовые методы для [добавления](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#adding-bulk-messages) или [удаления](https://docs.aspose.com/email/ru/net/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) нескольких элементов.
{{% /alert %}}