---
title: "Trabajar con archivos PST de gran tamaño"
url: /es/net/working-with-large-pst-files/
weight: 130
type: docs
---

El rendimiento puede degradarse al procesar archivos PST de gran tamaño.
Las siguientes sugerencias te ayudarán a mejorar el rendimiento de tu aplicación al procesar archivos de gran tamaño.

{{% alert color="primary" %}}
Considere los métodos de devolución `IEnumerable` al recorrer carpetas o mensajes en una publicación.
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
Prefer [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) para acceder a las propiedades básicas de los mensajes.
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
Evite usar el [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) or [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) métodos para todos los mensajes, a menos que necesite tener acceso a todas las propiedades.
{{% /alert %}}

{{% alert color="primary" %}}
Considera usar [EnumerateMessagesEntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessagesentryid/) para recuperar fácilmente todos los identificadores de mensajes contenidos en una carpeta.
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
Considera usar [ExtractProperty](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractproperty/) para leer una sola propiedad que falta en MessageInfo.
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
Considera usar [ExtractAttachments](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractattachments/) si solo se requieren los archivos adjuntos.
{{% /alert %}}

```csharp
foreach (var msgId in folder.EnumerateMessagesEntryId())
{
   var attachments = pst.ExtractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Use [criterios de búsqueda](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst)filtrado basado en el filtrado para obtener los mensajes que necesita.
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
Considera usar [SaveMessageToStream](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/savemessagetostream/) si es necesario guardar los mensajes de pst.
{{% /alert %}}

En lugar de usar:

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
Prefiero los métodos masivos a [add](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#adding-bulk-messages) or [delete](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) varios artículos.
{{% /alert %}}

