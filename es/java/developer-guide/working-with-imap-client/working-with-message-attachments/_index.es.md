---
title: "Trabajando con Archivos Adjunto usando IMAP"
url: /es/java/trabajando-con-archivos-adjunto-usando-imap/
weight: 30
type: docs
---


## **Listar Archivos Adjunto usando el Cliente IMAP**

Para obtener información sobre los archivos adjuntos como el nombre, tamaño sin recuperar los datos del archivo adjunto, utiliza las siguientes características de la API:

- [ImapAttachmentInfo](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfo/) - Representa la información de un archivo adjunto. 
- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfocollection/) - Representa una colección de ImapAttachmentInfo. 
- [listAttachments(int sequenceNumber)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listAttachments-int-) - Obtiene información de cada archivo adjunto en un mensaje.

El siguiente ejemplo de código muestra cómo usar el cliente IMAP para recuperar información sobre mensajes de correo electrónico y sus archivos adjuntos de un servidor y luego mostrar los detalles del archivo adjunto para cada mensaje. Permite acceder y procesar archivos adjuntos de mensajes de correo electrónico utilizando el protocolo IMAP.

```java
ImapMessageInfoCollection messageInfoCollection = imapClient.listMessages();

for (ImapMessageInfo message : messageInfoCollection) {
    ImapAttachmentInfoCollection attachmentInfoCollection =
            imapClient.listAttachments(message.getSequenceNumber());

    for (ImapAttachmentInfo attachmentInfo : attachmentInfoCollection) {
        System.out.println(
                "Archivo Adjunto: " + attachmentInfo.getName() + " (tamaño: " + attachmentInfo.getSize() + ")");
    }
}
```