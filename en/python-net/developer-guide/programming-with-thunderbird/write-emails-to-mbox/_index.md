---
title: Write Messages to Thunderbird MBOX Files with Aspose.Email
ArticleTitle: Writing Messages to Thunderbird MBOX Files
type: docs
weight: 20
url: /python-net/write-messages-to-thunderbird-mbox-files-python/
---


If you need to programmatically add new messages to a Thunderbird mail storage file, Aspose.Email provides the [MboxrdStorageWriter](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxrdstoragewriter/) class to simplify this task. This class allows you to write messages to an existing MBOX file.

The steps below outline how to use the [MboxrdStorageWriter](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxrdstoragewriter/) along with the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class to create and store messages in Thunderbird’s mail format. A code sample is also provided to demonstrate the process.

1. Open the Thunderbird storage file in FileStream.
1. Create an instance of the [MboxrdStorageWriter](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxrdstoragewriter/) class and pass the above stream to the constructor.
1. Prepare a new message using the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class.
1. Call the `write_message()` method and pass the above [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) instance to add the message to Thunderbird storage.
1. Close all streams.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-CreateNewMessagesToThunderbird-CreateNewMessagesToThunderbird.py" >}}

