---
title: Accessing Gmail on SSL
ArticleTitle: Accessing Gmail on SSL
type: docs
weight: 40
url: /net/accessing-gmail-on-ssl/
---

## **SMTP**
This article shows how to perform [connect to a Gmail server](#connecting-to-gmail-smtp-server) and [send an email](#sending-an-email-message) using the SMTP protocol on SSL.
### **Connecting to Gmail SMTP server**
The following code snippet shows you how to connect to an SSL enabled SMTP server.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectingGmailSMTPServer-ConnectingGmailSMTPServer.cs" >}}
### **Sending an Email Message**
The code above set up the SMTPClient object to connect to the Gmail server. To send a message using the same client object, create a [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class object and send the message using the SMTP client object. The following code snippet shows you how to set the message properties, for example the subject, to and body:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendEmailMessage-SendEmailMessage.cs" >}}
## **IMAP**
This article shows how to perform a number of activities on an SSL enabled mail server using the IMAP protocol:

- Connect to a mail server.
- Get the total number of messages in an inbox.
- Save messages locally.
- Create a message an add it to a folder.
### **Connecting to the Mail Server**
Use Aspos.Email's [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) class object to connect to the mail server. The server's address, port, username and password are required to establish a connection. Gmail uses port 993 for the IMAP protocol, the following code snippet shows you how connects to Gmail using that port.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingIMAP-ConnectToGmailUsingIMAP.cs" >}}
### **Selecting a Folder and Getting the Total Number of Messages**
Checking the Inbox folder is the most frequent task when checking email. Using Aspose.Email, this can be done using just two simple lines of code. The following code snippet shows you how to access the Inbox folder and get the total number of messages in the folder.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetGmailMessageCountUsingIMAP-GetGmailMessageCountUsingIMAP.cs" >}}
### **Saving Messages to a Local Hard Drive**
Once a folder has been selected with the SelectFolder method, use the ListMessages function to get a list of all the messages in the folder in an ImapMessagesInfoCollection object. Iterate through this collection and save email messages to the local drive of computer as follows:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SaveGmailMessages-SaveGmailMessages.cs" >}}
### **Creating a New Folder**
The IMAP protocol also allows you to create a new folder on the email server. This can be done using a simple function call.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CreateNewGmailFolderUsingIMAP-CreateNewGmailFolderUsingIMAP.cs" >}}
### **Creating a New Message in a Folder**
Add a new message to the folder using the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) and [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) classes. The examples below creates a MailMessage object first by providing the subject, to and from values. It then subscribes to a folder and adds the message to it. The following code snippet shows you create a new message in a folder.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AddingMessageToGmailFolderUsingIMAP-AddingMessageToGmailFolderUsingIMAP.cs" >}}
## **POP3**
This article shows some examples that use the POP3 protocol on SSL. To connect to an SSL-protected server, we need to define the SSL port and two extra properties. The rest of the code is the same as for connecting to a normal POP3 server.

The code samples below show how to:

- Connect to an SSL server.
- Check the mailbox status
- Get information about the message
- Retrieve emails.
### **Connecting to Mail Server**
Connect to the SSL enabled mail server using the [Pop3client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) class as described below.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingPOP3-ConnectToGmailUsingPOP3.cs" >}}
### **Checking the Mailbox Status**
The following code snippet shows you how checks the number of messages stored in the mailbox and the size of the mailbox. Use [Pop3MailboxInfo](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo) class for this purpose.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMailboxStatus-CheckGmailMailboxStatus.cs" >}}
### **Checking Message Information**
This example checks all the messages in the mailbox using the [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection) class. Use the [Pop3Client.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/listmessages/index) function to get the [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection) collection. Then iterate through the collection to read the message information: message ID, index, subject and size



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMessageInformation-CheckGmailMessageInformation.cs" >}}
### **Retrieving Messages**
To get the messages from the mailbox, use the [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) class' FetchMessage() method to get the message into a [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) type object. The following code snippet shows you how to counts the number of emails in the mailbox and then iterates through them to retrieve each one.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-RetrieveGmailMessages-RetrieveGmailMessages.cs" >}}
