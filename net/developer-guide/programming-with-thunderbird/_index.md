---
title: Programming with Thunderbird
type: docs
weight: 110
url: /net/programming-with-thunderbird/
---


## **Reading Messages**
[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) is an open-source, cross-platform email client, developed by the Mozilla Foundation. It stores emails in its own file structure, managing messages indices and subfolders through proprietary file formats. Aspose.Email can work with Thunderbird mail storage structures. The [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader) class lets developers read messages from Mozilla Thunderbird’s mail storage file. This article shows how to read the messages from Thunderbird email storage:

1. Open the Thunderbird’s storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader) class and pass the above stream to the constructor.
1. Call [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/methods/readnextmessage/index) to get the first message.
1. Use the same [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/methods/readnextmessage/index) in a while loop to read all the messages.
1. Close all the streams.

The following code snippet shows you how to read all the messages from a Thunderbird mail storage.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.cs" >}}
## **Writing Messages**
The [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter) class provides the facility to write new messages to Thunderbird’s mail storage file. To write messages:

1. Open the Thunderbird storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter) class and pass the above stream to the constructor.
1. Prepare a new message using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class.
1. Call the [WriteMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/methods/writemessage/index) method and pass the above [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) instance to add the message to Thunderbird storage.
1. Close all streams.

The following code snippet shows you how to writes messages to Thunderbird’s mail storage.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Thunderbird-CreateNewMessagesToThunderbird-WritingNewMessagesToThunderbird.cs" >}}
## **Getting Total Number of Messages from MBox File**
The [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader) class provides the capability to read the number of items available in an MBox file. This can be used to develop applications for showing the progress of activity while processing such a file.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.cs" >}}
## **Get Current Message Size**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.cs" >}}
