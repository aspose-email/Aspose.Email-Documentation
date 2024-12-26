---
title: Working with Attachments and Embedded Objects
ArticleTitle: Working with Attachments and Embedded Objects
type: docs
weight: 20
url: /java/working-with-attachments-and-embedded-objects/
---


## **Managing Email Attachments**

An email attachment is a file that is sent along with an email message. The file may be sent as a separate message as well as a part of the message to which it is attached. The [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) class is used with the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage//) class. All messages include a body. In addition to the body, you might want to send additional files. These are sent as attachments and are represented as an instance of the [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) class. You can send any number of attachments but the size of the attachment is limited by the mail server. Gmail, for example, does not support file sizes greater than 10MB.
{{% alert %}}
**Try it out!**

Add or remove email attachments online with the free [**Aspose.Email Editor App**](https://products.aspose.app/email/editor).
{{% /alert %}}

### **Adding Attachment**

To attach an attachment to an email, please follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Create an instance of the [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
1. Load attachment into the [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) instance.
1. Add the [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) instance into the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.

The following code snippet shows you how to add an attachment to an email.

```java
// Create an instance of MailMessage class
MailMessage message = new MailMessage();
message.setFrom(new MailAddress("sender@from.com"));
message.getTo().add("receiver@to.com");
message.setSubject("This is message");
message.setBody("This is body");

// Load an attachment
Attachment attachment = new Attachment("1.txt");

// Add Multiple Attachment in instance of MailMessage class and Save message to disk
message.getAttachments().addItem(attachment);
message.addAttachment(new Attachment("1.jpg"));
message.addAttachment(new Attachment("1.doc"));
message.addAttachment(new Attachment("1.rar"));
message.addAttachment(new Attachment("1.pdf"));
message.save("AddAttachments.eml");
```

Above, we described how to add attachments to your email message with Aspose.Email. What follows shows how to remove attachments, and display information about them on the screen.

### **Removing an Attachment**

To remove an attachment, follow the steps given below:

- Create an instance of [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
- Load attachment in the instance of [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
- Add the attachment to the instance of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Remove the attachments from the instance of [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class using the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class instance.

The following code snippet shows you how to remove an attachment.

```java
// Create an instance of MailMessage class
MailMessage eml = new MailMessage();
eml.setFrom(new MailAddress("sender@from.com"));
eml.getTo().add("receiver@to.com");

// Load an attachment
Attachment attachment = new Attachment("1.txt");
eml.getAttachments().addItem(attachment);

// Remove attachment from your MailMessage
eml.getAttachments().removeItem(attachment);
```

### **Displaying Attachment File Name**

To display the attachment file name, follow these steps:

1. Loop through the attachments in the email message and
   1. Save each attachment.
   1. Display each attachment name on the screen.

The following code snippet shows you how to display an attachment file name on the screen.

```java
MailMessage eml = MailMessage.load("Attachments.eml");

for (Attachment attachment : eml.getAttachments()) {
    // Display the attachment file name
    System.out.println(attachment.getName());
}
```

### **Extracting Email Attachments**

This topic explains how to extract an attachment from an email file. An email attachment is a file that is sent along with an email message. The file may be sent as a separate message as well as a part of the message to which it is attached. All email messages include an option to send additional files. These are sent as attachments and are represented as instances of the [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class. The [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class is used with the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class to work with attachments. To extract attachments from an email message, follow these steps:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Load an email file into the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
- Create an instance of the [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class and use it in a loop to extract all attachments.
- Save the attachment and display it on the screen.

|**Extracted attachments in email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
The following code snippet shows you how to Extract Email Attachments.

```java
MailMessage eml = MailMessage.load("Message.eml", new MsgLoadOptions());

for (Attachment attachment : eml.getAttachments()) {
    attachment.save("MessageEmbedded_out.eml");
    System.out.println(attachment.getName());
}
```

#### **Retrieving Content-Description from Attachment**

Aspose.Email API provides the capability to read attachment Content-Description from attachment header. The following code snippet shows you how to retrieve the content description from the attachment.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");
System.out.println(eml.getAttachments().get_Item(0).getHeaders().get_Item("Content-Description"));
```

#### **Determining if an Attachment is an Embedded Message**

The following code snippet demonstrates how to determine if the attachment is an embedded message or not.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");

System.out.println(eml.getAttachments().get_Item(0).isEmbeddedMessage()
        ? "Attachment is an embedded message."
        : "Attachment isn't an embedded message.");
```
#### **Determine TNEF Formatted Attachments**

The [Attachment.isTnef](https://reference.aspose.com/email/java/com.aspose.email/attachment/#isTnef--) property of the Aspose.Email Java API indicates whether the message attachment is a TNEF formatted message.

The following code snippet demonstrates how to determine if an attachment is TNEF formatted:

```java
MailMessage eml = MailMessage.load(fileName);

for (Attachment attachment : eml.getAttachments()) {
    System.out.println("Is Attachment TNEF?: " + attachment.isTnef());
}
```

#### **Extracting Attachment URI if Attachment is URI-attachment**

The following code snippet demonstrates how to extract Attachment URI.

~~~Java
MailMessage eml = MailMessage.load("fileName");

Attachment attachment = eml.getAttachments().get_Item(0);
if (attachment.isUri()) {
    InputStream inputStream = attachment.getContentStream();
    String uri = new String(IOUtils.toByteArray(inputStream), Charset.forName("utf-8"));
    System.out.println("Attachment URI: " + uri);
}
~~~

### **Adding Reference Attachments**

A reference attachment is an alternative to the local file attachment. In some cases, reference attachments may be preferable, for example, if you want to manage its access. The classes below are used to manage and manipulate email messages and their attachments:

- [ReferenceAttachment](https://reference.aspose.com/email/java/com.aspose.email/referenceattachment/) - Represents a reference attachment. 
- [AttachmentPermissionType](https://reference.aspose.com/email/java/com.aspose.email/attachmentpermissiontype/) - The permission type data associated with a web reference attachment. 
- [AttachmentProviderType](https://reference.aspose.com/email/java/com.aspose.email/attachmentprovidertype/) - The type of web service manipulating the attachment.

The following code sample demonstrates how to load an email message from a file, create a reference attachment with specific properties, and add the attachment to the email message:

```java
MailMessage eml = MailMessage.load("fileName");

ReferenceAttachment refAttach = new ReferenceAttachment("https://[attach_uri]")
refAttach.setName("Document.docx");
refAttach.setProviderType(AttachmentProviderType.OneDrivePro);
refAttach.setPermissionType(AttachmentPermissionType.AnyoneCanEdit);

eml.getAttachments().addItem(refAttach);
```

## **Working with Embedded Objects**

An embedded object is an object that was created with one application and enclosed within a document or file created by another application. For example, a Microsoft Excel spreadsheet can be embedded into a Microsoft Word report, or a video file can be embedded into a Microsoft PowerPoint presentation. When a file is embedded, rather than inserted or pasted into another document, it retains its original format. The embedded document can be opened in the original application and modified.

### **Embedding Objects into an Email**

The [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) class is used with the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class to embed objects in your email messages. To add an embedded object, follow these steps

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Specify the from, to and subject values in [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Create an instance of the [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) class.
1. Create an instance of the [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) class.
1. Load an embedded object into the [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/).
1. Add the loaded embedded object into the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class instance.
1. Add the [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) instance to the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class instance.

The code snippets below produce an email message with both plain text and HTML bodies and an image embedded into the HTML

|**Image embedded into email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
You can send any number of embedded objects. The size of the attachment is limited by the mail server. Gmail, for example, does not support file sizes greater than 10MB. The code snippets below demonstrate how to embed objects into an Email.

```java
// Create an instance of the MailMessage class and Set the addresses and Set the content
MailMessage mail = new MailMessage();
mail.setFrom(new MailAddress("sender@from.com"));
mail.getTo().add("receiver@to.com");
mail.setSubject("This is an email");

// Create the plain text part It is viewable by those clients that don't support HTML
AlternateView plainView = AlternateView.createAlternateViewFromString("This is my plain text content", null, "text/plain");

// Create the HTML part.To embed images, we need to use the prefix 'cid' in the img src value. 
// The cid value will map to the Content-Id of a Linked resource. 
// Thus <img src='cid:barcode'> will map to a LinkedResource with a ContentId of //'barcode'.
AlternateView htmlView = AlternateView.createAlternateViewFromString("Here is an embedded image.<img src=cid:barcode>", null, "text/html");

// Create the LinkedResource (embedded image) and Add the LinkedResource to the appropriate view
LinkedResource barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.JPEG);
barcode.setContentId("barcode");

mail.getLinkedResources().addItem(barcode);
mail.getAlternateViews().addItem(plainView);
mail.getAlternateViews().addItem(htmlView);
mail.save("EmbeddedImage_out.msg", SaveOptions.getDefaultMsgUnicode());
```

### **Removing Embedded Objects from Email**

[LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) accessed via [MailMessage.LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLinkedResources--) property. The [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) collection provides a method to completely remove embedded objects added into an email message. Use the overloaded version of [LinkedResourceCollection.removeAt](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/#removeAt-int-boolean-) method to remove all traces of an embedded object from an email message.

The sample code below shows how to remove embedded objects from an email message.

```java
// Load the test message with Linked Resources
MailMessage msg = MailMessage.load("EmlWithLinkedResources.eml");

// Remove a LinkedResource
msg.getLinkedResources().removeAt(0, true);

// Now clear the Alternate View for linked Resources
msg.getAlternateViews().get_Item(0).getLinkedResources().clear(true);
```

### **Extracting Embedded Objects**

This topic explains how to extract embedded objects from an email file. An embedded object is an object that was created with one application and enclosed within a document or file created by another application. For example, a Microsoft Excel spreadsheet can be embedded into a Microsoft Word report, or a video file can be embedded into a Microsoft PowerPoint presentation. When a file is embedded, rather than inserted or pasted into another document, it retains its original format. The embedded document can be opened in the original application and be modified. To extract an embedded object from an email message, follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Load an email file in the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Create a loop and create an instance of the [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class in it.
1. Save the attachment and display it on screen.
1. Specify the sender and recipient address in the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Send email using the [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class.

The code snippet below extracts embedded objects from an email.

|**Extracted embedded objects in email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
The following code snippet shows you how to extract embedded objects.

```java
MailMessage mailMsg = MailMessage.load("Message.msg", new MsgLoadOptions());

for (Attachment attachment : mailMsg.getAttachments()) {
    attachment.save("MessageEmbedded_out.msg");
    System.out.println(attachment.getName());
}
```

#### **Identify and Extract an embedded attachment from MSG formatted as RTF**

The following code can be used for messages formatted as RTF  to differentiate and extract attachments that are either Inline or appear as Icon in the message body. The following code snippet shows you how to identify and extract an embedded attachment from MSG formatted as RTF.

```java
public static void extractInlineAttachments() {
    MapiMessage message = MapiMessage.load("MSG file with RTF Formatting.msg");
    for (MapiAttachment attachment : message.getAttachments()) {

        if (isAttachmentInline(attachment)) {
            try {
                saveAttachment(attachment, UUID.randomUUID().toString());
            } catch (Exception ex) {
                System.err.println(ex);
            }
        }
    }
}

static boolean isAttachmentInline(MapiAttachment attachment) {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("\u0003ObjInfo".equals(property.getName())) {
            byte[] data = property.getData();
            int odtPersist1 = data[1] << 8 | data[0];
            return (odtPersist1 & 0x40) == 0;
        }
    }
    return false;
}

static void saveAttachment(MapiAttachment attachment, String fileName) throws IOException {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("Package".equals(property.getName())) {
            try (FileOutputStream fs = new FileOutputStream(fileName)) {
                fs.write(property.getData(), 0, property.getData().length);
            }
        }
    }
}
```

## **Retrieving Attachments from Signed Email**

Signed emails contain a single **smime.p7m** attachment. It means that the email is encrypted by SMIME. 
**Smime.p7m** file format is the digital signature. 
To see the contents of this email use the [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/) method. The method returns a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object without a digital signature.

```java
MailMessage signedEml = MailMessage.load("signed.eml");

if (signedEml.isSigned()) {
    for (int i = 0; i < signedEml.getAttachments().size(); i++) {
        System.out.println("Signed email attachment" + i + ": " + signedEml.getAttachments().get_Item(i).getName());
    }

    // The email is signed. Remove a signature.
    MailMessage eml = signedEml.removeSignature();

    System.out.println("Signature removed.");

    for (int i = 0; i < eml.getAttachments().size(); i++) {
        System.out.println("Email attachment" + i + ": " + eml.getAttachments().get_Item(i).getName());
    }
}
```

### **Working with Content-Type and Content-Disposition**

Aspose.Email API provides the capability to work with the attachment [Content-Type](https://datatracker.ietf.org/doc/html/rfc2045#section-5) and [Content-Disposition](https://datatracker.ietf.org/doc/html/rfc2183) from the attachment header. The following code snippet shows you how to get and change the content description from the attachment.

#### **Displaying Content-Type and Content-Disposition parameters**

The following code snippet shows you how to display parameters of Content-Type and Content-Disposition on the screen:

~~~Java
void run(MailMessage message) {
    // Attachments
    for (Attachment attachment : message.getAttachments()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
    // Linked Resources
    for (LinkedResource attachment : message.getLinkedResources()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
}

void printContentType(ContentType contentType) {
    System.out.println("media-type: " + contentType.getMediaType());
    System.out.println("charset: " + contentType.getCharSet());
    System.out.println("name: " + contentType.getName());
}

void printContentDisposition(ContentDisposition contentDisposition) {
    System.out.println("disposition-type: " + contentDisposition.getDispositionType());
    System.out.println("is-inline: " + contentDisposition.getInline());
    System.out.println("filename: " + contentDisposition.getFileName());
    System.out.println("creation-date: " + contentDisposition.getCreationDate());
    System.out.println("modification-date: " + contentDisposition.getModificationDate());
    System.out.println("read-date: " + contentDisposition.getReadDate());
    System.out.println("size: " + contentDisposition.getSize());
}
~~~

#### **Using Content-Type and Content-Disposition parameters with Attachments**

The following code snippet shows you how to use the Content-Type and Content-Disposition parameters with an attachment:

~~~Java
MailMessage eml = MailMessage.load(fileName);

Attachment attachment = new Attachment(pdfFileName, new ContentType("application/octet-stream"));
attachment.getContentDisposition().setDispositionType("attachment");
attachment.getContentDisposition().setFileName(fileName);

eml.addAttachment(attachment);
~~~
