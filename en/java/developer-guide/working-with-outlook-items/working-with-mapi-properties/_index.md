---
title: Working with MAPI Properties
ArticleTitle: Working with MAPI Properties
type: docs
weight: 60
url: /java/working-with-mapi-properties/
---

## **Setting and Accessing Outlook MAPI Properties**

Aspose.Email for Java provides the [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) class that represents a MAPI property:

- Name: the property name.
- Tag: the property tag.
- Data: the property data.

This topic also discusses how to set and access an Outlook Message (MSG) file MAPI properties using Aspose.Email for Java. In addition, a sample code has been provided about how to remove properties from MSGs and Attachments.

### **Read Properties**

To read data of MAPI properties from an MSG file:

1. Create an instance of the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class to load an MSG file using the [Load()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) static method.
2. Set a reference to the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) object [getProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getProperties--) method to get the [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/).
3. Get the [MapiProperty](https://reference.aspose.com/email/java/com.aspose.email/mapiproperty/) object from the [MapiPropertyCollection](https://reference.aspose.com/email/java/com.aspose.email/mapipropertycollection/) by the [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) keys.
4. Get the property data using an appropriate getXXX() method.
 
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-AccessOutlookMAPIProperties.java" >}}

### **Set Additional Properties**

The following code sample can be used to set additional properties of an Outlook [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAdditionalMAPIProperties-SetAdditionalProperties.java" >}}

### **Remove Properties**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-SetAndAccessOutlookMAPIProperties-RemoveProperties.java" >}}

## **Reading Named Mapi Properties from Email Messages**

Microsoft Outlook supports adding named MAPI properties to an MSG file. These properties are added by the user. Developers can add a named property, for example “MyProp”, to an MSG file using Aspose.Email.

This article illustrates Aspose.Email [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) [getNamedProperties()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getNamedProperties--) collection to read named MAPI properties from an MSG file.

### **Read Named MAPI Property**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMAPIProperty.java" >}}

### **Read Named Mapi Property from Attachment**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ReadNamedMapiProperties-ReadingNamedMapiPropertyFromAttachment.java" >}}
