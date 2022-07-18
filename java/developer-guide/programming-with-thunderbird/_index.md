---
title: Programming with Thunderbird
type: docs
weight: 100
url: /java/programming-with-thunderbird/
---

## **Reading Messages**
[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) is an open-source, cross-platform email client, developed by the Mozilla Foundation. It stores emails in its own file structure, managing messages indices and subfolders through proprietary file formats. Aspose.Email can work with Thunderbird mail storage structures. The [MboxrdStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) class lets developers read messages from Mozilla Thunderbird’s mail storage file. This article shows how to read the messages from Thunderbird email storage:

1. Open the Thunderbird’s storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) class and pass the above stream to the constructor.
1. Call [ReadNextMessage()](https://reference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) to get the first message.
1. Use the same [ReadNextMessage()](https://reference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) in a while loop to read all the messages.
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

## **Writing Messages**
The [MboxrdStorageWriter](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) class provides the facility to write new messages to Thunderbird’s mail storage file. To write messages:

1. Open the Thunderbird storage file in *FileStream*.
1. Create an instance of the [MboxrdStorageWriter](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) class and pass the above stream to the constructor.
1. Prepare a new message using the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) class.
1. Call the [WriteMessage()](https://reference.aspose.com/email/java/com.aspose.email/MboxrdStorageWriter#writeMessage\(com.aspose.email.MailMessage\)) method and pass the above [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) instance to add the message to Thunderbird storage.
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
The [MboxrdStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) class provides the capability to read the number of items available in an MBox file. This can be used to develop applications for showing the progress of activity while processing such a file.
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

## **Encoding option for MboxrdStorageReader class**
We can set preferred text encoding when loading Mbox files for reading:
~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
// Gets or sets a value indicating whether to keep the underlying stream open after disposing.
lo.setLeaveOpen(false);
// Gets or sets preferred encoding for messages.
lo.setPreferredTextEncoding(Charset.forName("utf-8"));
MboxrdStorageReader reader = new MboxrdStorageReader("sample.mbox", lo);
MailMessage message = reader.readNextMessage();
~~~