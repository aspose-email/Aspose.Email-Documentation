---
title: Loading and Saving Message
type: docs
weight: 40
url: /java/loading-and-saving-message/
---

# Loading and Saving Message
## **Detecting File Formats**
Aspose.Email API provides the capability to detect the file format of the provided message file. The [DetectFileFormat](https://reference.aspose.com/email/java/com.aspose.email/FileFormatUtil#detectFileFormat\(java.lang.String\)) method of [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil) class can be used to achieve this. The following classes and methods can be used to detect the loaded file format.

- [FileFormatType](https://reference.aspose.com/email/java/com.aspose.email/fileformattype) Class
- [FileFormatInfo](https://reference.aspose.com/email/java/com.aspose.email/fileformatinfo) Class
- [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil) Class
- [FileFormatUtil.detectFileFormat(Stream)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil#detectFileFormat\(java.io.InputStream\)) Method
- [FileFormatUtil.detectFileFormat(String)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil#detectFileFormat\(java.lang.String\)) Method

The following code snippet shows you how to detecting file formats.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetectingFileFormat-.java" >}}
## **Loading a Message with Load Options**
To load a message with specific load options, Aspose.Email provides the [LoadOptions](https://reference.aspose.com/email/java/com.aspose.email/loadoptions) class that can be used as follow:



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-LoadingAMessageWithLoadOptions-.java" >}}
### **Preserving Embedded Message Format during Loading**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-PreservingEmbeddedMessageFormatduringLoading-PreservingEmbeddedMessageFormatduringLoading.java" >}}
## **Saving and Converting Messages**
Aspose.Email makes it easy to convert any message type to another format. To demonstrate this feature, the code in this article loads three types of messages from disk and saves them back in other formats. The base class [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions) and the classes [EmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/emlsaveoptions), [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions), [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions), [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions) for additional settings when saving [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) can be used for saving messages to other formats. The article shows how to use these classes to save a sample email as:

- EML format.
- Outlook MSG.
- MHTML format.
- HTML format.
### **Load and Save an EML message**
The following code snippet shows you how to load an EML message and saves it to the disc in the same format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLAndSavingAsEML.java" >}}
### **Load and Save an EML message Preserving the Original Boundaries**
The following code snippet shows you how to load EML and save as EML preserving the original boundaries.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingAndSavingAsEMLPreservingTheOriginalBoundaries.java" >}}
### **Saving as EML Preserving TNEF Attachments**
The following code snippet shows you how to save as EML preserving TNEF attachments.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsEMLPreservingTNEFAttachments.java" >}}
### **Save EML as MSG**
The following code snippet shows you how to loads an EML message and converts it to MSG using the appropriate option from [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/SaveOptions).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLSavingToMSG.java" >}}
### **Saving as MSG with Preserved Dates**
The [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions) class allows you to save the source message as an Outlook Message file (MSG) preserving dates. The following code snippet shows you how to Saving as MSG with Preserved Dates.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsMSGWithPreservedDates.java" >}}
### **Saving MailMessage as MHTML**
Different options of MHTML can be used to obtain the desired results. The following code snippet shows you how to load an EML message into [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) and convert it to MHTML with a message date in the UTC system.

~~~Java
// Set options for MHTML output
MhtSaveOptions saveOptions = SaveOptions.getDefaultMhtml();
// save a message date as UTC date
saveOptions.setPreserveOriginalDate(false);

// Initialize and load an existing EML file
try (MailMessage mailMessage = MailMessage.load(dataDir + "Message.eml")) {
    mailMessage.save(outDir + "Message_out.mhtml", saveOptions);
}
~~~
#### **Converting to MHTML with Optional Settings**
The [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions) class provides additional options for saving email messages to MHTML format. The enumerator [MhtFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions) makes it possible to write additional email information to the output MHTML. The following additional fields can be written:

- WriteHeader – write the email header to the output file.
- WriteOutlineAttachments – write outline attachments to the output file.
- WriteCompleteEmailAddress – write the complete email address to the output file.
- NoEncodeCharacters – no transfer encoding of characters should be used.
- HideExtraPrintHeader – hide extra print header from the top of the output file.
- WriteCompleteToEmailAddress – write the complete recipient email address to the output file.
- WriteCompleteFromEmailAddress – write the complete sender email address to the output file.
- WriteCompleteCcEmailAddress – write the complete email addresses of any carbon-copied recipients to the output file.
- WriteCompleteBccEmailAddress – write the complete email address of any blind carbon-copied recipients to the output file.
- RenderCalendarEvent – write text from the calendar event to the output file.
- SkipByteOrderMarkInBody – write Byte Order Mark(BOM) bytes to the output file.
- RenderVCardInfo – write text from VCard AlternativeView to the output file.
- DisplayAsOutlook – display From header.
- RenderTaskFields – writes specific Task fields to the output file.
- None – No setting specified.

The following code snippet shows you how to convert EML files to MHTML with optional settings.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertingToMHTMLWithOptionalSettings.java" >}}
#### **Rendering Calendar Events while Converting to MHTML**
The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions) renders the Calendar events to the output MTHML. The following code snippet shows you how to render calendar events while converting to MHTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RenderingCalendarEvents-RenderingCalendarEvents.java" >}}
#### **Exporting Email to MHT without Inline Images**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertToMHTMLWithoutInlineImages.java" >}}
#### **Exporting Email to MHT with customized TimeZone**
[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) class provides the [setTimeZoneOffset](https://reference.aspose.com/email/java/com.aspose.email/mailmessage#setTimeZoneOffset\(double\)) property to set customized Timezone while exporting to MHT. The following code snippet shows you how to export email to MHT with customized TimeZone.


~~~java
MailMessage msg = MailMessage.load(filename, new MsgLoadOptions());
msg.setDate(new Date());

// Set the timezone offset in milliseconds
msg.setTimeZoneOffset(5*60*60*1000);

MhtSaveOptions mhtOptions = new MhtSaveOptions();
mhtOptions.setMhtFormatOptions(MhtFormatOptions.WriteHeader);
msg.save(dataDir + "ExportToMHTWithCustomTimezone_out.mhtml", mhtOptions);
~~~
### **Exporting Email to EML**
The following code snippet shows you how to export emails to EML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ExportingEmailToEML-ExportingEmailToEML.java" >}}
### **Saving Message as HTML**
The [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions) class allows you to export the message body to HTML. The following code snippet shows you how to Save Message as HTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingMessageAsHTML.java" >}}
#### **Saving as HTML without Embedding Resources**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingasHTMLwithoutEmbeddingResources.java" >}}
### **Saving Message as Outlook Template (.oft) file**
The following code snippet shows you how to save a message as an outlook template (.oft) file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessageAsOFT-SaveMessageAsOFT.java" >}}
