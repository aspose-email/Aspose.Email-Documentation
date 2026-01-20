---
title: Outlook Contacts Management
ArticleTitle: Outlook Contacts Management
type: docs
weight: 90
url: /net/outlook-contacts-management/
---


Like MapiMessage, Aspose.Email allows you to create Outlook contacts. The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class provides all the contact related properties required to create an Outlook contact. This article shows how to create, save and read an Outlook contact using the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.

## **Create and Save Outlook Contact**

To create a contact and save it to disc:

1. Instantiate a new object of the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.
1. Enter contact property information.
1. Add photo data (if any).
1. Save the contact as MSG or VCard format.

The following code snippet shows you how to create and save outlook contact.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cs" >}}

## **Save MAPI Distribution Lists to VCF Files**

The code sample below demonstrates how to save a distribution list to a multi-contact VCF file:

```cs
// convert the `msg` object to a `MapiMessage` object
var dlist = (MapiDistributionList)msg.ToMapiMessageItem();

//save the distribution list
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.Save("distribution_list.vcf", options);
```

## **Convert Multi-Contact VCF Files to MapiDistributionList**

Aspose.Email supports the conversion of multi-contact VCF files into `MapiDistributionList` objects, making it easy to manage and import multiple contacts directly into your applications. This feature is accessible through the following static methods in the [MapiDistributionList](https://reference.aspose.com/email/net/aspose.email.mapi/mapidistributionlist/#mapidistributionlist-class) class:

- [static MapiDistributionList FromVCF(string filePath)](https://reference.aspose.com/email/net/aspose.email.mapi/mapidistributionlist/fromvcf/#fromvcf_1)
- [static MapiDistributionList FromVCF(Stream stream)](https://reference.aspose.com/email/net/aspose.email.mapi/mapidistributionlist/fromvcf/#fromvcf)

The code sample below demonstrates how to use this feature:

```csharp
// Convert a multi-contact VCF file to a MapiDistributionList
MapiDistributionList dlist = MapiDistributionList.FromVCF(fileName);
```

## **Save Contacts in VCF Format**

To save the contact in version 3 VCF format, use the [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) enumerable to set the [VCardSaveOptions.Version](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) property. The following sample code demonstrates the use of [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) enumerable to save the contact VCF version 3 format:

```cs
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
options.Version = VCardVersion.V30;
dlist.Save("distribution_list.vcf", options);
```

## **Reading MAPI Contacts**

The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class can be used to load both Outlook MSG and VCard format contacts. The following code snippet shows you how to load Outlook contacts saved as MSG and VCF into a [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

### **Load Contacts from MSG Files**

The following code snippet shows you how to load contacts from MSG.

### **Load Contacts from VCards**

The following code snippet shows you how to load contacts from VCard.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cs" >}}

### **Load MAPI Contacts from vCard with Custom Options**

To provide more flexibility when converting vCard (.vcf) files into MAPI contacts, Aspose.Email for .NET provides an overload [MapiContact.FromVCard(string filePath, VCardLoadOptions options)](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/#methods) method that accepts a [VCardLoadOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardloadoptions/) object. It offers improved control over how vCard files are interpreted - especially when working with different vCard formats, encodings, or advanced parsing scenarios.

The following code sample demonstrates how to load a .vcf contact file into a [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) object using the overload that accepts [VCardLoadOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardloadoptions/). The loaded contact can then be used within PST files, MSG export, or other Outlook-compatible formats.

```cs
var mapiContact = MapiContact.FromVCard("contact.vcf", new VCardLoadOptions());
Console.WriteLine(mapiContact.NameInfo.DisplayName);
```

### **Load Contacts from VCards with Specified Encoding**

The following code snippet shows you how to load contacts from VCard with the specified encoding.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.cs" >}}

### **Save VCard Contact Items with Specified Encoding**

Customize the saving behavior when working with VCard files using the [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) class. The [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) property of the class will specify the encoding to be used when saving VCard contact items.

The following code sample shows how to implement this property in your project:

```cs
var cont = VCardContact.Load(fileName, Encoding.UTF8);
var opt = new VCardSaveOptions();
opt.PreferredTextEncoding = Encoding.UTF8;
cont.Save("my.vcard", opt);
```

### **Save VCard Files with Extended fields**

The [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/#vcardsaveoptionsuseextensions-property) property allows you to control whether extended fields can be used when saving vCard files. When set to true (default), extensions are permitted, providing compatibility with custom fields and additional contact information.

### **Read Multiple Contacts in VCard Format**

Our library makes it possible to get the list of all contacts from a VCard. It can be done using the following methods and steps:

```cs
// Checks whether VCard source stream contains multiple contacts.
VCardContact.IsMultiContacts(Stream stream)

// Loads list of all contacts from VCard file.
VCardContact.LoadAsMultiple(string filePath, Encoding encoding)

// Loads list of all contacts from VCard stream.
VCardContact.LoadAsMultiple(Stream stream, Encoding encoding)
```
The following code snippet demonstrates how to handle VCard files that contain multiple contacts:

```cs
using (FileStream stream = new FileStream("test.vcf", FileMode.Open, FileAccess.Read))
{
    if(VCardContact.IsMultiContacts(stream))
    {
        List<VCardContact> contacts = VCardContact.LoadAsMultiple(stream, Encoding.UTF8);
    }
}
```

### **Load vCard Contacts Asynchronously**

The [VCardContact]() class in Aspose.Email for .NET supports asynchronous loading of vCard files. This allows applications to efficiently **read single or multiple contacts from .vcf files or streams without blocking the main thread** - ideal for modern desktop, web, or mobile applications dealing with large contact lists. The following methods of this class can perform the task:

- `LoadAsync`

- `LoadAsMultipleAsync`

The following code sample demonstrates how to **asynchronously load multiple vCard contacts** from a .vcf file using VCardContact.LoadAsMultipleAsync. The loaded contacts are processed in a loop, printing each contact’s display name to the console. The asynchronous approach ensures the application remains responsive, even when reading large files.

```cs
var contacts = await VCardContact.LoadAsMultipleAsync("contacts.vcf", new VCardLoadOptions(), CancellationToken.None);

foreach (var contact in contacts)
{
    Console.WriteLine(contact.IdentificationInfo.DisplayName);
}
```

## **Render Contact Information to MHTML**

Outlook Contact can be converted to MHTML using Aspose.Email API. This example shows how a VCard is loaded into [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) and then converted to MHTML with the help of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) API.

```cs
//Load VCF Contact and convert to MailMessage for rendering to MHTML
var contact = MapiContact.FromVCard("Contact.vcf");

MemoryStream ms = new MemoryStream();
contact.Save(ms, ContactSaveFormat.Msg);
ms.Position = 0;
MapiMessage msg = MapiMessage.Load(ms, new MsgLoadOptions());
MailConversionOptions op = new MailConversionOptions();
MailMessage eml = msg.ToMailMessage(op);

//Prepare the MHT format options
MhtSaveOptions mhtSaveOptions = new MhtSaveOptions();
mhtSaveOptions.CheckBodyContentEncoding = true;
mhtSaveOptions.PreserveOriginalBoundaries = true;
MhtFormatOptions formatOp = MhtFormatOptions.WriteHeader | MhtFormatOptions.RenderVCardInfo;
mhtSaveOptions.RenderedContactFields = ContactFieldsSet.NameInfo | ContactFieldsSet.PersonalInfo | ContactFieldsSet.Telephones | ContactFieldsSet.Events;
mhtSaveOptions.MhtFormatOptions = formatOp;
eml.Save("ContactMhtml_out.mhtml", mhtSaveOptions);
```
