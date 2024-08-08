---
title: Add Embedded Images to Email Message in Aspose.Email
type: docs
weight: 20
url: /java/add-embedded-images-to-email-message-in-aspose-email/
---

## **Aspose.Email - Add Embedded Images to Email Message**
With Aspose.Email Java developers can easily embed any image into an email message as well as attach it, as discussed in [Manage Attachments in Email Message](/email/java/working-with-message-attachments). To embed an image, Aspose.Email uses a specialized class, [LinkedResource](https://apireference.aspose.com/email/java/com.aspose.email/linkedresource).

**Java**

``` java

 // Set Html body. It also contains <img> tag with cid. cid = LinkedResource.ContentID

message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>"

        + "<font color=blue>This line is in blue color</font><br><br>" +

        "Here is an embedded image.<img src=cid:companylogo>");

// Add linked resource

LinkedResource res = new LinkedResource(dataDir + "Aspose.png", MediaTypeNames.Image.PNG);

res.setContentId("companylogo");

// Add Linked resource to the message's Linked resource collection

message.getLinkedResources().addItem(res);

```
## **Download Running Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/addembeddedimagestoemail/AsposeEmbeddedImageInEmail.java)

{{% alert color="primary" %}} 

For more details, visit [Add Embedded Images to Email Message](http://docs.aspose.com:8082/docs/display/emailjava/Add+Embedded+Images+to+Email+Message).

{{% /alert %}}
