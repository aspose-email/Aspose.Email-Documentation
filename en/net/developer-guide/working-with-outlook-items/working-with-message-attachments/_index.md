---
title: Working with Message Attachments
type: docs
weight: 80
url: /net/working-with-message-attachments/
---


## **Managing Attachments with Aspose Outlook**

[Creating and Saving Outlook Message (MSG) Files](https://docs.aspose.com/email/net/creating-and-saving-msg-files/) explains how to create and save messages, and how to create MSG files with attachments. This article explains how to manage Microsoft Outlook attachments with Aspose.Email. Attachments from a message file are accessed and saved to disk using the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) property. The [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) property is a collection of type [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) class.

### **Check if the Attachment is Inline or Regular**

Inline and regular attachments serve different purposes. Inline attachments are visually integrated into the email message and are typically images or media files. Meanwhile, regular attachments are separate files attached to the email and can include various types of files. The [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) property of the [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) class gets a value indicating whether the attachment is inline or regular.

The following code sample extracts and displays information about each attachment in the loaded MapiMessage, including their display names and whether they are inline attachments or not.

```cs
var message = MapiMessage.Load(fileName);

foreach (var attach in message.Attachments)
{
    Console.WriteLine($"{attach.DisplayName0} : {attach.IsInline)}");
}
```

### **Save Attachments from Outlook Message (MSG) file**

To save attachments from an MSG file:

1. Iterate through the [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) collection and get the individual attachments.
1. To save the attachments, call the MapiAttachment class Save() method.

The following code snippet shows you how to save attachments to the local disk.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}

### **Getting Nested Mail Message Attachments**

Embedded OLE attachments also appear in the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class Attachment collection. The following code example parses a message file for embedded message attachments and saves it to the disk. The [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class FromProperties() static method can create a new message from embedded attachment. The following code snippet shows you how to get nested mail message attachments.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}

### **Removing Attachments**

Aspose Outlook library provides the functionality to remove attachments from Microsoft Outlook Message (.msg) files:

- Call the RemoveAttachments() method. It takes the path of the message file as a parameter. It is implemented as a public static method, so you don’t need to instantiate the object.

The following code snippet shows you how to removing Attachments.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}

You can also call the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class static method [DestoryAttachment()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/destroyattachments/). It works faster than RemoveAttachment(), because the RemoveAttachment() method parses the message file.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}

### **Adding MSG Attachments**

An Outlook message can contain other Microsoft Outlook messages in attachments either as regular or embedded messages. The [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) provides overloaded members of the Add method to create Outlook messages with both types of attachments.

{{% alert %}}
**Try it out!**

Add or remove email attachments with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}

### **Adding a ReferenceAttachment on a MapiMessage**

The [MapiAttachmentCollection.Add(string name, string sharedLink, string url, string providerName)](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) method of the [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) class allows adding a reference attachment in a MapiMessage. When the recipients of the email click on the reference attachment, they will be able to access the linked file if they have the appropriate permissions to do so. By using a reference attachment, you can send a smaller email message and ensure that everyone has access to the most up-to-date version of the file or item.

The method has the following parameters:

- *name* - the name of attachment
- *sharedLink* - a fully qualified shared link to the attachment provided by web service manipulating the attachment
- *url* - a file location
- *providerName* - a name of reference attachment provider

The code example below demonstrates how to add a reference attachment to a message:

```cs
// Let's say you want to send an email message that includes a link to a Document.pdf file stored on a Google Drive.
// Instead of attaching the document directly to the email message,
// you can create a reference attachment that links to the file on the Google Drive.

// Create a message
var msg = new MapiMessage("from@domain.com", "to@domain.com", "Outlook message file",
    "This message is created by Aspose.Email", OutlookMessageFormat.Unicode);

// Add reference attachment
msg.Attachments.Add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive");
//Also, you can set additional attachment properties
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPermissionType, AttachmentPermissionType.AnyoneCanEdit);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentOriginalPermissionType, 0);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentIsFolder, false);
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentProviderEndpointUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentPreviewUrl, "");
msg.Attachments[0].SetProperty(KnownPropertyList.AttachmentThumbnailUrl, "");
// Finally save the message
msg.Save(@"my.msg");
```

### **Embedding a Message as Attachment**

The following code snippet shows you how to embed an MSG file attachment to a message.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}

### **Reading Embedded Messages from Attachments**

The following code snippet shows you how to read embedded messages from attachments.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}

## **Attachments Insertion and Replacement**

Aspose.Email API provides the capability to insert attachments at specific index in the parent message. It also provides the facility to replace contents of an attachment with another message attachment.

{{% alert %}}
**Try it out!**

Run the [ReplaceAttach](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ReplaceAttach/ReplaceAttach) simple app project, and try the Aspose.Email capabilities to replace attachments in action.
{{% /alert %}} 

### **Insert at Specific location**

Aspose.Email API provides the capability to insert a MSG attachment to a parent MSG using the MapiAttachmentCollection's Insert method MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). The following code snippet shows you how to insert an attachment at a specific location.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}

### **Replace Attachment Contents**

This can be used to replace embedded attachment contents with the new ones using the Replace method. However, it can not be used to insert attachment with PR_ATTACH_NUM = 4(for example) in the collection with collection.Count = 2. The following code snippet shows you how to replace attachment contents.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}

### **Renaming an Attachment in MapiMessage**

It is possible to edit the DisplayName property value in MapiMessage attachments.

```cs
var msg = MapiMessage.Load(fileName);
msg.Attachments[0].DisplayName = "New display name 1";
msg.Attachments[1].DisplayName = "New display name 2";
```

## **Save Attachments from Digitally Signed Messages**

Aspose.Email API provides the capability to get or set a value indicating whether clear-signed message will be decoded. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}
