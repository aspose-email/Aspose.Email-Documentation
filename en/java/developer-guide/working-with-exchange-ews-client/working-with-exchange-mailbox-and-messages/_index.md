---
title: Working with Exchange Mailbox and Messages - Read Email from Exchange Server in Java
ArticleTitle: Working with Exchange Mailbox and Messages - Read Email from Exchange Server in Java
linktitle: Working with Exchange Mailbox and Messages
type: docs
weight: 20
url: /java/working-with-exchange-mailbox-and-messages/
keywords: java read email from exchange server
---


## **Getting Mailbox Information Using EWS**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class has members that can be used to get mailbox information from an Exchange Server by calling the [IEWSClient.getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getMailboxInfo\(\)) method. It returns an instance of type [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo). Get mailbox information from properties such as [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getInboxUri\(\)) and [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#setDraftsUri\(java.lang.String\)). This article shows how to access mailbox information using Exchange Web Services.

If you want to connect to the Exchange Server using Exchange Web Services (EWS), use the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) class. This class uses EWS to connect to and manage items on an Exchange Server. The following Java code snippet shows you how to get mailbox information using the exchange web services.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get mailbox size, exchange mailbox info, Mailbox and Inbox folder URI
System.out.println("Mailbox size: " + client.getMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
System.out.println("Inbox folder URI: " + mailboxInfo.getInboxUri());
System.out.println("Sent Items URI: " + mailboxInfo.getSentItemsUri());
System.out.println("Drafts folder URI: " + mailboxInfo.getDraftsUri());
~~~
## **Sending Email Messages**
You can send email messages using an Exchange Server with the help of the tools in [Aspose.Email.Exchange](#working-with-exchange-mailbox-and-messages). The IEWSClient.Send() method accepts a [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) instance as a parameter and sends the email. This article explains how to send email messages using Exchange Web Services.

Aspose.Email provides the IEWSClient class to connect to Microsoft Exchange Server using Exchange Web Services. The following code snippet shows you how to uses EWS to send emails using Microsoft Exchange Server. The following Java code snippet shows you how to sends email messages using EWS.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create instance of type MailMessage
MailMessage msg = new MailMessage();
msg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("recipient@ domain.com "));
msg.setSubject("Sending message from exchange server");
msg.setHtmlBody("<h3>sending message from exchange server</h3>");

// Send the message
client.send(msg);
~~~

## **Getting Message Class**

The [getMessageClass()](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/#getMessageClass--) method of the [ExchangeMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/) class gets a string representing the class for the message. The code sample below shows how to get the message class:

```java
try (IEWSClient client = EWSClient.getEWSClient(uri, credentials))
{
    ExchangeMessageInfoCollection messageInfoCollection = client.listMessagesFromPublicFolder(publicFolder);

    for (ExchangeMessageInfo messageInfo : messageInfoCollection)
    {
        System.out.println("Message Class: " + messageInfo.getMessageClass());
    }
}
```
## **Reading Emails from other User’s Mailbox**
Some accounts on Exchange Servers have the right to access multiple mailboxes, and some users have multiple email accounts on the same Exchange Server. In both cases, users can access other user's mailboxes using Aspose.Email for Java. This API provides mechanism for accessing folders and emails from other mailboxes using the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class. This functionality can be achieved using the overloaded [getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#getMailboxInfo\(\)) method and providing the user email address as a parameter.

The following code snippet shows you how to reading emails using [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo("otherUser@domain.com");
~~~
## **Listing Messages**
A list of the email messages in an Exchange mailbox can be fetched by calling the [IEWSClient.listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) method. Get the basic information about messages, such as subject, from, to and message ID, using the [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) method.
### **Simple Messages Listing**
To list the messages in an Exchange mail box:

1. Create an instance of the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class.
1. Call the listMessages method and create a message collection.
1. Loop through the collection and display message information.

The following Java code snippet shows you how to connects to an exchange server using EWS and lists messages from the inbox folder.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject: " + msgInfo.getSubject());
    System.out.println("From: " + msgInfo.getFrom().toString());
    System.out.println("To: " + msgInfo.getTo().toString());
    System.out.println("Message ID: " + msgInfo.getMessageId());
    System.out.println("Unique URI: " + msgInfo.getUniqueUri());
}
~~~
### **Listing Messages From Different Folders**
[The above code snippets](#simple-messages-listing), list all the messages in the Inbox folder. Its possible to get the list of messages from other folders as well. The [IEWSClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) method accepts a folder URI as a parameter. As long as the folder URI is valid, you can get the list of messages from that folder. Use the IEWSClient.getMailboxInfo().getXXXFolderUri property to get the URI of different folders. The rest of the code is same as for getting a list of messages. The following code snippet shows you how to listing messages from different folders using EWS.


~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get folder URI
String strFolderURI = "";
strFolderURI = client.getMailboxInfo().getInboxUri();
strFolderURI = client.getMailboxInfo().getDeletedItemsUri();
strFolderURI = client.getMailboxInfo().getDraftsUri();
strFolderURI = client.getMailboxInfo().getSentItemsUri();

// Get list of messages from the specified folder
ExchangeMessageInfoCollection msgCollection = client.listMessages(strFolderURI);
~~~
### **Listing Messages with Paging Support**
The following Java code snippet shows you how to get a list of messages with paging support.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
try {
    try {
        // Create some test messages to be added to server for retrieval later
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157_1 - " + UUID.randomUUID().toString(),
                    "EMAILNET-35157 Move paging parameters to separate class");
            client.appendMessage(client.getMailboxInfo().getInboxUri(), message);
        }
        // Verfiy that the messages have been added to the server
        ExchangeMessageInfoCollection totalMessageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RETREIVING THE MESSAGES USING PAGING SUPPORT ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
        // Total Pages Count
        System.out.println(pageInfo.getTotalCount());

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage, pageInfo.getPageOffset() + 1);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // foreach to while statements conversion
        for (ExchangeMessagePageInfo pageCol : pages) {
            retrievedItems += pageCol.getItems().size();
        }
        // Verify total message count using paging
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    client.dispose();
}
~~~
### **Getting Message Type Information from ExchangeMessageInfo**


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.listMessages(client.getMailboxInfo().getDeletedItemsUri());
System.out.println(list.get_Item(0).getMessageInfoType()); // MessageInfoType
~~~
## **Saving Messages**
This article shows how to get messages from an Exchange Server mailbox and save them to disk in EML and MSG formats:

- Save as EML on disk.
- Save to memory stream.
- Save as MSG.
### **Saving Messages to EML**
To get messages and save in EML format:

1. Create an instance of the IEWSClient class.
1. Provide the mailboxUri, username, password and domain.
1. Call the IEWSClient.listMessages() method to get an instance of the ExchangeMessagesInfoCollection collection.
1. Loop through the ExchangeMessagesInfoCollection collection to get the unique URI for each message.
1. Call the IEWSClient.saveMessage() method and pass the unique URI as a parameter.
1. Provide a the saveMessage() method with a path to where you want to save the file.

The following code snippet shows you how to use EWS to connect to the Exchange Server and save messages as EML files.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now save the message in disk
    client.saveMessage(strMessageURI, dataDir + msgInfo.getMessageId() + "out.eml");
}
~~~
### **Saving Messages to a Memory Stream**
Instead of saving EML files to disk, it is possible to save it to a memory stream. This is useful when you want to save the stream to some storage location like a database. Once the stream has been saved to a database, you can reload the EML file into the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class. The following code snippet shows you how to save messages from an Exchange Server mailbox to a memory stream using EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now save the message in memory stream
    ByteArrayOutputStream stream = new ByteArrayOutputStream();
    client.saveMessage(strMessageURI, stream);
}
~~~
### **Saving Messages in MSG Format**
The [IEWSClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#saveMessage\(java.lang.String,%20java.lang.String\)) method can directly save the message to EML format. To save the messages to MSG format, first call the [IEWSClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchMessage\(java.lang.String\)) method which returns an instance of the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class. Then call the [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.lang.String\)) method to save the message to MSG. The following code snippet shows you how to gets messages from an Exchange Server mailbox and saves them to MSG format using EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

int count = 0;
// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now get the message details using FetchMessage() and Save message as Msg
    MailMessage message = client.fetchMessage(strMessageURI);
    message.save(dataDir + (count++) + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~
## **Getting ExchangeMessageInfo from Message URI**
An email message is represented by its unique identifier, URI, and is integral part of the [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) object. In case, only message URI is available, then [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) object can also be retrieved using this available information. The overload version of [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.Iterable\)) takes a list of Ids to use [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection). The following code snippet shows you how to get [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) from message URI.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<String> ids = new ArrayList<String>();
List<MailMessage> messages = new ArrayList<MailMessage>();

for (int i = 0; i < 5; i++) {
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + UUID.randomUUID().toString(),
            "EMAILNET-35033 Messages saved from Sent Items folder doesn't contain 'To' field");
    messages.add(message);
    String uri = client.appendMessage(message);
    ids.add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(ids);

for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) messageInfoCol) {
    // Do something ...
    System.out.println(messageInfo.getUniqueUri());
}
~~~
## **Fetch Messages from an Exchange Server Mailbox**
Listing Messages on an Exchange Server used the [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) method to get a list of messages from an Exchange Server mailbox. The [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) method gets basic information about messages, for example, the subject, the message ID, from and to. To get the complete message details, Aspose.Email.Exchange provides the IEWSClient.fetchMessage() method. This method accepts the message URI as a parameter and returns am instance of the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class. The [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class then provides message details like body, headers and attachments. Find out more about the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) API, or find out how to manage emails with the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class. To fetch messages from Exchange Server Mailbox:

