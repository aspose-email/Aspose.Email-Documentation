---
title: Programming with Thunderbird
ArticleTitle: Programming with Thunderbird
type: docs
weight: 100
url: /java/programming-with-thunderbird/
---

## **Read Messages from MBOX**
[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) is an open-source, cross-platform email client, developed by the Mozilla Foundation. It stores emails in its own file structure, managing messages indices and subfolders through proprietary file formats. Aspose.Email can work with Thunderbird mail storage structures. The [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) class lets developers read messages from Mozilla Thunderbird’s mail storage file. This article shows how to read the messages from Thunderbird email storage:

1. Open the Thunderbird’s storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) class and pass the above stream to the constructor.
1. Call [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) to get the first message.
1. Use the same [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) in a while loop to read all the messages.
1. Close all the streams.

The following code snippet shows you how to read all the messages from a Thunderbird mail storage.
~~~Java
//Getting Marker information while reading messages from Mbox storage file
try (FileInputStream stream = new FileInputStream(dataDir + "Outlook.pst")) {
    MboxLoadOptions lo = new MboxLoadOptions();
    lo.setLeaveOpen(false);
    try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
        MailMessage msg;
        String[] fromMarker = {null};
        while ((msg = reader.readNextMessage(/* out */fromMarker)) != null) {
            System.out.println(fromMarker[0]);
        }
    }
}
~~~

### **Configure Load Options when Reading Messages from MBOX**

Aspose.Email API allows the following manipulations with messages when reading them from an MBOX file:

