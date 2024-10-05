---
title: Удаление сообщений с сервера
type: docs
weight: 50
url: /java/deleting-messages-from-server/
---


## **Удаление сообщений**

Класс [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) может удалять сообщения с IMAP-сервера. Функция [deleteMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) используется для удаления сообщений. Она принимает номер последовательности сообщения или уникальный идентификатор в качестве параметра. [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет методы [deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) и [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) для удаления сообщений по одному или несколько сразу. Следующий фрагмент кода показывает, как удалить электронное сообщение с идентификатором сообщения 1 с IMAP-сервера.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.setSecurityOptions(SecurityOptions.SSLImplicit);

    // Добавить тестовое сообщение
    client.selectFolder(ImapFolderInfo.IN_BOX);

    MailMessage eml = new MailMessage("from@from.com", "to@to.com");
    eml.setSubject("Сообщение для удаления");
    eml.setBody("Привет! Это сообщение будет удалено!");
    String emlId = client.appendMessage(eml);

    // Удалить добавленное сообщение
    client.deleteMessage(emlId);
    client.commitDeletes();
}
~~~

## **Удаление нескольких сообщений**

Несколько электронных писем можно удалить из почтового ящика, используя [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) API Aspose.Email. Метод [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) предоставляет ряд опций для удаления нескольких сообщений с сервера, используя уникальные идентификаторы, номера последовательности или элементы [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/). Следующий фрагмент кода показывает, как удалить несколько сообщений.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder(ImapFolderInfo.IN_BOX);

    // Добавить тестовые сообщения
    List<MailMessage> emlList = new ArrayList<>();
    for (int i = 0; i < 3; i++) {
        MailMessage eml = new MailMessage("from@from.com", "to@to.com");
        eml.setSubject("Сообщение для удаления " + i);
        eml.setBody("Привет! Это сообщение будет удалено!");

        emlList.add(eml);
    }

    AppendMessagesResult appendMessagesResult = client.appendMessages(emlList);
    List<String> uidList = new ArrayList<>();
    for (String uid : appendMessagesResult.getSucceeded().getValues()) {
        uidList.add(uid);
    }

    // Массовое удаление добавленных сообщений
    client.deleteMessagesByUids(uidList, true);
    client.commitDeletes();
}
~~~