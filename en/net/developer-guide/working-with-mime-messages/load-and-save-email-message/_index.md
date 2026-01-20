---
title: Load and Save Email Message
ArticleTitle: Load and Save Email Message
type: docs
weight: 40
url: /net/load-and-save-email-message/
---

## **Load Email Message**

### **Load from EML**

This section describes how to load an EML file into a MailMessage object using the [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/) class.
The EmlLoadOptions class provides various options to customize how the EML file is loaded, such as preserving embedded message formats or controlling TNEF attachment loading behavior.

1. Initialize an instance of EmlLoadOptions.
2. Configure the load options as needed.
3. Use the [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method to load the EML file with the specified options.

```csharp
using Aspose.Email;

// Initialize EmlLoadOptions
var loadOptions = new EmlLoadOptions
{
    // Configure load options
    PreferredTextEncoding = Encoding.UTF8, // Sets preferred encoding for the message
    PreserveEmbeddedMessageFormat = true, // Preserve format of embedded messages
    PreserveTnefAttachments = true, // Control TNEF attachment loading
    RemoveSignature = false // Do not remove the signature
};

// Load the EML file
var eml = MailMessage.Load("file.eml", loadOptions);
```

#### **Properties of EmlLoadOptions**

- [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email/loadoptions/preferredtextencoding/): Sets the preferred encoding for the message subject and body. Default is `null`.
- [PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/): Indicates whether to preserve the format of embedded messages during loading. Default is `false`.
- [PreserveTnefAttachments](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/preservetnefattachments/): Controls TNEF attachment loading behavior. Default is `false`.
- [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/): Specifies whether the signature should be removed while loading. Default is `false`.

### **Preserve Embedded Message Format**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveEmbeddedMSGFormatDuringLoad-PreserveEmbeddedMSGFormatDuringLoad.cs" >}}

### **Load Message With Signature/Without Signature**

Signature preservation is supported by default when loading EML files. To remove the signature, you can set the [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/#loadoptionsremovesignature-property) property to *true*.

The code sample below shows how to remove a signature when loading a message:

```cs
var msg = MailMessage.Load(fileName, new EmlLoadOptions() { RemoveSignature = true});
```

### **Load from EMLX**

The following section covers loading an EMLX file with the [EmlxLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlxloadoptions/#emlxloadoptions-class) class.
This class provides options similar to EmlLoadOptions, offering control over encoding, signature removal, and more.

1. Instantiate the EmlxLoadOptions.
2. Configure properties as necessary.
3. Use the [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method to load the EMLX file.

```csharp
using Aspose.Email;

// Instantiate EmlxLoadOptions
var loadOptions = new EmlxLoadOptions
{
    // Configure load options
    PreferredTextEncoding = Encoding.UTF8, // Set encoding preference
    PreserveEmbeddedMessageFormat = true, // Preserve embedded message formats
    RemoveSignature = true // Remove signatures during loading
};

// Load the EMLX file
var emlx = MailMessage.Load("file.emlx", loadOptions);
```

#### **Properties of EmlxLoadOptions**

- [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email/loadoptions/preferredtextencoding/): Sets preferred encoding for message subject and body. Default is `null`.
- [PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/): Indicates whether to preserve the format of embedded messages. Default is `false`.
- [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/): Specifies whether to remove the signature during loading. Default is `false`.

### **Load from HTML**

Learn how to load an HTML file into a MailMessage using the [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) class. 
This class is specifically designed to handle HTML content with options to manage resources and add plain text views.

1. Initialize an instance of HtmlLoadOptions.
2. Configure the necessary properties.
3. Use the [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method to load the HTML file with the specified options.

```csharp
using Aspose.Email;

// Initialize HtmlLoadOptions
var loadOptions = new HtmlLoadOptions
{
    // Configure load options
    PathToResources = "resources/", // Path to directory containing resource files
    PreferredTextEncoding = Encoding.UTF8, // Set encoding preference
    ShouldAddPlainTextView = true // Add plain text view of the body
};

// Load the HTML file
var html = MailMessage.Load("file.html", loadOptions);
```

#### **Properties of HtmlLoadOptions**

- [PathToResources](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/pathtoresources/): Defines the path to the directory containing resource  files (images, for ex.).
- [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email/loadoptions/preferredtextencoding/): Sets the preferred encoding for message subject and body. Default is `null`.
- [PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/): Determines whether to preserve the format of embedded messages. Default is `false`.
- [ShouldAddPlainTextView](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/shouldaddplaintextview/): Specifies whether to add a plain text view of the message body. Default is `false`.

### **Load from MHTML**

This section explains how to load an MHTML file using the [MhtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/mhtmlloadoptions/#mhtmlloadoptions-class) class.
The MhtmlLoadOptions class offers options to manage encoding, preserve embedded message formats, and handle TNEF attachments.

1. Create an instance of MhtmlLoadOptions.
2. Configure the desired properties.
3. Load the MHTML file using the [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method.

```csharp
using Aspose.Email;

// Create MhtmlLoadOptions
var loadOptions = new MhtmlLoadOptions
{
    // Set load options
    PreferredTextEncoding = Encoding.UTF8, // Set encoding preference
    PreserveEmbeddedMessageFormat = true, // Preserve format of embedded messages
    PreserveTnefAttachments = true, // Handle TNEF attachments
    RemoveSignature = false // Keep the signature
};

// Load the MHTML file
var mhtml = MailMessage.Load("file.mht", loadOptions);
```

#### **Properties of MhtmlLoadOptions**

- [MessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/messageformat/): Represents the mail message format, which can be EML, MSG, or MHTML. Default is EML.
- [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email/loadoptions/preferredtextencoding/): Sets preferred encoding for message subject and body. Default is `null`.
- [PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/): Determines whether to preserve the format of embedded messages. Default is `false`.
- [PreserveTnefAttachments](https://reference.aspose.com/email/net/aspose.email/mhtmlloadoptions/preservetnefattachments/): Controls TNEF attachment loading behavior. Default is `false`.
- [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/): Specifies whether to remove the signature during loading. Default is `false`.

### **Load from MSG**

This section explains how to load an MSG file into a MailMessage object using the [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/#msgloadoptions-class) class. 
The MsgLoadOptions class offers various properties to handle how MSG files are loaded, including options to preserve RTF content or manage TNEF attachments.

1. Create an instance of MsgLoadOptions.
2. Set the desired properties to customize loading.
3. Load the MSG file using the [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method.

```csharp
using Aspose.Email;

// Create MsgLoadOptions
var loadOptions = new MsgLoadOptions
{
    // Set load options
    KeepOriginalEmailAddresses = true, // Preserve original email addresses
    PreferredTextEncoding = Encoding.UTF8, // Set preferred encoding
    PreserveRtfContent = true, // Keep RTF content in the message
    PreserveTnefAttachments = true, // Handle TNEF attachments
    RemoveSignature = false, // Keep the signature
    Timeout = 5000 // Set timeout to 5 seconds
};

// Load the MSG file
var msg = MailMessage.Load("file.msg", loadOptions);
```

#### **Properties of MsgLoadOptions**

- [KeepOriginalEmailAddresses](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/keeporiginalemailaddresses/): Indicates whether to keep original email addresses. Default is `false`.
- [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email/loadoptions/preferredtextencoding/): Defines the preferred encoding for message subject and body. Default is `null`.
- [PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/): Determines if the format of embedded messages should be preserved. Default is `false`.
- [PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservertfcontent/): Specifies whether to keep RTF body content in the `MailMessage`. Default is `false`.
- [PreserveTnefAttachments](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservetnefattachments/): Manages TNEF attachment loading behavior. Default is `false`.
- [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/): Decides whether to remove the signature during loading. Default is `false`.
- [Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/): Limits the formatting time in milliseconds during conversion. Default is 3000 ms.

### **Load from TNEF**

Learn how to load a TNEF eml file with the [TnefLoadOptions](https://reference.aspose.com/email/net/aspose.email/tnefloadoptions/#tnefloadoptions-class) class. This class provides options to manage encoding and remove signatures during the loading process.

1. Instantiate the TnefLoadOptions.
2. Configure the properties as needed.
3. Use the [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method to load the TNEF file.

```csharp
using Aspose.Email;

// Instantiate TnefLoadOptions
var loadOptions = new TnefLoadOptions
{
    // Configure load options
    PreferredTextEncoding = Encoding.UTF8, // Set encoding preference
    PreserveEmbeddedMessageFormat = true, // Preserve embedded message formats
    RemoveSignature = true // Remove signatures during loading
};

// Load the TNEF file
var tnef = MailMessage.Load("file.eml", loadOptions);
```

#### **Properties of TnefLoadOptions**

- [MessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/messageformat/): Represents the mail message format, such as EML, MSG, or MHTML. Default is EML.
- [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email/loadoptions/preferredtextencoding/): Sets preferred encoding for message subject and body. Default is `null`.
- [PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/): Indicates whether to preserve the format of embedded messages. Default is `false`.
- [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/): Specifies whether to remove the signature during loading. Default is `false`.

## **Detecting File Formats**

Aspose.Email API provides the capability to detect the file format of the provided message file. The [DetectFileFormat](https://reference.aspose.com/email/net/aspose.email/fileformattype/) method of [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) class can be used to achieve this. The following classes and methods can be used to detect the loaded file format.

- [FileFormatType](https://reference.aspose.com/email/net/aspose.email/fileformattype/) Class
- [FileFormatInfo](https://reference.aspose.com/email/net/aspose.email/fileformatinfo/) Class
- [FileFormatUtil](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/) Class
- [FileFormatUtil.DetectFileFormat(Stream)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat) Method
- [FileFormatUtil.DetectFileFormat(String)](https://reference.aspose.com/email/net/aspose.email.tools/fileformatutil/detectfileformat/#detectfileformat_1) Method

The following code snippet shows you how to detect file formats.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectDifferentFileFormats-DetectDifferentFileFormats.cs" >}}


## **Save and Convert Messages**

Aspose.Email makes it easy to convert any message type to another format. To demonstrate this feature, the code in this article loads three types of messages from disk and saves them back in other formats. The base class [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) and the classes [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) for additional settings when saving [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) can be used for saving messages to other formats. The article shows how to use these classes to save a sample email as:

- EML format.
- Outlook MSG.
- MHTML format.
- HTML format.
  
### **Save to EML**

The following code snippet shows you how to load an EML message and saves it to the disc in the same format.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cs" >}}

#### **Preserve the Original Boundaries**

The following code snippet shows you how to load EML and save as EML preserving the original boundaries.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cs" >}}

#### **Preserve TNEF Attachments**

The following code snippet shows you how to save as EML preserving TNEF attachments.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cs" >}}

### **Save EML to MSG**

The following code snippet shows you how to load an EML message and convert it to MSG using the appropriate option from [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cs" >}}

#### **Preserve Dates**

The [MsgSaveOptions](https://reference.aspose.com/email/net/aspose.email/msgsaveoptions/) class allows you to save the source message as an Outlook Message file (MSG) preserving dates. The following code snippet shows you how to save as MSG with Preserved Dates.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SavingMSGWithPreservedDates-SavingMSGWithPreservedDates.cs" >}}

### **Save EML to MHTML**

Different options of MHTML can be used to obtain the desired results. The following code snippet shows you how to load an EML message into [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) and convert it to MHTML with a message date in the UTC system.

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

#### **Conversion Options**

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) class provides additional options for saving email messages to MHTML format. The enumerator [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) makes it possible to write additional email information to the output MHTML. The following additional fields can be written:

- `WriteHeader` – write the email header to the output file.
- `WriteOutlineAttachments` – write outline attachments to the output file.
- `WriteCompleteEmailAddress` – write the complete email address to the output file.
- `NoEncodeCharacters` – no transfer encoding of characters should be used.
- `HideExtraPrintHeader` – hide extra print header from the top of the output file.
- `WriteCompleteToEmailAddress` – write the complete recipient email address to the output file.
- `WriteCompleteFromEmailAddress` – write the complete sender email address to the output file.
- `WriteCompleteCcEmailAddress` – write the complete email addresses of any carbon-copied recipients to the output file.
- `WriteCompleteBccEmailAddress` – write the complete email address of any blind carbon-copied recipients to the output file.
- `RenderCalendarEvent` – write text from the calendar event to the output file.
- `SkipByteOrderMarkInBody` – write Byte Order Mark(BOM) bytes to the output file.
- `RenderVCardInfo` – write text from VCard AlternativeView to the output file.
- `DisplayAsOutlook` – display From header.
- `RenderTaskFields` – writes specific Task fields to the output file.
- `None` – No setting specified.

The following code snippet shows you how to convert EML files to MHTML with optional settings.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertMHTMLWithOptionalSettings.cs" >}}

#### **Render Calendar Events**

The [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/) renders the Calendar events to the output MTHML. The following code snippet shows you how to render calendar events while converting to MHTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-RenderingCalendarEvents-RenderingCalendarEvents.cs" >}}

#### **Exporting Email to MHT without Inline Images**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ConvertMHTMLWithOptionalSettings-ConvertToMHTMLWithoutInlineImages.cs" >}}

#### **Exporting Email to MHT with customized TimeZone**

[MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class provides the [TimeZoneOffset](https://reference.aspose.com/email/net/aspose.email/mailmessage/timezoneoffset/) property to set customized Timezone while exporting to MHT. The following code snippet shows you how to export email to MHT with customized TimeZone.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cs" >}}

#### **Font Adjustment**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ChangeFontWhileConvertingToMHT-ChangeFontWhileConvertingToMHT.cs" >}}

### **Save EML to HTML**

The [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) class allows you to export the message body to HTML. The following code snippet shows you how to save a message as HTML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveMessageAsHTML.cs" >}}

#### **Save without Embedded Resources**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsHTML-SaveAsHtmlWithoutEmbeddingResources.cs" >}}

### **Save EML to OFT**

The following code snippet shows you how to save a message as an outlook template (.oft) file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SaveMessageAsOFT-SaveMessageAsOFT.cs" >}}

### **Convert EML to MSG (MailMessage to MapiMessage)**

To convert a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object loaded from an EML file to a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object, use the [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/) class. This conversion  is often necessary because these two objects serve different purposes and cater to distinct needs in email processing. [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) is specifically designed for compatibility with Microsoft Outlook and Exchange Server, as it adheres to the Messaging Application Programming Interface (MAPI) format. This ensures that emails converted to MSG files are fully compatible with Microsoft products, allowing them to be opened, modified, and managed directly within Outlook. 

This conversion is also necessary when emails need to be archived, indexed, or processed by storages that require the MAPI format, PST/OST, OLM storages, for example. The [MapiConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/) class allows you to specify additional options, such as preserving the original message format, keeping original dates, and compressing the RTF body during conversion. The following code sample shows how to load an email from a file in .eml format and convert it into an Outlook .msg format allowing for customization but ensuring that certain characteristics of the original email are preserved during the conversion.

1. Create an instance of `MapiConversionOptions` and configure its properties.
2. Convert the `MailMessage` object to a `MapiMessage` object using the configured conversion options.

```csharp
MailMessage eml = MailMessage.Load("email.eml", new EmlLoadOptions());

// Create an instance of MapiConversionOptions
var conversionOptions = new MapiConversionOptions
{
    // Configure MapiConversionOptions
    Format = OutlookMessageFormat.Unicode, // Use Unicode format for MSG
    PreserveEmbeddedMessageFormat = true, // Preserve the format of embedded messages
    PreserveOriginalAddresses = true, // Keep original email addresses
    PreserveOriginalDates = true, // Preserve original dates
    PreserveEmptyDates = false, // Generate new dates if original are empty
    RemoveSignature = false, // Do not remove the signature
    UseBodyCompression = true, // Enable RTF body compression
    ForcedRtfBodyForAppointment = false // Disable forced RTF body for appointments
};

// Convert MailMessage to MapiMessage
MapiMessage msg = MapiMessage.FromMailMessage(eml, conversionOptions);
```

#### **Available Properties of MapiConversionOptions**

- [ASCIIFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/asciiformat/): Returns `MapiConversionOptions` configured with `OutlookMessageFormat` as ASCII, with `PreserveSignature` set to false and `UseBodyCompression` set to false. This option is useful when you need a plain ASCII format conversion.
  
- [UnicodeFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/unicodeformat/): Returns `MapiConversionOptions` with `OutlookMessageFormat` set to Unicode, and both `PreserveSignature` and `UseBodyCompression` set to false. Use this option for more comprehensive character support in MSG files.
  
- [ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/): When set to true, forces the use of RTF body for calendar appointments. This is useful if you want to ensure compatibility with certain mail clients. Default is true.
  
- [Format](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/format/): Specifies the output format for the MSG file. It can be set to either `OutlookMessageFormat.ASCII` or `OutlookMessageFormat.Unicode`, controlling whether the converted MSG should use ASCII or Unicode encoding.
  
- [PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/format/): Determines whether to retain the original EML format of embedded messages during conversion to `MapiMessage`. Setting this to true ensures that embedded emails retain their original structure. Default is false.
  
- [PreserveEmptyDates](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveemptydates/): When set to true, retains the original saving and modification dates from the EML. Otherwise, new dates will be generated if the original ones are empty.
  
- [PreserveOriginalAddresses](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveoriginaladdresses/): If set to true, maintains the original email addresses without validation. This is useful when working with email addresses that might not conform to strict standards but need to be preserved as-is. Default is false.
  
- [PreserveOriginalDates](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveoriginaldates/): Ensures the original sending and receiving dates are kept during the conversion process. Setting this to true retains these dates for better historical accuracy.
  
- [RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/removesignature/): Controls whether the digital signature, if present, will be removed from the message during conversion. Default is false, meaning the signature will be kept unless explicitly removed.
  
- [UseBodyCompression](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/usebodycompression/): Enables RTF body compression if set to true. This can help reduce the size of the MSG file, especially when dealing with large messages with rich formatting.
