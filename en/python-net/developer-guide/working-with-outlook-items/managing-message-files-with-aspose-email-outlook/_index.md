---
title: Managing Message Files with Aspose.Email.Outlook
type: docs
weight: 30
url: /python-net/managing-message-files-with-aspose-email-outlook/
---

## **Determine the MAPI item type in a PST folder**

A PST file typically contains various types of data, such as email messages, calendar events, contacts, and more. The [MapiItemType](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiitemtype/) class of the Aspose.Email allows you to access and categorize different types of MAPI items within a PST file. The code below demonstrates how to determine the type of a MAPI item in a PST folder:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("test.pst")
folder = pst.root_folder.get_sub_folder("Calendar")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    # Get the class type based on msg.SupportedType
    item_type = msg.supported_type

    # Non-supported type. It cannot be accessed as appropriate item type.
    if item_type == ae.mapi.MapiItemType.NONE:
        print("Item type not supported")
    # An email message.
    elif item_type == ae.mapi.MapiItemType.MESSAGE:
        # You can access to MapiMessage properties there.
        # A subject for example
        print(msg.subject)
    # A contact item. Can be accessed as MapiContact.
    elif item_type == ae.mapi.MapiItemType.CONTACT:
        contact = msg.to_mapi_message_item()
        # You can access to MapiContact properties there. 
        # A name_info.display_name for example. 
        print(contact.name_info.display_name)
    # A calendar item. Can be accessed as MapiCalendar.
    elif item_type == ae.mapi.MapiItemType.CALENDAR:
        calendar = msg.to_mapi_message_item()
        # You can access to MapiCalendar properties there. 
        # A location for example. 
        print(calendar.location)
    # A distribution list. Can be accessed as MapiDistributionList.
    elif item_type == ae.mapi.MapiItemType.DIST_LIST:
        dlist = msg.to_mapi_message_item()
        # You can access to MapiDistributionList properties there
    # A Journal entry. Can be accessed as MapiJournal.
    elif item_type == ae.mapi.MapiItemType.JOURNAL:
        journal = msg.to_mapi_message_item()
        # You can access to MapiJournal properties there
    # A StickyNote. Can be accessed as MapiNote.
    elif item_type == ae.mapi.MapiItemType.NOTE:
        note = msg.to_mapi_message_item()
        # You can access to MapiNote properties there
    # A Task item. Can be accessed as MapiTask.
    elif item_type == ae.mapi.MapiItemType.TASK:
        task = msg.to_mapi_message_item()
        # You can access to MapiTask properties there

```

## **Converting MSG to MIME message**
Aspose.Email API provides the capability of converting MSG file to MIME message using the ToMailMessage method.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertMSGToMimeMessage-ConvertMSGToMimeMessage.py" >}}

## **Setting Timeout to Conversion and Loading of a Message**

To limit the time in milliseconds of the message conversion (default value 3 sec), the **timeout** property of the [MailConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#mailconversionoptions-class) class is used. 

Here's how you can set a timeout for message conversion and loading processes:

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")
options = ae.mapi.MailConversionOptions()
options.timeout = 5000
mailMessage = msg.to_mail_message(options)
```

By setting a timeout for message conversion and loading processes, you can control the maximum time these operations are allowed to run. After setting the timeout, you can proceed with your message conversion and loading processes. 


## **Outlook Template (OFT) files Processing** 

### **Load, Modify, and Save an OFT File**

Outlook templates (OFT) offer a convenient way to streamline the process of sending repetitive email messages. Instead of composing the same email from scratch each time, you can create a message in Outlook and save it as an Outlook Template (OFT). Later, whenever you need to send a similar message, you can quickly generate it from the template. This approach saves you the effort of rewriting the same content in the message body, specifying the subject line, formatting, and more.

Aspose.Email's [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class provides a powerful tool to load and manipulate Outlook template files (OFT). Once an Outlook template is loaded into an instance of the MailMessage class, you can easily update properties such as sender, recipient, message body, subject, and various other attributes.

```py
import aspose.email as ae

# Load the OFT file
oft_file_path = "your_template.oft"
mail_message = ae.MailMessage.load(oft_file_path)

# Update properties as needed
mail_message.subject = "Updated Subject"
mail_message.body = "Updated body text."

# Save the updated message as an MSG file
msg_file_path = "updated_message.msg"
mail_message.save(msg_file_path, ae.MailMessageSaveType.outlook_message_format_unicode)

print(f"Updated message saved to {msg_file_path}")
```
After making the necessary updates, you can send the email using the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class:

```py
# Send the email
smtpClient.send(message)
```

### **Saving Outlook MSG file as Template**

For this purpose, you can use the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class to create an email, then save it as an OFT file. The following code sample will show you how to save an email as an Outlook Template:

```py
import aspose.email as ae

# Create a new MailMessage
message = ae.MailMessage()
message.subject = "Sample Outlook Template"
message.html_body = "<html><body>This is the body of the email.</body></html>"
message.from_address = ae.MailAddress("your.email@example.com", "Your Name")

# Save the MailMessage as an Outlook Template (OFT) file
oft_file_path = "sample_template.oft"
message.save(oft_file_path, ae.SaveOptions.default_oft)

print(f"Outlook Template saved as {oft_file_path}")
```
### **OFT or MSG: Determine the type of a MapiMessage**

The following code snippet illustrates how to determine whether a loaded MAPI message represents a standard email message or an Outlook Template (OFT):

