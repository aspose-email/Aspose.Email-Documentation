---
title: Parsing Microsoft Outlook Message Files
type: docs
weight: 80
url: /java/parsing-microsoft-outlook-message-files/
---


With Aspose.Email, you can parse Microsoft Outlook messages in just a few lines of codes. This article shows how. Aspose.Email has classes for performing many programming tasks with Outlook messages. The code example below shows how to:

1. Load an email message.
1. Get the email subject.
1. Get the name of the sender.
1. Get the full message body.
1. Find out if there are attachments.
1. Get the file names of any attachments and save them.

The following code snippet shows you how to parse Microsoft Outlook message files.



~~~Java
// The path to the File directory and Load Microsoft Outlook email message file
String dataDir = "data/";
MapiMessage msg = MapiMessage.fromFile(dataDir + "message3.msg");

// Obtain subject of the email message, sender, body and Attachment count
System.out.println("Subject:" + msg.getSubject());
System.out.println("From:" + msg.getSenderName());
System.out.println("Body:" + msg.getBody());
System.out.println("Attachment Count:" + msg.getAttachments().size());

// Iterate through the attachments
for (MapiAttachment attachment : msg.getAttachments()) {
    // Access the attachment's file name and Save attachment
    System.out.println("Attachment:" + attachment.getFileName());
    attachment.save(dataDir + attachment.getLongFileName());
}
~~~