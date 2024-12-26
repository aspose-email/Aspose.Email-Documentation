---
title: Read Embedded Email Attachments from Message in Aspose.Email
ArticleTitle: Read Embedded Email Attachments from Message in Aspose.Email
type: docs
weight: 30
url: /java/read-embedded-email-attachments-from-message-in-aspose-email/
---

## **Aspose.Email - Read Embedded Email Attachments from Message**
Sometimes, we get emails with other emails embedded in them as attachments. These embedded emails are complete messages with their own recipient list, subject, body and even attachments. Each of these messages can also contian embedded messages.
Using Aspose.Email Java, developers can access each embedded message as an individual message. This example shows to use the recursive functionality.

**Java**

{{< highlight java >}}

 MailMessage message = MailMessage.load(dataDir + "embedded.msg", MessageFormat.getMsg());

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Attachment Name: " + att.getName());

    // Get the name of attachment. If msg subject contains characters like :, /, \ etc., replace with space

    // because windows cannot save files with these characters

    // also save first 50 characters as file name to avoid long file names

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    if (attFileName.length() > 50)

    {

        attFileName = attFileName.substring(0, 50);

    }

    String attExt = (att.getName().substring(att.getName().lastIndexOf("."), att.getName().lastIndexOf(".") + 4));

    // Save the attachment to disk

    att.save(dataPath + attFileName + attExt);

    // Check if it is an orphaned text attachment file (ATT00001.txt....) and of type eml

    if ((attExt.equals(".eml")) || (att.getContentType().getMediaType().equals("text/plain") && att.getName().contains(".txt") == true && att.getName().contains("ATT") == true))

    {

        // Try to load this text file in MailMessage

        MailMessage attMsg = MailMessage.load(dataPath + attFileName + attExt, MessageFormat.getEml());

        // Call the function recursively to parse this message and attachments

        ParseMessage(attMsg);

    }

}

{{< /highlight >}}
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)

{{% alert color="primary" %}} 

For more details, visit [Read Embedded Email Attachments from Message](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}
