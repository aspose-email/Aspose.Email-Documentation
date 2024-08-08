---
title: Read Outlook Template File OFT
type: docs
weight: 40
url: /java/read-outlook-template-file-oft/
---

## **Aspose.Email - Read Outlook Template OFT**
Aspose.Email's [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) class can be used to load a Microsoft Outlook template (OFT) file. Once the Outlook template is loaded in an instance of theMailMessage class, you may update the sender, recipient, body, subject and other properties.

**Java**

``` java

 // Load the Outlook template (OFT) file in MailMessage's instance

MailMessage message = MailMessage.load(dataDir + "sample.oft");

// Set the sender and recipients information

String senderDisplayName = "John";

String senderEmailAddress = "john@abc.com";

String recipientDisplayName = "William";

String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));

message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));

message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Set the name, location and time in email body

String meetingLocation = "<u>" + "Hall 1, Convention Center, New York, USA" + "</u>";

String meetingTime = "<u>" + "Monday, June 28, 2010" + "</u>";

message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));

message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Save the message in MSG format and open in Office Outlook

MapiMessage mapimessage = new MapiMessage().fromMailMessage(message);

mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);

mapimessage.save(dataDir + "AsposeInvitation.msg");

```
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readoft/AsposeReadOFT.java)

{{% alert color="primary" %}} 

For more details, visit [Read Outlook Template File (OFT)](/email/java/managing-message-files-with-aspose-email-outlook/).

{{% /alert %}}