1. Create an instance of type IEWSClient.
1. Specify the server name, user name, password and domain.
1. Call listMessages to get the ExchangeMessageInfoCollection.
1. Loop through the ExchangeMessageInfoCollection collection to get ExchangeMessageInfo.UniqueURI values.
1. Call IEWSClient.fetchMessage() and pass ExchangeMessageInfo.UniqueURI as parameter.

The following code snippet shows you connect to the Exchange Server mailbox and fetches all the messages using EWS.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now get the message details using FetchMessage()
    MailMessage msg = client.fetchMessage(strMessageURI);

    for (Attachment att : (Iterable<Attachment>) msg.getAttachments()) {
        System.out.println("Attachment Name: " + att.getName());
    }
}
~~~

### **Using the FetchItem method to fetch a message**

{{% alert color="primary" %}}

Note, the [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) method returns message without attachments. To fetch messages with attachments, use the [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)) method, described in the section below. 

{{% /alert %}}

The [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\))  method is more preferred if you want to fetch a [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) and operate with MAPI properties. You can also use this method to fetching any Outlook item, such as a contact, appointment, task, etc.

```java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : msgCollection)
{
    // Now get the message using FetchItem()
    MapiMessage msg = client.fetchItem(msgInfo.getUniqueUri());

    // If necessary, you can cast the MapiMessage to the proper item type to simplify working with its properties.
    MapiContact contact = (MapiContact) msg.toMapiMessageItem();
}
```

