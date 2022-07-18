---
title: Fetch Messages from Exchange Server Mailbox using WebDav
type: docs
weight: 30
url: /java/fetch-messages-from-exchange-server-mailbox-using-webdav/
---

{{% alert color="primary" %}} 

Listing Messages on an Exchange Server used the [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method to get a list of messages from an Exchange Server mailbox. The [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method gets basic information about messages, for example, the subject, the message ID, from and to.

To get the complete message details, Aspose.Email.Exchange provides the [ExchangeClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) method. This method accepts the message URI as a parameter and returns an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) class. The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) class then provides message details like the body, headers, and attachments.

{{% /alert %}} 
## **Fetch Messages from an Exchange Server Mailbox**
To fetch messages from Exchange Server Mailbox:

1. Create an instance of type [ExchangeClient](https://reference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Specify the server name, user name, password, and domain.
1. Call the [listMessages](https://reference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) method to get the [ExchangeMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection).
1. Loop through the [ExchangeMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection) collection to get [ExchangeMessageInfo.getUniqueUri](https://reference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) values.
1. Call [ExchangeClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) and pass [ExchangeMessageInfo.getUniqueUri](https://reference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) as parameter.

The following code snippet connects to the Exchange Server mailbox and fetches all the messages.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-FetchMessagesFromAnExchangeServerMailbox-FetchMessagesFromAnExchangeServerMailbox.java" >}}
