---
title: Filter and Extract MBOX Messages with Aspose.Email in C#
ArticleTitle: Filtering and Extracting MBOX Messages
type: docs
weight: 20
url: /net/filter-extract-mbox-messages-csharp/
---


## **The Role of Message Filtering**

When working with large MBOX archives, loading every message into memory can be inefficient and unnecessary. In most scenarios, developers only need to scan basic metadata such as the subject, sender, recipient, or timestamp to:

- Display a list of messages in a UI
- Apply custom filters before extraction
- Generate reports or summaries
- Index messages for search

Filtering avoids the overhead of parsing full message bodies or attachments, making applications faster and more scalable.


## **Access Message Metadata**

Aspose.Email provides the [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class designed to access basic message metadata without reading the full MailMessage content. It acts as a summary object and is returned when calling [MboxStorageReader.EnumerateMessageInfo()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/#enumeratemessageinfo).

Key properties exposed by [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) to retrieve information about a message include:

- DateTime [Date](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/date/#mboxmessageinfodate-property) - Gets the date of message
- MailAddress [From](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/from/#mboxmessageinfofrom-property) - Gets the from address
- string [Subject](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/subject/) - Gets the message subject
- MailAddressCollection [To](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/to/) - Gets the address collection that contains the recipients of message
- MailAddressCollection [CC](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/cc/) - Gets the address collection that contains CC recipients
- MailAddressCollection [Bcc](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/bcc/) - Gets the address collection that contains BCC recipients of message

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader(fileName, new MboxLoadOptions());

foreach (var mboxMessageInfo in reader.EnumerateMessageInfo())
{
    Console.Writeline($"Subject: {mboxMessageInfo.Subject}");
    Console.Writeline($"Date: {mboxMessageInfo.Date}");
    Console.Writeline($"From: {mboxMessageInfo.From}");
    Console.Writeline($"To: {mboxMessageInfo.To}");
    Console.Writeline($"CC: {mboxMessageInfo.CC}");
    Console.Writeline($"Bcc: {mboxMessageInfo.Bcc}");
}
```

## **Extract Messages by EntryId**

The [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class includes the [EnumerateMessageInfo()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/) method, which enables you to iterate through each message in an MBOX file. By using this method, it becomes possible to extract individual messages without the need to traverse the entire storage repeatedly. This improves performance and reduces processing time.

The [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class provides the [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/entryid/) property, which provides access to unique identifiers for each message in the MBOX file. This identifier can be stored in a database or used as a reference to quickly find and extract specific messages when needed.

The [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) method in the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class enables developers to extract messages based on their unique EntryId. With the [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) method, you can leverage the stored EntryId to retrieve the corresponding message and perform additional operations with it.

The following code sample demonstrates how to extract messages from an MBOX file using identifiers:

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader("my.mbox", new MboxLoadOptions());

foreach (MboxMessageInfo msgInfo in reader.EnumerateMessageInfo())
{
    MailMessage eml = reader.ExtractMessage(msgInfo.EntryId, new EmlLoadOptions());
}
```

## **Filter and Search MBOX Emails Using MailQuery**

Aspose.Email for .NET provides the ability to filter or search messages within mailbox archives based on custom queries. This allows developers to retrieve only the messages that match specific criteria, improving performance and usability when working with large email archive files.

The following code sample demonstrates how to apply search criteria to a mail storage file with the MailQuery API. In this example, messages are selected if their subject includes the phrase "Project Update" and that were sent before today’s date. 

```cs
using Aspose.Email.Storage.Mbox;
using Aspose.Email;

var reader = MboxStorageReader.CreateReader("input.mbox", new MboxLoadOptions());
var mqb = new MailQueryBuilder();
mqb.Subject.Contains("Project Update");
mqb.SentDate.Before(DateTime.Today);

foreach (var message in reader.EnumerateMessages(mqb.GetQuery()))
{
    Console.WriteLine("Subject: " + message.Subject);
}
```


## **Configure Load Options when Reading Messages from MBOX** 

The following features will allow you to specify various options related to loading and processing messages:

- MailStorageConverter.MboxMessageOptions property - Gets or sets email load options when parsing an Mbox storage.

- MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options) method - EmlLoadOptions parameter specifies options when reading message from Mbox storage.

```cs
var reader = new MboxrdStorageReader(fileName, new MboxLoadOptions());
// Read messages preserving tnef attachments.
var eml = reader.ReadNextMessage(new EmlLoadOptions {PreserveTnefAttachments = true});
MailStorageConverter.MboxMessageOptions(new EmlLoadOptions {PreserveTnefAttachments = true});
// Convert messages from mbox to pst preserving tnef attachments.
var pst = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```

