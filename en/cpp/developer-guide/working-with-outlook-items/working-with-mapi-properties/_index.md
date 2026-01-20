---
title: Access and Manage Outlook MAPI Properties in C++
ArticleTitle: Access and Manage Outlook MAPI Properties 
linktitle: Working with MAPI Properties
type: docs
weight: 60
url: /cpp/working-with-mapi-properties/
description: Learn how to read, set, and remove MAPI properties in Outlook MSG files and attachments using Aspose.Email for C++. 
---

**MAPI properties** are metadata items used in Microsoft Outlook messages, defining attributes such as sender, recipient, subject, attachments, and custom data. 

**Aspose.Email for C++** allows developers to access, modify, and remove these properties programmatically in [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) objects, attachments, and named properties.

The [MapiProperty](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_property/) class represents a MAPI property, which contains:

- **Name** – The property’s string identifier.
- **Tag** – A numeric identifier used to reference the property.
- **Data** – A byte array representing the property’s value.

## **Read MAPI Properties**

Aspose.Email allows you to read MAPI properties using property tags.

The following code sample demonstrates how to read and display the subject property from a MAPI message file (.msg).

1. Get the directory path where the Outlook message files are stored.
2. Load the Outlook message file ("message.msg") into a [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) object.
3. Access the collection of MAPI properties from the message.
4. Try to retrieve the subject property using `PR_SUBJECT (ANSI)` tag.
5. If the ANSI subject property is not found, try to retrieve the Unicode subject property using `PR_SUBJECT_W`.
6. If the subject property exists, output its string value to the console.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-GetMAPIProperty-GetMAPIProperty.cpp" >}}

## **Set MAPI Properties**

MAPI properties can be set for messages or recipients to define custom attributes, email type, or synchronization status.

The following code sample demonstrates how to create a MAPI message, set multiple custom MAPI properties including sender and recipient details, message flags, and modification time, then save the message to a file.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetMAPIProperties-SetMAPIProperties.cpp" >}}

>**Note:** The ConvertDateTime() helper converts System::DateTime to a MAPI-compatible filetime byte array for date/time properties in the following way:

```cpp
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

## **Read Named MAPI Properties**

**Named MAPI properties** are custom properties added by users or applications. 

Aspose.Email allows reading these properties from messages and attachments. 

### **Reading Named MAPI Properties from MSG Files**

The following code sample demonstrates how to load a MAPI message file, retrieve all its named MAPI properties, and iterate through them to find and display the values of specific named properties ("TEST" and "MYPROP"). It shows how to access custom or extended properties in a MAPI message by enumerating the property collection and conditionally processing properties based on their name identifiers.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cpp" >}}

### **Accessing Named MAPI Properties in Attachments**

Named MAPI properties in attachments can be retrieved similarly:

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cpp" >}}

### **Removing MAPI Properties**

You can remove both standard and named MAPI properties from messages or attachments as shown in the code sample below:


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cpp" >}}
