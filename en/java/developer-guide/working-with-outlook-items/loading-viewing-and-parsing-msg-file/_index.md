---
title: Loading, Viewing and Parsing MSG file
ArticleTitle: Loading, Viewing and Parsing MSG file
type: docs
weight: 20
url: /java/loading-viewing-and-parsing-msg-file/
---


This topic explains how to load a Microsoft Outlook Message file (*.msg). The [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class is used to load MSG files and provides several static loading functions for different scenarios. The following code snippet shows you how to load MSG files from a file or from a stream.

## **Loading MSG Files**

The following code snippet shows you how to load MSG files.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

// Create an instance of MapiMessage from file
MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Get subject
System.out.println("Subject:" + msg.getSubject());

// Get from address
System.out.println("From:" + msg.getSenderEmailAddress());

// Get body
System.out.println("Body" + msg.getBody());

// Get recipients information
System.out.println("Recipient: " + msg.getRecipients());

// Get attachments
for (MapiAttachment att : msg.getAttachments())
{
    System.out.println("Attachment Name: " + att.getFileName());
    System.out.println("Attachment Display Name: " + att.getDisplayName());
}
~~~

The following code example shows how to use **MailMessage** to load a message in MSG format.

```Java
MailMessage eml = MailMessage.load("message.msg");
```

It should be noted that a resulting message is converted to EML format, including embedded message attachments. Don't use this loading method if you want to preserve some specific msg format properties of the original message.

To preserve the original format of embedded message attachments, use the [MsgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/#getPreserveEmbeddedMessageFormat--) property.

```Java
MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.setPreserveEmbeddedMessageFormat(true);
MailMessage msg = MailMessage.load(stream, msgLoadOptions);
```

## **Loading From Stream**

The following code snippet shows you how to load a file from a stream.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of MapiMessage from file
try (FileInputStream stream = new FileInputStream(dataDir + "message.msg"))
{
    // Create an instance of MapiMessage from file
    MapiMessage msg = MapiMessage.fromStream(stream);

    // Get subject
    System.out.println("Subject:" + msg.getSubject());

    // Get from address
    System.out.println("From:" + msg.getSenderEmailAddress());

    // Get body
    System.out.println("Body" + msg.getBody());

}
~~~

## **Converting EML to MSG Preserving Embedded EML Format**

EML files can be loaded into [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class by instantiating a [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody()) object and passing it to [MapiMessage.fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-java.lang.String-) method. If the EML file contains embedded EML files, use [MapiConversionOptions.setPreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmbeddedMessageFormat-boolean-) to retain the format of embedded EML files. The below code snippet shows how to load EML files into [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) while preserving the format of embedded EML files.

{{% alert %}}
**Try it out!**

Convert emails & message archives online with the free [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Email();

MailMessage eml = MailMessage.load(dataDir + "sample.eml", new EmlLoadOptions());

MapiConversionOptions options = MapiConversionOptions.getUnicodeFormat();

//Preserve Embedded Message Format
options.setPreserveEmbeddedMessageFormat(true);

//Convert EML to MSG with Options
MapiMessage msg = MapiMessage.fromMailMessage(eml, options);
~~~
