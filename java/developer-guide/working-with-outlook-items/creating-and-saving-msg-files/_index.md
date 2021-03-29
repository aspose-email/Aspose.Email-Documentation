---
title: Creating and Saving MSG Files
type: docs
weight: 10
url: /java/creating-and-saving-msg-files/
---


Aspose.Email supports creating Outlook message (MSG) files. This article explains how to:

- Create MSG messages.
- Create MSG messages with attachments.
- Create a MSG message with an RTF body.
- Save a message as a draft.
- Work with body compression.
## **Creating and Saving Outlook Messages**
The [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class has the [save](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#save\(java.lang.String\)) method that can save Outlook MSG files to disk or stream. The code snippets below create an instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class, set properties like from, to, subject and body. The [save](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#save\(java.lang.String\)) method takes the file name as an argument. In addition, the Outlook Messages can be created with a [compressed RTF body](#creating-msg-files-with-rtf-body) using the [MapiConversionOptions](https://apireference.aspose.com/email/java/com.aspose.email/MapiConversionOptions).

1. Create a new instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class and set the From, To, Subject and Body properties.
1. Call the [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) class [fromMailMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage#fromMailMessage\(java.lang.String\)) method which accepts the object of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) type. The [fromMailMessage](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage#fromMailMessage\(java.lang.String\)) method converts the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) into a [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) (MSG).
1. Call the [MapiMessage.save](https://apireference.aspose.com/java/email/com.aspose.email/MapiMessage#save\(java.lang.String\)) method to save the MSG file.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setBody("This is test body");

// Create an instance of the MapiMessage class and pass MailMessage as argument
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);

// Save the message (MSG) file
String strMsgFile = "CreatingAndSavingOutlookMessages_out.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~
## **Creating MSG Files With Attachments**
[In the example above](#creating-and-saving-outlook-messages), we created a simple MSG file. Aspose.Email also supports saving message files with attachments. All you need to do is to add the attachments to the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) instance. Add attachments by calling the *addItem* method on the [MailMessage.Attachments](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#getAttachments()) collection.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

String[] files = new String[2];
files[0] = "attachment.doc";
files[1] = "attachment.png";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setBody("This is test body");

// Add the attachments
for (String strFileName : files)
{
    mailMsg.getAttachments().addItem(new Attachment(strFileName));
}

// Create an instance of MapiMessage class and pass MailMessage as argument
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
String strMsgFile = "CreateMessagesWithAttachments.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~
## **Creating MSG Files With RTF Body**
You can also create Outlook Message (MSG) files with rich text (RTF) bodies with Aspose.Email. The RTF body supports text formatting. Create one by setting the [MailMessage.HtmlBody](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#getHtmlBody()) property. When you convert a [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) instance into a [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) instance, the HTML body is converted into RTF. This way, the formatting of the email body is preserved.

The following example creates an MSG file with an RTF body. There is one heading, bold and underline formatting applied in the HTML body. This formatting is retained when the HTML is converted into RTF.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setHtmlBody("<h3>rtf example</h3><p>creating an <b><u>outlook message (msg)</u></b> file using Aspose.Email.</p>");

MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
outlookMsg.save(dataDir + "CreatingMSGFilesWithRTFBody_out.msg");
~~~
## **Saving Message in Draft Status**
Emails are saved as drafts when someone has started editing them but wants to return to them to complete them later. Aspose.Email supports saving email messages in draft status by setting a message flag. Below is the sample code to save an Outlook email message (MSG) as a draft.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Change properties of an existing MSG file
String strExistingMsg = "message.msg";

// Load the existing file in MailMessage and Change the properties
MailMessage msg = MailMessage.load(dataDir + strExistingMsg, new MsgLoadOptions());
msg.setSubject(msg.getSubject() + " NEW SUBJECT (updated by Aspose.Email)");
msg.setHtmlBody(msg.getHtmlBody() + " NEW BODY (udpated by Aspose.Email)");

// Create an instance of type MapiMessage from MailMessage, Set message flag to un-sent (draft status) and Save it
MapiMessage mapiMsg = MapiMessage.fromMailMessage(msg);
mapiMsg.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapiMsg.save(dataDir + "SavingMessageInDraftStatus_out.msg");
~~~
## **Implications of Body Compression**
The RTF body compression method can be used to generate a smaller size MSG. However, this results in slower creation speed. To create messages with improved speed, set the flag to **false**. This flag, in turn, has an effect on the created PSTs: smaller MSG files result in smaller PST, and large MSG files result in slower PST creation.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MailMessage message = MailMessage.load(fileName);
MapiConversionOptions options = new MapiConversionOptions();
options.setUseBodyCompression(true);
MapiMessage ae_mapi = MapiMessage.fromMailMessage(message, options);
~~~
