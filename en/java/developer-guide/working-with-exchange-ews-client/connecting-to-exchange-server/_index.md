---
title: Connecting to Exchange Server
ArticleTitle: Connecting to Exchange Server
type: docs
weight: 10
url: /java/connecting-to-exchange-server/
---


In order to connect to Exchange servers 2007, 2010 and 2013 using Exchange Web Service, Aspose.Email provides the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) interface that implements the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class. The [EWSClient.getEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#getEWSClient\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\)) method instantiates and returns an [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) object that is further used to perform operations related to an Exchange mailbox and other folders. This article shows how to instantiate objects of [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
## **Connecting to Exchange Server using EWS**
The following code snippet shows you how to connect using Exchange Web Service (EWS).



~~~Java
private static IEWSClient getExchangeEWSClient() {
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String domain = "";
    final String username = "username@onmicrosoft.com";
    final String password = "password";
    NetworkCredential credentials = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
    return client;
}
~~~
## **Connecting to Exchange Server using IMAP**
Microsoft Exchange Server supports the IMAP protocol for accessing items in a mailbox. Use Aspose.Email's [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class to connect to the Exchange Server using the IMAP protocol. For more information about the [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class. First, make sure that IMAP services are enabled for your Exchange Server:

1. Open the Control Panel.
1. Go to Administrator Tools, then Services.
1. Check the status of the Microsoft Exchange IMAP4 service.
1. If it is not already running, enable/start it.

The following code snippet shows you how to connect and list messages from the Inbox folder of Microsoft exchange server using IMAP protocol.



~~~Java
// Connect to Exchange Server using ImapClient class
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.setSecurityOptions(SecurityOptions.Auto);

// Select the Inbox folder
imapClient.selectFolder(ImapFolderInfo.IN_BOX);

// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    System.out.println(msgInfo.getSubject());
}
// Disconnect from the server
imapClient.dispose();
~~~



The following code snippet shows you how to use SSL.



~~~Java
public static void run() {
    // Connect to Exchange Server using ImapClient class
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1");
    imapClient.setSecurityOptions(SecurityOptions.SSLExplicit);

    // Select the Inbox folder
    imapClient.selectFolder(ImapFolderInfo.IN_BOX);

    // Get the list of messages
    ImapMessageInfoCollection msgCollection = imapClient.listMessages();
    for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
        System.out.println(msgInfo.getSubject());
    }
    // Disconnect from the server
    imapClient.dispose();
}
~~~



After connecting to an Exchange server using IMAP and getting the [IMapMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfoCollection), The following code snippet shows you how to use the [MessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/MessageInfo) object's sequence number to save a specific message.



~~~Java
// Select the Inbox folder
imapClient.selectFolder(ImapFolderInfo.IN_BOX);
// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    // Fetch the message from inbox using its SequenceNumber from msgInfo
    MailMessage message = imapClient.fetchMessage(msgInfo.getSequenceNumber());

    // Save the message to disc now
    message.save(dataDir + msgInfo.getSequenceNumber() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~
