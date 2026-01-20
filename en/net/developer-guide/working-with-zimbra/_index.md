---
title: Read and Export Zimbra TGZ Files in Node.js via .NET
ArticleTitle: Read and Export Zimbra TGZ Files 
type: docs
weight: 120
url: /nodejs-net/read-export-zimbra-tgz-files/
---


**Zimbra** is a cloud-based email and collaboration suite that provides email, contacts, calendars, file sharing, tasks, and messaging - all accessible through the Zimbra Web Client on any device.

**Aspose.Email for Node.js via .NET** enables developers to read, extract, and export data from Zimbra TGZ backup files using the [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/) class. You can easily access all messages, count total items, and export messages, contacts, or calendar data from TGZ files to common formats.

## **Read All Messages from a Zimbra TGZ File**

The [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/) class allows you to read all messages stored in a Zimbra TGZ backup file.

The following example demonstrates how to iterate through all messages and display their folder location and subject.

```javascript
const asposeemail = require('@aspose/email');
const fs = require('fs');

// Path to the Zimbra TGZ file
const tgzPath = "ZimbraSample.tgz";

// Create a TgzReader instance
const reader = new asposeemail.TgzReader(tgzPath);

// Read and display all messages
while (reader.readNextMessage()) {
    const directoryName = reader.currentDirectory;
    console.log("Directory:", directoryName);

    const message = reader.currentMessage;
    console.log("Subject:", message.subject);
}

reader.dispose();
console.log("All messages read successfully from the Zimbra TGZ file.");
```

## **Count Total Items in a Zimbra TGZ File**

You can quickly determine how many email items exist in a TGZ backup using the [getTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/#tgzreadergettotalitemscount-method) method of the [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) class.

The following code sample will show you how to implement this method in your project:

```javascript
const asposeemail = require('@aspose/email');

const tgzFile = "ZimbraSample.tgz";
const reader = new asposeemail.TgzReader(tgzFile);

const totalCount = reader.getTotalItemsCount();
console.log(`Total items in TGZ file: ${totalCount}`);

reader.dispose();
```

## **Save Messages and Folder Structure from a Zimbra TGZ File**

The [exportTo()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/exportto/) method allows you to save all messages from a TGZ file while preserving the original folder structure. This is useful when restoring or migrating mailbox data.

The following code sample demonstrates how to extract and export all Zimbra email messages from a TGZ archive file using the Aspose.Email library.

```javascript
const asposeemail = require('@aspose/email');

const tgzFile = "ZimbraSample.tgz";
const outputDir = "Output/Zimbra/";

const reader = new asposeemail.TgzReader(tgzFile);
reader.exportTo(outputDir);

reader.dispose();
console.log(`All Zimbra messages exported to: ${outputDir}`);
```

## **Export Calendar and Contacts from Zimbra Backup Files**

Zimbra TGZ backups may include contact and calendar folders. You can export these to VCard (.vcf) and iCalendar (.ics) formats using the same [exportTo()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/exportto/) method.

```javascript
const asposeemail = require('@aspose/email');

const tgzFile = "ZimbraBackup.tgz";
const outputPath = "Output/ZimbraData/";

const reader = new asposeemail.TgzReader(tgzFile);

// Contacts can be found in "Contacts" and "Emailed Contacts" folders.
// Calendar entries can be found in the "Calendar" folder.
reader.exportTo(outputPath);

reader.dispose();
console.log("Zimbra calendar and contacts exported successfully.");
```


