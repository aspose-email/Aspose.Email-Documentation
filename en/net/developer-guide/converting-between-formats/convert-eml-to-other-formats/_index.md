---
title: Convert EML to HTML
ArticleTitle: Convert EML to HTML
type: docs
weight: 10
url: /net/converting-between-formats/
---

## **Convert EML to HTML**

To integrate email content into web applications, EML to HTML conversion is the right choice, facilitating visually appealing email presentation.

To convert EML to HTML, you will need the following classes:

- [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class is used to create an object representing an e-mail message. It allows to access message properties, such as subject, body, sender and recipients addreses, etc. With its methods, you can create, load and parse, modify, save emails, or perform other manipulations with them. 
- [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) class provides options for saving email messages in various formats. It enables users to customize the way email messages are saved in different formats. With this class, users can specify options for saving attachments, headers, metadata, and properties of email messages, set encoding options or choose whether to save messages with encryption or not. 

In the code sample below these classes work together to load an existing EML file and specify the format of the message as EML. Subsequently, they save the loaded email message as an HTML file using the specified default HTML saving options:

1. Use the [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method to load the existing file into a MailMessage object specifying the message format. 
2. Save the loaded MailMessage object as an HTML file using the [save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method. Use [SaveOptions.DefaultHtml()](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) to specify the save options for HTML format.

```cs
// Initialize and Load an existing EML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.eml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

### **Save EML Resources in a Separate File**

Aspose.Email provides the [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) enumeration allowing developers to manipulate resources in a HTML file. In the code sample below, this enum is used to save resources to a file and insert in HTML the 'src' tag with the path to this file:

1. Load the email message from the source file using the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method.
2. Create an instance of [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) with specified rendering and resource options.
3. Save the loaded email message as an HTML file to the target location using the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method with the HtmlSaveOptions parameter.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
UseRelativePathToResources = true
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

### **Embed Resources to an HTML File**

In some cases, it's required to embed resources, such as images, directly into the HTML file for seamless distribution and presentation. With Aspose.Email for .NET, you can easily achieve this using the [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) enumeration:

1. Load the email message from the source file using the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method.
2. Create a new [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) object and set the ResourceRenderingMode property to EmbedIntoHtml.
3. Save the loaded email message as an HTML file using the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method, specifying the target file path and passing the HtmlSaveOptions object as a parameter to embed resources into the HTML file.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.EmbedIntoHtml
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

## **Convert EML to ICS**

The following code sample demonstrates how to extract calendar event data from an EML file and save it to a separate ICS file for further use or manipulation.

```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// If an ICS view is found, save it to a file
if (icsView != null)
{
    File.WriteAllText("appointment.ics", icsView);
}
```

### **Customization**

Aspose.Email for .NET provides tools for customizing ICS (iCalendar) content extracted from EML (Electronic Mail) files.

**Customize the event details**

The following code sample demonstrates how to set various details of the appointment, such as the summary, location, and description. The code utilizes the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) class which represents calendar appointments or events in ICS (iCalendar) format. The class provides properties and methods to create, modify, and manage calendar events programmatically. 

```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// If an ICS view is found, load it to Appointment class object
var appointment = Appointment.Load(new MemoryStream(Encoding.UTF8.GetBytes(icsView)));

// Customize the event details
appointment.Summary = "Customized Event Summary";
appointment.Location = "Customized Location";
appointment.Description = "Customized Event Description";

// Add or modify attendees as needed
appointment.Attendees.Clear();
appointment.Attendees.Add("custom@example.com");

// Save the customized ICS content to a file
appointment.Save("customized_appointment.ics");
```

**Create a recurrence pattern**

The following code sample demonstrates how to create a weekly recurrence pattern for an appointment, where the appointment occurs every 5 weeks on Saturdays. The code utilizes the [Recurrence](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/recurrence/#appointmentrecurrence-property) property of the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) class which gets or sets the recurrence pattern.

```cs
var pattern = new  WeeklyRecurrencePattern(5, 7);
pattern. EndDate = new DateTime(2023, 8, 7);

appointment.Recurrence = pattern;
```

## **Add EML to MBOX**

MBOX is a commonly used format for storing multiple email messages in a single file, making it suitable for email archiving and migration purposes.  Use the [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) class to write email messages to an MBOX file. The following code sample demonstrates how to perform this task:

```cs
using (var message = MailMessage.Load("inputFile.eml")){
	using (var writer = new MboxrdStorageWriter("output.mbox", false)){
			writer.WriteMessage(message);
	}
} 
```

## **Convert EML to MHTML**

With Aspose.Email for .NET, you can easily convert EML files to MHTML format for various purposes such as archiving, compatability, offline viewing, etc. Load the email message using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2), then use the [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) class as a parameter to the [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method to specify the output file format when saving the message as a separate file:

```cs
// Initialize and Load an existing EML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.eml");
var mhtSaveOptions = new MhtSaveOptions;
message.Save("output.mhtml", mhtSaveOptions);
```

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) class provides various options for customizing output MHTML files to meet your specific requirements:

- Preserve original date formatting. You can choose to preserve the original formatting of the email messages during the conversion process:

  ```cs
  saveOptions.PreserveOriginalDate = true;
  ```

- Set output encoding. You can specify the encoding to be used when writing the output MHTML files:

  ```cs
  saveOptions.OutputEncoding = Encoding.UTF8; 
  ```

- Include attachments. This can be helpful if you want to preserve attachments when converting emails to MHTML format:

  ```cs
  saveOptions.SaveAttachments = true;
  ```

## **Convert EML to MSG**

Whether you need to migrate email data, archive messages, or integrate with Microsoft Outlook, Aspose.Email provides solutions to achieve your goals. MSG files are widely used by Microsoft Outlook. For EML to MSG conversion, use the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method to load the existing EML file specifying how it will be loaded with [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class).

The following code sample demonstrates how to convert EML files to MSG format:

```cs
// Load mail message
using (var message = MailMessage.Load("sourceFile.eml", new EmlLoadOptions())){
// Save as MSG
var msgSaveOptions = new MsgSaveOptions;
message.Save("output.msg", MsgSaveOptions);
} 
```

## **Convert EML to OFT**

To convert EML files to Outlook Template (OFT) format, load the existing email message using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method and save it with [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) specifying the default options for saving a message to OFT format: 

```cs
// load the EML file to be converted
var message = MailMessage.Load("My File.eml"); 
// save EML as a OFT 
message.Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Add EML to PST**

To convert EML files to Personal Storage Table (PST) format, load the message using the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) method, create the output file with the [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) and add the email to the created Inbox folder in the storage file using the [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/): 

```cs
using (var msg = MapiMessage.Load("sourceFile.eml", new EmlLoadOptions()))
{
    using (var personalStorage = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
  {
        var inbox = personalStorage.RootFolder.AddSubFolder("Inbox");
        inbox.AddMessage(msg);
  }
}
```

## **Add EML to OST**

Developers can easily convert EML files to Outlook Offline Storage Table (OST) format, enabling integration with Microsoft Outlook. The following code sample demonstrates how to add an EML message to an OST file:

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    // Load the EML file
    var msg = MapiMessage.Load("message.eml", new EmlLoadOptions());

    // Add the EML message to the OST file
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```

The [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class) parameter specifies additional options for loading EML files, such as preserving embedded message formats, removing signatures, and more. 

## **Convert EML to VCF**

Aspose.Email for .NET offers functionality to convert EML files to vCard (VCF) format, allowing developers to extract contact information from email messages. For this purpose, the library offers the [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class enabling developers to access alternate views within email messages and extract VCF content embedded within EML files for further use:


```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/vcard" (VCF)
var vcfView = eml.GetAlternateViewContent("text/vcard");
// If an VCF view is found, save it to a file
if (vcfView != null)
{
    File.WriteAllText("contact.vcf", vcfView);
}
```
