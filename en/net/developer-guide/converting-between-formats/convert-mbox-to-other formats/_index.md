---
title: Convert MBOX Files to Various Formats in C#  
ArticleTitle: Convert MBOX Files to Various Formats in C#  
type: docs
weight: 60
url: /net/converting-between-formats/convert-mbox-to-other-formats
--- 

Aspose.Email for .NET provides robust capabilities to convert email messages stored in MBOX format to various other formats. The library supports conversions to formats such as EML, EMLX, HTML, ICS, MHT, MHTML, MSG, OFT, OST, PST, TIFF, VCF, and XPS. Below, we provide detailed steps and code examples for converting MBOX files to these formats. For this purpose, Aspose.Email offers a robust set of features:

1. The [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) class is used to read messages from an MBOX file and retrieve the total count of email messages. It provides methods to access individual messages stored in the file.

2. The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class represents an email message. It supports loading and saving email messages in various formats and provides rich functionality to manipulate their properties.

3. The [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) class specifies the options to use when saving an email message. It contains both predefined options and customization options for saving messages in different formats.

## **Convert MBOX to EML**

EML files are used by several email clients to store email messages in plain text. Converting MBOX to EML allows for easy transfer and reading of email messages.

Below is the sample code demonstrating the conversion of MBOX to EML:

1. Create an instance of MboxrdStorageReader for the specified MBOX file ("sourceFile.mbox").
2. Use the [reader.GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/gettotalitemscount/) method to iterate through all emails in the file to get the total number of items starting from 0.
3. Read each message using the [reader.ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage) method.
4. Save each email as a .eml file with a unique name ("outputMessage"+i+".eml") using [SaveOptions.DefaultEml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulteml/).

```cs
using (var reader = new MboxrdStorageReader("sourceFile.mbox", false)){
	for (int i = 0; i < reader.GetTotalItemsCount(); i++){
		using (var message = reader.ReadNextMessage()){
			message.Save("outputMessage"+i+".eml", SaveOptions.DefaultEml);
		}
	}
}
```

## **Convert MBOX to EMLX**

For this type of conversion, use the same approach given above [Convert MBOX to EML](#convert-mbox-to-eml). However, when saving a message in EMLX format, choose [SaveOptions.DefaultEmlx](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultemlx/).

```cs
using (var reader = new MboxrdStorageReader("sourceFile.mbox", false)){
	for (int i = 0; i < reader.GetTotalItemsCount(); i++){
		using (var message = reader.ReadNextMessage()){
			message.Save("outputMessage"+i+".emlx", SaveOptions.DefaultEmlx);
		}
	}
}
```

## **Convert MBOX to HTML**

HTML format is widely used for displaying emails in web browsers. Converting MBOX to HTML allows for viewing emails in a web-friendly format.

The following code sample demonstrates how to read messages from an MBOX file and save each message as an HTML file.

1. Use the [MboxStorageReader.CreateReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2) method to load the MBOX file. This initializes the reader with the specified file path and load options.
2. Create the output directory if it doesn’t exist.
3. Set up a counter to create unique filenames for each HTML file. This ensures that each message is saved with a distinct name.
4. Iterate through all the messages in the MBOX file. The [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/) method of [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) returns an enumerable collection of email messages.
5. Define the file path for each HTML file using the counter. Combine the output directory and a filename pattern to generate unique file paths.
6. Configure the [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) to control how resources (like images and attachments) are handled during the HTML conversion. In this case, resources are saved to files and relative paths are used.
7. Save each email message as an HTML file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. Pass the file path and save options as parameters.

```cs
// Load mbox file
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());
// Ensure the output directory exists
Directory.CreateDirectory(outputDirectory);
// Iterate through mbox messages and save them as .html files
int count = 1;
foreach (var eml in mbox.EnumerateMessages())
{
    // Save each message as .html file
    var htmlFilePath = Path.Combine(outputDirectory, $"Message{count}.html");
    var htmlSaveOptions = new HtmlSaveOptions
    {
        ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
        UseRelativePathToResources = true
    };
    eml.Save(htmlFilePath, htmlSaveOptions);
```

### **Special Features**

1. **High Fidelity**:
    - Aspose.Email ensures that the conversion from MBOX to HTML retains the original formatting, layout, and embedded elements of the email messages. This includes preserving the text formatting, images, hyperlinks, and attachments, ensuring that the HTML representation closely mirrors the original email content.

2. **Customization**:
    - The SaveOptions.DefaultHtml property returns [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/) class which alows you to customize the conversion process. Users can specify various settings to control how emails are rendered in HTML format. This includes options for embedding images directly in the HTML file or linking to external resources.

3. **Efficiency and Scalability**:
    - Aspose.Email is designed to handle large MBOX files efficiently. The library can process thousands of email messages quickly and reliably, making it suitable for applications that need to convert large volumes of email data.

4. **Metadata Preservation**:
    - Aspose.Email ensures that important metadata such as subject, sender, recipient, date, and headers are preserved during the conversion. This ensures that the context and details of each email message are not lost in the process.

## **Convert MBOX to ICS**

ICS (iCalendar) format is widely used for storing calendar events and is supported by numerous calendar applications. This section covers the features and capabilities of Aspose.Email for .NET for converting MBOX files to ICS format, ensuring a smooth transition of calendar events stored within email messages. This is achieved with progressive components referenced in the code steps.

Below is an example code snippet demonstrating how to convert MBOX files to ICS using Aspose.Email for .NET:

1. Initialize MBOX reader to load the emails from the specified MBOX file path using the the [MboxStorageReader.CreateReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2) method.
2. Ensure the output directory exists where ICS files will be saved.
3. Initialize a Counter to keep track of the email message count for naming the ICS files.
4. Loop through each email message in the MBOX file using the [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/) method of the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) class.
5. Generate File Path for ICS.
6. Extract calendar content from the email in ICS format with the [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/).
7. Save the ICS content to the file. 

