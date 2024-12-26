---
title: Managing Message Files with Aspose.Email.Outlook
ArticleTitle: Managing Message Files with Aspose.Email.Outlook
type: docs
weight: 30
url: /java/managing-message-files-with-aspose-email-outlook/
---


## **Converting MSG to MIME message**

Aspose.Email API provides the capability of converting MSG files to MIME messages using the [toMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMailMessage-com.aspose.email.MailConversionOptions-) method.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiMessage msg = new MapiMessage(
                            "sender@test.com",
                            "recipient1@test.com; recipient2@test.com",
                            "Test Subject",
                            "This is a body of message.");
MailConversionOptions options = new MailConversionOptions();
options.setConvertAsTnef(true);
MailMessage mail = msg.toMailMessage(options);
~~~

## **Converting MSG to EML Preserving RTF Body** 

The API provides the following methods to preserve RTF body while converting MSG to EML:

- [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-) - Gets or sets a value indicating whether to keep the rtf body in MailMessage.
- [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-) - Gets or sets a value indicating whether to keep the rtf body in MailMessage.

The following code samples demonstrate how to keep the rtf body in MailMessage:

- using [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-)

```java
MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveRtfContent(true);
MailMessage message = MailMessage.load("fileName", options);
```
- using [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-)

```java
MapiMessage mapi = MapiMessage.load("fileName");
MailConversionOptions options = new MailConversionOptions();
options.setPreserveRtfContent(true);
MailMessage message = mapi.toMailMessage(options);
```
## **Converting MSG to MHTML Preserving Category Header**

Aspose.Email API provides the ability to add a category header while converting message to MHTML. This feature is specified by the [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) class as an additional option when saving MailMessage to Mhtml format.

The following code sample demonstrates how to create an MHT (MHTML) file from a MapiMessage object, customize the formatting and headers of the MHT file using MhtSaveOptions, set categories for the email message and then modify the format templates and rendering headers for the MHT file before saving it. 

```java
 MapiMessage msg = new MapiMessage("from@aaa.com", "to@aaa.com", "subj", "body");

msg.setCategories(new String[] { "Urgently", "Important" });

MhtSaveOptions saveOptions = new MhtSaveOptions();

saveOptions.getFormatTemplates().set_Item(MhtTemplateName.CATEGORIES,

    saveOptions.getFormatTemplates().get_Item(MhtTemplateName.CATEGORIES).replace("Categories", "Les catégories"));

saveOptions.getRenderingHeaders().add(MhtTemplateName.CATEGORIES);

msg.save("fileName.mhtml", saveOptions);
```

## **Reading and Writing Outlook Template File (.OFT)**

Outlook templates are very useful when you want to send a similar email message again and again. Instead of preparing the message from scratch each time, first, prepare the message in Outlook and save it as an Outlook Template (OFT). After that, whenever you need to send the message, you can create it from the template, saving time writing the same text in the body or the subject line, setting formatting and so on. Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class can be used to load and read an Outlook template (OFT) file. Once the Outlook template is loaded in an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class, you can update the sender, recipient, body, subject and other properties. After updating the properties:

- Send the email using the [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class or
- Save the message as MSG and do further updates/validation using Microsoft Outlook.

In the code samples below, we:

1. Load the template using the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Update some of the properties.
1. Save the message in MSG format.

The following code snippet shows you how to load the OFT file, update the message and save it in MSG format.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Load the Outlook template (OFT) file in MailMessage's instance
MailMessage message = MailMessage.load(dataDir + "sample.oft", new MsgLoadOptions());

// Set the sender and recipients information
String senderDisplayName = "John";
String senderEmailAddress = "john@abc.com";
String recipientDisplayName = "William";
String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));
message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));
message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Set the name, location and time in email body
String meetingLocation = "<u>" + "Hall 1, Convention Center, New York, USA" + "</u>";
String meetingTime = "<u>" + "Monday, June 28, 2010" + "</u>";
message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));
message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Save the message in MSG format and open in Office Outlook
MapiMessage mapimessage = MapiMessage.fromMailMessage(message);
mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapimessage.save(dataDir + "ReadAndWritingOutlookTemplateFile_out.msg");
~~~

### **Saving Outlook MSG file as Template**

The following code snippet shows you how to save the outlook MSG file as a template.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

