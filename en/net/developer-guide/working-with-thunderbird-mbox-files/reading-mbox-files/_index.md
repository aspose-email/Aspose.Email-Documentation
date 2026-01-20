---
title: Read MBOX Files with Aspose.Email in C#
ArticleTitle: Reading MBOX Files
type: docs
weight: 10
url: /net/read-mbox-files-csharp/
---


## **Aspose.Email Reading Capabilities**

[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) is an open-source, cross-platform email client, developed by the Mozilla Foundation. It stores emails in its own file structure, managing messages indices and subfolders through proprietary file formats. Thunderbird creates one .mbox file for each email folder (e.g., Inbox, Sent, Trash), and stores these files in the user’s profile directory. Each file contains all messages from that folder in a concatenated form.

Aspose.Email for .NET provides APIs for reading messages from Thunderbird .mbox files using the [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) class which allows developers to:

- Open and read messages sequentially, one by one
- Retrieve metadata like Subject, From, To, Date, etc., without loading full content
- Extract individual messages using unique identifiers (EntryId)
- Preserve encoding, TNEF attachments, and formatting
- Read files asynchronously for better performance on large archives


## **Read MBOX Files Synchronously** 

read messages from Mozilla Thunderbird mail storage file. This article shows how to read the messages from Thunderbird email storage:

1. Open the Thunderbird storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) class and pass the above stream to the constructor.
1. Call [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) to get the first message.
1. Use the same [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) in a while loop to read all the messages.
1. Close all the streams.

The following code snippet shows you how to read all the messages from a Thunderbird mail storage.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read);
// Create an instance of the MboxrdStorageReader class and pass the stream
var reader = new MboxrdStorageReader(stream, false);
// Start reading messages
var message = reader.ReadNextMessage();

// Read all messages in a loop
while (message != null)
{
    // Manipulate message - show contents
    Console.WriteLine("Subject: " + message.Subject);
    // Save this message in EML or MSG format
    message.Save(message.Subject + ".eml", SaveOptions.DefaultEml);
    message.Save(message.Subject + ".msg", SaveOptions.DefaultMsgUnicode);

    // Get the next message
    message = reader.ReadNextMessage();
}

// Close the streams
reader.Dispose();
stream.Close();
```

## **Read MBOX Files Asynchronously**

To enhance performance and responsiveness when processing large MBOX files, Aspose.Email for .NET provides asynchronous MBOX reading through the [CreateReaderAsync](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#methods) method. This feature is especially useful in applications that handle large email archives or run I/O-bound operations in background threads or web services. The following code sample demonstrates how to read email messages from an MBOX file asynchronously using an Aspose.Email storage reader:

```cs
string mboxFilePath = "emails.mbox";

    // Create a reader for the MBOX file asynchronously
    using (var reader = await MboxrdStorageReader.CreateReaderAsync(mboxFilePath, CancellationToken.None))
    {
    Console.WriteLine("MBOX reader initialized.");

    // Read messages from the MBOX file
        while (reader.ReadNextMessage() is var message && message != null)
        {
            Console.WriteLine($"Subject: {message.Subject}");
        }
    }
```

## **Read Email Messages in Batches with Pagination Support**

Get paginated access to messages stored in mailbox files. This feature enables developers to process large email archives more efficiently by retrieving messages in smaller portions - improving performance and reducing memory load. Use the following methods of the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class:

- [EnumerateMessages(int startIndex, int count)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages_5) - Returns an enumerable collection of MailMessage instances, starting from the specified index and limited by the given count.

- [EnumerateMessageInfo(int startIndex, int count)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/#enumeratemessageinfo_2) - Returns an enumerable collection of MboxMessageInfo objects with metadata only, also paged by index and count.

The code sample below demonstrates how to read a specific range of messages from a mail archive by defining a starting index and batch size. In the example, the method retrieves 10 messages starting from index 0.

```cs
using Aspose.Email.Storage.Mbox;
using Aspose.Email;

var reader = MboxStorageReader.CreateReader("input.mbox", new MboxLoadOptions());
int startIndex = 0;
int count = 10; // Retrieve messages in batches of 10

foreach (var message in reader.EnumerateMessages(startIndex, count))
{
    Console.WriteLine("Subject: " + message.Subject);
}
```


## **Set Preferred Text Encoding when Loading MBOX Files for Reading**

Encoding option is available for [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) class. This provides additional options for loading the mbox file and ensures that messages with the encoded content will be correctly read and processed. The following code snippet shows how you can set text encoding that satisfies your needs:

```cs
var reader = new MboxrdStorageReader("sample.mbox", new MboxLoadOptions() { PreferredTextEncoding = Encoding.UTF8});
var message = reader.ReadNextMessage();
```

## **Get Total Number of Messages from MBOX Files**

The [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) class provides the capability to read the number of items available in an MBox file. This can be used to develop applications for showing the progress of activity while processing such a file.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    Console.WriteLine("Total number of messages in Mbox file: " + reader.GetTotalItemsCount());
}
```

## **Get Current Message Size**

```cs
using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    MailMessage msg;
    while ((msg = reader.ReadNextMessage()) != null)
    {
        long currentDataSize = reader.CurrentDataSize;

        msg.Dispose();
    }
}
```

