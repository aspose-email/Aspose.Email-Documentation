---
title: "Работа с папками на сервере IMAP"
url: /ru/java/working-with-folders-on-imap-server/
weight: 60
type: docs
---


## **Получение информации о папках**

С Aspose.Email очень просто получать информацию о папках с сервера IMAP. Позвоните в [listFolders()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listFolders--) метод [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс. Он возвращает объект [ImapFolderInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapfolderinfocollection/) тип. Изучите эту коллекцию и получайте информацию об отдельных папках в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подпапок. В следующем фрагменте кода показано, как получить информацию о папке с сервера IMAP с помощью описанного метода Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get all folders in the currently subscribed folder
ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Iterate through the collection to get folder info one by one
for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoColl) {
    // Folder name and get New messages in the folder
    System.out.println("Folder name is " + folderInfo.getName());
    ImapFolderInfo folderExtInfo = client.getFolderInfo(folderInfo.getName());
    System.out.println("New message count: " + folderExtInfo.getNewMessageCount());
    System.out.println("Is it readonly? " + folderExtInfo.getReadOnly());
    System.out.println("Total number of messages " + folderExtInfo.getTotalMessageCount());
}
~~~

## **Удаление и переименование папок**

Папку на сервере IMAP можно удалить или переименовать в одну строку с помощью Aspose.Email:

- The [deleteFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteFolder-java.lang.String-) метод принимает имя папки в качестве параметра.
- Для [renameFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#renameFolder-java.lang.String-java.lang.String-) метод, вам нужно передать текущее имя папки и новое имя папки.

В следующем фрагменте кода показано, как удалить папку с сервера IMAP и переименовать папку. Каждая операция выполняется с помощью одной строки кода.

```java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Delete a folder and Rename a folder
client.deleteFolder("foldername");
client.renameFolder("foldername", "newfoldername");
```

## **Добавление нового сообщения в папку**

Вы можете добавить новое сообщение в папку, используя [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) and [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) классы. Сначала создайте [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) возражать, предоставляя субъекту ценности и исходя из них. Затем подпишитесь на папку и добавьте в нее сообщение. В следующем фрагменте кода показано, как добавить новое сообщение в папку.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create a message
MailMessage msg = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Subscribe to the Inbox folder and Append the newly created message
client.selectFolder(ImapFolderInfo.IN_BOX);
client.subscribeFolder(client.getCurrentFolder().getName());
client.appendMessage(client.getCurrentFolder().getName(), msg);
~~~

## **Добавьте несколько сообщений с поддержкой нескольких подключений**

Вы можете добавить несколько сообщений, используя [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) метод, предоставленный [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс. [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) метод принимает список [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и добавляет его в текущую папку, если папка не указана в качестве параметра. IMapClient также поддерживает режим MultiConnection для высоконагруженных операций. В следующем фрагменте кода показано, как добавить несколько сообщений в режиме MultiConnection.

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
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Test Message - " + UUID.randomUUID().toString(), "IMAP Group Append with MultiConnection");
    messages.add(message);
}

imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
imapClient.appendMessages(messages);
~~~

{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Переместить сообщения в другую папку почтового ящика**

Aspose.Email для Java позволяет перемещать сообщение из одной папки почтового ящика в другую с помощью [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) API. [moveMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#moveMessage-int-java.lang.String-) метод использует уникальный идентификатор сообщения и имя целевой папки для перемещения сообщения в папку назначения. В следующем фрагменте кода показано, как перемещать сообщения в другую папку почтового ящика.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// This example shows how to move a message from one folder of a mailbox to another one using the ImapClient API of Aspose.Email for Java
// Available from Aspose.Email for Java onwards
// -------------- Available API Overload Members --------------
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
                "EMAILNET-35151 ImapClient: Provide option to Move Message");
        client.selectFolder(ImapFolderInfo.IN_BOX);
        // Append the new message to Inbox folder
        String uniqueId = client.appendMessage(ImapFolderInfo.IN_BOX, message);
        ImapMessageInfoCollection messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Now move the message to the folder EMAILNET-35151
        client.moveMessage(uniqueId, folderName);
        client.commitDeletes();
        // Verify that the message was moved to the new folder
        client.selectFolder(folderName);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Verify that the message was moved from the Inbox
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

Aspose.Email API предоставляет возможность копировать сообщение из одной папки почтового ящика в другую. Это позволяет копировать как одно, так и несколько сообщений с помощью [copyMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessage-com.aspose.email.IConnection-int-java.lang.String-) and [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) методы. [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) Метод предоставляет возможность копировать несколько сообщений из исходной папки почтового ящика в папку почтового ящика назначения. В следующем фрагменте кода показано, как копировать сообщения в другую папку почтового ящика.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("exchange.aspose.com", "username", "password");
try {
    // Create the destination folder
    String folderName = "EMAILNET-35242";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        // Append a couple of messages to the server
        MailMessage message1 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Improvement of copy method.Add ability to 'copy' multiple messages per invocation.");
        String uniqueId1 = client.appendMessage(message1);

        MailMessage message2 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Improvement of copy method.Add ability to 'copy' multiple messages per invocation.");
        String uniqueId2 = client.appendMessage(message2);

        // Verify that the messages have been added to the mailbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());

        // Copy multiple messages using the CopyMessages command and Verify that messages are copied to the destination folder
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

## **Работа с папками почтовых ящиков специального назначения**

В некоторых хранилищах сообщений IMAP есть специальные почтовые ящики, например, для хранения черновиков или отправленных сообщений. Многие почтовые клиенты позволяют пользователям указывать, куда следует помещать черновики или отправленные сообщения, но для их настройки пользователь должен знать, какие почтовые ящики сервер выделил для этих целей. Aspose.Email может идентифицировать эти специальные почтовые ящики с помощью [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) класс, чтобы с ними было удобнее работать. В следующем примере кода показано, как получить доступ к этим специальным почтовым ящикам с помощью [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) class.

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
