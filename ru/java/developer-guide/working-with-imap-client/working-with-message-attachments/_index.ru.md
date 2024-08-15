---
title: "Работа с вложениями сообщений с помощью IMAP"
url: /ru/java/working-with-message-attachments-using-imap/
weight: 30
type: docs
---


## **Список вложений сообщений с помощью клиента IMAP**

Чтобы получить информацию о вложениях, таких как имя, размер, без извлечения данных вложения, используйте следующие функции API:

- [ImapAttachmentInfo](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfo/) - Представляет собой информацию о вложении.
- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfocollection/) - Представляет собой коллекцию IMapAttachmentInfo.
- [Список вложений (целочисленный порядковый номер)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listAttachments-int-) - Получает информацию о каждом вложении в сообщении.

В следующем примере кода показано, как использовать клиент IMAP для получения информации о сообщениях электронной почты и их вложениях с сервера и последующего отображения сведений о вложениях для каждого сообщения. Он позволяет получать доступ к вложениям из сообщений электронной почты и обрабатывать их с помощью протокола IMAP.

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


