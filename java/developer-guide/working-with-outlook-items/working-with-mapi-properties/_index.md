---
title: Working with MAPI Properties
type: docs
weight: 60
url: /java/working-with-mapi-properties/
---

## **Setting and Accessing Outlook MAPI Properties**
Aspose.Email for Java provides the [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/MapiProperty) class that represents a MAPI property:

- Name: the property name.
- Tag: the property's tag.
- Data: the property data.

This topic also discusses how to set and access an Outlook Message (MSG) file's MAPI properties using Aspose.Email for Java. In addition, a sample code has been provided about how to remove properties from MSGs and Attachments.
### **Read Properties**
To read data of MAPI properties from an MSG file:

1. Create an instance of the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) class to load an MSG file using the [fromFile()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#fromFile\(java.lang.String\)) static method.
1. Set a reference to the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) object's [getProperties()](https://reference.aspose.com/email/java/com.aspose.email/MapiPropertyContainer#getProperties\(\)) method to get the [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/MapiPropertyCollection).
1. Get the [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/MapiProperty) object from the [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/MapiPropertyCollection) by the [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/MapiPropertyTag) keys.
1. Get the property data using an appropriate getXXX() method.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-AccessOutlookMAPIProperties.java" >}}
### **Set Additional Properties**
The following code sample can be used to set additional properties of an Outlook [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAdditionalMAPIProperties-SetAdditionalProperties.java" >}}
### **Remove Properties**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-RemoveProperties.java" >}}
## **Reading Named Mapi Properties from Email Messages**
Microsoft Outlook supports adding named MAPI properties to an MSG file. These properties are added by the user. Developers can add a named property, for example “MyProp”, to an MSG file using Aspose.Email.

This article illustrates Aspose.Email's [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) [getNamedProperties()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessageItemBase#getNamedProperties\(\)) collection to read named MAPI properties from an MSG file.
### **Read Named MAPI Property**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMAPIProperty.java" >}}
### **Read Named Mapi Property from Attachment**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMapiPropertyFromAttachment.java" >}}
