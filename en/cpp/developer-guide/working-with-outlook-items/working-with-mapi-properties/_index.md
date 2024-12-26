---
title: Working with MAPI Properties using Email C++ Library
ArticleTitle: Working with MAPI Properties using Email C++ Library
linktitle: Working with MAPI Properties
type: docs
weight: 60
url: /cpp/working-with-mapi-properties/
description: Using C++ Email Library API, you can access and set Outlook MAPI properties and read Named MAPI Properties from MSG file. 
---

## **Accessing and Setting Outlook MAPI Property**
The MapiProperty class represents a MAPI property, which contains:

- Name: a string that represents the property's name.
- Tag: a long that represents the property's tag.
- Data: a byte array which represents the property's data.

### **Getting MAPI Property using the MAPI Property Tag**
To get MAPI properties:

1. Create an instance of MapiMessage by loading from files or stream.
1. Get the MapiProperty from MapiMessage.Properties by MapiPropertyTag keys.
1. Get the Data of the MapiProperty by method GetX.

The following code snippet shows you how to get MAPI property using the MAPI property tag with C++ Email Parser Library.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-GetMAPIProperty-GetMAPIProperty.cpp" >}}

### **Setting MAPI Properties**
The following code snippet shows you how to set MAPI properties.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetMAPIProperties-SetMAPIProperties.cpp" >}}

where the definition of convertDateTime method is as follow:

``` java

 int64_t filetime = t.ToFileTime();

System::ArrayPtr<uint8_t> d = System::MakeArray<uint8_t>(8, 0);

d[0] = (uint8_t)(filetime & 0xFF);

d[1] = (uint8_t)((filetime & 0xFF00) >> 8);

d[2] = (uint8_t)((filetime & 0xFF0000) >> 16);

d[3] = (uint8_t)((filetime & 0xFF000000) >> 24);

d[4] = (uint8_t)((filetime & 0xFF00000000) >> 32);

d[5] = (uint8_t)((filetime & 0xFF0000000000) >> 40);

d[6] = (uint8_t)((filetime & 0xFF000000000000) >> 48);

d[7] = (uint8_t)(((uint64_t)filetime & 0xFF00000000000000) >> 56);

```

## **Reading Named MAPI Properties from Outlook MSG Files**
Microsoft Outlook supports adding named MAPI properties to an MSG file. These named MAPI properties are added by the user. You can add a named property, for example “MyProp”, to an MSG file using Aspose.Email. This article illustrates Aspose.Email's capabilities to:

- Read Name MAPI Properties from an Outlook MSG file
- Read Properties from Attachments
- Remove Properties from MSGs and Attachments

### **Read Named MAPI Properties from MSG file**
The following code snippet shows you how to read named MAPI properties from MSG file.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cpp" >}}

### **Reading Named MAPI Property from Attachment**
Aspose.Email also allows you to traverse through the properties of a MapiAttachment and search for a named property, in a way similar to the example above, for MapiMessage. The following code snippet shows you how to search for a named property through the attachment's property collection.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cpp" >}}

### **Remove Properties from MSGs and Attachments**
The following code snippet shows you how to remove properties from MSGs and attachments.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cpp" >}}
