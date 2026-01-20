---
title: EWS Email Management Guide: Send, Read, and Organize Messages
ArticleTitle: Send, Read, and Organize Messages on Exchange Server
type: docs
weight: 20
url: /cpp/exchange-server-ews-email-management-guide/
---

## **Retrieve Exchange Mailbox Information with EWS**

Aspose.Email allows you to retrieve mailbox details from Microsoft Exchange using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class. By calling the [GetMailboxInfo()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ab7a471f46b5ebe0e3bf2c7f9166e2927) method, the client returns an [ExchangeMailboxInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_mailbox_info) object containing useful folder URIs such as Mailbox, Inbox, Drafts, and Sent Items.

To connect to the Exchange Server with Exchange Web Services (EWS), use the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class. This class uses EWS to connect to and manage items on an Exchange Server. 

The following code snippet demonstrates how to **get mailbox information** using the exchange web services.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMailboxInformationFromExchangeWebServices-GetMailboxInformationFromExchangeWebServices.cpp" >}}
## **Send Email Messages via EWS**

You can send emails through Exchange by calling the [IEWSClient->Send()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a02875ffd55c4033e7d88007a9ac2a83c) method. It takes a [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) object and submits it directly through the server using EWS.

The following code sample demonstrates how to send an HTML email message through an Exchange Server using Exchange Web Services (EWS) with Aspose.Email for C++. It shows the complete process of establishing a connection to Exchange, creating a mail message with sender, recipient, subject, and HTML content, and then sending the message using the EWS client's Send method.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailMessagesUsingExchangeWebServices-SendEmailMessagesUsingExchangeWebServices.cpp" >}}
## **Reading Emails from Other User’s Mailbox**
Some accounts on Exchange Servers have the right to access multiple mailboxes, and some users have multiple email accounts on the same Exchange Server. In both cases, users can access other users' mailboxes with Aspose.Email. The API provides a mechanism for accessing folders and emails from other mailboxes using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class. This functionality can be achieved using the overloaded [GetMailboxInfo()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ac95e7c7a5e8678b70b4f5c4356d88582) method and providing the user email address as a parameter.

The following code snippet shows you how to read emails using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) class.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AccessAnotherMailboxUsingExchangeWebServiceClient-1.cpp" >}}
## **List Messages Using EWS**

Aspose.Email for C++ allows you to retrieve message metadata from Exchange Server mailboxes through the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Using the EWS-based [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) API, you can list messages from any folder, browse message metadata, and implement paging for large mailboxes.


### **List Messages from the Inbox**

Use [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) to retrieve basic message information such as subject, sender, recipients, and message ID from the Inbox or any folder.

The following code sample demonstrates how to list and display basic information for all messages in an Exchange Server.

