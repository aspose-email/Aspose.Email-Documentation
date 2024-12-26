---
title: Convert MSG Files to Various Formats in C#  
ArticleTitle: Convert MSG Files to Various Formats in C#  
type: docs
weight: 20
url: /net/converting-between-formats/convert-msg-to-other-formats
--- 

MSG is a file format used by Microsoft Outlook and Exchange to store individual email messages. An MSG file contains the email's data, including headers, body, attachments, and metadata. These files are typically created when an email is saved to disk from an Outlook email client. However, there are scenarios where you may need to convert MSG files to other formats for compatibility, archival, or sharing purposes.

The primary components involved in these conversion processes include classes, methods, and enumerations that facilitate the loading, manipulation, and saving of MSG files:

- [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class - represents an MSG file, providing properties and methods specific to MSG format. It is used to load and manipulate MSG files before conversion.

- [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class - represents an email message. It is used to hold the email content once it's converted from MSG format, and subsequently save it in the desired format. 

- [Save Options](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) - defines the saving options and target formats for the MailMessage object. It is used to specify the format in which the MailMessage should be saved. Examples include SaveOptions.DefaultEml, SaveOptions.DefaultHtml, SaveOptions.DefaultMhtml, etc.

**Methods**

- [MapiMessage.Load](): Loads an MSG file from the specified file path into a MapiMessage object. This static method reads the MSG file and prepares it for conversion.
- [MapiMessage.ToMailMessage(Email.MailConversionOptions options = null)](): Converts the MapiMessage object to a MailMessage object. It is called on the MapiMessage object to transform it into a MailMessage for further processing and saving.
- [MailMessage.Save(string fileName, SaveOptions options)](): Saves the MailMessage object to the specified file path in the desired format. It is used to save the converted email message in various formats. Different SaveOptions are used depending on the target format.

By leveraging these components, developers can convert MSG files to a variety of formats, ensuring compatibility and flexibility in their applications. In the following sections, we will provide detailed examples and step-by-step instructions on how to perform these conversions using Aspose.Email for .NET.

## **Convert MSG to EML**

EML files are widely supported across different email clients, making it easier to share and access emails on various platforms. Converting to EML format allows for easier manipulation and processing of email data, especially when integrating with other systems or applications. Aspose.Email for .NET provides a straightforward and efficient way to perform this conversion. The code sample below demonstrates how to load an MSG file and save it as an EML file:

1. Load the MSG file using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method. This method reads the content of the MSG file and prepares it for further processing.
2. Save the loaded message as an EML file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class. Specify the output file name and the save options.

```cs
// Initialize and Load an existing MSG file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.msg");
message.Save("output.eml", SaveOptions.DefaultEml); 
```

>**Note:** Attachments in the MSG file are automatically included in the EML file, maintaining their integrity and accessibility. Inline images and embedded objects within the MSG file are accurately converted and preserved in the EML file.

You can customize email headers and footers before saving the email in EML format. This is useful for adding metadata or additional information. You can use the [Save Options](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) class to specify additional settings when saving the email. For instance, you can control how the email body is saved, manage encoding, and specify if inline attachments should be preserved.

## **Convert MSG to EMLX**

Converting MSG files to EMLX format is essential for scenarios where email messages need to be compatible with Apple Mail and other email clients that support EMLX format. Aspose.Email for .NET provides an easy and efficient way to perform this conversion.

1. Load the MSG file with the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method. This method reads the content of the MSG file and converts it to a MailMessage object.
2. Use the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class to save the MSG file in EMLX format. Specify the output file name and the save options.

```cs
// load the MSG file to be converted
var message = MailMessage.Load("My File.msg");
// save MSG as a EMLX 
message.Save("Saved File.emlx", SaveOptions.CreateSaveOptions(MailMessageSaveType.EmlxFormat)); 
```

Aspose.Email for .NET offers several special features that can be applied in the process of converting MSG to EMLX. These features enhance the conversion process by providing additional control, customization, and handling of various aspects of email messages. The code sample below demonstrates the implementation of some of them:

```cs
// Load the MSG file to be converted
var message = MailMessage.Load("My File.msg");

// Preserving original formatting and metadata
var saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.EmlxFormat);
saveOptions.PreserveOriginalHeaders = true;

// Handling attachments
if (message.Attachments.Count > 0)
    {
        Console.WriteLine("The email contains attachments which will be preserved.");
    }

// Customizing email headers
message.Headers.Add("X-Custom-Header", "CustomHeaderValue");

// Saving the MSG file as EMLX with the specified options
message.Save("Saved File.emlx", saveOptions);
```

## **Convert MSG to HTML**

Converting MSG files to HTML format can be valuable for displaying emails in web applications or archiving purposes. Aspose.Email for .NET is a robust solution for this task. The following code demonstrates how to load an MSG file and save it as an HTML file:

1. Initialize the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) object and load the MSG file located at "myMessage.msg". The [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method detects the format automatically based on the file extension.
2. Save the loaded message in HTML format to "output.html" using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method. The [SaveOptions.DefaultHtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) parameter ensures that the file is saved correctly in HTML format.

```cs
// Initialize and Load an existing MHTML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.mhtml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

### **Advanced MSG to HTML Conversion Features**

- **Preserving Email Formatting:**

Aspose.Email ensures that the original formatting of the email, including fonts, styles, and layout, is preserved during the conversion to HTML.

- **Handling Attachments:**

The conversion process can include attachments, either embedding them within the HTML or linking to them externally.

- **Customizing HTML Output:**

You can customize the HTML output by modifying the document's structure, adding custom styles, or including additional HTML elements.

- **Converting Inline Images and Embedded Objects:**

Inline images and embedded objects are converted and preserved within the HTML content, ensuring that the visual elements of the email are intact.

- **Encoding Options:**

You can specify encoding options to ensure that the HTML output is compatible with various browsers and email clients.

## **Convert MSG to ICS**

Converting MSG files containing calendar appointments to ICS format is a common task for ensuring compatibility with various calendar applications. Aspose.Email for .NET has a set of robust features to perform this conversion. They are used to load an MSG file, check if it contains a calendar item, and save it as an ICS file. The code sample below demonstrates how to convert an MSG file into ICS format:

1. Initialize the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object and load the MSG file located at "appointment.msg" using the [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method. The Load method detects the format automatically based on the file extension.
2. Check if the loaded MSG file is of type Calendar using the [MapiItemType](https://reference.aspose.com/email/net/aspose.email.mapi/mapiitemtype/). This is crucial to ensure that the file contains a calendar appointment before attempting the conversion.
3. Convert the MapiMessage object to a [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) object, which is necessary for saving the appointment in ICS format.
4. Save the calendar item in ICS format to "appointment.ics" with the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/save/#save_4) method.

```cs
var msg = MapiMessage.Load("appointment.msg");
            
if (msg.SupportedType == MapiItemType.Calendar)
{
    var calendar = (MapiCalendar)msg.ToMapiMessageItem();
    calendar.Save("appointment.ics", AppointmentSaveFormat.Ics);
}
```

### **Advanced MSG to ICS Conversion Features**

Aspose.Email for .NET offers several advanced features that enhance the process of converting MSG files containing calendar appointments to ICS format. These features provide greater flexibility and control over the conversion, ensuring that the output meets specific requirements and maintains the integrity of the original appointment data. Below are some notable features:

- **Preserving Appointment Details**: date, time, location, attendees, and recurrence patterns.

- **Handling Recurring Appointments**: all recurrence patterns are accurately converted and reflected in the ICS file.

- **Customizing Appointment Properties**: you can customize various properties of the appointment, such as setting reminders, adding categories, and modifying custom fields before saving as ICS.

- **Managing Attachments**: all relevant documents and files are included within an ICS file. 

- **Setting Time Zones**: set and adjust time zones for the appointment to make time-related data accurate and consistent across different regions. 

## **Convert MSG to MBOX**

Converting MSG files to MBOX format can be essential for managing and archiving email messages across different platforms. Aspose.Email for .NET provides a straightforward and efficient method to perform this conversion. Below, we’ll walk through the steps to convert an MSG file to MBOX format using a simple code example.

The MBOX format is widely used for storing collections of email messages, and converting MHTML files to MBOX format can be particularly useful for archiving or migrating email data. Aspose.Email for .NET provides the [WriteMessage](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage) method of the [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) class to write a message to the MBOX file. The following code sample demonstrates how to utilize these features in MHTML to MBOX conversion:

1. Load the MSG file using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) specifying the [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/#msgloadoptions-class).
2. Create an [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) object to write the messages to an MBOX file named "output.mbox". The second parameter specifies whether to append to an existing file (false means it will create a new file or overwrite an existing one).  
3. Write the loaded message to an MBOX file using the [WriteMessage](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage) method.

```cs
using (var message = MailMessage.Load("inputFile.msg", new MsgLoadOptions())){
    using (var writer = new MboxrdStorageWriter("output.mbox", false)){
        writer.WriteMessage(message);
    }
}
```

### **Special Features for MSG to MBOX Conversion**

The advanced features provided by Aspose.Email for .NET to enhance the process of converting MSG files to MBOX format include:

- Preserving email properties
- Attachments handling
- Email headers customization
- Multiple MSG files conversion
- Setting email save options

## **Convert MSG to MHT/MHTML**

Converting MSG files to MHT format is useful for creating a web archive of email messages, which can be easily shared or stored. Aspose.Email for .NET provides a simple solution to perform this conversion. The following code demonstrates how to load an MSG file and save it as an MHT file:

1. Use [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method to load the MSG file.
2. Use the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method with the appropriate save options to save the message in the MHT format.

```cs
var msg = MapiMessage.Load("file.msg");
msg.Save("file.mht", SaveOptions.DefaultMhtml);
```

Aspose.Email for .NET provides an array of **special features** that enhance the conversion of MSG files to MHT format. It ensures the preservation of the email’s original formatting and allows for the inclusion of attachments within the MHT file. Customization options through [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) enable embedded resources, management of inline images, and the addition of custom headers and footers. Furthermore, it handles embedded objects and offers detailed control over encoding for a flawless conversion experience. 

## **Convert MSG to OFT**

Converting MSG files to OFT (Outlook Template File) can be essential for creating reusable email templates in Microsoft Outlook. Aspose.Email for .NET provides a way to perform this conversion with minimal code. By utilizing the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class, you can convert an MSG file to an OFT format. Here's a code snippet that demonstrates how to achieve this:

1. Create a new [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object with the sender's email, recipient's email, subject, and body of the email template.
2. Use the [SaveAsTemplate]() method to save the MapiMessage as an OFT file (OFT Template).

```cs
using (MapiMessage mapi = new MapiMessage("test@from.to", "test@to.to", "template subject", "Template body"))
{
    string oftMapiFileName = "mapiToOft.msg";
    mapi.Save(oftMapiFileName, new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
} 
```
