---
title: Working with Exchange Mailbox and Messages
type: docs
weight: 20
url: /cpp/working-with-exchange-mailbox-and-messages/
---

## **Getting Mailbox Information Using EWS**
You can get mailbox information from an Exchange Server by calling the [GetMailboxInfo ](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ab7a471f46b5ebe0e3bf2c7f9166e2927)method of the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class. It returns an instance of type [ExchangeMailboxInfo](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_mailbox_info). Get mailbox information from properties such as MailboxUri, InboxUri, and DraftsUri. This article shows how to access mailbox information using Exchange Web Services.

To connect to the Exchange Server using Exchange Web Services (EWS), use the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class. This class uses EWS to connect to and manage items on an Exchange Server. The following code snippet shows you how to get mailbox information using the exchange web services.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailboxInformationFromExchangeWebServices-GetMailboxInformationFromExchangeWebServices.cpp" >}}
## **Sending Email Messages**
You can send email messages using an Exchange Server with the [IEWSClient->Send()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a02875ffd55c4033e7d88007a9ac2a83c) method accepts a [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) instance as a parameter and sends the email. This article explains how to send email messages using Exchange Web Services.

The following code snippet shows you how to sends email messages using [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailMessagesUsingExchangeWebServices-SendEmailMessagesUsingExchangeWebServices.cpp" >}}
## **Reading Emails from other User’s Mailbox**
Some accounts on Exchange Servers have the right to access multiple mailboxes, and some users have multiple email accounts on the same Exchange Server. In both cases, users can access other user's mailboxes using Aspose.Email. This API provides a mechanism for accessing folders and emails from other mailboxes using the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class. This functionality can be achieved using the overloaded [GetMailboxInfo()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac95e7c7a5e8678b70b4f5c4356d88582) method and providing the user email address as a parameter.

The following code snippet shows you how to read emails using the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessAnotherMailboxUsingExchangeWebServiceClient-1.cpp" >}}
## **Listing Messages**
A list of the email messages in an Exchange mailbox can be fetched by calling the [ListMessages](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method. Get the basic information about messages, such as subject, from, to and message ID, using the [ListMessages](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method.
### **Simple Messages Listing**
To list the messages in an Exchange mailbox:

1. Create an instance of the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Call the [ListMessages](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method to get the message collection.
1. Loop through the collection and display message information.

The following code snippet shows you how to connect to an exchange server using EWS and lists messages from the inbox folder.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesUsingEWS-ListingMessagesUsingEWS.cpp" >}}
### **Listing Messages From Different Folders**
The above code snippet list all the messages in the Inbox folder. It is possible to get the list of messages from other folders as well. The [ListMessages](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method accepts a folder URI as a parameter. As long as the folder URI is valid, you can get the list of messages from that folder. Use the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)->[get_MailboxInfo](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a63b3972a738e652a9bab4e3fcfd23a26)->xxxFolderUri property to get the URI of different folders. The rest of the code is the same as for getting a list of messages. The following code snippet shows you how to list messages from different folders using EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesFromFolders-ListingMessagesFromFolders.cpp" >}}
### **Listing Messages with Paging Support**
The following code snippet shows you how to get a list of messages with paging support.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingMessages-PagingSupportForListingMessages.cpp" >}}
### **Getting Message Type Information from ExchangeMessageInfo**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMessageTypeFromExchangeMessageInfo-GetMessageTypeFromExchangeMessageInfo.cpp" >}}
## **Saving Messages**
This article shows how to get messages from an Exchange Server mailbox and save them to disk in EML and MSG formats:

- Save as EML on disk.
- Save to memory stream.
- Save as MSG.
### **Saving Messages to EML**
To get messages and save in EML format:

1. Create an instance of the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.
1. Provide the mailboxUri, username, password and domain.
1. Call the [IEWSClient->ListMessages()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method to get an instance of the [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) collection.
1. Loop through the [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) collection to get the unique URI for each message.
1. Call the [IEWSClient->SaveMessage()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) method and pass the unique URI and save location as parameters.

The following code snippet shows you how to use EWS to connect to the Exchange Server and save messages as EML files.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesUsingExchangeWebServices-SaveMessagesUsingExchangeWebServices.cpp" >}}
### **Saving Messages to a Memory Stream**
Instead of saving EML files to disk, it is possible to save it to a memory stream. This is useful when you want to save the stream to some storage location like a database. Once the stream has been saved to a database, you can reload the EML file into the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class. The following code snippet shows you how to save messages from an Exchange Server mailbox to a memory stream using EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesToMemoryStreamUsingEWS-SaveMessagesToMemoryStream.cpp" >}}
### **Saving Messages in MSG Format**
The [IEWSClient->SaveMessage()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) method can directly save the message to EML format. To save the messages to MSG format, first, call the [IEWSClient->FetchMessage()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) method which returns an instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class. Then call the [MailMessage->Save()](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a41d3ada3ca8b7ca8130629b616f0b91c) method to save the message to MSG. The following code snippet shows you how to get messages from an Exchange Server mailbox and saves them to MSG format using EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesInMSGFormatExchangeEWS-SaveMessagesInMSGFormatExchangeEWS.cpp" >}}
## **Getting ExchangeMessageInfo from Message URI**
An email message is represented by its unique identifier, URI, and is an integral part of the ExchangeMessageInfo object. In case, only message URI is available, then [ExchangeMessageInfo](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) object can also be retrieved using this available information. The overload version of [ListMessages](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2b3b4ebfdd9423eeb63d59b5e74cc53a) takes a list of Ids and returns an [ExchangeMessageInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) collection. The following code snippet shows you how to get [ExchangeMessageInfo](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) from message URI.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetExchangeMessageInfoFromMessageURI-GetExchangeMessageInfoFromMessageURI.cpp" >}}
## **Fetch Messages from an Exchange Server Mailbox**
The [ListMessages()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) method is used to get a list of messages from an Exchange Server mailbox. The [ListMessages()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) method gets basic information about messages, for example, the subject, the message ID, from, and to. To get the complete message details, Aspose.Email provides the [IEWSClient->FetchMessage()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) method. This method accepts the message URI as a parameter and returns an instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class. The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class then provides message details like the body, headers, and attachments. To fetch messages from Exchange Server Mailbox:

1. Create an instance of type [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
1. Specify the server name, user name, password, and domain.
1. Call [IEWSClient->ListMessages()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) method to get the [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
1. Loop through the [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection) collection to get [ExchangeMessageInfo->get_UniqueUri()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) values.
1. Call [IEWSClient->FetchMessage()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) and pass [ExchangeMessageInfo->get_UniqueUri()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#a3cb9feb99e2ac195529cf9e5e7867cb7) as parameter.

The following code snippet demonstrates fetching all the messages using EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchMessageUsingEWS-FetchMessageUsingEWS.cpp" >}}
## **Pre-Fetch Message Size**
Microsoft Outlook InterOp provides the feature of retrieving message size before actually fetching the complete message from the server. In case of Aspose.Email API, the summary information retrieved from the Exchange server is represented by the [ExchangeMessageInfo](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) class. It provides the feature of retrieving message size by using the [Size](https://reference.aspose.com/email/cpp/class/aspose.email.clients.message_info_base#a04bc106203ed5cfec65f4d0320d14e8a) property. In order to retrieve the message size, the standard call to [IEWSClient->ListMessages()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) is used to retrieve the [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). The following code snippet shows you how to display message size using the [ExchangeMessageInfo](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PreFetchMessageSizeUsingIEWSClient-PreFetchMessageSizeUsingIEWSClient.cpp" >}}
## **Download Messages from Public Folders**
Microsoft Exchange Server lets users create public folders and post messages in them. To do this through your application, use Aspose.Email's [EWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class to connect to the Exchange Server and read and download messages and posts from public folders. The following code snippet shows you how to reads all public folders and subfolders, and list and download any messages found in these folders. This example only works with Microsoft Exchange Server 2007 or above since only these support EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}
## **Moving Messages**
You can move email messages from one folder to another with the help of the [IEWSClient](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class Move method. It takes the following parameters:

- The unique URI of the message which is to be moved.
- The unique URI of the destination folder.
### **Moving Messages between Folders**
The following code snippet shows you how to move a message in a mailbox from the Inbox folder to a folder called Processed. In this example, the application:

1. Reads messages from the Inbox folder.
1. Processes some of the messages based on some criteria (in this example, we find a keyword in the message subject).
1. Moves messages which fulfill the given condition to the processed folder.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveMessageFromOneFolderToAnotherusingEWS-MoveMessageFromOneFolderToAnotherusingEWS.cpp" >}}
## **Deleting Messages**
You can delete email messages from a folder with the help of the [IEWSClient->DeleteMessage](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a576fb78dcbac3bdb8b2bb87cab5d33c1) method. It takes the message's unique URI as a parameter.

The following code snippet shows you how to delete a message from the Inbox folder. For the purpose of this example, the code:

1. Reads messages from the Inbox folder.
1. Process messages based on some criteria (in this example, we find a keyword in the message subject).
1. Deletes the message.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMessagesFromUsingEWS-DeleteMessagesFromusingEWS.cpp" >}}
## **Copying Messages**
Aspose.Email API allows copying a message from one folder to another folder using the [IEWSClient->CopyItem](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a6e340250e1e0f51d68d4ffe7727f4e7f) method. The overloaded version of this method returns the Unique URI of the copied message as shown in this article.
### **Copying a Message to Another Folder**
The following code snippet shows you how to copy a message to another folder.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cpp" >}}
