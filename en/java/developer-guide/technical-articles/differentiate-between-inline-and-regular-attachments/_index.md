---
title: Differentiate between Inline and Regular Attachments
type: docs
weight: 10
url: /java/differentiate-between-inline-and-regular-attachments/
---

{{% alert color="primary" %}} 

Email messages may contain inline images as well as attachments. Using [MailMessage](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailMessage), the inline attachments can be extracted from the [LinkedResourceCollection](https://apireference.aspose.com/email//java/com.aspose.email/linkedresourcecollection) collection, while the regular attachments can be accessed and extracted with a message's [AttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/attachmentcollection) collection. However, this is different when the message is loaded using [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage), as all the inline images and regular attachments are accessible to user in the same [MapiAttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/mapiattachmentcollection). Hence, a method that can differentiate between an inline and a regular attachment when [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) is used is needed.

{{% /alert %}} 

This article explains how to differentiate inline attachments from regular ones using [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage). When deciding, the body type of [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) is taken into account as follow:

- **Plain text body**: Email messages with plain text body type need not be checked, as all attachments in such messages are always regular attachments.
- **HTML body**: For messages with a HTML body, the attachment should not only contain the PR_ATTACH_FLAGS (0x37140003) property, but its value should be equal to 0x00000004 for inline attachments. If this condition is met, then it further depends on the PR_ATTACH_CONTENT_LOCATION and PR_ATTACH_CONTENT_ID tags to determine the nature of attachment. However, in the absence of the PR_ATTACH_FLAGS MAPI tag, the attachment is checked for PR_ATTACH_DISPOSITION (0x3716001F or 0x3716001E) property to determine the attachment type.
- **RTF body**: If the body is RTF, then all OLE attachments are inline attachments. The value of PR_ATTACH_METHOD for all OLE attachments is equal to 0x00000006.

The following code sample demonstrates to programatically differentiate between inline and regular attachments. The function isInlineAttachment takes an attachment and MapiMessage as input parameters and returns true if the attachment is an inline attachment.

~~~java
public static boolean isInlineAttachment(MapiAttachment att, MapiMessage msg) {
    if (msg.getBodyType() == BodyContentType.PlainText)
        // ignore indications for plain text messages
        return false;
    else if (msg.getBodyType() == BodyContentType.Html) {
        // check the PidTagAttachFlags property
        if (att.getProperties().containsKey(0x37140003)) {
            Long attachFlagsValue = att.getPropertyLong(0x37140003);
            if (attachFlagsValue != null && (attachFlagsValue > 3 || attachFlagsValue < 1)) {
                // check PidTagAttachContentId property
                if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                        || att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W)) {
                    String contentId = att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                            ? att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            : att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W);
                    if (!contentId.isEmpty() && msg.getBodyHtml().contains(contentId)) {
                        return true;
                    }
                }
                // check PidTagAttachContentLocation property
                if (att.getProperties().containsKey(0x3713001E) 
                        || att.getProperties().containsKey(0x3713001F)) {
                    String contentLocation = att.getProperties().containsKey(0x3713001E) 
                            ? att.getPropertyString(0x3713001E) : att.getPropertyString(0x3713001F);
                    if (!contentLocation.isEmpty() && msg.getBodyHtml().contains(contentLocation)) {
                        return true;
                    }
                }
            } else if ((att.getProperties().containsKey(0x3716001F) && att.getPropertyString(0x3716001F).equalsIgnoreCase("inline"))
                    || (att.getProperties().containsKey(0x3716001E) && att.getPropertyString(0x3716001E).equalsIgnoreCase("inline"))) {
                return true;
            }
        } else if ((att.getProperties().containsKey(0x3716001F) && att.getPropertyString(0x3716001F).equalsIgnoreCase("inline"))
                || (att.getProperties().containsKey(0x3716001E) && att.getPropertyString(0x3716001E).equalsIgnoreCase("inline"))) {
            return true;
        }
        return false;
    } else if (msg.getBodyType() == BodyContentType.Rtf) {
        // If the body is RTF, then all OLE attachments are inline attachments.
        // OLE attachments have 0x00000006 for the value of the PidTagAttachMethod property
        if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_METHOD)) {
            return att.getPropertyLong(MapiPropertyTag.PR_ATTACH_METHOD) == 0x00000006;
        }
        return false;
    } else
        throw new ArgumentOutOfRangeException();
}
~~~



This code snippet uses the isInlineAttachment() function to evaluate attachments.

**Java**

~~~java
String fileName = ("Sample.msg");
MapiMessage message = MapiMessage.fromFile(fileName);
MapiAttachmentCollection attachments = message.getAttachments();
for (int i = 0; i < attachments.size(); i++) {
    MapiAttachment attachment = (MapiAttachment) attachments.get(i);
    if (isInlineAttachment(attachment, message)) {
        System.out.println(attachment.getLongFileName() + " is inline attachment");
    } else {
        System.out.println(attachment.getLongFileName() + " is regular attachment");
    }
}
~~~