## **Pre-Fetch Message Size**
Microsoft Outlook InterOp provides the feature of retrieving message size before actually fetching the complete message from the server. In case of Aspose.Email API, the summary information retreived from Exchange server is represented by [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) class. It provides the same feature of retrieving message size using the Size property. In order to retrieve the message size, the standard call to IEWSClient's listMessages is used that retrieves collection of [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). The following code snippet shows you how to display message size using the [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) class.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject: " + msgInfo.getSubject());
    System.out.println("From: " + msgInfo.getFrom().toString());
    System.out.println("To: " + msgInfo.getTo().toString());
    System.out.println("Message Size: " + msgInfo.getSize());
    System.out.println("==================================");
}
~~~
## **Download Messages Recursively**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient)’s [listSubFolders()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listSubFolders\(com.aspose.email.ExchangeFolderInfo\)) method can be used to get messages from folders and subfolders from an Exchange Server mailbox recursively. This requires Exchange Server 2007 or greater, because it uses EWS. The following code snippet shows you how to download the whole mailbox (folders and subfolders) of an Exchange Server. The folder structure is created locally and all messages download.



~~~Java
public static void run() {
    try {
        downloadAllMessages();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void downloadAllMessages() {
    try {
        String rootFolder = domain + "-" + username;
        new File(rootFolder).mkdirs();
        String inboxFolder = rootFolder + "\\Inbox";
        new File(inboxFolder).mkdirs();

        System.out.println("Downloading all messages from Inbox....");
        // Create instance of IEWSClient class by giving credentials
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Call the recursive method to read messages and get sub-folders
            listMessagesInFolder(client, folderInfo, rootFolder);
        }

        System.out.println("All messages downloaded.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

// Recursive method to get messages from folders and sub-folders
private static void listMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, String rootFolder) {
    // Create the folder in disk (same name as on IMAP server)
    String currentFolder = rootFolder + "\\" + folderInfo.getDisplayName();
    new File(currentFolder).mkdirs();

    // List messages
    ExchangeMessageInfoCollection msgInfoColl = client.listMessages(folderInfo.getUri());
    System.out.println("Listing messages....");
    int i = 0;
    for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
        // Get subject and other properties of the message
        System.out.println("Subject: " + msgInfo.getSubject());

        // Get rid of characters like ? and :, which should not be included in a file name
        String fileName = msgInfo.getSubject().replace("?", " ").replace(":", " ");

        MailMessage msg = client.fetchMessage(msgInfo.getUniqueUri());
        msg.save(dataDir + "\\" + fileName + "-" + i + ".msg");

        i++;
    }
    System.out.println("============================\n");
    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Download Messages from Public Folders**
Microsoft Exchange Server lets users create public folders and post messages in them. To do this through your application, use Aspose.Email's [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class to connect to the Exchange Server and read and download messages and posts from public folders. The following code snippet shows you how to reads all public folders, and subfolders, and lists and downloads any messages found in these folders. This example only works with Microsoft Exchange Server 2007 or above since only these support EWS.



~~~Java
public static void run() {
    try {
        readPublicFolders();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void readPublicFolders() {
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.listPublicFolders();
    for (ExchangeFolderInfo publicFolder : (Iterable<ExchangeFolderInfo>) folders) {
        System.out.println("Name: " + publicFolder.getDisplayName());
        System.out.println("Subfolders count: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Folder Name: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Call this method recursively for any subfolders
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Moving Messages**
You can move email messages from one folder to another with the help of the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class [move](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#moveItem\(java.lang.String,%20java.lang.String\)) method. It takes the parameters:

- The unique URI of the message which is to be moved.
- The unique URI of the destination folder.
### **Moving Messages between Folders**
The following code snippet shows you how to move a message in a mailbox from the Inbox folder to a folder called Processed. In this example, the application:

1. Reads messages from the Inbox folder.
1. Processes some of the messages based on some criteria (in this example, we find a keyword in the message subject).
1. Moves messages which fulfill the given condition to the processed folder.

~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// List all messages from Inbox folder
System.out.println("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Move message to "Processed" folder, after processing certain messages based on some criteria
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("process this message")) {
        client.moveItem(mailboxInfo.getDeletedItemsUri(), msgInfo.getUniqueUri()); // EWS
        System.out.println("Message moved...." + msgInfo.getSubject());
    } else {
        // Do something else
    }
}
~~~
## **Deleting Messages**
You can delete email messages from a folder with the help of the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) method. It takes the message's unique URI as a parameter.

The following code snippet shows you how to delete a message from the Inbox folder. For the purpose of this example, the code:

1. Reads messages from the Inbox folder.
1. Process messages based on some criteria (in this example, we find a keyword in the message subject).
1. Deletes the message.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// List all messages from Inbox folder
System.out.println("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Delete message based on some criteria
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("delete") == true) {
        client.deleteItem(msgInfo.getUniqueUri(), DeletionOptions.getDeletePermanently()); // EWS
        System.out.println("Message deleted...." + msgInfo.getSubject());
    } else {
        // Do something else
    }
}
~~~
## **Copying Messages**
Aspose.Email API allows to copy a message from one folder to another folder using the [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)) method. The overloaded version of this method returns the Unique URI of the copied message as shown in this article.
### **Copying a Message to Another Folder**
The following code snippet shows you how to copy a message to another folder.



~~~Java
try {
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
