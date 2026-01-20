---
title: Send, Retrieve, and Manage Gmail Emails via SMTP, IMAP, and POP3
ArticleTitle: Send, Retrieve, and Manage Gmail Emails via SMTP, IMAP, and POP3
type: docs
weight: 40
url: /net/send-retrieve-manage-gmail-emails-smtp-imap-pop3/
---

This guide demonstrates how to **connect to a Gmail server** and perform common email operations such as **sending, receiving, and managing messages** using Aspose.Email for .NET. You’ll learn how to **work with SMTP, IMAP, and POP3 protocols over SSL**.


## **Send Emails via Gmail SMTP Server**

### **Connecting to the Gmail SMTP server**

To send emails through Gmail using the SMTP protocol, create an instance of the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class and configure its connection properties, including server address, port number, credentials, and security options as shown in the code sample below.


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectingGmailSMTPServer-ConnectingGmailSMTPServer.cs" >}}

### **Send an Email Message**

Once the connection is configured, you can send an email by creating a [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) object and passing it to the [SmtpClient.Send()](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/send/#send_5) method.   

The following code sample demonstrates how to create an email message, set its properties, for example the subject, to and body and send it with Aspose.Email in C#.


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendEmailMessage-SendEmailMessage.cs" >}}

## **Managing Emails Using the IMAP Protocol**

This section shows how to perform several IMAP operations such as **connecting to a Gmail account, accessing folders, retrieving messages, and creating folders on the server**.

### **Connecting to the IMAP Server**

To connect to Gmail via IMAP, use the [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) class and specify the server, port, and credentials. Gmail uses port 993 for secure IMAP connections.

The following code sample demonstrates how to create and configure an [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) to connect securely to a Gmail IMAP server:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingIMAP-ConnectToGmailUsingIMAP.cs" >}}

### **Selecting a Folder and Getting Message Count**

You can access the Inbox folder and retrieve the total number of messages using Aspose.Email [SelectFolder](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/selectfolder/#selectfolder_2) method as shown in the code sample below:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetGmailMessageCountUsingIMAP-GetGmailMessageCountUsingIMAP.cs" >}}

### **Saving Messages Locally**

After selecting a folder, use the [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) method to get all message summaries, then download and [save](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/savemessage/#savemessage_5) each message as an EML file. The following code sample demonstrates how to perform this task:


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SaveGmailMessages-SaveGmailMessages.cs" >}}

### **Creating a New Folder**
IMAP allows you to create folders directly on the email server. With Aspose.Email, you can do it with just a line of code:


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CreateNewGmailFolderUsingIMAP-CreateNewGmailFolderUsingIMAP.cs" >}}

### **Adding a New Message to a Folder**

You can create and append a message to a specific folder using the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) and [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) classes.

The code sample below constructs a [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) with sender, recipient, subject, and body. Then, it selects the Inbox folder on the IMAP server, subscribes to that folder if not already subscribed, and finally appends the created message to the selected folder.


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AddingMessageToGmailFolderUsingIMAP-AddingMessageToGmailFolderUsingIMAP.cs" >}}

## **Retrieving Emails Using the POP3 Protocol**

This section demonstrates how to connect to a Gmail account via **POP3**, check mailbox information, and download messages securely using **SSL**.

### **Connecting to the POP3 Server**

Create and configure a [Pop3client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) instance to connect to Gmail POP3 server. Use port 995 for SSL connections. The process is shown in the code sample below.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingPOP3-ConnectToGmailUsingPOP3.cs" >}}

### **Checking Mailbox Status**

Use the [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo) method to check the number of messages and total mailbox size as shown in the code sample below.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMailboxStatus-CheckGmailMailboxStatus.cs" >}}

### **Retrieving Message Information**

To get information about all messages in the mailbox, use the [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages) method. The following code sample obtains a collection of message metadata using `ListMessages()`, then iterates through each message info object to display key details such as the message unique ID, sequence index, subject, and size. This allows a client to preview message summaries without downloading the full email content.


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMessageInformation-CheckGmailMessageInformation.cs" >}}

### **Fetching and Saving Messages**

Use the [FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage_2) method to retrieve messages one by one and save them locally as .eml files.


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-RetrieveGmailMessages-RetrieveGmailMessages.cs" >}}
