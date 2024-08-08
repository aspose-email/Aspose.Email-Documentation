---
title: Working with Outlook Message Attachments using C++ Email Parser API
linktitle: Working with Message Attachments
type: docs
weight: 70
url: /cpp/working-with-message-attachments/
description: You can manage Outlook message attachments with the C++ Email Parser Library, save and delete them, and embed messages as an attachment.
---

## **Managing Attachments with Aspose Outlook**
Creating and Saving Outlook Message (MSG) Files explained how to create and save messages, and how to create MSG files with attachments. This article explains how to manage Microsoft Outlook attachments with Aspose.Email. Attachments from a message file are accessed and saved to disk using the MapiMessage class Attachments property. The Attachments property is a collection of type MapiAttachmentCollection class.

### **Save Attachments from Outlook Message (MSG) file**
To save attachments from an MSG file:

1. Iterate through the MapiAttachmentCollection collection and get the individual attachments.
1. To save the attachments, call the MapiAttachment class Save() method.

The following code snippet shows you how to saves attachments to the local disk.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cpp" >}}

### **Removing Attachments**
Aspose Outlook library provides the functionality to remove attachments from Microsoft Outlook Message (.msg) files:

- Call the RemoveAttachments() method. It takes the path of the message file as a parameter. It is implemented as a public static method, so you don’t need to instantiate the object.

The following code snippet shows you how to remove Attachments using C++ Email Parser Library.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cpp" >}}

You can also call the MapiMessage class static method DestoryAttachment(). It works faster than RemoveAttachment(), because the RemoveAttachment() method parses the message file.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DestroyAttachment-DestroyAttachment.cpp" >}}

### **Adding MSG Attachments**
An Outlook message can contain other Microsoft Outlook messages in attachments either as regular or embedded messages. The MapiAttachmentCollection provides overloaded members of the Add method to create Outlook messages with both types of attachments.

### **Embedding Message as Attachment**
The following code snippet shows you how to outlook MSG files embedded in a MSG file contains a PR_ATTACH_METHOD whose value equals 5.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cpp" >}}
