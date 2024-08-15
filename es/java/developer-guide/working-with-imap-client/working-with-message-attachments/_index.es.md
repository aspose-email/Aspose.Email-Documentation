---
title: "Trabajar con archivos adjuntos de mensajes mediante IMAP"
url: /es/java/working-with-message-attachments-using-imap/
weight: 30
type: docs
---


## **Listar los archivos adjuntos de los mensajes mediante el cliente IMAP**

Para obtener información sobre los archivos adjuntos, como el nombre y el tamaño, sin obtener los datos del archivo adjunto, utilice las siguientes funciones de la API:

- [ImapAttachmentInfo](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfo/) - Representa la información de un adjunto.
- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfocollection/) - Representa una colección de IMAPAttachmentInfo.
- [ListAttachments (int SequenceNumber)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listAttachments-int-) - Obtiene la información de cada adjunto de un mensaje.

El siguiente ejemplo de código muestra cómo usar el cliente IMAP para recuperar información sobre los mensajes de correo electrónico y sus archivos adjuntos de un servidor y, a continuación, mostrar los detalles de los archivos adjuntos de cada mensaje. Permite acceder a los archivos adjuntos de los mensajes de correo electrónico y procesarlos mediante el protocolo IMAP.

```java
ImapMessageInfoCollection messageInfoCollection = imapClient.listMessages();

for (ImapMessageInfo message : messageInfoCollection) {
    ImapAttachmentInfoCollection attachmentInfoCollection =
            imapClient.listAttachments(message.getSequenceNumber());

    for (ImapAttachmentInfo attachmentInfo : attachmentInfoCollection) {
        System.out.println(
                "Attachment: " + attachmentInfo.getName() + " (size: " + attachmentInfo.getSize() + ")");
    }
}
```


