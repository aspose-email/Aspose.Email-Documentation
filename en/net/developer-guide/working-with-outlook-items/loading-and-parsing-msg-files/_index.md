---
title: Loading and Parsing MSG Files
ArticleTitle: Loading and Parsing MSG Files
type: docs
weight: 20
url: /net/loading-and-parsing-msg-files/
---

Using Aspose.Email for .NET, developers can load as well as parse contents from Outlook message files.

- To load MSG files from disk, use the static [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) method of the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class. The class provides several static loading functions for different scenarios.
- To parse MSG file contents, the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) exposes a number of methods and properties.

In this article you will learn how to load and parse an MSG file to display its contents. The code samples with steps will give you a clear understanding of how to implement the functionality of loading and parsing Outlook MSG files in your project. 

First, learn to load MSG files from file or from stream.

## **Load MSG Files**

The following code snippet shows you how to load MSG files.

```cs
// Create an instance of MapiMessage from file
var msg = MapiMessage.Load(@"message.msg");

// Get subject
Console.WriteLine("Subject:" + msg.Subject);

// Get from address
Console.WriteLine("From:" + msg.SenderEmailAddress);

// Get body
Console.WriteLine("Body" + msg.Body);

// Get recipients information
Console.WriteLine("Recipient: " + msg.Recipients);

// Get attachments
foreach (var att in msg.Attachments)
{
    Console.Write("Attachment Name: " + att.FileName);
    Console.Write("Attachment Display Name: " + att.DisplayName);
}
```

The following code example shows how to use MailMessage to load a message in MSG format.

```csharp

var eml = MailMessage.Load("message.msg");

```

It should be noted that a resulting message is converted to EML format, including embedded message attachments. Don't use this loading method if you want to preserve some specific msg format properties of the original message.

To preserve the original format of embedded message attachments, use the [msgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/) property.

```csharp

var msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.PreserveEmbeddedMessageFormat = true;
var msg = MailMessage.Load(stream, msgLoadOptions);

```

## **Load from Stream**

The following code snippet shows you how to load file from stream.

```cs
// Create an instance of MapiMessage from file
byte[] bytes = File.ReadAllBytes(@"message.msg");

using (MemoryStream stream = new MemoryStream(bytes))
{
    stream.Seek(0, SeekOrigin.Begin);
    // Create an instance of MapiMessage from file
    MapiMessage msg = MapiMessage.Load(stream);

    // Get subject
    Console.WriteLine("Subject:" + msg.Subject);

    // Get from address
    Console.WriteLine("From:" + msg.SenderEmailAddress);

    // Get body
    Console.WriteLine("Body" + msg.Body);

}
```

## **Convert EML to MSG While Preserving Embedded EML Format**

EML files can be loaded into [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class by instantiating a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object and passing it to [MapiMessage.FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) method. If the EML file contains embedded EML files, use [MapiConversionOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveembeddedmessageformat/) to retain the format of embedded EML files. The below code snippet shows how to load EML files into [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) while preserving the format of embedded EML files.

```cs
// Load the EML file into a MailMessage object
var mailMessage = MailMessage.Load(emlFilePath);

// Set conversion options to preserve the format of embedded EML messages
var options = new MapiConversionOptions
    {
        PreserveEmbeddedMessageFormat = true
    };

// Convert MailMessage to MapiMessage, preserving embedded EML files
var mapiMessage = MapiMessage.FromMailMessage(mailMessage, options);

// Save the converted message in MSG format
mapiMessage.Save(msgFilePath);
```

{{% alert %}}
**Try it out!**

Convert emails & message archives online with the free [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}

## **Parse Outlook Message Files**

Aspose.Email for .NET provides the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class that is used to open and parse an MSG file. As there may be many recipients in an MSG file, the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class exposes the [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) property that returns a [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) which represents a collection of [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) objects. The [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) object further exposes methods for working with recipient attributes.

The following sequence of steps serves this purpose:

1. Create an instance of the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class using the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) static method.
1. Display the sender name, subject, and body from the MSG file using [SenderName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/sendername/), [Subject](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/subject/) and [Body](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/body/) properties.
1. Use the [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) property to get a reference to the collection of [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) objects associated with the MSG file.
1. Loop through the [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) collection to display contents for each [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) object through its public methods.

```cs
//Instantiate an MSG file to load an MSG file from disk
var outlookMessageFile = MapiMessage.Load(dataDir + "message.msg");
//Display sender's name
Console.WriteLine("Sender Name : " + outlookMessageFile.SenderName);
//Display Subject
Console.WriteLine("Subject : " + outlookMessageFile.Subject);
//Display Body
Console.WriteLine("Body : " + outlookMessageFile.Body);
//Display Recipient's info
Console.WriteLine("Recipients : \n");

//Loop through the recipients collection associated with the MapiMessage object
foreach (var rcp in outlookMessageFile.Recipients)
{
	//Display recipient email address
	Console.WriteLine("Email : " + rcp.EmailAddress);
	//Display recipient name
	Console.WriteLine("Name : " + rcp.DisplayName);
	//Display recipient type
	Console.WriteLine("Recipient Type : " + rcp.RecipientType);
}
```

{{% alert %}}
**Try it out!**

Parse email files online with the free [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}
