---
title: Working with Exchange Mailbox and Messages using WebDav
ArticleTitle: Working with Exchange Mailbox and Messages using WebDav
type: docs
weight: 20
url: /net/working-with-exchange-mailbox-and-messages-using-webdav/
---


## **Getting Mailbox Information using WebDav**
The [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class has members that can be used to get mailbox information from an Exchange Server by calling the [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) method. It returns an instance of type [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo). Get mailbox information from properties such as [MailboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/mailboxuri), [InboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/inboxuri), and [DraftsUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/draftsuri). This article shows how to access mailbox information directly from an Exchange Server.

To get the Exchange Mailbox information:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Specify the Exchange Server, username, password and domain in the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) constructor.
1. Call the [ExchangeClient.GetMailboxSize()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxsize/index) method to get mailbox size.
1. Call the [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) method to get an instance of the [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo) class.
1. Get the mailbox information using the [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo) class' different properties.

The following code snippet shows you how to get exchange mailbox information.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromExchangeServer.cs" >}}
## **Sending Email Messages**
You can send email messages using an Exchange Server with the help of the tools in Aspose.Email.Exchange. The [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) method accepts a [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instance as a parameter and sends the email. This article explains how to send email messages using an Exchange server.
### **Sending Email Messages Using Exchange Server**
To send emails using an Exchange Server:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Specify server name, username, password, and domain.
1. Create an instance of the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
1. Specify the from, to, subject and other [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) properties.
1. Call the [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) method to send the email.

The following code snippet shows you how to sends email messages using Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendEmailMessagesUsingExchangeServer-SendEmailMessagesUsingExchangeServer.cs" >}}
## **Reading Emails from other User’s Mailbox**
Some accounts on Exchange Servers have the right to access multiple mailboxes, and some users have multiple email accounts on the same Exchange Server. In both cases, users can access other user's mailboxes using Aspose.Email for .NET. This API provides a mechanism for accessing folders and emails from other mailboxes using the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class. This functionality can be achieved using the overloaded [GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) method and providing the user email address as a parameter.

The following code snippet shows you how to use the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class to access another mailbox.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-AccessAnotherMailboxUsingExchangeClient-AccessAnotherMailboxUsingExchangeClient.cs" >}}
## **Listing Messages**
A list of the email messages in an Exchange mailbox can be fetched by calling the [ExchangeClient.ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method. Get the basic information about messages, such as subject, from, to and message ID, using the [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method.
### **Simple Messages Listing**
To list the messages in an Exchange mailbox:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Call the [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method and create a message collection.
1. Loop through the collection and display message information.

The following code snippet shows you how to connects to the Exchange mailbox and get a list of messages from the inbox folder.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListExchangeServerMessages-ListExchangeServerMessages.cs" >}}
### **Listing Messages From Different Folders**
The above code snippets list all the messages in the Inbox folder. It is possible to get the list of messages from other folders as well. The [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method accepts a folder URI as a parameter. As long as the folder URI is valid, you can get the list of messages from that folder. Use the ExchangeClient.MailboxInfo.xxxFolderUri property to get the URI of different folders. The rest of the code is the same as for getting a list of messages. The following code snippet shows you how to list messages from different folders using [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesFromDifferentFolders-ListMessagesFromDifferentFolders.cs" >}}
### **Listing Messages by ID**
The above code snippet used the [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method to list all the messages in a specified Exchange Server mailbox folder. If you know the message ID of a message beforehand, you can get the message using the [ListMessagesbyId()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessagesbyid) method. To get the message, pass the folder URI and message ID. This scenario is useful when you already know the message ID, for example, when message IDs are saved to the database. The following code snippet shows you how to list messages by ID.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesByID-ListMessagesByID.cs" >}}
## **Saving Messages**
This topic shows how to get messages from an Exchange Server mailbox and save them to disk in EML and MSG formats:

- Save as EML on disk.
- Save to memory stream.
- Save as MSG.
### **Saving Messages to EML**
To get messages and save in EML format:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Provide the server name, username, password, and domain.
1. Call the [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method to get an instance of the [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) collection.
1. Loop through the [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) collection to get the unique URI for each message.
1. Call the [ExchangeClient.SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) method and pass the unique URI as a parameter.
1. Provide the [SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) method with a path to where you want to save the file.

The following code snippet shows you how to save messages to EML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ExchangeClientSaveMessagesInEMLFormat-ExchangeClientSaveMessagesInEMLFormat.cs" >}}
### **Saving Messages to a Memory Stream**
Instead of saving EML files to disk, it is possible to save it to a memory stream. This is useful when you want to save the stream to some storage location like a database. Once the stream has been saved to a database, you can reload the EML file into the [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class. The following code snippet shows you how to save messages from an Exchange Server mailbox to a memory stream.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesToMemoryStream-SaveMessagesToMemoryStream.cs" >}}
### **Saving Messages in MSG Format**
The [ExchangeClient.SaveMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) method can directly save the message to EML format. To save the messages to MSG format, first, call the [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) method which returns an instance of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class. Then call the [MailMessage.Save()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index) method to save the message to MSG. The following code snippet shows you how to gets messages from an Exchange Server mailbox and saves them to MSG format.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesInMSGFormatExchangeClient-SaveMessagesInMSGFormatExchangeClient.cs" >}}
## **Fetch Messages from an Exchange Server Mailbox**
Listing Messages on an Exchange Server used the [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method to get a list of messages from an Exchange Server mailbox. The [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method gets basic information about messages, for example, the subject, the message ID, from and to. To get the complete message details, Aspose.Email.Exchange provides the [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) method. This method accepts the message URI as a parameter and returns an instance of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class. The [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class then provides message details like body, headers, and attachments. To fetch messages from Exchange Server Mailbox:

1. Create an instance of type [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Specify the mailboxUri, user name, password, and domain.
1. Call [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) to get the [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Loop through the [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) collection to get [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) values.
1. Call [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) and pass  [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) as a parameter.

The following code snippet shows you connect to the Exchange Server mailbox and fetch all the messages.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FetchMessageUsingExchangeClient-FetchMessageUsingExchangeClient.cs" >}}
## **Pre-Fetch Message Size**
Microsoft Outlook InterOp provides the feature of retrieving message size before actually fetching the complete message from the server. In the case of Aspose.Email API, the summary information retrieved from the Exchange server is represented by [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo) class. It provides the same feature of retrieving message size using the Size property. In order to retrieve the message size, the standard call to ExchangeClient's [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) is used that retrieves collection of [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). The following code snippet shows you how to display message size using the [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo) class.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-PreFetchMessageSizeUsingExchangeClient-PreFetchMessageSizeUsingExchangeClient.cs" >}}
## **Moving Messages**
You can move email messages from one folder to another with the help of the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class [MoveItems](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/moveitems/index) method. It takes the parameters:

- The unique URI of the message which is to be moved.
- The unique URI of the destination folder.
### **Moving Messages between Folders**
The following code snippet shows you how to move a message in a mailbox from the Inbox folder to a folder called Processed. In this example, the application:

1. Reads messages from the Inbox folder.
1. Processes some of the messages based on some criteria (in this example, we find a keyword in the message subject).
1. Moves messages which fulfill the given condition to the processed folder.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-MoveMessageFromOneFolderToAnotherUsingExchangeClient-MoveMessageFromOneFolderToAnotherUsingExchangeClient.cs" >}}
## **Deleting Messages**
You can delete email messages from a folder with the help of the [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class [DeleteMessage](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/deletemessage/index) method. It takes the message's unique URI as a parameter.
### **Deleting Messages from an Exchange Server**
The following code snippet shows you how to delete a message from the Inbox folder. For the purpose of this example, the code:

1. Reads messages from the Inbox folder.
1. Process messages based on some criteria (in this example, we find a keyword in the message subject).
1. Delete the message.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.cs" >}}
