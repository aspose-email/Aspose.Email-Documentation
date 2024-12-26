---
title: Working with MAPI Properties
ArticleTitle: Working with MAPI Properties
type: docs
weight: 70
url: /net/working-with-mapi-properties/
---


## **Accessing and Setting Outlook MAPI Property**

The [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) class represents a MAPI property, which contains:

- [Name](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/name/): a string that represents the name property.
- [Tag](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/tag/): a long type value that represents the tag property .
- [Data](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/data/): a byte array which represents the data property.
  
### **Get MAPI Properties Using Property Tags**

To get MAPI properties:

1. Create an instance of [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) by [loading from files or stream](https://docs.aspose.com/email/net/loading-viewing-and-parsing-msg-file/#loading-from-stream).
2. Get the [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) from [MapiMessage.Properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) by [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/) keys.

The following code snippet shows you how to get MAPI property using the MAPI property tag.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-GetMAPIProperty-GetMAPIProperty.cs" >}}

### **Set MAPI Properties**

The following code snippet shows you how to set MAPI properties.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-SetMAPIProperties.cs" >}}

where the definition of convertDateTime method is as follows:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-ConvertDateTime.cs" >}}

### **Additional Properties**

The following code snippet shows you how to set additional MAPI properties.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetAdditionalMAPIProperties-SetAdditionalMAPIProperties.cs" >}}
  
### **Read Named MAPI Properties from MSG Files**

The following code snippet shows you how to read named MAPI properties from the MSG file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cs" >}}

### **Read Named MAPI Properties from Attachments**

Aspose.Email also allows you to traverse through the properties of a [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) and search for a named property, in a way similar to the example above, for [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). The following code snippet shows you how to search for a named property through the attachment property collection.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cs" >}}

### **Remove Properties from MSGs and Attachments**

The following code snippet shows you how to remove properties from MSGs and attachments.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cs" >}}
