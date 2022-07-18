---
title: Parsing Outlook Message Files
type: docs
weight: 40
url: /net/parsing-outlook-message-files/
---

{{% alert color="primary" %}} 

Using Aspose.Email for .NET, developers can not only load but also parse contents from Outlook message files.

- To load MSG files from disk, use the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) class' static [MapiMessage.FromFile](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/methods/fromfile) method.
- To parse MSG file contents, the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) exposes a number of methods and properties.

This topic shows how to loaded and then parsed and MSG file to display its contents.

{{% /alert %}} 

Aspose.Email for .NET provides the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) class that is used to open and parse an MSG file. As there may be many recipients in an MSG file, the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) class exposes the [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/recipients) property that returns a [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection) which represents a collection of [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient) objects. The [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient) object further exposes methods for working with recipient attributes.

The following sequence of steps serves this purpose:

1. Create an instance of the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage) class using the [MapiMessage.FromFile](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/methods/fromfile) static method.
1. Display the sender name, subject, and body from the MSG file using [SenderName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/properties/sendername), [Subject](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/subject) and [Body](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/properties/body) properties.
1. Use the [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/recipients) property to get a reference to the collection of [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient) objects associated with the MSG file.
1. Loop through the [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection) collection to display contents for each [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient) object through its public methods.

```cs
// The path to the resource directory.
string dataDir = RunExamples.GetDataDir_Email();

//Instantiate an MSG file to load an MSG file from disk
var outlookMessageFile = MapiMessage.FromFile(dataDir + "message.msg");
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
