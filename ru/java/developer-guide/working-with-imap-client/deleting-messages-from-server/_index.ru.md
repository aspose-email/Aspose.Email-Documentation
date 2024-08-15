---
title: "Удаление сообщений с сервера"
url: /ru/java/deleting-messages-from-server/
weight: 50
type: docs
---


## **Удаление сообщений**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс может удалять сообщения с сервера IMAP. [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class [deleteMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) функция используется для удаления сообщений. В качестве параметра она принимает порядковый номер сообщения или уникальный идентификатор. [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) provides [deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) and [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) методы удаления сообщений по одному или по нескольким. В следующем фрагменте кода показано, как удалить сообщение электронной почты с идентификатором сообщения 1 с сервера IMAP.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.setSecurityOptions(SecurityOptions.SSLImplicit);

    // Append test message
    client.selectFolder(ImapFolderInfo.IN_BOX);

    MailMessage eml = new MailMessage("from@from.com", "to@to.com");
    eml.setSubject("Message to delete");
    eml.setBody("Hey! This Message will be deleted!");
    String emlId = client.appendMessage(eml);

    // Delete appended message
    client.deleteMessage(emlId);
    client.commitDeletes();
}
~~~

## **Удаление нескольких сообщений**

Несколько писем можно удалить из почтового ящика с помощью [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) API Aspose.Email. [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) метод предоставляет ряд опций для удаления нескольких сообщений с сервера с использованием уникальных идентификаторов, порядковых номеров или [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) элементы. В следующем фрагменте кода показано, как удалить несколько сообщений.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder(ImapFolderInfo.IN_BOX);

    // Append test messages
    List<MailMessage> emlList = new ArrayList<>();
    for (int i = 0; i < 3; i++) {
        MailMessage eml = new MailMessage("from@from.com", "to@to.com");
        eml.setSubject("Message to delete " + i);
        eml.setBody("Hey! This Message will be deleted!");

        emlList.add(eml);
    }

    AppendMessagesResult appendMessagesResult = client.appendMessages(emlList);
    List<String> uidList = new ArrayList<>();
    for (String uid : appendMessagesResult.getSucceeded().getValues()) {
        uidList.add(uid);
    }

    // Bulk Delete appended Messages
    client.deleteMessagesByUids(uidList, true);
    client.commitDeletes();
}
~~~
