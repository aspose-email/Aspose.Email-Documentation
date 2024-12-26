---
title: Convert MHTML Files to Various Formats in C#  
ArticleTitle: Convert MHTML Files to Various Formats in C#  
type: docs
weight: 40
url: /net/converting-between-formats/convert-mhtml-to-other-formats
--- 

Converting MHTML files to various formats is a common requirement in many applications, especially those dealing with email archiving, document management, and data exchange. MHTML, or MIME HTML, is a web archive format used to combine HTML code and its resources, such as images, into a single file. However, for compatibility and usability purposes, it might be necessary to convert MHTML files into other formats such as MSG, EML, or OST. In this article, we will explore how to achieve this using Aspose.Email for .NET, a robust and versatile library designed for email processing and management in .NET applications.

Aspose.Email for .NET simplifies the conversion process through its rich set of features and methods. The main components involved in the MHTML conversion process include:

- [MhtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/mhtmlloadoptions/): This component specifies the options for loading MHTML files. It allows for customization of how the MHTML content is interpreted and processed.
- [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/): This class represents an email message and serves as a bridge for loading MHTML content. It facilitates the extraction and manipulation of the email data within the MHTML file.
- [Save Options](https://reference.aspose.com/email/net/aspose.email/saveoptions/): Depending on the target format, Aspose.Email for .NET provides various save options such as EmlSaveOptions, MsgSaveOptions, etc. These options determine the parameters and settings for saving the converted file in the desired format.

File format conversion methods are also used to streamline the conversion process, allowing for seamless transformation from MHTML to formats like EML, MSG, PST, and others.

## **Convert MHTML to EML**

Converting MHTML to EML is one of the common tasks when dealing with email files. The EML format is widely used for storing individual email messages, making it a suitable format for email archiving and exchange. The code snippet below will show you how Aspose.Email can be used to convert an MHTML file to EML format:

1. Load the MHTML file using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method. This method reads the content of the MHTML file and prepares it for further processing.
2. Save the loaded message as an EML file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class. Specify the output file name and the save options.

```cs
// Initialize and Load an existing MHTML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.mhtml");
message.Save("output.eml", SaveOptions.DefaultEml);
```

## **Convert MHTML to EMLX**

The EMLX format is commonly used by Apple's Mail application and is beneficial for users who need to ensure compatibility with macOS systems. Aspose.Email for .NET provides functionality to convert MHTML files to EMLX format. The following code sample demonstrates its work ensuring compatibility with Apple's Mail application and other macOS-based email clients.

1. Load the MHTML file with the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method.
2. Use the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class to save the MHTML content as an EMLX file. Specify the output file name and the save options.

```cs
// load the MHTML file to be converted
var message = MailMessage.Load("My File.mhtml");
// save MHTML as a EMLX 
message.Save("Saved File.emlx", SaveOptions.CreateSaveOptions(MailMessageSaveType.EmlxFormat)); 
```

## **Convert MHTML to HTML**

Converting MHTML files to HTML format is often necessary for displaying email content in web browsers or for further processing in web-based applications. Aspose.Email for .NET provides a straightforward way to perform this conversion. The following code sample shows how to convert MHTML files to HTML format using Aspose.Email for .NET:

1. Use the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method to load the MHTML file. This method reads the content of the MHTML file and prepares it for further processing.
2. Use the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class to save the MHTML content as an HTML file. Specify the output file name and the save options.

```cs
// Initialize and Load an existing MHTML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.mhtml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

The library also allows modifying or adding custom properties to the HTML output, such as custom headers, subject, or body content. You can also embed attachments within the HTML content if needed. To ensure that the email content is correctly displayed in web browsers or email clients, customize the HTML formatting: inline styles, external CSS, and HTML tags.

## **Convert MHTML to ICS**

Converting MHTML files to ICS format is essential for managing calendar events and appointments. The ICS format is widely used for calendar data exchange, enabling interoperability between different calendar applications. Aspose.Email for .NET provides a seamless way to perform this conversion. Use the [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) method to extract the ICS content from the MHTML file. This method retrieves the calendar information in the "text/calendar" format. The following code sample demonstrates how to convert an MHTML file to ICS format using Aspose.Email for .NET:

1. Load the MHTML file using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) method. This method reads the content of the MHTML file and prepares it for further processing.
2. Extract the ICS content with the  [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/).
3. If the ICS content is not null, save it to a file using File.WriteAllText.

```cs
var eml = MailMessage.Load("message.mhtml", new MhtmlLoadOptions());

var icsView = eml.GetAlternateViewContent("text/calendar");

if (icsView != null)
{
  File.WriteAllText("appointment.ics", icsView);
}
```

### **Customisation Options**

Aspose.Email for .NET provides several special features that can be applied in the process of converting MHTML to ICS. These features offer enhanced control and flexibility, enabling developers to customize the conversion process according to specific requirements.

- **Custom Date and Time Formats:**
You can specify custom date and time formats for the ICS content to match the desired output format.

- **Timezone Handling:**
Manage timezone information to ensure that calendar events are accurately represented across different timezones.

- **Encoding Options:**
Specify encoding options to ensure that the ICS content is correctly encoded, preventing issues with special characters.

- **Handling Attachments:**
Extract and include attachments from the MHTML file in the ICS content, if necessary.

- **Custom Properties:**
Add custom properties to the ICS file, such as custom fields or metadata.

Below is an example demonstrating how to create an Appointment object from the ICS content when converting MHTML to ICS. 

```cs
// Load the MHTML file
        var eml = MailMessage.Load("message.mhtml", new MhtmlLoadOptions());
            
        // Extract the ICS content
        var icsView = eml.GetAlternateViewContent("text/calendar");

        if (icsView != null)
        {
            // Create a new Appointment object from the ICS content
            var appointment = Appointment.Load(new MemoryStream(Encoding.UTF8.GetBytes(icsView)));

            // Customize the ICS properties
            appointment.StartDate  = new DateTime (2024, 12, 10);
            appointment.EndDate = new DateTime (2014, 12, 11);

            // Add a custom property
            appointment.Summary = "Custom Event Summary";

            // Save the customized ICS content to a file
            var icsContent = appointment.SaveToString();
            File.WriteAllText("custom_appointment.ics", icsContent);
        }
```

The customization, in this case, is achieved by utilizing the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) class, representing a calendar to an e-mail, and its extensive methods and properties.  

## **Convert MHTML to MBOX**

The MBOX format is widely used for storing collections of email messages, and converting MHTML files to MBOX format can be particularly useful for archiving or migrating email data. Aspose.Email for .NET provides the [WriteMessage](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage) method of the [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) class to write a message to the MBOX file. The following code sample demonstrates how to utilize these features in MHTML to MBOX conversion:

1. Load the MHTML file using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2).
2. Initialize the [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) to write the loaded message to an MBOX file. Specify the output file name and whether to append to an existing MBOX file.
3. Write the message to the MBOX file.

```cs
using (var message = MailMessage.Load("inputFile.mhtml", new MhtmlLoadOptions())){
using (var writer = new MboxrdStorageWriter("output.mbox", false)){
        writer.WriteMessage(message);
    }
}
```

### **Additional Options**

- **Appending to Existing MBOX Files:**
You can append messages to an existing MBOX file rather than creating a new one. This is useful for maintaining a single MBOX file that consolidates multiple emails.

- **Custom Message Headers:**
Modify or add custom headers to the messages before saving them to the MBOX file.

- **Handling Attachments:**
Ensure that attachments are correctly preserved and included in the converted MBOX file.

- **Encoding Options:**
Specify encoding options to ensure that message content is correctly encoded, especially when dealing with special characters or different languages.

The code sample below demonstrates how to use some of these special features when converting MHTML to MBOX:

```cs
// Load the MHTML file
using (var message = MailMessage.Load("inputFile.mhtml", new MhtmlLoadOptions()))
{
// Customize message headers
message.Subject = "Customized Subject";
message.Headers.Add("X-Custom-Header", "CustomHeaderValue");

// Create an MboxrdStorageWriter to append the message to an existing MBOX file
using (var writer = new MboxrdStorageWriter("output.mbox", true)) // true to append
{
// Write the message to the MBOX file
writer.WriteMessage(message);
}
}
```

## **Convert MHTML to MSG**

Converting MHTML files to MSG format is useful for scenarios where you need to manage or share email messages within Microsoft Outlook. Aspose.Email enables this conversion ensuring that the email message retains its original formatting and content. The following code sample demonstrates how to convert an MHTML file to MSG format using Aspose.Email for .NET:

1. Load the MHTML file using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2).
2. Use the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class to save the loaded message as an MSG file. Specify the output file name and use the [DefaultMsgUnicode](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmsgunicode/) save option to ensure the file is saved in the correct format.

```cs
var eml = MailMessage.Load("message.mhtml", new MhtmlLoadOptions());

eml.Save("message.msg", SaveOptions.DefaultMsgUnicode);
```

### **Additional Features**

Aspose.Email for .NET offers several special features that can be implemented in the process of conversion enhancing control and customization options, and allowing developers to tailor the conversion process to specific needs.

- **Custom Message Properties:**
Modify or add custom properties to the MSG file, such as custom headers, subject, or body content.

- **Handling Attachments:**
Ensure that attachments are correctly preserved and included in the converted MSG file. You can also add new attachments or modify existing ones.

- **Setting Message Flags:**
Set flags on the message, such as read/unread status or importance level.

- **Encoding Options:**
Specify encoding options to ensure that message content is correctly encoded, especially when dealing with special characters or different languages.

- **HTML Formatting:**
Ensure that the HTML content of the email is correctly formatted and preserved in the MSG file.

The code sample below demonstrates how to use some of these special features when converting MHTML to MSG:

```cs
 // Load the MHTML file
var eml = MailMessage.Load("message.mhtml", new MhtmlLoadOptions());

// Customize message properties
eml.Subject = "Customized Subject";
eml.Headers.Add("X-Custom-Header", "CustomHeaderValue");

// Add an attachment
var attachment = new Attachment("path/to/attachment.txt");
eml.Attachments.Add(attachment);

// Set message flags
eml.IsRead = true; // Mark as read
eml.Priority = MailPriority.High; // Set high priority

// Save the loaded message as an MSG file with default Unicode options
eml.Save("message.msg", SaveOptions.DefaultMsgUnicode);
```

## **Convert MHTML to OFT**

Converting MHTML files to OFT format is useful for scenarios where you need to create email templates for Microsoft Outlook. Aspose.Email for .NET is a robust solution for performing this conversion. The following code sample shows how to convert an MHTML file to OFT format using Aspose.Email for .NET:

1. Load the MHTML file using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2).
2. Save the loaded message as an OFT file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class. Specify the output file name and use the [DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/) save option to ensure the file is saved in the correct format.


```cs
var eml = MailMessage.Load("message.mhtml", new MhtmlLoadOptions());

eml.Save("message.oft", SaveOptions.DefaultOft);
```

### **Special Features**

Aspose.Email for .NET offers several special features that can be implemented in the process of converting MHTML to OFT such as customizing message properties, attachments handling, setting message flags, encoding options, and HTML formatting. The code samples below demonstrate the implementation of some of these features:  

```cs
eml.Subject = "Customized Subject";
eml.Headers.Add("X-Custom-Header", "CustomHeaderValue");
```

These lines demonstrate how to modify the subject and add a custom header to the message before saving it as an OFT file.

```cs
var attachment = new Attachment("path/to/attachment.txt");
eml.Attachments.Add(attachment);
```

This code adds a new attachment to the email message.

```cs
eml.IsRead = true; // Mark as read
eml.Priority = MailPriority.High; // Set high priority
```

These lines set the message as read and assign it a high priority.

## **Convert MHTML to OST**

If you need to store and manage email messages within Microsoft Outlook while offline, converting them to OST (Offline Storage Table) format might be useful. For MHTML to OST conversion, Aspose.Email for .NET provides a straightforward method. In a few lines of code, you can load an existing OST file, then a MHTML file, and add it to the target folder. The following code sample shows how to perform this conversion:

1. Use the [PersonalStorage.FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) method to load an existing OST file.
2. Use the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) method to load the MHTML file. This method reads the content of the MHTML file and converts it to a MapiMessage object.
3. Locate the target folder within the OST file (e.g., "Inbox") and use the [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method to add the converted MHTML message to that folder.

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    // Load the EML file
    var msg = MapiMessage.Load("message.mhtml", new MhtmlLoadOptions());

    // Add the EML message to the OST file
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```

Apart from the ability to modify or add custom properties, such as custom headers, subject, or body content, to the MHTML file before saving it as an OST message, Aspose.Email also allows adding new attachments or modifying existing ones, setting classification flags, such as read/unread status, importance level, or follow-up flags; preserving the rich HTML formatting of the email content, including styles, images, and embedded resources; creating new folders or organizing messages into existing folders within the OST file to maintain an organized structure.

```cs
// Load the OST file
using (var ost = PersonalStorage.FromFile("storage.ost"))
    {
    // Load the MHTML file
    var msg = MapiMessage.Load("message.mhtml", new MhtmlLoadOptions());

    // Customize message properties
    msg.Subject = "Customized Subject";
    msg.Headers.Add("X-Custom-Header", "CustomHeaderValue");

    // Add an attachment
    var attachment = new MapiAttachment("path/to/attachment.txt", "attachment.txt");
    msg.Attachments.Add(attachment);

    // Set message flags
    msg.SetMessageFlags(MapiMessageFlags.MSGFLAG_READ); // Mark as read
    msg.Importance = MapiImportance.High; // Set high importance

    // Get the target folder
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");

    // Add the customized message to the OST file
    folderInfo.AddMessage(msg);
    }
```

## **Convert MHTML to PST**

Converting MHTML files to PST (Personal Storage Table) format is useful for scenarios where you need to store and manage email messages within Microsoft Outlook. Aspose.Email for .NET offers a four-step solution to perform this conversion:

1. Create a new PST file with the [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method. This method initializes a new PST file with the specified name and file format version.
2. Create a subfolder within the PST file (e.g., "Inbox") using the AddSubFolder method.
3. Load the MHTML file using the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) method. This method reads the content of the MHTML file and converts it to a MapiMessage object.
4. Add the message to the PST file with the [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method to add the converted MHTML message to the specified folder within the PST file.

```cs
using (var pst = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
{ 
    var inbox = pst.RootFolder.AddSubFolder("Inbox");
    var msg = MapiMessage.Load("sourceFile.mhtml", new MhtmlLoadOptions());
    inbox.AddMessage(msg);
}
```

For more options to be used while converting MHTML files to PST format see [Convert MHTML to OST](#convert-mhtml-to-ost).

## **Convert MHTML to VCF**

Converting MHTML files to VCF (vCard) format is a common solution if you need to extract and save contact information from emails. Aspose.Email for .NET

1. Use the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method to load the MHTML file. This method reads the content of the MHTML file and converts it to a MailMessage object.
2. Use the [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) method to find the alternate view with the media type "text/vcard". This method extracts the vCard content from the email message.
3. Check if the vCard content is found, and if so, save it to a VCF file using File.WriteAllText.

```cs
var eml = MailMessage.Load("message.mhtml", new MhtmlLoadOptions());

var vcfView = eml.GetAlternateViewContent("text/vcard");

if (vcfView != null)
{
    File.WriteAllText("contact.vcf", vcfView);
}
```

### **Special Features for MHTML to VCF Conversion**

- **Custom Property Handling:**
Modify or add custom properties to the vCard before saving it. This can include custom fields, additional contact information, or personalized data.

- **Multi-Contact Extraction:**
Extract multiple contact entries if the MHTML file contains several vCard entries, and save each contact as a separate VCF file.

- **Encoding Options:**
Ensure proper encoding of contact information to support various character sets and internationalization.

- **vCard Versions:**
Convert and save the vCard in different versions (v2.1, v3.0, v4.0) based on the target application's compatibility requirements.

- **Handling Embedded Images:**
Extract and save embedded images or photos associated with the contacts in the vCard.

- **Merging Contacts:**
Combine multiple vCard entries into a single VCF file for streamlined contact management.

Below is an example demonstrating how to use some of these special features when converting MHTML to VCF:

```cs
// Load the MHTML file
var eml = MailMessage.Load("message.mhtml", new MhtmlLoadOptions());

// Find the alternate view with MediaType "text/vcard" (VCF)
var vcfView = eml.GetAlternateViewContent("text/vcard");

// If a VCF view is found, save it to a file
if (vcfView != null)
    {
    // Ensure proper encoding
    var encodedVcfView = Encoding.UTF8.GetString(Encoding.UTF8.GetBytes(vcfView));

    // Save the vCard to a file
    File.WriteAllText("contact.vcf", encodedVcfView);
    }
```
