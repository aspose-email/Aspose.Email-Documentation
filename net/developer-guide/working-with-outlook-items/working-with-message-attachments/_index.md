---
title: Working with Message Attachments
type: docs
weight: 80
url: /net/working-with-message-attachments/
---


## **Managing Attachments with Aspose Outlook**
[Creating and Saving Outlook Message (MSG) Files](/email/net/managing-message-files-with-aspose-email-outlook/) explained how to create and save messages, and how to create MSG files with attachments. This article explains how to manage Microsoft Outlook attachments with Aspose.Email. Attachments from a message file are accessed and saved to disk using the [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.outlook/mapimessage) class [Attachments](http://www.aspose.com/api/net/email/aspose.email.outlook/mapimessageitembase/properties/attachments) property. The [Attachments](http://www.aspose.com/api/net/email/aspose.email.outlook/mapimessageitembase/properties/attachments) property is a collection of type [MapiAttachmentCollection](http://www.aspose.com/api/net/email/aspose.email.outlook/MapiAttachmentCollection) class.
### **Save Attachments from Outlook Message (MSG) file**
To save attachments from an MSG file:

1. Iterate through the [MapiAttachmentCollection](http://www.aspose.com/api/net/email/aspose.email.outlook/MapiAttachmentCollection) collection and get the individual attachments.
1. To save the attachments, call the MapiAttachment class Save() method.

The following code snippet shows you how to saves attachments to the local disk.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}
### **Getting Nested Mail Message Attachments**
Embedded OLE attachments also appear in the [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.outlook/mapimessage) class Attachment collection. The following code example parses a message file for embedded message attachments and saves it to disk. The [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.outlook/mapimessage) class FromProperties() static method can create a new message from embedded attachment. The following code snippet shows you how to get nested mail message attachments.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}
### **Removing Attachments**
Aspose Outlook library provides the functionality to remove attachments from Microsoft Outlook Message (.msg) files:

- Call the RemoveAttachments() method. It takes the path of the message file as a parameter. It is implemented as a public static method, so you don’t need to instantiate the object.

The following code snippet shows you how to removing Attachments.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}



You can also call the [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.outlook/mapimessage) class static method [DestoryAttachment()](http://www.aspose.com/api/net/email/aspose.email.outlook/mapimessage/methods/destroyattachments). It works faster than RemoveAttachment(), because the RemoveAttachment() method parses the message file.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}
### **Adding MSG Attachments**
An Outlook message can contain other Microsoft Outlook messages in attachments either as regular or embedded messages. The [MapiAttachmentCollection](http://www.aspose.com/api/net/email/aspose.email.outlook/MapiAttachmentCollection) provides overloaded members of the Add method to create Outlook messages with both types of attachments.

{{% alert %}}
**Try it out!**

Add or remove email attachments with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}

### **Embedding Message as Attachment**
The following code snippet shows you how to outlook MSG files embedded in a MSG file contains a PR_ATTACH_METHOD whose value equals 5.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}
### **Reading Embedded Message from Attachment**
The following code snippet shows you how to read embedded message from attachment.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}
## **Attachments Insertion and Replacement**
Aspose.Email API provides the capability to insert attachments at specific index in the parent message. It also provides the facility to replace contents of an attachment with another message attachment. The following code snippet shows you how to attachments Insertion and Replacement.
### **Insert at Specific location**
Aspose.Email API provides the capability to insert a MSG attachment to a parent MSG using the MapiAttachmentCollection's Insert method MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). The following code snippet shows you how to insert at specific location.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}
### **Replace Attachment Contents**
This can be used to replace embedded attachment contents with the new ones using the Replace method. However, it can not be used to insert attachment with PR_ATTACH_NUM = 4(for example) in the collection with collection.Count = 2. The following code snippet shows you how to replace attachment contents.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}
## **Save Attachments from Digitally Signed Message**
Aspose.Email API provides the capability to get or set a value indicating whether clear-signed message will be decoded. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}