```py
msg = ae.mapi.MapiMessage.Load("message.msg");
isOft = msg.is_template # returns false

msg = ae.mapi.MapiMessage.Load("message.oft");
isOft = msg.IsTemplate; # returns true
```
After loading the MSG file, the code checks whether the **is_template** property of the [MapiMessaage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class  is True or False. In case it returns *false*, the loaded message is a standard email message, not an Outlook Template, otherwise, if it returns *true*, the message is not a standard email message, it is an Outlook Template.

### **Saving MapiMessage or MailMessage as OFT** 

The [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) is an abstract base class for classes that allow the user to specify additional options when saving a MailMessage into a particular format. The following code sample demonstrates how to save a message to OFT format:

```py
import aspose.email as ae

# Save the MailMessage to OFT format
eml = ae.MailMessage.load("message.eml")

eml.save("message.oft", ae.SaveOptions.default_oft)

# or alternative way 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# or alternative way 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
eml.save("message.oft", save_options)

# Save the MapiMessage to OFT format
msg = ae.mapi.MapiMessage.load("message.msg")

msg.save("message.oft", ae.SaveOptions.default_oft)

# or alternative way 2
save_options = ae.MsgSaveOptions(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)

# or alternative way 3
save_options = ae.SaveOptions.create_save_options(ae.MailMessageSaveType.outlook_template_format)
msg.save("message.oft", save_options)
```

## **Managing Messages with Digital Signatures**

The library provides the [LoadOptions](https://reference.aspose.com/email/python-net/aspose.email/loadoptions/#loadoptions-class) class, an abstract base class for classes that allow the user to specify additional options when loading a MailMessage from a particular format. The signature preserving option is set by default.

### **Convert from EML to MSG Preserving Signature** 

The code sample below demonstrates how to load a message, convert it to MSG format and save as MSG (the signature is preserved by default): 

```python

import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
message = ae.MailMessage.load("Message.eml", loadOptions)
# Save as MSG
message.save("ConvertEMLToMSG_out.msg", ae.SaveOptions.default_msg_unicode)
```

### **Convert S/MIME Messages from MSG to EML**

Aspose.Email allows you to convert from MSG to EML preserving a digital signature as shown in the following code snippet.

```python
import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
smime_eml = ae.MailMessage.load("smime.eml", loadOptions)

conversion_options = ae.mapi.MapiConversionOptions(ae.mapi.OutlookMessageFormat.UNICODE)
msg = ae.mapi.MapiMessage.from_mail_message(smime_eml, conversion_options)
# Save File to disk
msg.save("ConvertMIMEMessagesFromMSGToEML_out.msg")
```
## **Set Color Category for Outlook MSG Files**

Sometimes you may need to differentiate emails of particular importance and visually organize them. The library provides a way to do this by assigning a specific color to a message item. When you set a color category for an item, it allows you to easily identify and locate related items at a glance. Use [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/#followupmanager-class) class to set the color category for a message as in the following code example:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Add Two categories
ae.mapi.FollowUpManager.add_category(msg, "Purple Category")
ae.mapi.FollowUpManager.add_category(msg, "Red Category")

# Retrieve the list of available categories
categories = ae.mapi.FollowUpManager.get_categories(msg)

# Remove the specified category and then Clear all categories
ae.mapi.FollowUpManager.remove_category(msg, "Red Category")
ae.mapi.FollowUpManager.clear_categories(msg)

```

## **Accessing Follow Up Information from MSG file**

### **Extract Read and Delivery Receipt Information**

The code sample below demonstrates how to extract recipient information and their track status from an Outlook message (MSG) file:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("received.msg")

for recipient in msg.recipients:
    print(f"Recipient: {recipient.display_name}")
    print(f"Delivery time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_DELIVERY]}")
    print(f"Read time:  {recipient.properties[ae.mapi.MapiPropertyTag.RECIPIENT_TRACKSTATUS_TIME_READ]}")
```

## **Creating Forward and Reply Messages**

Aspose.Email provides straightforward ways to create forward and reply messages based on the existing ones. 

### **Creating a Forward Message**

You can use the [ForwardMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/forwardmessagebuilder/#forwardmessagebuilder-class) class to create a forward message by setting the source message, sender, recipients, subject, and body. Forward messages can include the original message as an attachment or as the body of the forwarded message. You have the flexibility to customize additional properties such as attachments, headers, and formatting options. The code sample below shows how to create a forward message:

```python

import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ForwardMessageBuilder()
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART

forwardMsg = builder.build_response(msg)
forwardMsg.save("forward_out.msg")

```

### **Creating a Reply Message**

The [ReplyMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/replymessagebuilder/#replymessagebuilder-class) class is used to configure reply settings, including the source message, sender, recipients, reply mode, subject prefix, and the reply message body. Reply messages can be created in different reply modes like "Reply to Sender" or "Reply to All" based on your requirement. You can customize various properties such as attachments, headers, and formatting options for the reply message. The code sample below shows how to create a forward message:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ReplyMessageBuilder()

# Set ReplyMessageBuilder Properties
builder.reply_all = True
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART
builder.response_text = "<p><b>Dear Friend,</b></p> I want to do is introduce my co-author and co-teacher. <p><a href=\"www.google.com\">This is a first link</a></p><p><a href=\"www.google.com\">This is a second link</a></p>";

replyMsg = builder.build_response(msg)
replyMsg.save("reply_out.msg")

```
