---
title: Write MBOX Files with Aspose.Email in C#
ArticleTitle: Writing MBOX Files
type: docs
weight: 30
url: /net/writing-mbox-files-csharp/
---



## **Write MBOX Files**

If you need to create or update MBOX files programmatically, use Aspose.Email [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) class which allows you to write new messages to Thunderbird mail storage file.

The following code snippet shows you how to write messages to Thunderbird mail storage:  

1. Open the Thunderbird storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) class and pass the above stream to the constructor.
1. Prepare a new message using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Call the [WriteMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage/) method and pass the above [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance to add the message to Thunderbird storage.
1. Close all streams.



```cs
// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Write);

// Initialize MboxStorageWriter and pass the above stream to it
var writer = new MboxrdStorageWriter(stream, false);
// Prepare a new message using the MailMessage class
var message = new MailMessage("from@domain.com", "to@domain.com", Guid.NewGuid().ToString(), "added from Aspose.Email");
message.IsDraft = false;
// Add this message to storage
writer.WriteMessage(message);
// Close all related streams
writer.Dispose();
stream.Close();
```

