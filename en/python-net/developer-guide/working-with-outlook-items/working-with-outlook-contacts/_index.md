---
title: Working with Outlook Contacts
type: docs
weight: 90
url: /python-net/working-with-outlook-contacts/
---


## **Creating, Saving and Reading Contacts**
Like MapiMessage, Aspose.Email allows you to create Outlook contacts. The MapiContact class provides all the contact related properties required to create an Outlook contact. This article shows how to create, save and read an Outlook contact using the MapiContact class.
### **Create and Save Outlook Contact**
To create a contact and save it to disc:

1. Instantiate a new object of the MapiContact class.
1. Enter contact property information.
1. Add photo data (if any).
1. Save the contact as MSG or VCard format.

The following code snippet shows you how to create and save outlook contact.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
contact.professional_info = ae.mapi.MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant")
contact.personal_info.personal_home_page = "B2BTies.com"
contact.physical_addresses.work_address.address = "Im Astenfeld 59 8580 EDELSCHROTT"
contact.electronic_addresses.email1 = ae.mapi.MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com")
contact.telephones = ae.mapi.MapiContactTelephonePropertySet("06605045265")
contact.personal_info.children = ["child1", "child2", "child3"]
contact.categories = ["category1", "category2", "category3"]
contact.mileage = "Some test mileage"
contact.billing = "Test billing information"
contact.other_fields.journal = True
contact.other_fields.private = True
contact.other_fields.reminder_topic = "Test topic"
contact.other_fields.user_field1 = "ContactUserField1"
contact.other_fields.user_field2 = "ContactUserField2"
contact.other_fields.user_field3 = "ContactUserField3"
contact.other_fields.user_field4 = "ContactUserField4"

# Add a photo
with open(data_dir + "Desert.jpg", "rb") as file:
    buffer = file.read()
    contact.photo = ae.mapi.MapiContactPhoto(buffer, ae.mapi.MapiContactPhotoImageFormat.Jpeg)

# Save the Contact in MSG format
contact.save(data_dir + "MapiContact_out.msg", ae.mapi.ContactSaveFormat.MSG)

# Save the Contact in VCF format
contact.save(data_dir + "MapiContact_out.vcf", ae.mapi.ContactSaveFormat.V_CARD)
```

### **Save Contact in VCF Format Version 3**

To save a contact in VCF format Version 3, use the *version* property of the [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) class. Create a new instance of the VCardSaveOptions class, set the version property of the VCardSaveOptions object to VCardVersion.V30. This sets the vCard version to 3.0., call the *save* method of the MapiContact object, passing the file name "contact.vcf" and the VCardSaveOptions object as parameters. This saves the contact as a vCard file with the specified file name and options. The following code snippet shows you how to save a contact in VCF format Version 3:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.version = ae.personalinfo.vcard.VCardVersion.V30
contact.save("contact.vcf", options)
```

### **Reading a MapiContact**
The MapiContact class can be used to load both Outlook MSG and VCard format contacts. The following code snippet shows you how to load Outlook contacts saved as MSG and VCF into a MapiContact.
#### **Loading a Contact from MSG**
The following code snippet shows you how to loading a contact from MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
#### **Loading a Contact from VCard**
The following code snippet shows you how to loading a contact from vCard.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCF-LoadingContactFromVCF.py" >}}
#### **Loading a Contact from VCard with Specified Encoding**
The following code snippet shows you how to loading a contact from vcard with specified encoding.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.py" >}}

#### **Saving VCard Contact Items with Specified Encoding**

When saving a vCard file, it is possible to specify the character encoding to be used ensuring compatibility with non-ASCII characters. Set the *preferred_text_encoding* property of the VCardSaveOptions object to "utf-8". The following code snippet shows how to implement this function into your project:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.preferred_text_encoding = "utf-8"
contact.save("contact.vcf", options)
```

#### **Saving VCard Files with Extended fields**

When saving a vCard file, you can also specify options including the usage of extended fields that is additional properties or attributes that can be added to a vCard beyond the standard set of fields defined by the vCard specification. The *use_extensions* property of the [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) class allows you to do it. The following code snippet shows how to save a VCard file with extended fields:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)
```
#### **Reading Multiple Contacts in VCard format**

You will need the following methods to get the list of all contacts from a VCard:

```
# Checks whether VCard source stream contains multiple contacts.
aspose.email.personalinfo.vcard.VCardContact.is_multi_contacts(stream)

# Loads list of all contacts from VCard file.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(file_path, encoding)

# Loads list of all contacts from VCard stream.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(stream, encoding)
```
The code snippet below will demonstrate the process of reading multiple contacts from a VCard file:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)

if ae.personalinfo.vcard.VCardContact.is_multi_contacts("contact.vcf"):
    ae.personalinfo.vcard.VCardContact.load_as_multiple("contact.vcf")
```

## **Rendering Contact Information to MHTML**
Outlook Contact can be converted to MHTML using Aspose.Email API. This example shows how a VCard is loaded into MapiContact and then converted to MHTML with the help of MailMessage API.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.py" >}}
