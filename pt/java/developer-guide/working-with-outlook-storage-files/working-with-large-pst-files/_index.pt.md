---
title: "Trabalhando com grandes arquivos PST"
url: /pt/java/trabalhando-com-grandes-arquivos-pst/
weight: 130
type: docs
---

O desempenho pode ser degradado ao processar grandes arquivos PST. As seguintes sugestões ajudarão a melhorar o desempenho do seu aplicativo ao processar grandes arquivos.

{{% alert color="primary" %}}
Considere métodos que retornam `Iterable` ao percorrer pastas ou mensagens em um pst.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    for (FolderInfo folder : pst.getRootFolder().enumerateFolders())
        for (MessageInfo messageInfo : folder.enumerateMessages()) {
            // Faça algo com a mensagem
        }
}
```

{{% alert color="primary" %}}
Prefira [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/) para acessar propriedades básicas da mensagem.
{{% /alert %}}

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    System.out.println("Assunto: " + messageInfo.getSubject());
    System.out.println("Para: " + messageInfo.getDisplayTo());
    System.out.println("Importância: " + messageInfo.getImportance());
    System.out.println("Classe da Mensagem: " + messageInfo.getMessageClass());
}
```
{{% alert color="primary" %}}
Evite usar os métodos [ExtractMessage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) ou [EnumerateMapiMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) para todas as mensagens, a menos que você precise ter acesso a todas as propriedades.
{{% /alert %}}

{{% alert color="primary" %}}
Considere usar [EnumerateMessagesEntryId](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessagesEntryId--) para recuperar facilmente todos os IDs de mensagem contidos em uma pasta.
{{% /alert %}}

```java
for (String id : folder.enumerateMessagesEntryId())
{
    // Use o id para recuperar uma propriedade (extractProperty),
    // extrair uma MapiMessage (extractMessage),
    // extrair anexos da mensagem (extractAttachments),
    // salvar msg em um stream (saveMessageToStream).
}
```
{{% alert color="primary" %}}
Considere usar [ExtractProperty](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractProperty-byte---long-) para ler uma única propriedade que está faltando em MessageInfo.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    String transportMessageHeaders =
            pst.extractProperty(org.apache.commons.codec.binary.Base64.decodeBase64(msgId),
                    KnownPropertyList.TRANSPORT_MESSAGE_HEADERS.getTag()).getString();
}
```
{{% alert color="primary" %}}
Considere usar [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) se apenas os anexos forem necessários.
{{% /alert %}}

```java
for (String msgId : folder.enumerateMessagesEntryId()) {
    MapiAttachmentCollection attachments = pst.extractAttachments(msgId);
}
```

{{% alert color="primary" %}}
Use filtragem baseada em [critérios de busca](https://docs.aspose.com/email/pt/java/working-with-messages-in-a-pst-file/#searching-messages-and-folders-in-pst) para obter as mensagens desejadas.
{{% /alert %}}

```java
try (PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {

    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // Mensagens não lidas
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);

    for (FolderInfo folder : pst.getRootFolder().enumerateFolders()) {
        MessageInfoCollection unread = folder.getContents(builder.getQuery());
    }
}
```

{{% alert color="primary" %}}
Considere usar [SaveMessageToStream](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) se for necessário salvar mensagens do pst.
{{% /alert %}}

Em vez de usar:

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
Prefira métodos em massa para [adicionar](https://docs.aspose.com/email/pt/java/working-with-messages-in-a-pst-file/#adding-bulk-messages) ou [deletar](https://docs.aspose.com/email/pt/java/working-with-messages-in-a-pst-file/#delete-items-in-bulk-from-pst-file) múltiplos itens.
{{% /alert %}}