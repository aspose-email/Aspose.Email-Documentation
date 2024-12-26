---
title: Convert MSG to Other Formats
ArticleTitle: Convert MSG to Other Formats
type: docs
weight: 10
url: /java/convert-msg-to-other-formats/
---

## **Aspose.Email - Convert MSG to Other Formats**
Conversion

**Java**

``` java

 // Initialize and Load an existing MSG file by specifying the MessageFormat

MailMessage msg = MailMessage.load(dataDir + "message.msg");

// Save the Email message to disk by specifying the EML and MHT MailMessageSaveType

msg.save(dataDir + "AsposeMessage.eml");

msg.save(dataDir + "Asposemessage.mhtml");

```

Aspose.Email makes it easy to convert any message type to another format. To demonstrate this feature, different types of messages can be loaded from disk and saves them back in other formats. The base class SaveOptions and the classes EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions for additional settings when saving MailMessage can be used for saving messages to other formats. The article shows how to use these classes to save a sample email as:

- [EML format](/email/java/loading-and-saving-message/#loading-eml-and-saving-as-eml)).
- [Outlook MSG](/email/java/loading-and-saving-message/#loading-eml-saving-to-msg).
- [MHTML format](/email/java/loading-and-saving-message/#saving-mailmessage-as-mhtml).
- [HTML format](/email/java/loading-and-saving-message/#exporting-email-to-eml).
  and also shows how to preserver original email address
- [Preserve Original Email Address](/email/java/loading-and-saving-message/)
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
