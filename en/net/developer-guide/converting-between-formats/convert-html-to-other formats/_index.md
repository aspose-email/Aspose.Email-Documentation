---
title: Convert HTML to Other Formats
type: docs
weight: 60
url: /net/converting-between-formats/convert-html-to-other-formats
---

## **Convert HTML to EML**

Aspose.Email for .NET provides a method to convert HTML files to EML format using the [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) and [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) methods to load the existing HTML file and save it in EML format respectively:


```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.eml", SaveOptions.DefaultEml);
```

In the code sample, the [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) class allows you to specify additional options when loading a MailMessage from HTML format. The following code sample demonstrates the use of this class. In the example, it specifies a text representation of the message body:

```cs
// Create an instance of HtmlLoadOptions
var loadOptions = new HtmlLoadOptions();

// Set the ShouldAddPlainTextView property to true to generate a plain text view along with HTML
loadOptions.ShouldAddPlainTextView = true;

// Load an HTML file
var mailMessage = MailMessage.Load("input.html", loadOptions);

// Access the plain text view of the email message
var plainTextView = mailMessage.GetAlternateViewContent("text/plain");

// Print or further process the plain text view
Console.WriteLine("Plain Text View:");
Console.WriteLine(plainTextView);
```

## **Convert HTML to EMLX**

You can easily convert HTML files to EMLX. All the properties and classes provided by the API for HTML to EML conversion are available for this type of conversion as well:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.emlx", SaveOptions.DefaultEmlx);
```
For additional settings, see [Convert HTML to EML](#convert-html-to-eml) paragraph.

## **Convert HTML to ICS**

To perform the task, the library offers the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) class to represent and manage calendar events. The following code sample demonstrates how to create an appointment form HTML content and save it to an ICS (iCalendar) file format:

```cs
// Sample HTML content
var htmlContent = File.ReadAllText("content.html");

// Create and initialize an instance of the Appointment class
var appointment = new Appointment(
    "Meeting Room 3 at Office Headquarters",// Location
    "Monthly Meeting",                      // Summary
    "Please confirm your availability.",    // Description
    new DateTime(2015, 2, 8, 13, 0, 0),     // Start date
    new DateTime(2015, 2, 8, 14, 0, 0),     // End date
    "from@domain.com",                      // Organizer
    "attendees@domain.com")
{
    HtmlDescription = htmlContent
};

// Save the event to an ICS file
appointment.Save("output.ics", AppointmentSaveFormat.Ics);
```


## **Generate MBOX from HTML content**

To perform HTML to MBOX conversion, use the [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class, specifying the HTML content file path and an instance of [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). This method parses the HTML content and generates a corresponding MailMessage object, preserving the structure and formatting of the original HTML. After loading the HTML content into a MailMessage object, write the message to an MBOX file using the [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) class:


```cs
using (var eml = MailMessage.Load("content.html", new HtmlLoadOptions())){
    using (var writer = new MboxrdStorageWriter("output.mbox", false)){
        writer.WriteMessage(eml);
    }
}
```

## **Convert HTML to MHTML**

Use the [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) class to load the existing file, specifying a path to it and an instance of [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). This method parses the HTML content and generates a corresponding MailMessage object, preserving the structure and formatting of the original HTML. After loading the HTML content into a MailMessage object, developers can save it as an MHTML file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method, specifying the desired output file path and utilizing the [SaveOptions.DefaultMhtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmhtml/) option:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.mhtml", SaveOptions.DefaultMhtml);
```

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) class provides a variety of options for configuring the behavior and settings of the output MHTML file instead of the SaveOptions.DefaultMhtml. With its [properties](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#properties), you can specify additional options when saving MailMessage to MHTML format.
The most popular of them are:

- [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/mhtformatoptions/) - Allows you to customize how the email message is saved in MHT format to best suit your needs.
- [SaveAttachments](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveattachments/) - Gets or sets a value indicating whether to save attachments.
- [SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Defines whether need to save all headers in output mhtml or not. Default value is false.
- [PreserveOriginalDate](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/preserveoriginaldate/) - Defines whether need keep original date in mail message when saving or not. Default value is true.

The following code sample demonstrates how these properties can be used:

```cs
var mhtSaveOprtions = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader,
    SaveAttachments = true,
    SaveAllHeaders = true,
    PreserveOriginalDate = true
}
```

## **Convert HTML to MSG**

After loading the HTML content into a MailMessage object, save it as an MSG file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method, specifying the desired output file path and utilizing the [SaveOptions.DefaultMsgUnicode](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmsgunicode/) option. This option ensures that the output file is saved in the MSG format with Unicode encoding.

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.msg", SaveOptions.DefaultMsgUnicode);
```
Additionally, Aspose.Email for .NET offers a range of advanced features and options for HTML to MSG conversion:

## **Convert HTML to OFT**

After loading the HTML content into a MailMessage object, save it as an OFT file using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method, specifying the desired output file path and utilizing the [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/) option:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("template.oft", SaveOptions.DefaultOft);
```

## **Add message with source HTML content to PST**

HTML to PST conversion involves creating a new PST (Personal Storage Table) file with a new folder, loading an HTML file and adding it to the new folder:

1. Create an instance of a PersonalStorage object representing a new PST file using the [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.
2. Access the root folder of the PST file and add a subfolder to it using the [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder) method of the [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class.
3. Load the content of an HTML file into a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) object using the [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) method with an instance of [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) to specify that the content is in HTML format.
4. Add the loaded MapiMessage object (representing the HTML content) to the folder within the PST file using the [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method.

```cs
using (var pst = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
{ 
    var inbox = pst.RootFolder.AddSubFolder("Inbox");
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    inbox.AddMessage(msg);
}
```

## **Add message with source HTML content to OST**

he following code sample with steps will show you how these components work together to add HTML content to OST file:

1. Load an existing OST file with the [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) method of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class used to represent the storage file that will store the email messages. 
2. Load the HTML file using the [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) method of the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) class representing an email message in Microsoft Outlook format. 
3. Specify [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) to enable additional options when loading MailMessage from HTML format.
4. Retrieve the root folder of the OST file using the [RootFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/rootfolder/) property of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) object.
5. Obtain the Inbox folder within the OST file using the [GetSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder) method on the root folder.
6. Add the loaded MapiMessage object (representing the HTML content) to the Inbox folder using the [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method on the folder.

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
``` 

## **Convert HTML to VCF**

The following code sample demonstrates how to create a contact item, populate it with HTML content, and save it to a VCF file:

1. Read the content of an HTML file into a string variable using the File.ReadAllText method.
2. Create a new MapiContact object by instantiating the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/#mapicontact-class) class.
3. Set the contact properties: display name, email address.
4. Set the body content of the contact to HTML using [SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/setbodycontent/#setbodycontent).
5. Save the contact as a VCF file using the [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_4) method.

```cs
var content = File.ReadAllText("content.html");
            
// Create a new MapiContact
var contact = new MapiContact();
contact.NameInfo.DisplayName = "John Doe";
contact.ElectronicAddresses.Email1.EmailAddress = "john.doe@example.com";
contact.SetBodyContent(content, BodyContentType.Html);

// Save the contact to a VCF file
contact.Save("contact.vcf", ContactSaveFormat.VCard)
```
