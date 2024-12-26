---
title: Listing Messages from Exchange Server using WebDav
ArticleTitle: Listing Messages from Exchange Server using WebDav
type: docs
weight: 60
url: /java/listing-messages-from-exchange-server-using-webdav/
---

A list of the email messages in an Exchange mailbox can be fetched by calling the [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method. Get the basic information about messages, such as subject, from, to and message ID, using the [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method.

This article shows how to connect to an Exchange Server and list the emails in a mailbox directly or using WebDav. It further shows how to list messages from different folders and how to list messages by ID.
## **List Exchange Server Messages**
To list the messages in an Exchange mailbox:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Call the [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method and create a message collection.
1. Loop through the collection and display message information.

The code snippet below connects to the Exchange mailbox and get the list of messages from the Inbox folder.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromInboxFolderOnExchangeServer.java" >}}
## **Listing Messages from Different Folders**
The above code snippets list all the messages in the Inbox folder. It is possible to get the list of messages from other folders as well. The [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method accepts a folder URI as a parameter. As long as the folder URI is valid, you can get the list of messages from that folder.

Use ExchangeClient.getMailboxInfo().xxxFolderUri[](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) property to get the URI of different folders. The rest of the code is the same as for getting a list of messages.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromOtherFoldersOnExchangeServer.java" >}}
