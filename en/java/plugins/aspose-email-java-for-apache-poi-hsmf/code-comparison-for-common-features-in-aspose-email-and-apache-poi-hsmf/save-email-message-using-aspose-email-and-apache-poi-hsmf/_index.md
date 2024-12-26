---
title: Save Email Message using Aspose.Email and Apache POI HSMF
ArticleTitle: Save Email Message using Aspose.Email and Apache POI HSMF
type: docs
weight: 50
url: /java/save-email-message-using-aspose-email-and-apache-poi-hsmf/
---

## **Aspose.Email - Save Email Message**
MailMessage.save method is available to save EMail messages in various formats.

**Java**

{{< highlight java >}}

 MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

messageMSG.save(dataDir + "AsposeMessage.msg");

messageMSG.save(dataDir + "AsposeMessage.eml");

messageMSG.save(dataDir + "AsposeMessage.emlx");

messageMSG.save(dataDir + "AsposeMessage.mht");

{{< /highlight >}}
## **Apache POI HSMF - Save Email Message**
EMail body can be extracted to create new file.

**Java**

{{< highlight java >}}

 String filename = "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

PrintWriter txtOut = new PrintWriter("ApacheMessage.txt");

txtOut.println("Email Body: " + msg.getTextBody());

txtOut.close();

{{< /highlight >}}
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)

{{% alert color="primary" %}} 

For more details, visit [Update and Save an Email](/email/java/loading-and-saving-message/).

{{% /alert %}}
