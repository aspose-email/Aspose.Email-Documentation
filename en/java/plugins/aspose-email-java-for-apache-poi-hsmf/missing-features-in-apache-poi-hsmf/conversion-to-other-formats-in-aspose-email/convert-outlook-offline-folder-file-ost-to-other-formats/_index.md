---
title: Convert Outlook Offline Folder File (OST) to Other Formats
ArticleTitle: Convert Outlook Offline Folder File (OST) to Other Formats
type: docs
weight: 20
url: /java/convert-outlook-offline-folder-file-ost-to-other-formats/
---

## **Aspose.Email - Convert OST to Other Formats**
{{% alert color="primary" %}} 

Microsoft Outlook creates PST file for email storage when you use POP3 or IMAP mail servers to download messages. It creates an OST file when you use Microsoft Exchange as your mail server. OST supports larger file sizes compared to PST.

{{% /alert %}} 

Aspose.Email makes it possible to convert an OST file to PST with a single line of code. Similarly, OST file can be created from PST file using the same line of code with the FileFormat enumerator.

**Java**

{{< highlight java >}}

 PersonalStorage ost = PersonalStorage.fromFile(dataDir + "outlook.ost");

ost.saveAs(dataDir + "AsposeOST-PST.pst", FileFormat.Pst);

{{< /highlight >}}
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
