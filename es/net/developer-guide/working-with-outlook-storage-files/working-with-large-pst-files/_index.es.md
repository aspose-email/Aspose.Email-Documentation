---
title: "Trabajar con archivos PST grandes"
url: /es/net/working-with-large-pst-files/
weight: 130
type: docs
---

El rendimiento puede verse degradado al procesar archivos PST grandes. Las siguientes sugerencias te ayudarán a mejorar el rendimiento de tu aplicación al procesar archivos grandes.

{{% alert color="primary" %}}
Considera métodos que devuelvan `IEnumerable` al recorrer carpetas o mensajes en un pst.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

foreach (var folder in pst.RootFolder.EnumerateFolders())
foreach (var messageInfo in folder.EnumerateMessages())
{
    // Haz algo con el mensaje
}
```

{{% alert color="primary" %}}
Prefiere [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) para acceder a las propiedades básicas del mensaje.
{{% /alert %}}

```csharp
foreach (var messageInfo in folder.EnumerateMessages())
{
    Console.WriteLine($"Asunto: {messageInfo.Subject}");
    Console.WriteLine($"Para: {messageInfo.DisplayTo}");
    Console.WriteLine($"Importancia: {messageInfo.Importance}");
    Console.WriteLine($"Clase de Mensaje: {messageInfo.MessageClass}");
}
```

{{% alert color="primary" %}}
Evita usar los métodos [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) o [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) para todos los mensajes a menos que necesites acceder a todas las propiedades.
{{% /alert %}}

{{% alert color="primary" %}}
Considera usar [EnumerateMessagesEntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessagesentryid/) para recuperar fácilmente todos los IDs de los mensajes contenidos en una carpeta.
{{% /alert %}}

 ```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
   // Usa id para recuperar una propiedad (ExtractProperty),
	 // extraer un MapiMessage (ExtractMessage),
	 // extraer los adjuntos del mensaje (ExtractAttachments),
	 // guardar mensaje en un stream(SaveMessageToStream).
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
Considera usar [ExtractAttachments](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractattachments/) si solo se requieren los adjuntos.
{{% /alert %}}

```csharp
foreach (var msgId in folder.EnumerateMessagesEntryId())
{
   var attachments = pst.ExtractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Usa el filtrado basado en [criterios de búsqueda](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst) para obtener los mensajes que requieres.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

var builder = new PersonalStorageQueryBuilder();
// Mensajes no leídos
builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);

foreach (var folder in pst.RootFolder.EnumerateFolders())
{
    var unread = folder.GetContents(builder.GetQuery());
}
```

{{% alert color="primary" %}}
Considera usar [SaveMessageToStream](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/savemessagetostream/) si es necesario guardar mensajes del pst.
{{% /alert %}}

En lugar de usar:

```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
    var msg = pst.ExtractMessage(id);
    msg.Save(@"message.msg");
}
```

Usa:

```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
    pst.SaveMessageToStream(id, File.OpenWrite(@"message.msg"));
}
```

{{% alert color="primary" %}}
Prefiere métodos en masa para [agregar](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#adding-bulk-messages) o [eliminar](https://docs.aspose.com/email/es/net/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) múltiples elementos.
{{% /alert %}}