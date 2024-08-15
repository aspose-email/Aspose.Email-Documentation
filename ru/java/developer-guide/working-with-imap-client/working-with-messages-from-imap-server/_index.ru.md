---
title: "Работа с сообщениями с сервера IMAP"
url: /ru/java/working-with-messages-from-imap-server/
weight: 20
type: docs
---


## **Отображение идентификаторов сообщений MIME с сервера**

[ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) предоставляет MIME [MessageId](https://reference.aspose.com/email/java/com.aspose.email/messageinfobase/#getMessageId--) для идентификации сообщения без извлечения всего сообщения. В следующем фрагменте кода показано, как указать MIME MessageID.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");

try {
    ImapMessageInfoCollection messageInfoCol = client.listMessages("Inbox");
    for (ImapMessageInfo info : messageInfoCol) {
        // Display MIME Message ID
        System.out.println("Message Id = " + info.getMessageId());
    }
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Список сообщений с сервера**

Aspose.Email предоставляет перегруженный вариант из 2 человек [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) для получения заданного количества сообщений на основе запроса. В следующем фрагменте кода показано, как составить список сообщений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");

// Select the inbox folder and Get the message info collection
ImapQueryBuilder builder = new ImapQueryBuilder();
MailQuery query = builder
        .or(builder.or(builder.or(builder.or(builder.getSubject().contains(" (1) "), builder.getSubject().contains(" (2) ")), builder.getSubject().contains(" (3) ")),
                builder.getSubject().contains(" (4) ")), builder.getSubject().contains(" (5) "));
ImapMessageInfoCollection messageInfoCol4 = client.listMessages(query, 4);
System.out.println((messageInfoCol4.size() == 4) ? "Success" : "Failure");
~~~

## **Рекурсивный список сообщений с сервера**

Протокол IMAP поддерживает рекурсивный список сообщений из папки почтового ящика. Это также помогает отображать сообщения из подпапок папки. В следующем фрагменте кода показано, как рекурсивно перечислять сообщения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");
client.selectFolder("InBox");
ImapMessageInfoCollection msgsColl = client.listMessages(true);
System.out.println("Total Messages: " + msgsColl.size());
~~~

## **Список сообщений с помощью MultiConnection**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) обеспечивает [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setUseMultiConnection-int-) свойство, которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете настроить количество подключений, которое будет использоваться в режиме нескольких подключений, используя [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setConnectionsQuantity-int-). В следующем фрагменте кода показано использование режима нескольких подключений для перечисления сообщений и сравнивается его производительность с режимом одиночного подключения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

imapClient.selectFolder("Inbox");
imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol1 = imapClient.listMessages(true);
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

imapClient.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol2 = imapClient.listMessages(true);
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Performance Relation: " + performanceRelation);
~~~
{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Получайте сообщения в порядке убывания**

Aspose.Email предоставляет [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) метод, который перечисляет сообщения с поддержкой пейджинга. Некоторые перегрузки [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) accept [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) в качестве параметра. [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) обеспечивает [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) свойство, для которого задано значение **false**, возвращает электронные письма в порядке убывания.

Следующий пример кода демонстрирует использование [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) собственность [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) класс для изменения порядка писем.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

PageSettings pageSettings = new PageSettings();
pageSettings.setAscendingSorting(false);
ImapPageInfo pageInfo = imapClient.listMessagesByPage(5, pageSettings);
ImapMessageInfoCollection messages = pageInfo.getItems();

for (ImapMessageInfo message : messages) {
    System.out.println(message.getSubject() + " -> " + message.getDate().toString());
}
~~~

## **Получение сообщений с сервера и сохранение на диск**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс может получать сообщения с сервера IMAP и сохранять сообщения в формате EML на локальный диск. Для сохранения сообщений на диск необходимо выполнить следующие шаги:

1. Создайте экземпляр [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Укажите имя хоста, порт, имя пользователя и пароль в iMapClient [constructor](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#ImapClient\(java.lang.String,%20int,%20java.lang.String,%20java.lang.String\)).
1. Выберите папку, используя [selectFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#selectFolder-com.aspose.email.IConnection-java.lang.String-) method.
1. Позвоните [listMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) метод получения [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) object.
1. Пройдите итерацию через [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) коллекция, позвоните в [saveMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#saveMessage-com.aspose.email.IConnection-int-java.io.OutputStream-) метод и укажите выходной путь и имя файла.

В следующем фрагменте кода показано, как получать сообщения электронной почты с сервера и сохранять их.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Select the inbox folder and Get the message info collection
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Download each message
for (int i = 0; i < list.size(); i++) {
    // Save the EML file locally
    client.saveMessage(list.get_Item(i).getUniqueId(), dataDir + list.get_Item(i).getUniqueId() + ".eml");
}
~~~

## **Сохранение сообщений в формате MSG**

[В приведенном выше примере](#fetch-messages-from-server-and-save-to-disc), электронные письма сохраняются в формате EML. Чтобы сохранить электронные письма в формате MSG, [ImapClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessage-com.aspose.email.IConnection-int-) метод должен быть вызван. Он возвращает сообщение в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс. [MailMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) Затем можно вызвать метод для сохранения сообщения в MSG. В следующем фрагменте кода показано, как сохранять сообщения в формате MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the file directory.
String dataDir = "data/";

// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");

// Select the inbox folder and Get the message info collection
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Download each message
for (int i = 0; i < list.size(); i++) {
    // Save the message in MSG format
    MailMessage message = client.fetchMessage(list.get_Item(i).getUniqueId());
    message.save(dataDir + list.get_Item(i).getUniqueId() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~

## **Групповая выборка сообщений**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) обеспечивает [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) метод, который принимает итерацию последовательных номеров или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Следующий фрагмент кода демонстрирует использование [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) метод получения сообщений по порядковым номерам и уникальному идентификатору.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
System.out.println("ListMessages Count: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (ImapMessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : imapClient.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : imapClient.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~

## **Отправка электронных письмов/Организация электронных писем в беседы**

Aspose.Email позволяет группировать все пересылки, ответы и ответы на все сообщения, связанные с одним и тем же разговором, в иерархическом порядке. По сути, протокол IMAP может поддерживать функцию THREAD, определенную в RFC-5256. Кроме того, существует еще одно расширение IMAP, предоставленное Gmail и описываемое как X-GM-EXT-1.

Доступны следующие функции потоковой обработки электронной почты:

- [getMessageThreads](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getMessageThreads-com.aspose.email.BaseSearchConditions-) метод - получает цепочки сообщений с помощью [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
- boolean [getGmExt1Supported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getGmExt1Supported--) - Получает информацию о том, поддерживается ли расширение Gmail X-GM-EXT-1.
- boolean [getThreadSupported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadSupported--) - Получает информацию о том, поддерживается ли расширение THREAD.
- String[] [getThreadAlgorithms](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadAlgorithms--) - Получает поддерживаемые алгоритмы THREAD.

В следующих примерах кода показано использование этих функций для получения цепочек электронной почты из Gmail:

```java
  ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password", SecurityOptions.SSLImplicit);

try {

    client.selectFolder(ImapFolderInfo.IN_BOX);

   // get a list of messages that we'll group by conversation

   ImapMessageInfoCollection messages = client.listMessages();

   // make sure the IMAP server supports X-GM-EXT-1 extension

   if (client.getGmExt1Supported()) {

       // gets unique conversationId for our example

       Set<String> conversationIds = new HashSet<String>();

       for (ImapMessageInfo messageInfo : messages) {

           if (messageInfo.getConversationId() != null)

                conversationIds.add(messageInfo.getConversationId());

       }

       for (String conversationId : conversationIds) {

           // create the necessary search conditions for a thread

           XGMThreadSearchConditions conditions = new XGMThreadSearchConditions();

            conditions.setConversationId(conversationId);

            conditions.setUseUId(true);

           // get results

           List<MessageThreadResult> conversation = client.getMessageThreads(conditions);

           // print the email conversation in hierarchically manner

           printConversaton("", conversation, messages);

            System.out.println("--------------------");

       }

   }

} finally {

    client.dispose();

}

/**

 * <p>

 * Prints the email conversation in hierarchically manner

 * </p>

 */

public static void printConversaton(String indent, Iterable<MessageThreadResult> conversation,

    Iterable<ImapMessageInfo> messages) {

   for (MessageThreadResult thread : conversation) {

       for (ImapMessageInfo messageInfo : messages) {

           if (thread.getUniqueId().equals(messageInfo.getUniqueId())) {

                System.out.println(indent + " (" + thread.getUniqueId() + ") " + messageInfo.getSubject());

               break;

           }

       }

       if (thread.getChildMessages().size() != 0) {

            printConversaton(indent += "-", thread.getChildMessages(), messages);

       }

   }

}
```
Код немного меняется, если сервер IMAP поддерживает функцию THREAD:

Проверьте, поддерживает ли сервер IMAP расширение THREAD:

```java
 if (client.getThreadSupported())
```
Создайте подходящие условия поиска для темы:
```java
 ThreadSearchConditions conditions = new ThreadSearchConditions();

conditions.setAlgorithm(client.getThreadAlgorithms()[0]);

conditions.setUseUId(true);
```

## **Список сообщений с поддержкой пейджинга**

В сценариях, когда почтовый сервер содержит большое количество сообщений в почтовом ящике, часто требуется перечислить или получить сообщения с поддержкой пейджинга. API Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) позволяет получать сообщения с сервера с поддержкой пейджинга.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// This example shows the paging support of ImapClient for listing messages from the server
// Available in Aspose.Email for Java and onwards
final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    try {
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        // Create some test messages and append these to server's inbox
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157 - " + UUID.randomUUID(),
                    "EMAILNET-35157 Move paging parameters to separate class");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        // List messages from inbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages();
        // Verify the number of messages added
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RETREIVE THE MESSAGES USING PAGING SUPPORT////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();
        PageSettings pageSettings = new PageSettings();
        ImapPageInfo pageInfo = client.listMessagesByPage(itemsPerPage, 0, pageSettings);
        System.out.println(pageInfo.getTotalCount());
        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(itemsPerPage, pageInfo.getNextPage().getPageOffset(), pageSettings);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;

        // foreach to while statements conversion
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Получение папок и рекурсивное чтение сообщений**

В этой статье большинство [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) функции используются для создания приложения, рекурсивно перечисляющего все папки и подпапки с сервера IMAP. Оно также сохраняет сообщения в каждой папке и подпапке в формате MSG на локальном диске. На диске папки и сообщения создаются и сохраняются в той же иерархической структуре, что и на сервере IMAP. В следующем фрагменте кода показано, как рекурсивно получать информацию о сообщениях и подпапках.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() throws Exception {
    // Создайте экземпляр ImapClient class
    ImapClient client = new ImapClient();

    // Specify host, username, password, Port and SecurityOptions for your client
    client.setHost("imap.gmail.com");
    client.setUsername("your.username@gmail.com");
    client.setPassword("your.password");
    client.setPort(993);
    client.setSecurityOptions(SecurityOptions.Auto);
    try {
        // The root folder (which will be created on disk) consists of host and username
        String rootFolder = client.getHost() + "-" + client.getUsername();

        // Create the root folder and List all the folders from IMAP server
        new File(rootFolder).mkdirs();
        ImapFolderInfoCollection folderInfoCollection = client.listFolders();
        for (ImapFolderInfo folderInfo : folderInfoCollection) {
            // Позвоните recursive method to read messages and get sub-folders
            listMessagesInFolder(folderInfo, rootFolder, client);
        }
        // Disconnect to the remote IMAP server
        client.dispose();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex);
    }

    System.out.println("Downloaded messages recursively from IMAP server.");
}

/// Recursive method to get messages from folders and sub-folders
private static void listMessagesInFolder(ImapFolderInfo folderInfo, String rootFolder, ImapClient client) {
    // Create the folder in disk (same name as on IMAP server)
    String currentFolder = "data/";
    new File(currentFolder).mkdirs();

    // Read the messages from the current folder, if it is selectable
    if (folderInfo.getSelectable()) {
        // Send status command to get folder info
        ImapFolderInfo folderInfoStatus = client.getFolderInfo(folderInfo.getName());
        System.out.println(folderInfoStatus.getName() + " folder selected. New messages: " + folderInfoStatus.getNewMessageCount() + ", Total messages: "
                + folderInfoStatus.getTotalMessageCount());

        // Select the current folder and List messages
        client.selectFolder(folderInfo.getName());
        ImapMessageInfoCollection msgInfoColl = client.listMessages();
        System.out.println("Listing messages....");
        for (ImapMessageInfo msgInfo : msgInfoColl) {
            // Get subject and other properties of the message
            System.out.println("Subject: " + msgInfo.getSubject());
            System.out.println("Read: " + msgInfo.isRead() + ", Recent: " + msgInfo.getRecent() + ", Answered: " + msgInfo.getAnswered());

            // Get rid of characters like ? and :, which should not be included in a file name and Save the message in MSG format
            String fileName = msgInfo.getSubject().replace(":", " ").replace("?", " ");
            MailMessage msg = client.fetchMessage(msgInfo.getSequenceNumber());
            msg.save(currentFolder + "\\" + fileName + "-" + msgInfo.getSequenceNumber() + ".msg", SaveOptions.getDefaultMsgUnicode());
        }
        System.out.println("============================\n");
    } else {
        System.out.println(folderInfo.getName() + " is not selectable.");
    }

    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ImapFolderInfoCollection folderInfoCollection = client.listFolders(folderInfo.getName());
        for (ImapFolderInfo subfolderInfo : folderInfoCollection) {
            listMessagesInFolder(subfolderInfo, rootFolder, client);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~

## **Получите UID или порядковый номер сообщения**

Публичный API Aspose.Email предоставляет следующие возможности для получения идентификационной информации сообщения, такой как UID или порядковый номер, которые могут потребоваться при обработке сообщений, полученных с сервера:

[MailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/) class — представляет идентификационную информацию о сообщении в почтовом ящике.
- [getSequenceNumber()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getSequenceNumber--) method - Возвращает порядковый номер сообщения.
- [getUniqueId()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getUniqueId--) метод - получает уникальный идентификатор сообщения.

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс — представляет собой сообщение электронной почты и позволяет получить доступ к свойствам сообщения, например теме, телу, адресам отправителя и получателя и т. д.
- [getItemId](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getItemId--) метод — представляет идентификационную информацию о сообщении в почтовом ящике.

В приведенном ниже примере кода показано, как получать и отображать сведения о сообщениях из папки «INBOX» на сервере IMAP с помощью [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class:

```java
try (ImapClient client = new ImapClient(imapHost, port, emailAddress, password, securityOption)) {
    ImapMessageInfoCollection msgs = client.listMessages("INBOX");
    List<Integer> seqIds = new ArrayList<>();
    for (ImapMessageInfo msg : msgs) {
        seqIds.add(msg.getSequenceNumber());
    }
    Iterable<MailMessage> msgsViaFetch = client.fetchMessagesBySequences(seqIds);
    for (MailMessage thisMsg : msgsViaFetch) {
        System.out.println("Message ID: " + thisMsg.getItemId().getUniqueId()
                + " SequenceNumber: " + thisMsg.getItemId().getSequenceNumber()
                + " Subject: " + thisMsg.getSubject());
    }
}
```
## **Получение дополнительных параметров в виде сводной информации**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("host.domain.com", "username", "password");
try {
    MailMessage message = new MailMessage("from@domain.com", "to@doman.com", "EMAILNET-38466 - " + UUID.randomUUID().toString(),
            "EMAILNET-38466 Add extra parameters for UID FETCH command");

    // append the message to the server
    String uid = client.appendMessage(message);

    // wait for the message to be appended
    Thread.sleep(5000);

    // Define properties to be fetched from server along with the message
    List<String> messageExtraFields = Arrays.asList("X-GM-MSGID", "X-GM-THRID");

    // retreive the message summary information using it's UID
    ImapMessageInfo messageInfoUID = client.listMessage(uid, messageExtraFields);

    // retreive the message summary information using it's sequence number
    ImapMessageInfo messageInfoSeqNum = client.listMessage(1, messageExtraFields);

    // List messages in general from the server based on the defined properties
    ImapMessageInfoCollection messageInfoCol = client.listMessages(messageExtraFields);

    ImapMessageInfo messageInfoFromList = messageInfoCol.get_Item(0);

    // verify that the parameters are fetched in the summary information
    for (String paramName : messageExtraFields) {
        System.out.println(messageInfoFromList.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoUID.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoSeqNum.getExtraParameters().containsKey(paramName));
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Получение информации в заголовке списка «Отказаться от подписки»**

Заголовок List-Unsubscribe содержит URL-адрес для отказа от подписки на списки рассылки, например на рекламные объявления, информационные бюллетени и т. д. Чтобы получить заголовок List-Unsubscribe, используйте [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) собственность [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) класс. В следующем примере показано использование [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) свойство для получения заголовка List-Unsubscribe.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
for (ImapMessageInfo imapMessageInfo : messageInfoCol) {
    System.out.println("ListUnsubscribe Header: " + imapMessageInfo.getListUnsubscribe());
}
~~~
