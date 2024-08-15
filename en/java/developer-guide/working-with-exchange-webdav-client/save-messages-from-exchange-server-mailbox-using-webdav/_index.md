---
title: Save Messages from Exchange Server Mailbox using WebDav
type: docs
weight: 90
url: /java/save-messages-from-exchange-server-mailbox-using-webdav/
---

This article shows how to get messages from an Exchange Server mailbox and save them to disk in EML and MSG formats.
## **Save Messages from an Exchange Server Mailbox to EML**
To get messages and save in EML format:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Provide the server name, username, password, and domain.
1. Call the [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method to get an instance of the [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) collection.
1. Loop through the [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) collection to get the unique URI for each message.
1. Call the [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) method and pass the unique URI as a parameter.
1. Provide a [saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) method with a path to where you want to save the file.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesAsEML.java" >}}
## **Save Messages to an OutputStream**
Instead of saving EML files to disk, it is possible to save it to an OutputStream. This is useful when you want to save the stream to some storage location like a database. Once the stream has been saved to a database, you can reload the EML file into the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class.

The code snippets below save messages from an Exchange Server mailbox to a memory stream.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesToOutputStream.java" >}}
## **Save Messages in MSG Format**
The [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) method can directly save the message to EML format. To save the messages to MSG format, first, call the [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) method which returns an instance of the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class. Then call the [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.io.OutputStream\)) method to save the message to MSG.

The code snippet below gets messages from an Exchange Server mailbox and saves them to MSG format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesInMSGFormat.java" >}}
