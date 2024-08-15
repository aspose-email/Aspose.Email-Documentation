---
title: Working with Messages from IMAP Server
type: docs
weight: 20
url: /java/working-with-messages-from-imap-server/
---


## **Listing MIME Message IDs from Server**

[ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) provides the MIME [MessageId](https://reference.aspose.com/email/java/com.aspose.email/messageinfobase/#getMessageId--) for message identification without extracting the complete message. The following code snippet shows you how to list MIME messageId.

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

## **Listing Messages from Server**

Aspose.Email provides a 2-member overloaded variant of [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) to retrieve a specified number of messages based on a query. The following code snippet shows you how to list messages.

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

## **Listing Messages from Server Recursively**

The IMAP protocol supports listing messages recursively from a mailbox folder. This helps list messages from subfolders of a folder as well. The following code snippet shows you how to list messages recursively.

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

## **Listing Messages with MultiConnection**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) provides a [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setUseMultiConnection-int-) property which can be used to create multiple connections for heavy operations. You may also set the number of connections to be used during multiconnection mode by using [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setConnectionsQuantity-int-). The following code snippet demonstrates the use of the multiconnection mode for listing messages and compares its performance with single connection mode.

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

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}} 

## **Get Messages in descending order**

Aspose.Email provides [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) method which lists messages with paging support. Some overloads of [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) accept [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) as a parameter. [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) provides an [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) property which when set to **false**, returns emails in descending order.

The following example code demonstrates the use of [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) property of the [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) class to change the order of emails.

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

## **Fetch Messages from Server and Save to disc**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class can fetch messages from an IMAP server and save the messages in EML format to a local disk. The following steps are required to save the messages to disk:

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Specify a hostname, port, username, and password in the ImapClient [constructor](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#ImapClient\(java.lang.String,%20int,%20java.lang.String,%20java.lang.String\)).
1. Select the folder using [selectFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#selectFolder-com.aspose.email.IConnection-java.lang.String-) method.
1. Call the [listMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) method to get the [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) object.
1. Iterate through the [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) collection, call the [saveMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#saveMessage-com.aspose.email.IConnection-int-java.io.OutputStream-) method and provide the output path and file name.

The following code snippet shows you how to fetch email messages from a server and save them.

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

## **Saving Messages in MSG Format**

[In the above example](#fetch-messages-from-server-and-save-to-disc), the emails are saved in EML format. To save emails in MSG format, the [ImapClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessage-com.aspose.email.IConnection-int-) method needs to be called. It returns the message in an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class. The [MailMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) method can then be called to save the message to MSG. The following code snippet shows you how to save messages in MSG Format.

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

## **Group Fetch Messages**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) provides a [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) method which accepts iterable of Sequence Numbers or Unique ID and returns a list of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). The following code snippet demonstrates the use of the [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) method to fetch messages by Sequence Numbers and Unique ID.

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

## **Email Threading/Organize Emails into Conversations** 

Aspose.Email makes it possible to group all forwards, replies, and reply-all messages related to the same conversation together in hierarchical manner. Basically, the IMAP protocol may support the THREAD capability defined in RFC-5256. Besides, there is another IMAP extension provided by Gmail and described as X-GM-EXT-1. 

The following email threading features are available for use:

- [getMessageThreads](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getMessageThreads-com.aspose.email.BaseSearchConditions-) method - Receives message threads by [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
- boolean [getGmExt1Supported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getGmExt1Supported--) - Gets information whether Gmail X-GM-EXT-1 extension is supported.
- boolean [getThreadSupported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadSupported--) - Gets information whether THREAD extension is supported.
- String[] [getThreadAlgorithms](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadAlgorithms--) - Gets supported THREAD algorithms.

The following code samples show the usage of these features to get the email threads from Gmail:

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
The code slightly changes if the IMAP server supports THREAD capability:

Check if the IMAP server supports THREAD extension:

```java
 if (client.getThreadSupported())
```
Create the suitable search conditions for a thread:
```java
 ThreadSearchConditions conditions = new ThreadSearchConditions();

conditions.setAlgorithm(client.getThreadAlgorithms()[0]);

conditions.setUseUId(true);
```

## **Listing Messages with Paging Support**

In scenarios, where the email server contains a large number of messages in the mailbox, it is often desired to list or retrieve the messages with paging support. Aspose.Email API [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) lets you retrieve the messages from the server with paging support.

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

## **Getting Folders and Reading Messages Recursively**

In this article, most of the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) features are used to create an application that lists all the folders and sub-folders recursively from an IMAP server. It also saves the messages in each folder and sub-folder in MSG format on a local disk. In disk, folders and messages are created and saved in the same hierarchical structure as on the IMAP server. The following code snippet shows you how to get the messages and sub-folders information recursively.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() throws Exception {
    // Create an instance of the ImapClient class
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
            // Call the recursive method to read messages and get sub-folders
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

## **Get Message UID or Sequence Number**

Aspose.Email public API provides the following features to get the message identification info such as UID or sequence number which might be required when processing messages received from the server:

[MailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/) class - Represents identification information about a message in a mailbox.
- [getSequenceNumber()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getSequenceNumber--) method - Gets the sequence number of a message.
- [getUniqueId()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getUniqueId--) method - Gets the unique id of a message.

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class - Represents an e-mail message and allows to access message properties, ex. subject, body, sender and recipients addreses, etc.
- [getItemId](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getItemId--) method - Represents identification information about a message in a mailbox.

The code sample below demonstrates how to fetch and display the details of messages from the "INBOX" folder on an IMAP server using the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class:

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
## **Retrieving Extra Parameters as Summary Information**

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

## **Getting List-Unsubscribe Header Information**

List-Unsubscribe header contains the URL for unsubscribing from email lists e.g. advertisements, newsletters, etc. To get the List-Unsubscribe header, use the [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) property of the [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) class. The following example shows the use of the [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) property to get the List-Unsubscribe header.

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
