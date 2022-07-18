---
title: Parsing Outlook Message Files
type: docs
weight: 40
url: /java/parsing-outlook-message-files/
---

{{% alert color="primary" %}} 

Using Aspose.Email for Java, developers can not only load but also parse contents from Outlook message files.

- To load MSG files from disk, use the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) class' static [fromFile](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#fromFile\(java.lang.String\)) method.
- To parse MSG file contents, the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) exposes a number of methods.

This topic shows how to loaded and then parsed and MSG file to display its contents.

{{% /alert %}} 

Aspose.Email for Java provides the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) class that is used to open and parse an MSG file. As there may be many recipients in an MSG file, the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) class exposes the [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessageItemBase#getRecipients\(\)) method that returns a [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/MapiRecipientCollection) which represents a collection of [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/MapiRecipient) objects. The [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/MapiRecipient) object further exposes methods for working with recipient attributes.

The following sequence of steps serves this purpose:

1. Create an instance of the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) class to load an MSG file from the [fromFile](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#fromFile\(java.lang.String\)) static method.
1. Display the sender name, subject, and body from the MSG file using [getSenderName()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#getSenderName\(\)), [getSubject()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessageItemBase#getSubject\(\)) and [getBody()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#getBody\(\)) methods.
1. Call the [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessageItemBase#getRecipients\(\)) method exposed by the [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/MapiRecipient) class to get a reference to the collection of [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/MapiRecipient) objects associated with the MSG file.
1. Loop through the [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/MapiRecipientCollection) collection to display contents for each [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/MapiRecipient) object through its public methods.



```java
// The path to the resource directory.
String dataDir = Utils.getSharedDataDir(ParsingOutlookMessageFiles.class) + "outlook/";

//Instantiate an MSG file to load an MSG file from disk
MapiMessage outlookMessageFile = MapiMessage.fromFile(dataDir + "message.msg");
//Display sender's name
System.out.println("Sender Name : " + outlookMessageFile.getSenderName());
//Display Subject
System.out.println("Subject : " + outlookMessageFile.getSubject());
//Display Body
System.out.println("Body : " + outlookMessageFile.getBody());
//Display Recipient's info
System.out.println("Recipients : \n");

//Loop through the recipients collection associated with the MapiMessage object
for (int i = 0; i < outlookMessageFile.getRecipients().size(); i++) {
	//Set a reference to the MapiRecipient object
	MapiRecipient rcp = (MapiRecipient) outlookMessageFile.getRecipients().get_Item(i);
	//Display recipient email address
	System.out.println("Email : " + rcp.getEmailAddress());
	//Display recipient name
	System.out.println("Name : " + rcp.getDisplayName());
	//Display recipient type
	System.out.println("Recipient Type : " + rcp.getRecipientType());
}
```

{{% alert %}}
**Try it out!**

Parse email files online with the free [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}