**Convert Messages from MBOX to PST Preserving TNEF Attachments**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailStorageConverter.setMboxMessageOptions(emlLoadOptions);
// Convert messages from mbox to pst preserving tnef attachments.
PersonalStorage storage = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```
[MailStorageConverter.MboxMessageOptions()](https://reference.aspose.com/email/java/com.aspose.email/mailstorageconverter/) property - Gets or sets email load options when parsing an Mbox storage.

**Read Messages Preserving TNEF Attachments**

```java
MboxrdStorageReader reader = new MboxrdStorageReader("Input.mbox", new MboxLoadOptions());
// Read messages preserving tnef attachments.
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailMessage eml = reader.readNextMessage(emlLoadOptions);
```
[MboxrdStorageReader.readNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/emlloadoptions/#getPreserveTnefAttachments--) method - EmlLoadOptions parameter specifies options when reading a message from Mbox storage.

**Enumerate Messages Preserving TNEF Attachments**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
// Enumerate messages preserving tnef attachments.
for (MailMessage message : reader.enumerateMessages(emlLoadOptions)) {
    // do something
}
```
[MboxrdStorageReader.enumerateMessages(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader/#enumerateMessages--) method - Specifies EmlLoadOptions when reading a message from Mbox storage.

## **Extract Messages from MBOX by Identifiers**

Sometimes it is required to extract selected messages by identifiers. For example, your application stores identifiers in a database and extracts a message on demand. This is the efficient way to avoid traversing through the entire storage each time to find a specific message to extract. To implement this feature for MBOX files, Aspose.Email provides the following methods and classes:

- [MboxMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/) class with the [EntryId](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/#getEntryId--) property - Gets the entry identifier. 
- [enumerateMessageInfo()](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#enumerateMessageInfo--) method of the [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) class - Exposes the enumerator, which supports an iteration of messages in storage.
- [extractMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#extractMessage-java.lang.String-com.aspose.email.EmlLoadOptions-) method of the [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) class - Gets the message from MBOX.

The code sample below demonstrates how to extract messages from MBOX by identifiers:

```java
MboxStorageReader reader = MboxStorageReader.createReader("my.mbox", new MboxLoadOptions());

for (MboxMessageInfo msgInfo : reader.enumerateMessageInfo()) {
    MailMessage eml = reader.extractMessage(msgInfo.getEntryId(), new EmlLoadOptions());
}
```
**Note:** The message ID is unique within the storage file. IDs are created by Aspose.Email and cannot be used in other third-party MBOX processing libs or apps.

## **Writing Messages**
The [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) class provides the facility to write new messages to Thunderbird’s mail storage file. To write messages:

1. Open the Thunderbird storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) class and pass the above stream to the constructor.
1. Prepare a new message using the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) class.
1. Call the [WriteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageWriter#writeMessage\(com.aspose.email.MailMessage\)) method and pass the above [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) instance to add the message to Thunderbird storage.
1. Close all streams.

The following code snippet shows you how to writes messages to Thunderbird’s mail storage.
~~~Java
//Getting marker information while writing messages to Mbox storage file
try (FileOutputStream writeStream = new FileOutputStream(dataDir + "inbox")) {
    try (MboxrdStorageWriter writer = new MboxrdStorageWriter(writeStream, false)) {
        MailMessage msg = MailMessage.load(dataDir + "Message.msg");
        String[] fromMarker = {null};
        writer.writeMessage(msg, fromMarker);
        System.out.println(fromMarker[0]);
    }
}
~~~

## **Getting Total Number of Messages from MBox File**
The [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) class provides the capability to read the number of items available in an MBox file. This can be used to develop applications for showing the progress of activity while processing such a file.
~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader("inbox.dat", lo)) {
    System.out.println("Total number of messages in Mbox file: " + reader.getTotalItemsCount());
}
~~~

## **Get Current Message Size**
~~~Java
FileInputStream stream = new FileInputStream(dataDir + "ExampleMbox.mbox");
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
    MailMessage msg = null;
    while ((msg = reader.readNextMessage()) != null) {
        //returns the number of bytes read
        long currentDataSize = reader.getCurrentDataSize();
        System.out.println("Bytes read: " + currentDataSize);
    }
}
~~~

## **Set Preferred Text Encoding when Loading Mbox Files**

The [setPreferredTextEncoding(Charset value)](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/#setPreferredTextEncoding-java.nio.charset.Charset-) method of the [MboxLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/) class gets or sets preferred encoding for messages. Create a reader for the Mbox file with specified load options and your messages with the encoded content will be correctly read and processed. The following code sample shows how to implement this feature into a project:

~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
lo.setPreferredTextEncoding(Charset.forName("utf-8"));
MboxrdStorageReader reader = new MboxrdStorageReader("sample.mbox", lo);
MailMessage message = reader.readNextMessage();
~~~

## **Split Mbox Storage into Smaller Parts**

Aspose.Email provides the following components designed to have more control over Mbox storage processing, allowing you to split large files into manageable parts and implement custom actions during the process:

- [MboxStorageReader.SplitInto(long chunkSize, String outputPath)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#splitInto-long-java.lang.String-) method - Allows you to split Mbox storage into smaller parts, making it easier to manage and process large Mbox files.

MboxStorageReader.SplitInto(long chunkSize, String outputPath, String partFileNamePrefix) A variation of the previous method, this one also lets you specify a custom prefix for the split Mbox file names.

MboxStorageReader.setEmlCopyingEventHandler Event This event occurs before an email is copying to a new Mbox file. You can customize actions before emails are processed.

MboxStorageReader.setEmlCopiedEventHandler Event This event occurs after an email is copied to a new Mbox file. You can perform post-processing actions on emails.

MboxStorageReader.setMboxFileCreatedEventHandler Event This event occurs when a new Mbox file is created. You can handle this event to react to file creation.

MboxStorageReader.setMboxFileFilledEventHandler Event This event occurs when a new Mbox file is filled with emails. You can respond to the file being populated with emails.

NewStorageEventHandler(Object sender, NewStorageEventArgs e) Represents a delegate for handling events that occur after a new storage file is created or processed.

MimeItemCopyEventHandler(Object sender, MimeItemCopyEventArgs e) Represents a delegate for handling events related to the copying of Mime items, typically used in scenarios where a MailMessage object is copied from one storage to another.

NewStorageEventArgs Represents arguments used in events that are raised after a new storage file is created or after it is processed.

MimeItemCopyEventArgs Represents event arguments related to a copying of a MailMessage object from one storage to another, either before the copy begins or after it is complete.

The code sample below demonstrates how to interact with Mbox files, handle events related to these files, and perform operations like splitting the Mbox storage into smaller parts while keeping track of the message count and part count:

```java
messageCount = 0;
partCount = 0;

// Create an instance of MboxrdStorageReader
MboxLoadOptions lo = new MboxLoadOptions();
lo.setLeaveOpen(false);
MboxrdStorageReader mbox = new MboxrdStorageReader("my.mbox", lo);

// Subscribe to events
mbox.setMboxFileCreatedEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("New Mbox file created: " + e.getFileName());
        partCount++;
    }
});

mbox.setMboxFileFilledEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Mbox file filled with messages: " + e.getFileName());
    }
});

mbox.setEmlCopiedEventHandler(new MimeItemCopyEventHandler() {
    public void invoke(Object sender, MimeItemCopyEventArgs e) {
        System.out.println("Message added to new Mbox file. Subject: " + e.getItem().getSubject());
        messageCount++;
    }
});

// Split the Mbox storage into smaller parts
mbox.splitInto(10000000, testOutPath, "Prefix");

// Output the final messageCount and partCount
System.out.println("Total messages added: " + messageCount);
System.out.println("Total parts created: " + partCount);
```
