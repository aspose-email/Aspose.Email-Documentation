---
title: Converting and Processing Outlook Templates (OFT)
ArticleTitle: Converting and Processing Outlook Templates (OFT)
type: docs
weight: 40
url: /python-net/converting-and-processing-oft-files/
---

**Outlook templates (OFT)** offer a convenient way to streamline the process of sending repetitive email messages. Instead of composing the same email from scratch each time, you can create a message in Outlook and save it as an Outlook Template (OFT). Later, whenever you need to send a similar message, you can quickly generate it from the template. This approach saves you the effort of rewriting the same content in the message body, specifying the subject line, formatting, and more.

## **Load, Modify, and Save an OFT File**

Aspose.Email provides a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class to load and manipulate Outlook template files (OFT). Once an Outlook template is loaded into an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class, you can easily update properties such as sender, recipient, message body, subject, and various other attributes.

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

## **Save MSG Files as Outlook Templates**

To create an email, then save it as an OFT file, use the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) class. The following code sample shows how to save an email as an Outlook Template:

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

## **Identify OFT and MSG File Types**

The following code snippet illustrates how to determine whether the loaded MAPI message represents a standard email message or an Outlook Template (OFT):

```py
msg = ae.mapi.MapiMessage.Load("message.msg");
isOft = msg.is_template # returns false

msg = ae.mapi.MapiMessage.Load("message.oft");
isOft = msg.IsTemplate; # returns true
```

After loading the MSG file, the code checks whether the **is_template** property of the [MapiMessaage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class  is True or False. In case it returns *false*, the loaded message is a standard email message, not an Outlook Template, otherwise, if it returns *true*, the message is not a standard email message, it is an Outlook Template.

## **Save MapiMessage or MailMessage as OFT** 

The [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) is an abstract base class that allows the user to specify additional options when saving a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) into a particular format. The following code sample demonstrates how to save a message to OFT format:

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
