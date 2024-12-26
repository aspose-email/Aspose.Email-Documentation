---
title: Convert OFT Files to Various Formats in C#  
ArticleTitle: Convert OFT Files to Various Formats in C#  
type: docs
weight: 35
url: /net/converting-between-formats/convert-oft-to-other-formats
--- 

One of the essential features is the ability to convert OFT (Outlook File Template) files to various other formats, such as EML, EMLX, MSG, MHTML, and more. In this section, we will guide you through the process of converting OFT files to these formats, highlighting the straightforward and efficient methods provided by Aspose.Email for .NET.

When converting OFT files to other formats using Aspose.Email for .NET, several key components are involved in the process. Here's a detailed breakdown of these components:

- [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class - Represents a Microsoft Outlook message in memory. It is used to load and manipulate OFT files. It provides methods to read from OFT files and convert them to other formats.

- [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method - Loads an OFT file into a MapiMessage object. It is a static method of the MapiMessage class that reads an OFT file from the specified path.

- [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method - Saves the MapiMessage object to a specified format. It is used to convert and save the loaded OFT file into the desired format, such as EML, MSG, or MHTML with a target file path where the converted file will be saved.

- [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) class - Provides options for saving the message in different formats. It contains predefined options for various formats like EML, MSG, and MHTML and ensures that the message is saved with the correct format settings.

## **Convert OFT to EML**

Converting OFT files to EML format is often essential for email data migration, archiving, or ensuring compatibility with various email clients. The EML format is widely supported and can be opened by numerous email applications. To perform the conversion, consider the following code sample with steps:

1. Load the OFT file into a MapiMessage object using the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2).
2. Save the loaded file using the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method specifying the target file name and saving options.

```cs
var oft = MapiMessage.Load("template.oft");
oft.Save("message.eml", SaveOptions.DefaultEml);
```

Aspose.Email for .NET offers several **customization options** when converting OFT files to EML format. These options allow you to control various aspects of the conversion process. Here are some customization possibilities along with code samples:

### **Modify Email Subject or Body**

You can modify the email's subject or body before saving it as EML.

```cs
using Aspose.Email;
using Aspose.Email.Mapi;

// Load the OFT file
var oft = MapiMessage.Load("template.oft");

// Modify the email subject
oft.Subject = "Updated Subject";

// Modify the email body
oft.Body = "This is the updated body content of the email.";

// Save the modified email as EML
oft.Save("updated_message.eml", SaveOptions.DefaultEml);
```

### **Handling Attachments**

You can add or remove attachments from the email before conversion.

```cs
using Aspose.Email;
using Aspose.Email.Mapi;

// Load the OFT file
var oft = MapiMessage.Load("template.oft");

// Add a new attachment
var attachment = new MapiAttachment("new_attachment.txt", System.IO.File.ReadAllBytes("new_attachment.txt"));
oft.Attachments.Add(attachment);

// Remove an existing attachment (if any)
if (oft.Attachments.Count > 0)
{
    oft.Attachments.RemoveAt(0);
}

// Save the modified email as EML
oft.Save("message_with_attachments.eml", SaveOptions.DefaultEml);
```

The range of options also includes setting encoding, managing headers, and more all of which help tailor the conversion process to meet specific requirements.

## **Convert OFT to EMLX**

1. Use the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method to load the OFT file into a MapiMessage object. This method reads the OFT file from the specified path.
2. Once the OFT file is loaded, use the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method of the MapiMessage object to save it in the EMLX format. Specify the target file name and the appropriate saving options.

```cs
var oft = MapiMessage.Load("template.oft");
oft.Save("message.emlx", SaveOptions.DefaultEmlx);
```

### **Customize Message Properties**

Aspose.Email provides various customization options while converting OFT files to EMLX format. You can modify properties such as subject, body, attachments, etc.

```cs
using Aspose.Email;
using Aspose.Email.Mapi;

public class Program
{
    public static void Main()
    {
        // Load the OFT file
        var mapiMessage = MapiMessage.FromFile("input.oft");

        // Customize message properties
        mapiMessage.Subject = "Customized Subject";
        mapiMessage.Body = "This is the customized body of the email.";

        // Add an attachment
        mapiMessage.Attachments.Add("attachment.txt", System.Text.Encoding.UTF8.GetBytes("Attachment content"));

        // Convert and save the customized message to EMLX format
        var emlMessage = mapiMessage.ToMailMessage(new MailConversionOptions());
        emlMessage.Save("output.emlx", SaveOptions.DefaultEmlx);
    }
}
```

## **Convert OFT to HTML**

Converting OFT files to HTML format allows the email content to be easily displayed in web browsers and integrated into web applications. Aspose.Email for .NET simplifies this process, ensuring that the converted HTML maintains the original formatting and structure of the OFT file.

The code sample below shows how to load an OFT file using the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) class and save it as an HTML file with the default HTML save options. The resulting HTML file can be easily used in web environments, facilitating the display and sharing of email content online.

1. Use the [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method to load an OFT file into a MapiMessage object.
2. Save the loaded message as an HTML file using the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method and choosing [SaveOptions.DefaultHtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) as the save options.

```cs
var oft = MapiMessage.Load("template.oft");
oft.Save("message.html", SaveOptions.DefaultHtml);
```

Aspose.Email for .NET offers various customization options while converting OFT files to HTML format, allowing developers to tailor the output to specific requirements. These customization possibilities include setting HTML save options such as embedding resources, setting the character encoding, and specifying the format for inline images. Here are some code samples demonstrating these customizations:

### **Embedding Resources**

To ensure that images and other resources are embedded within the HTML file, you can use the [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) class to set the 'EmbedResources' property.

```cs
var oft = MapiMessage.Load("template.oft");

// Create HTML save options with embedded resources
HtmlSaveOptions options = SaveOptions.DefaultHtml;
options.EmbedResources = true;

// Save as HTML with embedded resources
oft.Save("message_embedded.html", options);
```

### **Specifying Character Encoding**

You can specify the character encoding for the HTML file by setting the Encoding property of the [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) class.

```cs
var oft = MapiMessage.Load("template.oft");

// Create HTML save options with specified encoding
HtmlSaveOptions options = SaveOptions.DefaultHtml;
options.Encoding = System.Text.Encoding.UTF8;

// Save as HTML with specified encoding
oft.Save("message_utf8.html", options);
```

### **Inline Images**

To include images as inline base64 encoded strings within the HTML file, you can set the HtmlFormatOptions property to WriteInlineImages.
