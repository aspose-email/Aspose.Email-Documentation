---
title: Loading and Saving Message
type: docs
weight: 40
url: /net/loading-and-saving-message/
---

# Loading and Saving Message
## **Detecting File Formats**
Aspose.Email API provides the capability to detect the file format of the provided message file. The [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/methods/detectfileformat/index) method of [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil) class can be used to achieve this. The following classes and methods can be used to detect the loaded file format.

- [FileFormatType](https://reference.aspose.com/email/net/aspose.email/fileformattype) Class
- [FileFormatInfo](https://reference.aspose.com/email/net/aspose.email/fileformatinfo) Class
- [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil) Class
- [FileFormatUtil.DetectFileFormat(Stream)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/methods/detectfileformat) Method
- [FileFormatUtil.DetectFileFormat(String)](https://reference.aspose.com/email/net/aspose.email.tools.fileformatutil/detectfileformat/methods/1) Method

The following code snippet shows you how to detecting file formats.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectDifferentFileFormats-DetectDifferentFileFormats.cs" >}}
## **Loading a Message with Load Options**
The following code snippet shows you how to load a message with load options.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cs" >}}
### **Preserving Embedded Message Format during Loading**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveEmbeddedMSGFormatDuringLoad-PreserveEmbeddedMSGFormatDuringLoad.cs" >}}
## **Saving and Converting Messages**
Aspose.Email makes it easy to convert any message type to another format. To demonstrate this feature, the code in this article loads three types of messages from disk and saves them back in other formats. The base class [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions) and the classes [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions), [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions), [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions), [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions) for additional settings when saving [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) can be used for saving messages to other formats. The article shows how to use these classes to save a sample email as:

- EML format.
- Outlook MSG.
- MHTML format.
- HTML format.
### **Load and Save an EML message**
The following code snippet shows you how to load an EML message and saves it to the disc in the same format.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cs" >}}
### **Load and Save an EML message Preserving the Original Boundaries**
The following code snippet shows you how to load EML and save as EML preserving the original boundaries.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cs" >}}
### **Saving as EML Preserving TNEF Attachments**
The following code snippet shows you how to save as EML preserving TNEF attachments.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cs" >}}
### **Save EML as MSG**
The following code snippet shows you how to loads an EML message and converts it to MSG using the appropriate option from [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cs" >}}
### **Saving as MSG with Preserved Dates**
The [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions) class allows you to save the source message as an Outlook Message file (MSG) preserving dates. The following code snippet shows you how to Saving as MSG with Preserved Dates.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SavingMSGWithPreservedDates-SavingMSGWithPreservedDates.cs" >}}
### **Saving MailMessage as MHTML**
Different options of MHTML can be used to obtain the desired results. The following code snippet shows you how to load an EML message into [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) and convert it to MHTML with a message date in the UTC system.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Set options for MHTML output
MhtSaveOptions saveOptions = SaveOptions.DefaultMhtml;
saveOptions.PreserveOriginalDate = false; // save a message date as UTC date

// Initialize and load an existing EML file
using (MailMessage mailMessage = MailMessage.Load(folderPath + "Message.eml"))
{
    mailMessage.Save(folderPath + "Message_out.mhtml", saveOptions);
}
```

#### **Converting to MHTML with Optional Settings**
The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions) class provides additional options for saving email messages to MHTML format. The enumerator [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions) makes it possible to write additional email information to the output MHTML. The following additional fields can be written:

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



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertMHTMLWithOptionalSettings.cs" >}}
#### **Rendering Calendar Events while Converting to MHTML**
The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions) renders the Calendar events to the output MTHML. The following code snippet shows you how to render calendar events while converting to MHTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RenderingCalendarEvents-RenderingCalendarEvents.cs" >}}
#### **Exporting Email to MHT without Inline Images**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertToMHTMLWithoutInlineImages.cs" >}}
#### **Exporting Email to MHT with customized TimeZone**
[MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class provides the [TimeZoneOffset](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/timezoneoffset) property to set customized Timezone while exporting to MHT. The following code snippet shows you how to export email to MHT with customized TimeZone.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cs" >}}
#### **Changing Font while Converting to MHT**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ChangeFontWhileConvertingToMHT-ChangeFontWhileConvertingToMHT.cs" >}}
### **Exporting Email to EML**
The following code snippet shows you how to export emails to EML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToEML-ExportEmailToEML.cs" >}}
### **Saving Message as HTML**
The [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions) class allows you to export the message body to HTML. The following code snippet shows you how to Save Message as HTML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveMessageAsHTML.cs" >}}
#### **Saving as HTML without Embedding Resources**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveAsHtmlWithoutEmbeddingResources.cs" >}}
### **Saving Message as Outlook Template (.oft) file**
The following code snippet shows you how to save a message as an outlook template (.oft) file.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsOFT-SaveMessageAsOFT.cs" >}}
