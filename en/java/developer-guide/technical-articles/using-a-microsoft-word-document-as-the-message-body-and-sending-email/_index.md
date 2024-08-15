---
title: Using a Microsoft Word Document as the Message Body and Sending Email
type: docs
weight: 140
url: /java/using-a-microsoft-word-document-as-the-message-body-and-sending-email/
---


This article shows you how to use a Microsoft Word document as the email body and send it to recipients. The sample document is a sales invoice from the Northwind database sample, exported to Microsoft Word format. Aspose.Email for Java deals with network protocols and Microsoft Outlook features and cannot handle Microsoft Word documents. To overcome this, the samples in this article use [Aspose.Words for Java](https://products.aspose.com/words/java/) to load the Word document and convert it to MHTML format. Aspose.Email for Java uses the MHTML document in the email body.
## **Using Microsoft Word Documents as Email Body**
The programming samples below illustrate how to send a Word document as an email body using Aspose.Words for Java and Aspose.Email for Java:

1. Load a Microsoft Word document using Aspose.Word for Java's [Document](https://apireference.aspose.com/words/java/com.aspose.words/Document) class.
1. Save it in MHTML format.
1. Load the MHTML document using Aspose.Email for Java's [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class to set the email body.
1. Set other message properties using different [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class properties and methods.
1. Send the email using Aspose.Email for Java's [SMTPClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) class.

The source document, a sales invoice exported to Microsoft Word from the Microsoft Northwind sample can be seen below. 

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_1.png)

When the message has been sent and received in Microsoft Outlook, it looks like the message below. 

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_2.png)

The HTML formatting and images are preserved as in the original source document when viewed in either Outlook or a web email client like Gmail or Hotmail. Below is a screenshot of the message when opened with Gmail in a Chrome browser. 

![todo:image_alt_text](using-a-microsoft-word-document-as-the-message-body-and-sending-email_3.png)

The following code snippet shows you how to use a Microsoft Word document as the message body and send an email by using [SmtpClient](https://apireference.aspose.com/email/java/com.aspose.email/smtpclient) class instance.



~~~Java
// The path to the File directory
String dataDir = "data/";

// Load a Word document from disk and save it to stream as MHTML
Document wordDocument = new Document(dataDir + "Test.doc");
ByteArrayOutputStream mhtmlStream = new ByteArrayOutputStream();
wordDocument.save(mhtmlStream, SaveFormat.MHTML);

// Load the MHTML in a MailMessage object
MailMessage message = MailMessage.load(new ByteArrayInputStream(mhtmlStream.toByteArray()), new MhtmlLoadOptions());
message.setSubject("Sending Invoice in Email");
message.setFrom(new MailAddress("sender@gmail.com"));
message.setTo(MailAddressCollection.to_MailAddressCollection("recipient@gmail.com"));

// Save the message in MSG format to disk
message.save(dataDir + "WordDocAsEmailBody_out.msg", SaveOptions.getDefaultMsgUnicode());

    // Send the email message
try (SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "sender@gmail.com", "pwd")) {
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    client.send(message);
}
~~~