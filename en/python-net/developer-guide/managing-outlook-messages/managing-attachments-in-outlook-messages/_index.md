---
title: Managing Attachments in Outlook Messages
ArticleTitle: Managing Attachments in Outlook Messages
type: docs
weight: 60
url: /python-net/managing-attachments-in-outlook-messages/
---


The [Creating and Saving Outlook Message (MSG) Files](https://docs.aspose.com/email/python-net/creating-and-saving-msg-files/) article explained the steps involved in creating and saving messages, including MSG files with attachments. This article delves into the management of Microsoft Outlook attachments using Aspose.Email. It will guide you through accessing and saving attachments from a message file utilizing the [attachments](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#properties) property of the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class. This property is a collection belonging to the [MapiAttachmentCollection](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/) class, allowing for efficient handling of attachments. 

## **Check Inline vs Regular Attachments**

"Inline" and "Regular" attachments refer to the way they are included in an email message. **Regular** attachments are files attached in the traditional way. They are typically displayed in a list within the email client and can be downloaded by a recipient and saved to a local storage. **Inline** attachments, also known as embedded or inline images, are typically used for including images or other media within the body of the email. They are not displayed in a separate list but are instead shown directly within the email's content, such as in the body of the email. This allows you to include images or other media that are part of the message's content. The code sample below demonstrates how to determine whether an attachment is inline or regular:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

for attachment in msg.attachments:
    print(f"{attachment.display_name}:{attachment.is_inline}")
```

## **Identify Reference Attachments in MAPI Messages**

The Aspose.Email API includes the `is_reference` property of the [MapiAttachment](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachment/#mapiattachment-class) class which enables developers to identify reference attachments in a message. Try the code sample below to see how it works in a python project:

```py
import aspose.email as ae

# Load or create a MapiMessage
msg = ae.MapiMessage.load("Message_With_Reference_Attachment.msg")

# Iterate through the attachments
for attachment in msg.attachments:
    if attachment.is_reference:
        # Process reference attachment
        pass
```

## **Save Attachments from MSG Files**

To save attachments from an MSG file:

1. Iterate through the [MapiAttachmentCollection](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/) collection and get the individual attachments.
1. To save the attachments, call the [MapiAttachment](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachment/#mapiattachment-class) class [Save()](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachment/#methods) method.

The following code snippet shows you how to save attachments to the local disk:

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

## **TNEF Attachments Handling**

### **Load and Save Attachments in TNEF Format**

Aspose.Email provides methods for handling TNEF attachments. These methods allow saving and loading attachments in TNEF format, commonly used in Outlook messages (winmail.dat).

- [static MapiAttachment MapiAttachment.load_from_tnef(string fileName)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachment/#methods) – Loads an attachment from a TNEF file.
- [static MapiAttachment MapiAttachment.load_from_tnef(Stream stream)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachment/#methods) – Loads an attachment from a TNEF stream.
- [void MapiAttachment.save_to_tnef(string filename)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachment/#methods) – Saves an attachment to a TNEF file.
- [void MapiAttachment.save_to_tnef(Stream stream)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachment/#methods) – Saves an attachment to a TNEF stream.

The following code sample demonstrates how to extract, save, and re-add TNEF format email attachments while managing them through memory streams or files:


```py
# Load the EML message (which contains a winmail.dat TNEF attachment)
msg = MapiMessage.load("message.eml")

# Save the first attachment as winmail.dat in memory
ms = io.BytesIO()
msg.attachments[0].save_to_tnef("winmail.dat")

# Reset the stream position to the beginning
ms.seek(0)

# Load the TNEF attachment from the file and add it back to the message
from_tnef_attachment = MapiAttachment.load_from_tnef("winmail.dat")
msg.attachments.add(from_tnef_attachment)

# (Optional) If you also want to load from the memory stream instead of the file
# Load the TNEF attachment directly from memory stream and add it
ms.seek(0)
from_tnef_attachment_from_stream = MapiAttachment.load_from_tnef(ms)
msg.attachments.add(from_tnef_attachment_from_stream)
```


## **Retrieve Nested Mail Message Attachments**

The Embedded OLE (Object Linking and Embedding) attachments also appear in the attachment collection of the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) class. The code example below demonstrates how to parse a message file and extract embedded message attachments, subsequently saving them to disk for further use. The [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) class offers a [from_properties](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods) static method to create a new message from an embedded attachment. The following code snippet shows you how to get nested mail message attachments:

```py
import aspose.email as ae

eml = ae.mapi.MapiMessage.load("my.msg")

# Create a MapiMessage object from the individual attachment
get_attachment = ae.mapi.MapiMessage.from_properties(eml.attachments[0].object_data.properties)

# Create an object of type MailMessageInterpreter from the above message and save the embedded message to a file on disk
mail_message = get_attachment.to_mail_message(ae.mapi.MailConversionOptions())
mail_message.save("NestedMailMessageAttachments_out.eml", ae.SaveOptions.default_eml)
```

## **Remove Attachments**

Aspose.Email library provides the functionality to remove attachments from Microsoft Outlook Message (.msg) files. Use the [remove_attachments(path)](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods) method which requires the path of the message file as its parameter. As a public static method, you can call it directly without needing to instantiate an object, making the process straightforward and efficient.

The following code snippet shows you how to remove attachments from MSG files using Aspose.Email:

```py
import aspose.email as ae

ae.mapi.MapiMessage.remove_attachments("AttachmentsToRemove_out.msg")
```

You can also call the static **destroy_attachments**  method of the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class. It works faster than **remove_attachments** because the **remove_attachments** method parses the message file.

```py
import aspose.email as ae

# Destroy attachments in the MapiMessage
ae.mapi.MapiMessage.destroy_attachments(data_dir + "AttachmentsToDestroy_out.msg")
```

## **Add MSG Attachments**

An Outlook message can contain other Microsoft Outlook messages in attachments either as regular or embedded ones. The [MapiAttachmentCollection](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/) provides overloaded members of the [add](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/#methods) method to create Outlook messages with both types of attachments.
{{% alert %}}
**Try it out!**

Add or remove email attachments online with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}

### **Add Reference Attachments to MAPI Messages**

**Reference attachment** typically refers to an attachment that contains a reference or link to an external resource rather than the actual file itself. These references are often used in HTML emails to link to external images or resources hosted on a remote server. Instead of embedding the entire file, a reference attachment includes a URL or reference to the external content.
 
To add a reference attachment to a MAPI message, use the `add` method of the [MapiAttachmentCollection](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/) class and the [ReferenceAttachmentOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/referenceattachmentoptions/) class to specify:

- The content URL (direct link to the file)

- The provider URL (link to the file’s location or UI view)

- The attachment provider name (e.g., "GoogleDrive") 

as shown in the code sample below. 

```python
import aspose.email as ae

# Load or create a MapiMessage
msg = ae.MapiMessage()
msg.subject = "Email with Reference Attachment"
msg.body = "This message contains a cloud-based reference attachment."

# Create ReferenceAttachmentOptions
options = ae.ReferenceAttachmentOptions(
    "https://drive.google.com/file/d/1HJ-M3F2qq1oRrTZ2GZhUdErJNy2CT3DF/",
    "https://drive.google.com/drive/my-drive",
    "GoogleDrive"
)

# Add the reference attachment to the message
msg.attachments.add("Document.pdf", options)

# Save the message to MSG format
msg.save("Message_With_Reference_Attachment.msg")
```

### **Embed Messages as Attachments**

The following code snippet demonstrates how to embed Outlook MSG files as attachments within another MSG file. An embedded MSG file includes a PR_ATTACH_METHOD property with a value of 5, indicating that it is an attachment of type "message". 

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

The following code snippet shows you how to read embedded messages from attachments.

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

## **Insert and Replace Attachments**

Aspose.Email API offers the functionality to insert attachments at a specific index within the parent message. Additionally, it provides the ability to replace the contents of an existing attachment with a different message attachment. Below are code snippets demonstrating how to perform attachment insertion and replacement.

### **Insert Attachments at Specific Locations**

Aspose.Email API enables you to insert a MSG attachment into a parent MSG using the Insert method of the [MapiAttachmentCollection](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/). This method is used with the signature *MapiAttachmentCollection Insert(int index, string name, MapiMessage msg)*. Below is a code snippet illustrating how to insert an attachment at a specific location:

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

You can use the [replace](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiattachmentcollection/) method to update the contents of an embedded attachment with new data. However, note that this method cannot be used to insert an attachment with PR_ATTACH_NUM = 4 into a collection where collection.Count = 2. Below is a code snippet demonstrating how to replace attachment contents:

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

## **Rename Attachments in MapiMessages**

With Aspose.Email, you can easily modify the display names of attachments in email messages loaded from a file. The following code sample demonstrates how to achieve this:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("message.msg")

msg.attachments[0].display_name = "New display name 1"
msg.attachments[1].display_name = "New display name 2"
```
