---
title: Loading and Saving Messages
type: docs
weight: 40
url: /java/loading-and-saving-message/
---

# **Loading and Saving Email Messages**

## **Detect a File Format**

Aspose.Email API provides the capability to detect the file format of the provided message file. The [DetectFileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) method of the [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat(java.lang.String)) class can be used to achieve this. The following classes and methods can be used to detect the loaded file format.

- [FileFormatType](https://reference.aspose.com/email/java/com.aspose.email/fileformattype/) Class
- [FileFormatInfo](https://reference.aspose.com/email/java/com.aspose.email/fileformatinfo/) Class
- [FileFormatUtil](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/) Class
- [FileFormatUtil.detectFileFormat(Stream)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.io.InputStream-) Method
- [FileFormatUtil.detectFileFormat(String)](https://reference.aspose.com/email/java/com.aspose.email/fileformatutil/#detectFileFormat-java.lang.String-) Method

The following code snippet shows you how to detect file formats.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DetectingFileFormat-.java" >}}

## **Load an Email Message**

To load a message with specific load options, Aspose.Email provides the [LoadOptions](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/) class that can be used as follow:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-LoadingAMessageWithLoadOptions-.java" >}}

### **Preserve Embedded Message Format during Loading**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-PreservingEmbeddedMessageFormatduringLoading-PreservingEmbeddedMessageFormatduringLoading.java" >}}

## **Save and Convert Email Messages**

Aspose.Email makes it easy to convert any message type to another format. To demonstrate this feature, the code in this article loads three types of messages from disk and saves them back in other formats. The base class [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/) and the classes [EmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) for additional settings when saving [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) can be used for saving messages to other formats. The article shows how to use these classes to save a sample email as:

- EML format.
- Outlook MSG.
- MHTML format.
- HTML format.
  
### **Load and Save an Email Message**

The following code snippet shows you how to load an EML message and saves it to the disc in the same format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLAndSavingAsEML.java" >}}

### **Load and Save an Email Message Preserving the Original Boundaries**

The following code snippet shows you how to load EML and save as EML preserving the original boundaries.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingAndSavingAsEMLPreservingTheOriginalBoundaries.java" >}}

### **Saving as EML Preserving TNEF Attachments**

The following code snippet shows you how to save as EML preserving TNEF attachments.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsEMLPreservingTNEFAttachments.java" >}}

### **Save EML to MSG**

The following code snippet shows you how to loads an EML message and converts it to MSG using the appropriate option from [SaveOptions](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-LoadingEMLSavingToMSG.java" >}}

### **Save EML to MSG with Preserved Dates**

The [MsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/msgsaveoptions/) class allows you to save the source message as an Outlook Message file (MSG) preserving dates. The following code snippet shows you how to Saving as MSG with Preserved Dates.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingAsMSGWithPreservedDates.java" >}}

### **Save EML as MHTML**

Different options of MHTML can be used to obtain the desired results. The following code snippet shows you how to load an EML message into [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) and convert it to MHTML with a message date in the UTC system.

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
#### **Format MHT Headers Globally when Saving from EML** 

With Aspose.Email, you can use the global formatting options for the Mht header. The global options set the common formatting of an Mht header for all [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) instances. This feature is designed to avoid setting formatting for each instance of [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/).

Use the following methods of the [GlobalFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/) class and the code sample below to set the formatting of an Mht header:

- [setPageHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setPageHeaderFormat-java.lang.String-) - PageHeaderFormat for instances of HeadersFormattingOptions if DefaultPageHeaderFormat is not set.
- [setHeaderFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setHeaderFormat-java.lang.String-) - HeaderFormat for instances of HeadersFormattingOptions if DefaultHeaderFormat is not set.
- [setBeforeHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setBeforeHeadersFormat-java.lang.String-) - BeforeHeadersFormat for instances of HeadersFormattingOptions if BeforeHeadersFormat is not set.
- [setAfterHeadersFormat(String value)](https://reference.aspose.com/email/java/com.aspose.email/globalformattingoptions/#setAfterHeadersFormat-java.lang.String-) - AfterHeadersFormat for instances of HeadersFormattingOptions if AfterHeadersFormat is not set.

```java
// saveOptions1 and saveOptions2 have the same mht header formatting
MhtSaveOptions saveOptions1 = new MhtSaveOptions();
MhtSaveOptions saveOptions2 = new MhtSaveOptions();
```

#### **Convert EML to MHTML with Optional Settings**

The [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) class provides additional options for saving email messages to MHTML format. The enumerator [MhtFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/) makes it possible to write additional email information to the output MHTML. The following additional fields can be written:

- WriteHeader - write the email header to the output file.
- WriteOutlineAttachments - write outline attachments to the output file.
- WriteCompleteEmailAddress - write the complete email address to the output file.
- NoEncodeCharacters - no transfer encoding of characters should be used.
- HideExtraPrintHeader - hide extra print header from the top of the output file.
- WriteCompleteToEmailAddress - write the complete recipient email address to the output file.
- WriteCompleteFromEmailAddress - write the complete sender email address to the output file.
- WriteCompleteCcEmailAddress - write the complete email addresses of any carbon-copied recipients to the output file.
- WriteCompleteBccEmailAddress - write the complete email address of any blind carbon-copied recipients to the output file.
- RenderCalendarEvent - write text from the calendar event to the output file.
- SkipByteOrderMarkInBody - write Byte Order Mark(BOM) bytes to the output file.
- RenderVCardInfo -write text from VCard AlternativeView to the output file.
- DisplayAsOutlook - display From header.
- RenderTaskFields - writes specific Task fields to the output file.
- None - No setting specified.

The following code snippet shows you how to convert EML files to MHTML with optional settings.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertingToMHTMLWithOptionalSettings.java" >}}

#### **Render Calendar Events while Converting to MHTML**

The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/mhtformatoptions/#RenderCalendarEvent) renders the Calendar events to the output MTHML.The following code snippet shows you how to render calendar events while converting to MHTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-RenderingCalendarEvents-RenderingCalendarEvents.java" >}}

#### **Export Email to MHT without Inline Images**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-ConvertToMHTMLWithoutInlineImages.java" >}}

#### **Export Email to MHT with Customized TimeZone**

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class provides the [setTimeZoneOffset](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setTimeZoneOffset-double-) property to set customized Timezone while exporting to MHT. The following code snippet shows you how to export email to MHT with customized TimeZone.

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

### **Save Email as HTML**

The [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/) class allows you to export the message body to HTML. The following code snippet shows you how to save a message as HTML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingMessageAsHTML.java" >}}

### **Save Email Message as HTML with Relative Path to Resources**

When exporting email messages to HTML format, it is possible to choose to save email resources with relative paths. This feature provides more flexibility in how resources are linked in the output HTML file, making it easier to share and display saved emails on different systems. The [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) property provides ability to save resources with relative paths. Default property value is false (resources are saved with absolute paths). When set to true, resources are saved with relative paths. HTML files with relative paths are more portable and can be viewed correctly regardless of the hosting environment file structure. You can choose between absolute and relative paths depending on the requirements. You can define custom paths for resources using the [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) event.

**Save with Default Relative Path to Resources**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(true);

msg.save("target.html", htmlSaveOptions);
```
In this case, resources will be saved in the [html file name].files folder, in the same path as the .html file and the HTML will reference the resources via relative paths.

**Save with Absolute Path to Resources**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

msg.save("target.html", htmlSaveOptions);
```
As in the first case, resources will be saved in the [html file name].files folder by default, but the HTML will reference resources using absolute paths.

**Custom Relative Path using ResourceHtmlRenderingHandler Event**

```java
MapiMessage msg = MapiMessage.load(sourceFileName);

HtmlSaveOptions htmlSaveOptions = new HtmlSaveOptions();
htmlSaveOptions.setResourceRenderingMode(ResourceRenderingMode.SaveToFile);
htmlSaveOptions.setUseRelativePathToResources(false);

htmlSaveOptions.setResourceHtmlRenderingHandler(new ResourceHtmlRenderingHandler() {
    @Override
    public void invoke(Object sender, ResourceHtmlRenderingEventArgs args) {
        if (sender instanceof AttachmentBase) {
            AttachmentBase attachment = (AttachmentBase) sender;
            // Since UseRelativePathToResources = true, you should assign a relative path to the PathToResourceFile property.
            args.setPathToResourceFile("images\\" + attachment.getContentType().getName());
        }
    }
});

msg.save(targetPath + "A Day in the Park.html", htmlSaveOptions);
```
By using the [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) event, you can set custom relative or absolute paths for resources. When customizing paths with the [ResourceHtmlRenderingHandler](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderinghandler/) event handler, and since [UseRelativePathToResources](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#getUseRelativePathToResources--) is set to true, you should assign a relative path to the [PathToResourceFile](https://reference.aspose.com/email/java/com.aspose.email/resourcehtmlrenderingeventargs/#setPathToResourceFile-java.lang.String-) property to ensure correct referencing.

#### **Preserve Custom Icons in a Message while Converting to HTML** 

Sometimes, the message contains in-line attachments, that are displayed as icon images in a message body. Such messages may create problems while converting them to HTML, since the icon images are lost. This is because attachment’s icons are not held directly in the message.

The user of the Aspose.Email can customize the icons for attachments when converting the message to HTML. For that, the [HtmlSaveOptions.ResourceHtmlRendering](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/#HtmlSaveOptions--) event is used to customize the rendering of resource files (such as attachments) when saving an email message as an HTML file. In the code sample below, the event handler is used to dynamically set the path to resource files (icons) based on the content type of the attachment. This allows for customized rendering of resources in the HTML output based on their file type.

```java

 HtmlSaveOptions options = new HtmlSaveOptions();

options.setResourceHtmlRenderingHandler(new ResourceHtmlRenderingHandler() {

   @Override

   public void invoke(Object sender, ResourceHtmlRenderingEventArgs e) {

        AttachmentBase attachment = (AttachmentBase) sender;

        e.setCaption(attachment.getContentType().getName());

       if (attachment.getContentType().getName().endsWith(".pdf")) {

            e.setPathToResourceFile("pdf_icon.png");

       } else if (attachment.getContentType().getName().endsWith(".docx")) {

            e.setPathToResourceFile("word_icon.jpg");

       } else if (attachment.getContentType().getName().endsWith(".jpg")) {

            e.setPathToResourceFile("jpeg_icon.png");

       } else {

            e.setPathToResourceFile("not_found_icon.png");

       }

   }

});

options.setResourceRenderingMode(ResourceRenderingMode.SubstituteFromFile);

String fileName = "message.msg";

MailMessage mailMessage = MailMessage.load(fileName);

mailMessage.save("fileName.html", options);

```

#### **Set Time and Timezone when Saving EML as HTML**

Aspose.Email users can set the time and timezone display formats in [HtmlSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlsaveoptions/). The [HeadersFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/headersformattingoptions/) class allows to specify headers formatting options when saving MailMessage to Mhtml or Html format. The following methods of the [HtmlFormatOptions](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/) class specify the fields to be displayed in the output file:

- [RenderCalendarEvent](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderCalendarEvent) - Indicates that text from calendar event should be written in output mhtml.
- [RenderVCardInfo](https://reference.aspose.com/email/java/com.aspose.email/htmlformatoptions/#RenderVCardInfo) - Indicates that text from VCard AlternativeView should be written in output html.

The following code sample shows how to set the time and timezone when saving EML to HTML:

```java
MailMessage msg = MailMessage.load("fileName");
HtmlSaveOptions options = new HtmlSaveOptions();
options.setHtmlFormatOptions(HtmlFormatOptions.WriteHeader);
options.getFormatTemplates().set_Item("DateTime", "MM d yyyy HH:mm tt");
```

#### **Saving as HTML without Embedding Resources**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ConvertEmailMessages-SavingasHTMLwithoutEmbeddingResources.java" >}}

### **Saving a Message as an Outlook Template (.oft) file**

The following code snippet shows you how to save a message as an outlook template (.oft) file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessageAsOFT-SaveMessageAsOFT.java" >}}
