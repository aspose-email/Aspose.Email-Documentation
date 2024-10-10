---
title: "Работа с вложениями сообщений с использованием IMAP"
url: /ru/java/работа-с-вложениями-сообщений-с-использованием-imap/
weight: 30
type: docs
---


## **Список вложений сообщений с использованием IMAP-клиента**

Чтобы получить информацию о вложениях, таких как имя, размер, не извлекая данные вложений, используйте следующие функции API:

- [ImapAttachmentInfo](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfo/) - Представляет информацию о вложении. 
- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapattachmentinfocollection/) - Представляет коллекцию ImapAttachmentInfo. 
- [listAttachments(int sequenceNumber)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listAttachments-int-) - Получает информацию для каждого вложения в сообщении.

Следующий пример кода демонстрирует, как использовать IMAP-клиент для получения информации о электронных письмах и их вложениях с сервера, а затем отображает детали вложений для каждого сообщения. Это позволяет вам получать доступ к вложениям из электронных сообщений и обрабатывать их с использованием протокола IMAP.

```java
ImapMessageInfoCollection messageInfoCollection = imapClient.listMessages();

for (ImapMessageInfo message : messageInfoCollection) {
    ImapAttachmentInfoCollection attachmentInfoCollection =
            imapClient.listAttachments(message.getSequenceNumber());

    for (ImapAttachmentInfo attachmentInfo : attachmentInfoCollection) {
        System.out.println(
                "Вложение: " + attachmentInfo.getName() + " (размер: " + attachmentInfo.getSize() + ")");
    }
}
```