---
title: Load Email Message using Aspose.Email and Apache POI HSMF
type: docs
weight: 40
url: /java/load-email-message-using-aspose-email-and-apache-poi-hsmf/
---

## **Aspose.Email - Load Email Messages**
{{% alert color="primary" %}} 

The **load** method exposed by **MailMessage** class can be called by developers to load Email messages.

{{% /alert %}} 

Load different type of email messages

**Java**

{{< highlight java >}}

 //Create MailMessage instance by loading an Eml/Msg/Emlx/Mht file

MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

MailMessage messageEML 	= MailMessage.load(dataDir + "message.eml");

MailMessage messageEMLX = MailMessage.load(dataDir + "message.emlx");

MailMessage messageMHT 	= MailMessage.load(dataDir + "message.mht");

{{< /highlight >}}
## **Apache POI HSMF - Load Email Messages**
{{% alert color="primary" %}} 

Apache POI HSMF provides MAPIMessages constructor which takes filename to load new MAPIMessage.

{{% /alert %}} 

**Java**

{{< highlight java >}}

 String filename = dataDir + "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

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
