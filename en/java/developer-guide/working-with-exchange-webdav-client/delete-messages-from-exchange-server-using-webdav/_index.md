---
title: Delete Messages from Exchange Server using WebDav
ArticleTitle: Delete Messages from Exchange Server using WebDav
type: docs
weight: 20
url: /java/delete-messages-from-exchange-server-using-webdav/
---

You can delete email messages from a folder with the help of the [ExchangeClient.deleteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#deleteMessage\(java.lang.String\)) method. It takes the message's unique URI as a parameter.

The sample code below deletes a message from the Inbox folder. For the purpose of this example, the code:

1. Reads messages from the Inbox folder.
1. Process messages based on some criteria (in this example, we find a keyword in the message subject).
1. Delete the message.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.java" >}}
