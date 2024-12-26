---
title: Managing Message Attachments
ArticleTitle: Managing Message Attachments
type: docs
weight: 80
url: /net/managing-message-attachments/
---

## **Handling Attachments in Outlook**

[Creating and Saving Outlook Message (MSG) Files](https://docs.aspose.com/email/net/creating-and-saving-msg-files/) explains how to create and save messages, and how to create MSG files with attachments. This article explains how to manage Microsoft Outlook attachments with Aspose.Email. Attachments from a message file are accessed and saved to disk using the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) property. The [Attachments](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/attachments/) property is a collection of type [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) class.

### **Check Attachment Type (Inline or Regular)**

Inline and regular attachments serve different purposes. Inline attachments are visually integrated into the email message and are typically images or media files. Meanwhile, regular attachments are separate files attached to the email and can include various types of files. The [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) property of the [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) class gets a value indicating whether the attachment is inline or regular.

The following code sample extracts and displays information about each attachment in the loaded MapiMessage, including their display names and whether they are inline attachments or not.

```cs
var message = MapiMessage.Load(fileName);

foreach (var attach in message.Attachments)
{
    Console.WriteLine($"{attach.DisplayName0} : {attach.IsInline)}");
}
```

### **Check Attachment Type (IsReference)**

The [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/#mapiattachment-class) class includes the [IsReference](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isreference/) property which allows developers to identify reference attachments in a message. With thefollowing code sample, you can check if an attachment is a reference attachment:

```cs
foreach (var attachment in msg.Attachments)
{
    if (attachment.IsReference)
    {
        // Process reference attachment
    }
}
```

### **Save Attachments from MSG Files**

To save attachments from an MSG file:

1. Iterate through the [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) collection and get the individual attachments.
1. To save the attachments, call the MapiAttachment class Save() method.

The following code snippet shows you how to save attachments to the local disk.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveAttachmentsFromOutlookMSGFile-SaveAttachmentsFromOutlookMSGFile.cs" >}}

### **Extract Attachments from RTF-Formatted MSG Files**

For messages formatted as RTF, the following code can be used to differentiate and extract attachments that are either Inline or appear as Icon in the message body. The following code snippet shows you how to Identify and Extract an embedded attachment from MSG formatted as RTF.

```csharp

var eml = MapiMessage.Load("MSG file with RTF Formatting.msg");

foreach (var attachment in eml.Attachments)
{
    if (IsAttachmentInline(attachment))
    {
        try
        {
            SaveAttachment(attachment, Data.Out/new Guid().ToString());
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }
}

static bool IsAttachmentInline(MapiAttachment attachment)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "\x0003ObjInfo")
        {
            var odtPersist1 = BitConverter.ToUInt16(property.Data, 0);
            return (odtPersist1 & (1 << (7 - 1))) == 0;
        }
    }
    return false;
}

static void SaveAttachment(MapiAttachment attachment, string fileName)
{
    foreach (var property in attachment.ObjectData.Properties.Values)
    {
        if (property.Name == "Package")
        {
            using var fs = new FileStream(fileName, FileMode.Create, FileAccess.Write);
            fs.Write(property.Data, 0, property.Data.Length);
        }
    }
}
```

### **Get Nested Mail Message Attachments**

Embedded OLE attachments also appear in the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class Attachment collection. The following code example parses a message file for embedded message attachments and saves it to the disk. The [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class FromProperties() static method can create a new message from embedded attachment. The following code snippet shows you how to get nested mail message attachments.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetNestedMailMessageAttachments-GetNestedMailMessageAttachments.cs" >}}

### **Remove Attachments**

Aspose Outlook library provides the functionality to remove attachments from Microsoft Outlook Message (.msg) files:

- Call the RemoveAttachments() method. It takes the path of the message file as a parameter. It is implemented as a public static method, so you don’t need to instantiate the object.

The following code snippet shows you how to removing Attachments.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-RemoveAttachmentsFromFile-RemoveAttachmentsFromFile.cs" >}}

You can also call the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class static method [DestoryAttachment()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/destroyattachments/). It works faster than RemoveAttachment(), because the RemoveAttachment() method parses the message file.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DestroyAttachment-DestroyAttachment.cs" >}}

### **Add MSG Attachments**

An Outlook message can contain other Microsoft Outlook messages in attachments either as regular or embedded messages. The [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/) provides overloaded members of the Add method to create Outlook messages with both types of attachments.

{{% alert %}}
**Try it out!**

Add or remove email attachments with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}

### **Add Reference Attachments to MapiMessages**

The [ReferenceAttachmentOptions](https://reference.aspose.com/email/net/aspose.email.mapi/referenceattachmentoptions/) class simplifies the addition of reference attachments by encapsulating all necessary properties in a single object.

**Parameters of ReferenceAttachmentOptions:**

- **sharedLink**: A fully qualified shared link to the attachment provided by the web service hosting the file.
- **url**: The file location or resource URL.
- **providerName**: The name of the reference attachment provider (e.g., Google Drive, Dropbox).
- **Example**: Adding a Reference Attachment with ReferenceAttachmentOptions

```cs
var options = new ReferenceAttachmentOptions(
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive");

// Add reference attachment
msg.Attachments.Add("Document.pdf", options);
```

### **Embed Messages as Attachments**

The following code snippet shows you how to embed an MSG file attachment to a message.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EmbedMessageAsAttachment-EmbedMessageAsAttachment.cs" >}}

### **Read Embedded Messages from Attachments**

The following code snippet shows you how to read embedded messages from attachments.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReadEmbeddedMessageFromAttachment-ReadEmbeddedMessageFromAttachment.cs" >}}

## **Inserting and Replacing Attachment**

Aspose.Email API provides the capability to insert attachments at specific index in the parent message. It also provides the facility to replace contents of an attachment with another message attachment.

{{% alert %}}
**Try it out!**

Run the [ReplaceAttach](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/ReplaceAttach/ReplaceAttach) simple app project, and try the Aspose.Email capabilities to replace attachments in action.
{{% /alert %}} 

### **Insert Attachments at Specific Locations**

Aspose.Email API provides the capability to insert a MSG attachment to a parent MSG using the MapiAttachmentCollection's Insert method MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). The following code snippet shows you how to insert an attachment at a specific location.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-InsertMSGAttachmentAtSpecificlocation-InsertMSGAttachmentAtSpecificlocation.cs" >}}

### **Replace Attachment Contents**

This can be used to replace embedded attachment contents with the new ones using the Replace method. However, it can not be used to insert attachment with PR_ATTACH_NUM = 4(for example) in the collection with collection.Count = 2. The following code snippet shows you how to replace attachment contents.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-ReplaceEmbeddedMSGAttachmentContents-ReplaceEmbeddedMSGAttachmentContents.cs" >}}

### **Rename Attachments in MapiMessage**

It is possible to edit the DisplayName property value in MapiMessage attachments.

```cs
var msg = MapiMessage.Load(fileName);
msg.Attachments[0].DisplayName = "New display name 1";
msg.Attachments[1].DisplayName = "New display name 2";
```

## **Save Attachments from Digitally Signed Messages**

Aspose.Email API provides the capability to get or set a value indicating whether clear-signed message will be decoded. 

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DecodeClearSignedContent-DecodeClearSignedContent.cs" >}}
