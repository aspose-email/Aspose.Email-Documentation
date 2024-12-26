---
title: Check PST Password Protection
ArticleTitle: Check PST Password Protection
type: docs
weight: 10
url: /java/check-pst-password-protection/
---

## **Aspose.Email - Check PST Password Protection**
Microsoft Outlook lets users password protect PST files to restrict access to them. Aspose.Email can detect password protection on a PST file. This page shows how to check a PST for a password and also how to check if the password applied on it is correct.

**Java**

``` java

 if (pst.getMessageStoreProperties().contains(MapiPropertyTag.PR_PST_PASSWORD))

{

    long passwordHash = pst.getMessageStoreProperties().get_Item(MapiPropertyTag.PR_PST_PASSWORD).getLong();

    return passwordHash != 0;

}

```
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)

{{% alert color="primary" %}} 

For more details, visit [Working with PST Password Protection Properties](/email/java/working-with-calendar-items-in-pst-file/).

{{% /alert %}}