```cs
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

Directory.CreateDirectory(outputDirectory);

int count = 1;

foreach (var eml in mbox.EnumerateMessages())
{
    var icsFilePath = Path.Combine(outputDirectory, $"Message{count}.ics");

    var icsContent = eml.GetAlternateViewContent("text/calendar");

    if (icsContent != null)
    {
        File.WriteAllText(icsFilePath, icsContent);
    }
}
```

### **MBOX to ICS Conversion Capabilities**

- The SaveOptions class allows developers to customize how data is saved during the conversion. This includes options for controlling the formatting and structure of the resulting ICS files.
- Aspose.Email provides the ability to extract calendar events from email messages. Using the MailMessage and Appointment classes, events embedded in emails can be accurately identified and converted to the ICS format.
- The library is designed to handle large MBOX files efficiently. It can process numerous email messages quickly, making it suitable for applications that require converting large volumes of data.
- Aspose.Email ensures that all relevant data within the MBOX file is accurately converted to the ICS format. This includes preserving event details such as the event summary, start and end times, recurrence patterns, attendees, and more.

## **Convert MBOX to MHT/MHTML**

MHT (MHTML) files are used to archive web pages and emails in a single file. Converting MBOX to MHT can help in preserving emails as web-archive files. Aspose.Email for .NET provides powerful tools to facilitate this conversion, ensuring that the integrity and formatting of the original emails are maintained.

Below is the sample code demonstrating the MBOX to MHT conversion:

