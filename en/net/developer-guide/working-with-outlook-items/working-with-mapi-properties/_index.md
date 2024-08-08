---
title: Working with MAPI Properties
type: docs
weight: 70
url: /net/working-with-mapi-properties/
---


## **Accessing and Setting Outlook MAPI Property**

The [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) class represents a MAPI property, which contains:

- [Name](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/name/): a string that represents the name property.
- [Tag](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/tag/): a long type value that represents the tag property .
- [Data](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/data/): a byte array which represents the data property.
  
### **Getting MAPI Property using the MAPI Property Tag**

To get MAPI properties:

1. Create an instance of [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) by [loading from files or stream](https://docs.aspose.com/email/net/loading-viewing-and-parsing-msg-file/#loading-from-stream).
2. Get the [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) from [MapiMessage.Properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) by [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/) keys.

The following code snippet shows you how to get MAPI property using the MAPI property tag.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-GetMAPIProperty-GetMAPIProperty.cs" >}}

### **Setting MAPI Properties**

The following code snippet shows you how to set MAPI properties.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-SetMAPIProperties.cs" >}}

where the definition of convertDateTime method is as follows:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-ConvertDateTime.cs" >}}

### **Some Additional Properties**

The following code snippet shows you how to set additional MAPI properties.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetAdditionalMAPIProperties-SetAdditionalMAPIProperties.cs" >}}

## **Reading Named MAPI Properties from Outlook MSG Files**

Microsoft Outlook supports adding named MAPI properties to an MSG file. These named MAPI properties are added by the user. You can add a named property, for example, “MyProp”, to an MSG file using Aspose.Email. This article illustrates Aspose.Email's capabilities to:

- [**Accessing and Setting Outlook MAPI Property**](#accessing-and-setting-outlook-mapi-property)
  - [**Getting MAPI Property using the MAPI Property Tag**](#getting-mapi-property-using-the-mapi-property-tag)
  - [**Setting MAPI Properties**](#setting-mapi-properties)
  - [**Some Additional Properties**](#some-additional-properties)
- [**Reading Named MAPI Properties from Outlook MSG Files**](#reading-named-mapi-properties-from-outlook-msg-files)
  - [**Read Named MAPI Properties from MSG file**](#read-named-mapi-properties-from-msg-file)
  - [**Reading Named MAPI Property from Attachment**](#reading-named-mapi-property-from-attachment)
  - [**Remove Properties from MSGs and Attachments**](#remove-properties-from-msgs-and-attachments)
  
### **Read Named MAPI Properties from MSG file**

The following code snippet shows you how to read named MAPI properties from the MSG file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cs" >}}

### **Reading Named MAPI Property from Attachment**

Aspose.Email also allows you to traverse through the properties of a [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) and search for a named property, in a way similar to the example above, for [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). The following code snippet shows you how to search for a named property through the attachment property collection.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cs" >}}

### **Remove Properties from MSGs and Attachments**

The following code snippet shows you how to remove properties from MSGs and attachments.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cs" >}}
