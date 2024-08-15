---
title: Working with Outlook Contacts
type: docs
weight: 90
url: /net/working-with-outlook-contacts/
---


## **Creating, Saving and Reading Contacts**

Like MapiMessage, Aspose.Email allows you to create Outlook contacts. The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class provides all the contact related properties required to create an Outlook contact. This article shows how to create, save and read an Outlook contact using the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.

### **Create and Save Outlook Contact**

To create a contact and save it to disc:

1. Instantiate a new object of the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.
1. Enter contact property information.
1. Add photo data (if any).
1. Save the contact as MSG or VCard format.

The following code snippet shows you how to create and save outlook contact.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cs" >}}

### **Save Mapi Distribution List to a Single Multi Contact VCF File**

The code sample below demonstrates how to save a distribution list to a multi-contact VCF file:

```cs
// convert the `msg` object to a `MapiMessage` object
var dlist = (MapiDistributionList)msg.ToMapiMessageItem();

//save the distribution list
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.Save("distribution_list.vcf", options);
```


### **Save Contact in Version 3 VCF Format**

To save the contact in version 3 VCF format, use the [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) enumerable to set the [VCardSaveOptions.Version](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) property. The following sample code demonstrates the use of [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) enumerable to save the contact VCF version 3 format:

```cs

```

### **Reading a MapiContact**

The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class can be used to load both Outlook MSG and VCard format contacts. The following code snippet shows you how to load Outlook contacts saved as MSG and VCF into a [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

#### **Loading a Contact from MSG**

The following code snippet shows you how to load contacts from MSG.

#### **Loading a Contact from VCard**

The following code snippet shows you how to load contacts from VCard.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cs" >}}

#### **Loading a Contact from VCard with Specified Encoding**

The following code snippet shows you how to load contacts from VCard with the specified encoding.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.cs" >}}

#### **Saving VCard Contact Items with Specified Encoding**

Customize the saving behavior when working with VCard files using the [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) class. The [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) property of the class will specify the encoding to be used when saving VCard contact items.

The following code sample shows how to implement this property in your project:

```cs
var cont = VCardContact.Load(fileName, Encoding.UTF8);
var opt = new VCardSaveOptions();
opt.PreferredTextEncoding = Encoding.UTF8;
cont.Save("my.vcard", opt);
```

#### **Saving VCard Files with Extended fields**

The [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/#vcardsaveoptionsuseextensions-property) property allows you to control whether extended fields can be used when saving vCard files. When set to true (default), extensions are permitted, providing compatibility with custom fields and additional contact information.

### **Reading Multiple Contacts in VCard format**

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

## **Rendering Contact Information to MHTML**

Outlook Contact can be converted to MHTML using Aspose.Email API. This example shows how a VCard is loaded into [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) and then converted to MHTML with the help of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) API.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.cs" >}}