1. Initialize MBOX reader to load the emails from the specified MBOX file using the the [MboxStorageReader.CreateReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2) method.
2. Iterate over each email message in the MBOX file with the [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/gettotalitemscount/) method of the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) class. Read the next email message in the iteration using the [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/readnextmessage/#readnextmessage) method.
3. Save the email message as an MHTML file with the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method, using the iteration index for the file name and the [SaveOptions.DefaultMhtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmhtml/), a predefined option for saving messages in MHT format.

```cs
using (var reader = new MboxrdStorageReader("sourcFile.mbox", false)){
  for (int i = 0; i < reader.GetTotalItemsCount(); i++){
    using (var message = reader.ReadNextMessage()){
      message.Save("outputMessage"+i+".mht", SaveOptions.DefaultMhtml);
    }
  }
}
```

### **Additional Features**

While converting from MBOX to MHT/MHTML, developers can also take advantage of other useful features provided by Aspose.Email for .NET:

- Developers can customize the save options to suit their specific needs. For instance, they can specify options to include or exclude attachments, inline images, and other resources.
- Aspose.Email can handle inline and embedded resources (such as images and attachments) within email messages. These resources are preserved and correctly referenced in the resulting MHT files.
- During the conversion process, important metadata such as email headers, subject, sender, recipient, and date are preserved, ensuring that no critical information is lost.
- Developers can programmatically change the subject, body, and other properties of email messages before saving them in the desired format using the rich functionality of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class to manipulate email properties. 

## **Convert MBOX to MSG**

MSG is a file format used by Microsoft Outlook to store individual email messages. Converting MBOX to MSG is useful for accessing MBOX emails directly in Outlook. 

Aspose.Email for .NET offers a comprehensive set of features and abilities that facilitate the conversion process, ensuring that all critical email attributes such as sender and recipient information, subject, date, and message body are accurately preserved, attachments embedded within MBOX emails are seamlessly converted and included in the MSG files, the original format of the email is preserved, ensuring that the MSG file reflects the same layout and formatting as the original MBOX email. If the MBOX emails contain custom properties or extended MAPI (Messaging Application Programming Interface) properties, they are retained and accurately represented in the MSG files.

The following code sample is a representation of a minimal simple set of the library features and abilities. It demonstrates how to convert emails from an MBOX file to individual MSG files by reading each email message from the MBOX file and saving it in the MSG format.

1. Create an instance of [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) to read the MBOX file.
2. Loop through each email in the MBOX file from 0 to the total number of items in it using [reader.GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/gettotalitemscount/).
3. Read the next email message with the [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage) method.
4. Use the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method to save the email message in MSG format with the loop index i as an output path and filename for the MSG file and SaveOptions.DefaultMsgUnicode specifying that the MSG file should be saved using the Unicode format, preserving all extended characters and properties.

```cs
using (var reader = new MboxrdStorageReader("sourcFile.mbox", false)){
	for (int i = 0; i < reader.GetTotalItemsCount(); i++){
		using (var message = reader.ReadNextMessage()){
			message.Save("outputMessage" + i + ".msg", SaveOptions.DefaultMsgUnicode);
		}
	}
} 
```
The use of [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) and [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) ensures that each email is correctly read from the MBOX file and accurately saved in the desired format.

## **Convert MBOX to OFT**

OFT (Outlook File Template) is a file format used by Microsoft Outlook to store email templates. These templates can be used to create pre-formatted email messages, which are useful for repetitive email tasks. Converting MBOX to OFT allows users to leverage existing email content stored in MBOX files to create reusable templates in Outlook.

Aspose.Email for .NET facilitates the conversion of MBOX to OFT files through a straightforward process involving several key components. Firstly, the [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class is used to create a reader instance that loads and reads the MBOX file, using the [CreateReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2) method with the specified file path and load options ([MboxLoadOptions](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxloadoptions/)). Each email message within the MBOX file is then processed using the [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages) method, which iterates over the messages. Each message, represented as a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) object, is saved as an OFT file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method with [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/). This ensures that the original email formatting and details are preserved during the conversion. By utilizing these components, Aspose.Email for .NET ensures a seamless and efficient conversion process from MBOX to OFT, catering to various application needs for email data management and migration.

The code snippet below outlines a process to convert email messages from an MBOX file format to Outlook Template (OFT) files using Aspose.Email for .NET:

1. Initialize a reader to handle MBOX files passing mboxFilePath (the path to the MBOX file) and [MboxLoadOptions](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxloadoptions/) (specifying any optional loading configurations).
2. Create an output directory if it doesn't exist.
3. Initialize message counter.
4. Iterate through each email message (eml) in the MBOX file using [mbox.EnumerateMessages()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages). This method returns each message as a MailMessage object.
5. Use the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method to save each email as an OFT file at the specified file path. The [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/) ensures that the email message is converted and saved in the OFT format with default options.

```cs
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

Directory.CreateDirectory(outputDirectory);

int count = 1;

foreach (var eml in mbox.EnumerateMessages())
{
    // Save each message as .oft file
    var oftFilePath = Path.Combine(outputDirectory, $"Message{count}.oft");
    eml.Save(oftFilePath, SaveOptions.DefaultOft);
```

## **Convert MBOX to OST**

An OST (Offline Storage Table) format is a data file used by Microsoft Outlook to store copies of mailbox items from an Exchange server, enabling offline access and synchronization with the server when connected. Converting MBOX files to OST format enables seamless email data integration into Microsoft Outlook's ecosystem, ensuring compatibility, offline access capabilities, and synchronization with Exchange servers, thereby enhancing productivity and data management within corporate environments. 

The process of converting MBOX to OST using Aspose.Email for .NET involves several key components and steps. The code sample below demonstrates the process of importing email messages from an MBOX file into a Microsoft Outlook OST (Offline Storage Table) file.

1. Firstly, the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) is utilized to read the MBOX file specified by mboxFilePath. This component, configured with [MboxLoadOptions](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxloadoptions/), parses the MBOX file and prepares to extract messages.
2. Once messages are extracted, a [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) instance is created using [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) method, targeting the OST file specified by ostFilePath. 
3. Within this OST file, the Inbox folder (retrieved via [GetPredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getpredefinedfolder/)) is identified as the destination folder for converted messages.
4. Iteratively, each message in the MBOX file is processed using [mbox.EnumerateMessages()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages). For each message, it undergoes transformation into a MapiMessage object using [MapiMessage.FromMailMessage(eml)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage_3), where eml represents the extracted email in MailMessage format. 
5. Finally, each MapiMessage is added to the Inbox folder within the OST file using [folderInfo.AddMessage(msg)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/).