try (MapiMessage mapi = new MapiMessage("test@from.to", "test@to.to", "template subject", "Template body")) {
    mapi.saveAsTemplate(dataDir + "mapiToOft.msg");
}
~~~

## **Setting Color Category for Outlook MSG Files**

A color category marks an email message for some kind of importance or category. Microsoft Outlook lets users assign color categories to differentiate emails. To handle the color category, use the [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/). It contains functions such as [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-), [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-), [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) and [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-).

- [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-) takes [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) and the color category string, for example, "Purple Category" or "Red Category" as arguments.
- [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-) takes [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) and the color category string to be removed from the message.
- [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) is used to remove all the color categories from the message.
- [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-) is used to retrieve all the color categories from a particular message.

The following example performs the tasks as given below:

1. Add a color category.
2. Add another color category.
3. Retrieve the list of all categories.
4. Remove all categories.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Add Two category
FollowUpManager.addCategory(msg, "Purple Category");
FollowUpManager.addCategory(msg, "Red Category");

// Retrieve the list of available categories
IList categories = FollowUpManager.getCategories(msg);

// Remove the specified category and then Clear all categories
FollowUpManager.removeCategory(msg, "Red Category");
FollowUpManager.clearCategories(msg);
~~~

## **Accessing Follow Up Information form MSG file**

Aspose.Email API provides the capability to access the follow-up information from a sent or received message. It can retrieve the Read, Delivery Read Receipt and vote results information from a message file.

### **Retrieving Read and Delivery Receipt Information**

The following code snippet shows you how to retrieve read and delivery receipt information.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Recipient: " + recipient.getDisplayName());

    // Get the PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY property
    System.out.println("Delivery time: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY).getDateTime());

    // Get the PR_RECIPIENT_TRACKSTATUS_TIME_READ property
    System.out.println("Read time" + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ).getDateTime());
}
~~~

## **Creating Forward and Reply Messages**

Aspose.Email API provides the capability of creating and formatting forward and reply messages. The [ReplyMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/replymessagebuilder/) and [ForwardMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/forwardmessagebuilder/) classes of the API are used to create the Reply and Forward messages respectively. A Reply or Forward message can be specified to be created using any of the modes of [OriginalMessageAdditionMode](https://reference.aspose.com/email/java/com.aspose.email/originalmessageadditionmode/) enum. This enum has the following values:

- **OriginalMessageAdditionMode.None** - The original message is not included in the response message.
- **OriginalMessageAdditionMode.Attachment** - The original message is included as an attachment in the response message
- **OriginalMessageAdditionMode.Textpart** - The original message is included as a text in the body of the response message

### **Creating Reply Message**

The following code snippet shows you how to creat a reply message.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ReplyMessageBuilder builder = new ReplyMessageBuilder();

// Set ReplyMessageBuilder Properties
builder.setReplyAll(true);
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
builder.setResponseText(
        "<p><b>Dear Friend,</b></p> I want to do is introduce my co-author and co-teacher. <p><a href=\"www.google.com\">This is a first link</a></p><p><a href=\"www.google.com\">This is a second link</a></p>");

MapiMessage replyMsg = builder.buildResponse(originalMsg);
replyMsg.save(dataDir + "reply_out.msg");
~~~

### **Creating a Forward Message**

The following code snippet shows you how to create a forward message.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ForwardMessageBuilder builder = new ForwardMessageBuilder();
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
MapiMessage forwardMsg = builder.buildResponse(originalMsg);
forwardMsg.save(dataDir + "forward_out.msg");
~~~

## **Preserve Empty Dates when Converting a Message**

[MapiConversionOptions.setPreserveEmptyDates(boolean)](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmptyDates-boolean-) property indicating whether it is necessary to keep empty dates when converting a message. This API appears in Aspose.Email 21.5
The following code snippet shows you how to preserve empty dates.

~~~java
MailMessage mailMessage = MailMessage.load("message.eml");
System.out.println(mailMessage.getDate()); // zero date
MapiConversionOptions mco = MapiConversionOptions.getUnicodeFormat();
// keep empty dates when converting a message
mco.setPreserveEmptyDates(true);
MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, mco);
System.out.println(mapiMessage.getClientSubmitTime()); // zero date
// check zero date
if (mapiMessage.getClientSubmitTime().equals(JavaHelper.ZERO_DATE))
    System.out.println("ZERO DATE");
~~~
