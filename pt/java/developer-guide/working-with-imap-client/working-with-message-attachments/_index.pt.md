---
title: "Trabalhando com Anexos de Mensagem usando IMAP"
url: /pt/java/trabalhando-com-anexos-de-mensagem-usando-imap/
weight: 30
type: docs
---


## **Listar Anexos de Mensagem usando o Cliente IMAP**

Para obter informações sobre anexos, como nome e tamanho, sem buscar os dados do anexo, use os seguintes recursos da API:

- [ImapAttachmentInfo](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfo/) - Representa informações de um anexo. 
- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfocollection/) - Representa uma coleção de ImapAttachmentInfo. 
- [listAttachments(int sequenceNumber)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listAttachments-int-) - Obtém informações para cada anexo em uma mensagem.

O seguinte exemplo de código mostra como usar o cliente IMAP para recuperar informações sobre mensagens de email e seus anexos de um servidor e, em seguida, exibir os detalhes do anexo para cada mensagem. Isso permite acessar e processar anexos de mensagens de email usando o protocolo IMAP.

```java
ImapMessageInfoCollection messageInfoCollection = imapClient.listMessages();

for (ImapMessageInfo message : messageInfoCollection) {
    ImapAttachmentInfoCollection attachmentInfoCollection =
            imapClient.listAttachments(message.getSequenceNumber());

    for (ImapAttachmentInfo attachmentInfo : attachmentInfoCollection) {
        System.out.println(
                "Anexo: " + attachmentInfo.getName() + " (tamanho: " + attachmentInfo.getSize() + ")");
    }
}
```