```cs
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

using (var ost = PersonalStorage.FromFile(ostFilePath))
{
    var folderInfo = ost.GetPredefinedFolder(StandardIpmFolder.Inbox);

    foreach (var eml in mbox.EnumerateMessages())
    {
        var msg = MapiMessage.FromMailMessage(eml);
        folderInfo.AddMessage(msg);
    }
} 
```

## **Convert MBOX to PST**

The PST (Personal Storage Table) format is a data file used by Microsoft Outlook to store local copies of messages, calendar events, and other items. Converting MBOX files to PST format allows for seamless email data integration into Microsoft Outlook's ecosystem, ensuring compatibility and ease of access. 

The process of converting MBOX to PST is similar to [MBOX to OST conversion](#convert-mbox-to-ost) and involves the following components and steps:

1. The [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) is employed to read the MBOX file specified by mboxFilePath.
2. The [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) instance is created using the [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method, targeting the PST file specified by pstFilePath and specifying the Unicode format for better compatibility.
3. Within this PST file, an "Inbox" folder is created using the [CreatePredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/createpredefinedfolder/#createpredefinedfolder) method, setting it up as the destination for the converted messages. 
4. Iteratively, each message in the MBOX file is processed using [mbox.EnumerateMessages()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages). For each message, it is converted into a MapiMessage object using [MapiMessage.FromMailMessage(eml)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage_3), where eml represents the extracted email in MailMessage format. 
5. Finally, each MapiMessage is added to the "Inbox" folder within the PST file using [folderInfo.AddMessage(msg)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/), completing the conversion process.

```cs
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

using (var personalStorage = PersonalStorage.Create(pstFilePath, FileFormatVersion.Unicode))
{
    var folderInfo = personalStorage.CreatePredefinedFolder("Inbox", StandardIpmFolder.Inbox);

    foreach (var eml in mbox.EnumerateMessages())
    {
        var msg = MapiMessage.FromMailMessage(eml);
        folderInfo.AddMessage(msg);
    }
}
```

## **Convert MBOX to TIFF**

TIFF (Tagged Image File Format) is a versatile and widely used image format that supports high-quality graphics. It is commonly used for storing raster graphics and is favored due to its ability to handle detailed images with lossless compression. 

Aspose.Email for .NET provides a robust solution for converting MBOX files to TIFF format. The provided code snippet demonstrates the process of reading an MBOX file and converting each email message to a TIFF image.

1. Initialize the MBOX reader using the [CreateReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2) method of the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class which is responsible for reading the MBOX file. Specify file path and load options using [MboxLoadOptions](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxloadoptions/).
2. Create an output directory for the TIFF file if it doesn't exist.
3. Iterate through each email message in the MBOX file using [mbox.EnumerateMessages()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages).
4. Construct the file path for each TIFF file, naming them sequentially as "Message1.tiff", "Message2.tiff", etc.
5. Initialize Mail Printer to convert email messages to TIFF format.
6. Set Printer properties:
    - [FormattingFlags](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/formattingflags/#mailprinterformattingflags-property) ensures that mail information (like sender, recipient, etc.) is included in the output.
    - [PageUnit](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/pageunit/) sets the unit of measure for the printer settings to centimeters.
    - [AutoFitWidth](https://reference.aspose.com/email/net/aspose.email.printing/messageformattingflags/#messageformattingflags-enumeration) ensures the content width is adjusted to fit the page.
7. Use the last line to convert the email message to a TIFF file and save it to the specified path.

```cs
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

Directory.CreateDirectory(outputDirectory);

int count = 1;

foreach (var eml in mbox.EnumerateMessages())
{
    var tiffFilePath = Path.Combine(outputDirectory, $"Message{count}.tiff");

    var printer = new Printing.MailPrinter();

    printer.FormattingFlags = Printing.MessageFormattingFlags.MailInfo;

    printer.PageUnit = Printing.PrinterUnit.Cm;

    printer.FormattingFlags = Aspose.Email.Printing.MessageFormattingFlags.AutoFitWidth;

    printer.Print(eml, tiffFilePath, Aspose.Email.Printing.PrintFormat.Tiff);
```

### **Special Features**

- **Custom Formatting:**

You can customize the output format further by adjusting the [FormattingFlags](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/formattingflags/#mailprinterformattingflags-property) property. Options include attachments or headers customization, and more.

- **Page Settings:**

Modify [PageUnit](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/pageunit/) and other properties to fit specific page layout requirements (e.g., inches, pixels).

- **Multi-page TIFFs:**

Aspose.Email allows the creation of multi-page TIFF files, which can be useful for emails with long bodies or multiple attachments.


## **Convert MBOX to VCF**

VCF (vCard File) is a widely used format for storing contact information. It is commonly used to exchange contact details between different applications and devices due to its simplicity and compatibility.

Aspose.Email provides a set of features for your .NET applications to implement this functionality in your project. The code snippet below illustrates how to perform MBOX to VCF conversion by reading a MBOX file and converting each email message to a VCF contact file.

1. Initialize the MBOX Reader to read the MBOX file using the [CreateReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2) method of the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class.
2. Ensure the output directory exists, creating it if necessary.
3. Set up a counter to keep track of the number of messages processed.
4. Iterate through each email message in the MBOX file with the [mbox.EnumerateMessages()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages).
5. Construct the file path for each VCF file, naming them sequentially.
6. Retrieve the vCard (VCF) content from the email message using the [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/).
7. If vCard content exists, write it to the VCF file at the specified path.

Print a message to the console confirming the VCF file has been saved.

```cs
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

Directory.CreateDirectory(outputDirectory);

int count = 1;

foreach (var eml in mbox.EnumerateMessages())
{
    var vcfFilePath = Path.Combine(outputDirectory, $"Message{count}.vcf");

    var vcfView = eml.GetAlternateViewContent("text/vcard");

    if (vcfView != null)
    {
        File.WriteAllText(vcfFilePath, vcfView);
    }

    Console.WriteLine($"Message {count} saved as: {vcfFilePath}");

}
```

## **Convert MBOX to XPS**

XPS (XML Paper Specification) is a fixed-layout document format that preserves document fidelity and supports high-quality graphics. It is commonly used for sharing, printing, and archiving documents due to its ability to maintain layout and design across different devices.

Aspose.Email for .NET provides a robust solution for converting MBOX files to XPS format which involves reading an MBOX file and converting each email message to an XPS document. The following code snippet demonstrates how to implement this feature into your project: 

1. Use the [CreateReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/createreader/#createreader_2) method of the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class to read the MBOX file, specifying the file path and load options with [MboxLoadOptions](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxloadoptions/).
2. Ensure the output directory for the XPS files exists, creating it if necessary.
3. Iterate through each email message in the MBOX file using the [mbox.EnumerateMessages()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessages/#enumeratemessages).
4. Construct the file path for each XPS file, naming them sequentially as "Message1.xps", "Message2.xps", etc.
5. Initialize Mail Printer to handle the conversion of email messages to XPS format.
6. Configure Printer properties to ensure the email content is formatted correctly:
    - [FormattingFlags](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/formattingflags/#mailprinterformattingflags-property) ensures that mail information (like sender, recipient, etc.) is included in the output.
    - [PageUnit](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/pageunit/) sets the unit of measure for the printer settings to centimeters.
    - [AutoFitWidth](https://reference.aspose.com/email/net/aspose.email.printing/messageformattingflags/#messageformattingflags-enumeration) ensures the content width is adjusted to fit the page.
7. Use the last line to convert the email message to an XPS file and save it to the specified path.

```cs
var mbox = MboxStorageReader.CreateReader(mboxFilePath, new MboxLoadOptions());

Directory.CreateDirectory(outputDirectory);

int count = 1;

foreach (var eml in mbox.EnumerateMessages())
{
    var xpsFilePath = Path.Combine(outputDirectory, $"Message{count}.xps");

    var printer = new Printing.MailPrinter();

    printer.FormattingFlags = Printing.MessageFormattingFlags.MailInfo;

    printer.PageUnit = Printing.PrinterUnit.Cm;

    printer.Print(eml, xpsFilePath, Printing.PrintFormat.XPS);

    Console.WriteLine($"Message {count} saved as: {xpsFilePath}");

    count++;
}
```
