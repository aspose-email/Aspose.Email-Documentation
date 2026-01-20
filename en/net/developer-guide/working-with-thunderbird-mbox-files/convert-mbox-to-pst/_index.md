---
title: Convert MBOX to PST with Aspose.Email in C#
ArticleTitle: Converting MBOX to PST
type: docs
weight: 40
url: /net/convert-mbox-to-pst-csharp/
---


## **Convert MBOX to PST. Basic Conversion**

When migrating mail data from clients like Mozilla Thunderbird to Microsoft Outlook, converting MBOX archives to the PST (Personal Storage Table) format is often required. The PST format is native to Outlook and Exchange and supports advanced features like folder structures and MAPI-based message handling.

Aspose.Email for .NET allows developers to manually transfer messages from MBOX files into Outlook-compatible storage with full control over the conversion process. Below is an example that demonstrates how to load messages from an MBOX archive and save them into a structured Outlook data file:

1. Initialize the MBOX reader using [MboxStorageReader.CreateReader()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2).
2. Generate a PST file using [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4).
3. Add a mail folder (e.g., “Inbox”) to the storage.
4. Loop through each message, convert it to a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), and insert it into the folder.


```cs
// Load the source file
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

// Create the destination Outlook data file
using (var personalStorage = PersonalStorage.Create(pstFilePath, FileFormatVersion.Unicode))
{
    // Add a folder to hold imported messages
    var folderInfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);

    // Process each message from the source file
    foreach (var eml in mbox.EnumerateMessages())
    {
        var msg = MapiMessage.FromMailMessage(eml);
        folderInfo.AddMessage(msg);
    }
}
```


## **Remove Digital Signatures During Conversion**

In some cases, digital signatures embedded in messages are not needed in the target file. To exclude them during the transfer, set the `RemoveSignature` property in the [MboxToPstConversionOptions](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/) to *true*.

The following code sample shows how to utilize this property:

```cs
var pstDataStream = new MemoryStream();
var personalStorage = PersonalStorage.Create(pstDataStream, FileFormatVersion.Unicode);
MailStorageConverter.MboxToPst(new MboxrdStorageReader(new FileStream(fileName, FileMode.Open, FileAccess.Read), new MboxLoadOptions()),
personalStorage,
    "Inbox",
new MboxToPstConversionOptions() { RemoveSignature = true });
```

