---
title: Loading, Viewing and Parsing MSG file
type: docs
weight: 20
url: /net/loading-viewing-and-parsing-msg-file/
---


This topic explains how to load a Microsoft Outlook Message file (*.msg). The [MapiMessage](https://apireference.aspose.com/net/email/aspose.email.mapi/mapimessage) class is used to load MSG files and provides several static loading functions for different scenarios. The following code snippet shows you how to load MSG files from file or from stream.
## **Loading MSG Files**
The following code snippet shows you how to load MSG files.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadMSGFiles-LoadMSGFiles.cs" >}}

The following code example shows how to use MailMessage to load a message in MSG format.

```csharp

MailMessage eml = MailMessage.Load("message.msg");

```

It should be noted that a resulting message is converted to EML format, including embedded message attachments. Don't use this loading method if you want to preserve some specific msg format properties of the original message.

To preserve the original format of embedded message attachments, use the [msgLoadOptions.PreserveEmbeddedMessageFormat](https://apireference.aspose.com/email/net/aspose.email/loadoptions/properties/preserveembeddedmessageformat) property.

```csharp

MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.PreserveEmbeddedMessageFormat = true;
var msg = MailMessage.Load(stream, msgLoadOptions);

```

## **Loading from Stream**
The following code snippet shows you how to load file from stream.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingFromStream-LoadingFromStream.cs" >}}

Converting EML to MSG preserving embedded EML format

EML files can be loaded into [MapiMessage](https://apireference.aspose.com/net/email/aspose.email.mapi/mapimessage) class by instantiating a [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) object and passing it to [MapiMessage.FromMailMessage](https://apireference.aspose.com/net/email/aspose.email.mapi/mapimessage/methods/frommailmessage/index) method. If the EML file contains embedded EML files, use [MapiConversionOptions.PreserveEmbeddedMessageFormat](https://apireference.aspose.com/net/email/aspose.email.mapi/mapiconversionoptions/properties/preserveembeddedmessageformat) to retain the format of embedded EML files. The below code snippet shows how to load EML files into [MapiMessage](https://apireference.aspose.com/net/email/aspose.email.mapi/mapimessage) while preserving the format of embedded EML files.

{{% alert %}}
**Try it out!**

Convert emails & message archives online with the free [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}


{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}
