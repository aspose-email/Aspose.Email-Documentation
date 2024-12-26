---
title: First Application with Aspose.Email Outlook
ArticleTitle: First Application with Aspose.Email Outlook
type: docs
weight: 280
url: /java/first-application-with-aspose-email-outlook/
---


This section demonstrates how to use Aspose.Email Mapi. We create a small application that loads an outlook message file (TestMessage.msg) and displays the subject, from and to addresses, and body content. Follow these steps to create your first application using Aspose.Email Outlook.

1. Create an instance of the [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) class by giving the path of the message file.
1. Use the public properties to display the subject, from, to and body.

The implementation of above steps is demonstrated below in the following code snippet.



~~~Java
// Load the outlook message file
MapiMessage msg = MapiMessage.fromFile("outlookmessage.msg");

// Use the public properties
//read subject
System.out.print("Subject:" + msg.getSubject());

//sender name
System.out.print("From:" + msg.getSenderName());

//message body
System.out.print("Body:" + msg.getBody());

//Attachments
for(MapiAttachment att : msg.getAttachments())
{
    System.out.print("Attachment Name:"+att.getFileName());
    att.save(att.getFileName());
}
~~~
