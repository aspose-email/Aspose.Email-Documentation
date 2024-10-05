---
title: Работа с папками на IMAP-сервере
type: docs
weight: 60
url: /java/working-with-folders-on-imap-server/
---


## **Получение информации о папках**

Получить информацию о папках с IMAP-сервера очень просто с Aspose.Email. Вызовите метод [listFolders()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listFolders--) класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Он возвращает объект типа [ImapFolderInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapfolderinfocollection/). Итерация по этой коллекции позволяет получить информацию о каждом отдельном папке в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подкаталогов. Следующий фрагмент кода показывает, как получить информацию о папках с IMAP-сервера, используя описанный метод Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Получить все папки в текущей подписанной папке
ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Итерация по коллекции для получения информации о папках
for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoColl) {
    // Имя папки и получить новые сообщения в папке
    System.out.println("Имя папки: " + folderInfo.getName());
    ImapFolderInfo folderExtInfo = client.getFolderInfo(folderInfo.getName());
    System.out.println("Количество новых сообщений: " + folderExtInfo.getNewMessageCount());
    System.out.println("Только для чтения? " + folderExtInfo.getReadOnly());
    System.out.println("Общее количество сообщений: " + folderExtInfo.getTotalMessageCount());
}
~~~

## **Удаление и переименование папок**

Папку на IMAP-сервере можно удалить или переименовать в одной строке с Aspose.Email:

- Метод [deleteFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteFolder-java.lang.String-) принимает имя папки в качестве параметра.
- Для метода [renameFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#renameFolder-java.lang.String-java.lang.String-) необходимо передать текущее имя папки и новое имя папки.

Следующий фрагмент кода показывает, как удалить папку с IMAP-сервера и как переименовать папку. Каждая операция выполняется одной строкой кода.

```java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Удалить папку и переименовать папку
client.deleteFolder("foldername");
client.renameFolder("foldername", "newfoldername");
```

## **Добавление нового сообщения в папку**

Вы можете добавить новое сообщение в папку, используя классы [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Сначала создайте объект [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) , указав тему, а также адреса отправителя и получателя. Затем подпишитесь на папку и добавьте в нее сообщение. Следующий фрагмент кода показывает, как добавить новое сообщение в папку.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Создать сообщение
MailMessage msg = new MailMessage("user@domain1.com", "user@domain2.com", "тема", "сообщение");

// Подпишитесь на папку "Входящие" и добавьте только что созданное сообщение
client.selectFolder(ImapFolderInfo.IN_BOX);
client.subscribeFolder(client.getCurrentFolder().getName());
client.appendMessage(client.getCurrentFolder().getName(), msg);
~~~

## **Добавление нескольких сообщений с поддержкой многосоединений**

Вы можете добавить несколько сообщений, используя метод [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) предоставленный классом [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Метод [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) принимает список [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и добавляет его в текущую папку, если папка не предоставлена в качестве параметра. ImapClient также поддерживает режим MultiConnection для операций с высокой нагрузкой. Следующий фрагмент кода показывает, как добавить несколько сообщений, используя режим MultiConnection.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Тестовое сообщение - " + UUID.randomUUID().toString(), "IMAP Групповое добавление с MultiConnection");
    messages.add(message);
}

imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
imapClient.appendMessages(messages);
~~~

{{% alert color="primary" %}} 

Обратите внимание, что использование режима многосоединений не гарантирует улучшения производительности.

{{% /alert %}} 

## **Перемещение сообщений в другую папку почтового ящика**

Aspose.Email для Java позволяет перемещать сообщение из одной папки почтового ящика в другую с помощью API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Метод [moveMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#moveMessage-int-java.lang.String-) использует уникальный идентификатор сообщения и имя целевой папки для перемещения сообщения в целевую папку. Следующий фрагмент кода показывает, как перемещать сообщения в другую папку почтового ящика.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Этот пример показывает, как переместить сообщение из одной папки почтового ящика в другую, используя API ImapClient от Aspose.Email для Java
// Доступно начиная с Aspose.Email для Java
// -------------- Доступные члены перегрузки API --------------
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName)
// void ImapClient.moveMessage(int sequenceNumber, String folderName)
// void ImapClient.moveMessage(String uniqueId, String folderName)

final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    String folderName = "EMAILNET-35151";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35151 - " + UUID.randomUUID(),
                "EMAILNET-35151 ImapClient: Предоставить возможность перемещения сообщений");
        client.selectFolder(ImapFolderInfo.IN_BOX);
        // Добавить новое сообщение в папку "Входящие"
        String uniqueId = client.appendMessage(ImapFolderInfo.IN_BOX, message);
        ImapMessageInfoCollection messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Теперь переместите сообщение в папку EMAILNET-35151
        client.moveMessage(uniqueId, folderName);
        client.commitDeletes();
        // Проверьте, что сообщение было перемещено в новую папку
        client.selectFolder(folderName);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Проверьте, что сообщение было перемещено из "Входящих"
        client.selectFolder(ImapFolderInfo.IN_BOX);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Копирование сообщений в другую папку почтового ящика**

API Aspose.Email предоставляет возможность копировать сообщение из одной папки почтового ящика в другую. Он позволяет копировать как одно сообщение, так и несколько сообщений, используя методы [copyMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessage-com.aspose.email.IConnection-int-java.lang.String-) и [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-). Метод [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) предоставляет возможность копировать несколько сообщений из исходной папки почтового ящика в целевую папку почтового ящика. Следующий фрагмент кода показывает, как копировать сообщения в другую папку почтового ящика.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("exchange.aspose.com", "username", "password");
try {
    // Создать целевую папку
    String folderName = "EMAILNET-35242";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        // Добавить пару сообщений на сервер
        MailMessage message1 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Улучшение метода копирования. Добавить возможность 'копирования' нескольких сообщений за один вызов.");
        String uniqueId1 = client.appendMessage(message1);

        MailMessage message2 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Улучшение метода копирования. Добавить возможность 'копирования' нескольких сообщений за один вызов.");
        String uniqueId2 = client.appendMessage(message2);

        // Проверьте, что сообщения были добавлены в почтовый ящик
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());

        // Скопируйте несколько сообщений, используя команду CopyMessages, и проверьте, что сообщения скопированы в целевую папку
        client.copyMessagesByUids(Arrays.asList(uniqueId1, uniqueId2), folderName);

        client.selectFolder(folderName);
        msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Работа со специальными почтовыми ящиками**

Некоторые хранилища IMAP сообщений включают специальные почтовые ящики, такие как те, которые используются для хранения черновиков или отправленных сообщений. Многие почтовые клиенты позволяют пользователям указывать, куда должны быть помещены черновики или отправленные сообщения, но их настройка требует от пользователя знания о том, какие почтовые ящики сервер отводит для этих целей. Aspose.Email может идентифицировать эти специальные почтовые ящики, используя класс [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) , чтобы упростить работу с ними. Следующий пример кода демонстрирует, как получить доступ к этим специальным почтовым ящикам с помощью класса [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/).

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();
System.out.println(mailboxInfo.getInbox());
System.out.println(mailboxInfo.getDraftMessages());
System.out.println(mailboxInfo.getJunkMessages());
System.out.println(mailboxInfo.getSentMessages());
System.out.println(mailboxInfo.getTrash());
~~~