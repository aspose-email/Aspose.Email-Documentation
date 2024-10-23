---
title: "Trabalhando com grandes arquivos PST"
url: /pt/net/trabalhando-com-grandes-arquivos-pst/
weight: 130
type: docs
---

O desempenho pode ser degradado ao processar grandes arquivos PST. As seguintes sugestões ajudarão você a melhorar o desempenho do seu aplicativo ao processar arquivos grandes.

{{% alert color="primary" %}}
Considere métodos que retornam `IEnumerable` ao percorrer pastas ou mensagens em um pst.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

foreach (var folder in pst.RootFolder.EnumerateFolders())
foreach (var messageInfo in folder.EnumerateMessages())
{
    // Faça algo com a mensagem
}
```

{{% alert color="primary" %}}
Prefira [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/) para acessar propriedades básicas da mensagem.
{{% /alert %}}

```csharp
foreach (var messageInfo in folder.EnumerateMessages())
{
    Console.WriteLine($"Assunto: {messageInfo.Subject}");
    Console.WriteLine($"Para: {messageInfo.DisplayTo}");
    Console.WriteLine($"Importância: {messageInfo.Importance}");
    Console.WriteLine($"Classe da Mensagem: {messageInfo.MessageClass}");
}
```

{{% alert color="primary" %}}
Evite usar os métodos [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) ou [EnumerateMapiMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemapimessages/) para todas as mensagens, a menos que você precise ter acesso a todas as propriedades.
{{% /alert %}}

{{% alert color="primary" %}}
Considere usar [EnumerateMessagesEntryId](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessagesentryid/) para recuperar facilmente todos os IDs das mensagens contidas em uma pasta.
{{% /alert %}}

 ```csharp
foreach (var id in folder.EnumerateMessagesEntryId())
{
   // Use id para recuperar uma propriedade (ExtractProperty),
	 // extrair uma MapiMessage (ExtractMessage),
	 // extrair anexos da mensagem (ExtractAttachments),
	 // salvar msg em um stream(SaveMessageToStream).
}
 ```

{{% alert color="primary" %}}
Considere usar [ExtractProperty](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractproperty/) para ler uma única propriedade que está faltando no MessageInfo.
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
Considere usar [ExtractAttachments](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractattachments/) se apenas os anexos forem necessários.
{{% /alert %}}

```csharp
foreach (var msgId in folder.EnumerateMessagesEntryId())
{
   var attachments = pst.ExtractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Use filtragem baseada em [critérios de busca](https://docs.aspose.com/email/pt/net/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst) para obter as mensagens que você precisa.
{{% /alert %}}

```csharp
using var pst = PersonalStorage.FromFile(@"storage.pst");

var builder = new PersonalStorageQueryBuilder();
// Mensagens não lidas
builder.HasNoFlags(MapiMessageFlags.MSGFLAG_READ);

foreach (var folder in pst.RootFolder.EnumerateFolders())
{
    var unread = folder.GetContents(builder.GetQuery());
}
```

{{% alert color="primary" %}}
Considere usar [SaveMessageToStream](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/savemessagetostream/) se for necessário salvar mensagens de um pst.
{{% /alert %}}

Em vez de usar:

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
Prefira métodos em massa para [adicionar](https://docs.aspose.com/email/pt/net/working-with-messages-in-a-pst-file/#adding-bulk-messages) ou [excluir](https://docs.aspose.com/email/pt/net/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) múltiplos itens.
{{% /alert %}}