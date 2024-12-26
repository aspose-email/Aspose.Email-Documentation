---
title: Extract Message Body using Aspose.Email and Apache POI HSMF
ArticleTitle: Extract Message Body using Aspose.Email and Apache POI HSMF
type: docs
weight: 20
url: /java/extract-message-body-using-aspose-email-and-apache-poi-hsmf/
---

## **Aspose.Email - Extract Message Body**
The MailMessage represents an email message and allows developers to access email message properties. The header information (discussed in [Extracting Email Headers](http://www.aspose.com/docs/display/emailjava/Extracting+Email+Headers)) can be extracted and manipulated in different ways.

**Java**

{{< highlight java >}}

 MailMessage msg = MailMessage.load(dataDir + "message.msg");

System.out.println("Body:"+ msg.getBody());

System.out.println("Text Body:"+ msg.getTextBody());

System.out.println("Text Body HTML:"+ msg.getHtmlBody());

{{< /highlight >}}
## **Apache POI HSMF - Extract Message Body**
MAPIMessage can access email message body.

**Java**

{{< highlight java >}}

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("Text Body:"+ msg.getTextBody());

{{< /highlight >}}
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

For more details, visit [Displaying Email Information on Screen](/email/java/display-information-in-custom-order-in-mhtml-files/).

{{% /alert %}}