1. Create an instance of [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
2. Call [ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) with the target folder URI.
3. Iterate through [ExchangeMessageInfoCollection](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection/).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesUsingEWS-ListingMessagesUsingEWS.cpp" >}}
### **List Messages from Any Folder**

[ListMessages](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) accepts any valid folder URI, allowing you to list items from Deleted Items, Drafts, Sent Items, or custom folders. Use the `IEWSClient->get_MailboxInfo->xxxFolderUri` property to get the URI of different folders.

The following code sample demonstrates how to access different Exchange Server folder URIs and retrieve messages from a specified folder.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ListingMessagesFromFolders-ListingMessagesFromFolders.cpp" >}}
### **Pagination in Message Listing**
For large mailboxes, use [ListMessagesByPage](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a50ea10548ed8e1b305bdeb322b8c109f) to load messages in smaller blocks.

The following code sample demonstrates how to implement pagination for retrieving large numbers of messages from an Exchange Server inbox.

1. First, it creates multiple test messages on the server.
2. Then, uses the [ListMessagesByPage](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a50ea10548ed8e1b305bdeb322b8c109f) method to retrieve messages in smaller batches (5 messages per page in this case), iterating through all pages until the last page is reached.
3. Finally, the code verifies that all messages were successfully retrieved by counting the total items across all pages.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingMessages-PagingSupportForListingMessages.cpp" >}}
### **Get Message Type Information**

Use [ExchangeMessageInfo->MessageInfoType](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info#ad0019f9e3e774fa0f763456f41028b91) to determine the underlying Exchange message type (e.g., email, meeting request, etc.).

The following code sample demonstrates how to connect to an Exchange Server and retrieve message type information from the Deleted Items folder.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetMessageTypeFromExchangeMessageInfo-GetMessageTypeFromExchangeMessageInfo.cpp" >}}

## **Save Messages Using Exchange Web Services (EWS)**

Aspose.Email enables you to **retrieve messages from an Exchange Server mailbox** and **save them in multiple formats**, such as EML, memory streams, and MSG. The examples below demonstrate how to fetch message information and store messages using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) API.

### **Save Messages as EML Files**

To save mailbox messages as EML files:

1. Create an [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) instance using valid credentials.
2. Call [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) to retrieve an [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection).
3. Loop through the collection to access each message unique URI.
4. Call [SaveMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a1a735b25973171ac5111c3469a54f7fa) to store each message on disk in EML format.

The following code sample demonstrates how to save email messages from an Exchange Server inbox as individual EML files locally using Aspose.Email for C++.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesUsingExchangeWebServices-SaveMessagesUsingExchangeWebServices.cpp" >}}

### **Save Messages to a Memory Stream**

Instead of writing to disk, you can save messages to a memory stream—useful for storing emails in a database or processing them in memory.

The following code sample demonstrates how to save email messages from an Exchange Server inbox into memory streams.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesToMemoryStreamUsingEWS-SaveMessagesToMemoryStream.cpp" >}}

### **Save Messages in MSG Format**

To save messages as MSG:

1. Retrieve the message using [FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905), which returns a [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message).
2. Call [MailMessage::Save()](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message#a41d3ada3ca8b7ca8130629b616f0b91c) with MSG save options.

The following code sample demonstrates how to fetch and save email messages from an Exchange Server inbox as Outlook MSG format files.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveMessagesInMSGFormatExchangeEWS-SaveMessagesInMSGFormatExchangeEWS.cpp" >}}

## **Retrieve Message Details by Message URI**

When only a message unique URI is available, you can still retrieve full [ExchangeMessageInfo](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info) objects. The [IEWSClient::ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2b3b4ebfdd9423eeb63d59b5e74cc53a) overload accepts a list of message IDs (URIs) and returns an [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_message_info_collection). Use this feature when you store or receive message URIs externally and need to load metadata (subject, sender, size, etc.) without fetching full messages.

The following code sample demonstrates how to create multiple email messages on an Exchange Server and then retrieve their message information using unique identifiers.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GetExchangeMessageInfoFromMessageURI-GetExchangeMessageInfoFromMessageURI.cpp" >}}

## **Fetch Full Message Content**

[ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#aad8420247acd17cb1d73303ed1982d1e) returns **summary information** (subject, sender, IDs). To load **full message content** — body, headers, attachments — use [FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905).

The following code sample demonstrates how to fetch complete messages from an Exchange Server inbox and extract attachment information:

1. Create an [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) instance.
2. Call [ListMessages()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a37cfefda7e1ab560a073b3e31f4d27ca) to get basic message metadata.
3. Extract each message UniqueUri.
4. Call [FetchMessage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#ae0edf4afafbe6339541687aeacc84905) to retrieve full message details.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchMessageUsingEWS-FetchMessageUsingEWS.cpp" >}}

## **Fetch Message Size (Without Downloading Full Message)**

Aspose.Email provides message size information without fetching the entire email, through the [ExchangeMessageInfo::Size](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.message_info_base#a04bc106203ed5cfec65f4d0320d14e8a) property.

This is useful for:

- mailbox statistics
- quota calculations
- filtering large messages before downloading

The following code sample demonstrates how to list and display message metadata including size from an Exchange Server inbox.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PreFetchMessageSizeUsingIEWSClient-PreFetchMessageSizeUsingIEWSClient.cpp" >}}

## **Download Emails from Exchange Public Folders**

Exchange public folders allow storing shared messages across users.

Aspose.Email [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) allows you to perform the following operations wih these folders and messages stored in them:

- List public folders
- Browse subfolders recursively 
- Download messages and save them (e.g., as MSG files)

>**Note:** Microsoft Exchange Server 2007 or later is required, as earlier versions do not support EWS.

The following code sample demonstrates how to download messages from all public folders and their subfolders on an Exchange Server recursively, and save them as Outlook MSG files locally.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DownloadMessagesFromPublicFolders-DownloadMessagesFromPublicFolders.cpp" >}}

## **Move Messages Between Exchange Folders**

You can move messages from one Exchange folder to another using the [IEWSClient::MoveItem](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a9fcc589e5315a803263cf528e084737a) method.
It requires:

- The unique URI of the message to move.
- The destination folder unique URI.

The following code sample demonstrates how to filter and move specific email messages from an Exchange Server inbox to another folder based on content criteria.

1. Connect to Exchange Server using EWS credentials.
2. Get mailbox information (folder URIs).
3. List all messages from the Inbox.
4. Iterate through each message.
5. Check if subject contains "process this message".
6. Move matching messages to Deleted Items folder.
7. Output confirmation for each moved message.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveMessageFromOneFolderToAnotherusingEWS-MoveMessageFromOneFolderToAnotherusingEWS.cpp" >}}

## **Delete Messages from an Exchange Folder**

You can delete email messages from a folder with the help of the [IEWSClient->DeleteMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a576fb78dcbac3bdb8b2bb87cab5d33c1) method. It takes the message's unique URI as a parameter.

The following code sample demonstrates how to filter and delete specific email messages from an Exchange Server inbox based on subject criteria.

1. Iterate through Inbox messages.
2. Process messages based on some criteria (in this example, we find a keyword in the message subject).
3. Delete matching messages.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMessagesFromUsingEWS-DeleteMessagesFromusingEWS.cpp" >}}

## **Copy Messages to Another Exchange Folder**

Use [IEWSClient::CopyItem](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a6e340250e1e0f51d68d4ffe7727f4e7f) to duplicate a message into a different folder.
The overloaded version returns the URI of the newly created copy.

The following code sample demonstrates how to create an email message on an Exchange Server and copy it to another folder.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyingMessageToAnotherFolder-CopyingMessageToAnotherFolder.cpp" >}}
