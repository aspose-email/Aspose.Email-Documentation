---
title: Working with Message Attachments
ArticleTitle: Working with Message Attachments
type: docs
weight: 70
url: /python-net/working-with-message-attachments/
---


## **Managing Attachments with Aspose Outlook**
Creating and Saving Outlook Message (MSG) Files explained how to create and save messages, and how to create MSG files with attachments. This article explains how to manage Microsoft Outlook attachments with Aspose.Email. Attachments from a message file are accessed and saved to disk using the MapiMessage class Attachments property. The Attachments property is a collection of type MapiAttachmentCollection class.

### **Check if the Attachment is Inline or Regular**

"Inline" and "Regular" attachments refer to the way they are included in an email message. **Regular** attachments are files attached in the traditional way. They are typically displayed in a list within the email client and can be downloaded by a recipient and saved to a local storage. **Inline** attachments, also known as embedded or inline images, are typically used for including images or other media within the body of the email. They are not displayed in a separate list but are instead shown directly within the email's content, such as in the body of the email. This allows you to include images or other media that are part of the message's content. The code sample below demonstrates how to determine whether an attachment is inline or regular:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

for attachment in msg.attachments:
    print(f"{attachment.display_name}:{attachment.is_inline}")
```

### **Save Attachments from Outlook Message (MSG) file**

To save attachments from an MSG file:

1. Iterate through the MapiAttachmentCollection collection and get the individual attachments.
1. To save the attachments, call the MapiAttachment class Save() method.

The following code snippet shows you how to saves attachments to the local disk.

```py
import aspose.email as ae

data_dir = "C://dataDir/"
file_name = "message.msg"

# Create an instance of MapiMessage from file
message = ae.mapi.MapiMessage.from_file(data_dir + file_name)

# Iterate through the attachments collection
for attachment in message.attachments:
    # Save the individual attachment
    attachment.save(data_dir + attachment.file_name)
```

### **Getting Nested Mail Message Attachments**

Embedded OLE attachments also appear in the MapiMessage class Attachment collection. The following code example parses a message file for embedded message attachments and saves it to disk. The MapiMessage class FromProperties() static method can create a new message from embedded attachment. The following code snippet shows you how to get nested mail message attachments.

```py
import aspose.email as ae

eml = ae.mapi.MapiMessage.load("my.msg")

# Create a MapiMessage object from the individual attachment
get_attachment = ae.mapi.MapiMessage.from_properties(eml.attachments[0].object_data.properties)

# Create an object of type MailMessageInterpreter from the above message and save the embedded message to a file on disk
mail_message = get_attachment.to_mail_message(ae.mapi.MailConversionOptions())
mail_message.save("NestedMailMessageAttachments_out.eml", ae.SaveOptions.default_eml)
```

### **Removing Attachments**

Aspose Outlook library provides the functionality to remove attachments from Microsoft Outlook Message (.msg) files:

- Call the RemoveAttachments() method. It takes the path of the message file as a parameter. It is implemented as a public static method, so you don’t need to instantiate the object.

The following code snippet shows you how to removing Attachments.


```py
import aspose.email as ae

ae.mapi.MapiMessage.remove_attachments("AttachmentsToRemove_out.msg")
```

You can also call the MapiMessage class static method DestoryAttachment(). It works faster than RemoveAttachment(), because the RemoveAttachment() method parses the message file.

```py
import aspose.email as ae

# Destroy attachments in the MapiMessage
ae.mapi.MapiMessage.destroy_attachments(data_dir + "AttachmentsToDestroy_out.msg")
```

### **Adding MSG Attachments**

An Outlook message can contain other Microsoft Outlook messages in attachments either as regular or embedded messages. The MapiAttachmentCollection provides overloaded members of the Add method to create Outlook messages with both types of attachments.
{{% alert %}}
**Try it out!**

Add or remove email attachments online with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}

### **Add a Reference Attachment to a MapiMessage**

"Reference attachment" typically refers to an attachment that contains a reference or link to an external resource rather than the actual file itself. These references are often used in HTML emails to link to external images or resources hosted on a remote server. Instead of embedding the entire file, a reference attachment includes a URL or reference to the external content.
 
Aspose.Email provides a set of tools for correct reference attachments display presented in the following code sample: 

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

# Add reference attachment
msg.attachments.add("Document.pdf",
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive")

# Also, you can set additional attachment properties
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PERMISSION_TYPE, int(ae.AttachmentPermissionType.ANYONE_CAN_EDIT))
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_ORIGINAL_PERMISSION_TYPE, 0)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_IS_FOLDER, False)
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PROVIDER_ENDPOINT_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_PREVIEW_URL, "")
msg.attachments[0].set_property(ae.mapi.KnownPropertyList.ATTACHMENT_THUMBNAIL_URL, "")
# Finally save the message
msg.save("msg_with_ref_attach.msg")
```
### **Embed a Message as Attachment**
The following code snippet shows you how to outlook MSG files embedded in a MSG file contains a PR_ATTACH_METHOD whose value equals 5.

```py
import aspose.email as ae

# Create a new MapiMessage
message = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Subj", "This is a message body")

# Load the attachment message
attach_msg = ae.mapi.MapiMessage.load("Message.msg")

# Add the attachment to the message
message.attachments.add("Weekly report.msg", attach_msg)

# Save the message with the embedded message attachment
message.save("WithEmbeddedMsg_out.msg")
```
### **Read Embedded Messages from Attachments**
The following code snippet shows you how to read embedded message from attachment.

```py
import aspose.email as ae

file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.from_file(file_name)

# Check if the first attachment is an Outlook message
if message.attachments[0].object_data.is_outlook_message:
    # Get the embedded message as MapiMessage
    embedded_message = message.attachments[0].object_data.to_mapi_message()
    # Perform further operations with the embedded message
    # ...
```
## **Attachments Insertion and Replacement**
Aspose.Email API provides the capability to insert attachments at specific index in the parent message. It also provides the facility to replace contents of an attachment with another message attachment. The following code snippet shows you how to attachments Insertion and Replacement.
### **Insert at Specific location**
Aspose.Email API provides the capability to insert a MSG attachment to a parent MSG using the MapiAttachmentCollection's Insert method MapiAttachmentCollection Insert(int index, string name, MapiMessage msg). The following code snippet shows you how to insert at specific location.

```py
import aspose.email as ae
from io import BytesIO

file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.load(file_name)

# Save the attachment to a memory stream
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Load the attachment from the memory stream
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Insert the loaded attachment at index 1
message.attachments.insert(1, "new 11", get_data)
```
### **Replace Attachment Contents**
This can be used to replace embedded attachment contents with the new ones using the Replace method. However, it can not be used to insert attachment with PR_ATTACH_NUM = 4(for example) in the collection with collection.Count = 2. The following code snippet shows you how to replace attachment contents.

```py
import aspose.email as ae
from io import BytesIO
file_name = "path/to/file.msg"

# Load the MapiMessage from file
message = ae.mapi.MapiMessage.load(file_name)

# Save the attachment to a memory stream
memory_stream = BytesIO()
message.attachments[2].save(memory_stream)

# Load the attachment from the memory stream
get_data = ae.mapi.MapiMessage.load(memory_stream)

# Replace the attachment at index 1 with the loaded attachment
message.attachments.replace(1, "new 1", get_data)
```
### **Rename an Attachment in a MapiMessage**

It is possible to modify the display names of the attachments in email messages loaded from a file. The code sample below shows how to do this:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

msg.attachments[0].display_name = "New display name 1"
msg.attachments[1].display_name = "New display name 2"
```
