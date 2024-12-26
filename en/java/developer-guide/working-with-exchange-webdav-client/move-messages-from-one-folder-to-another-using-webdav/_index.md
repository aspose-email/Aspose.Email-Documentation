---
title: Move Messages from One Folder to Another using WebDav
ArticleTitle: Move Messages from One Folder to Another using WebDav
type: docs
weight: 70
url: /java/move-messages-from-one-folder-to-another-using-webdav/
---

You can move email messages from one folder to another with the help of the [ExchangeClient.moveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#moveMessage\(com.aspose.email.ExchangeMessageInfo,%20java.lang.String\)) method. It takes the parameters:

- The unique URI of the message which is to be moved.
- The unique URI of the destination folder.
## **Move Messages between Folders**
The sample code below that moves a message in a mailbox from the Inbox folder to a folder called Processed. In this example, the application:

1. Reads messages from the Inbox folder.
1. Processes some of the messages based on some criteria (in this example, we find a keyword in the message subject).
1. Moves messages which fulfill the given condition to the Processed folder.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-MoveMessageFromOneFolderToAnother-MoveMessagesBetweenFolders.java" >}}
