---
title: Extract Message Headers using Aspose.Email and Apache POI HSMF
type: docs
weight: 30
url: /java/extract-message-headers-using-aspose-email-and-apache-poi-hsmf/
---

## **Aspose.Email - Extract Message Headers**
The email header represents an Internet and RFC defined standard set of header fields included in Internet email messages. An email header can be specified using the MailMessage class. Common header types are defined in the HeaderType class. It is a sealed class working like normal enumeration.

**Java**

{{< highlight java >}}

 //Gets Email Headers

System.out.println("From: " 	+ message.getFrom());

System.out.println("To: " 	+ message.getTo());

System.out.println("CC: " 	+ message.getCC());

System.out.println("Bcc: " 	+ message.getBcc());

System.out.println("Subject: " 	+ message.getSubject());

{{< /highlight >}}
## **Apache POI HSMF - Extract Message Headers**
MAPIMessage class provides the methods to access headers of email messages.

**Java**

{{< highlight java >}}

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("From: " + msg.getDisplayFrom());

System.out.println("To: " + msg.getDisplayTo());

System.out.println("CC: " + msg.getDisplayCC());

System.out.println("BCC: " + msg.getDisplayBCC());

System.out.println("Subject: " + msg.getSubject());

{{< /highlight >}}
## **Download Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

For more details, visit [Extracting Email Headers](/email/java/extracting-message-contents-from-emails/).

{{% /alert %}}
