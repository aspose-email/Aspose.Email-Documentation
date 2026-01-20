---
title: Managing Outlook Contacts in PST Files 
ArticleTitle: Managing Outlook Contacts in PST Files
type: docs
weight: 90
url: /python-net/managing-outlook-contacts-in-python/
---


## **Creating, Saving and Reading Contacts**

Aspose.Email allows you to create and process Outlook contacts. The [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/#mapicontact-class) class provides all the contact related properties required to create and manipulate an Outlook contact. This article shows how to create, save and read an Outlook contact using the [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/#mapicontact-class) class.

### **Create and Save Outlook Contacts**

**To create a contact and save it to disc**, follow these steps:

1. Instantiate a new object of the [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/#mapicontact-class) class.
1. Enter contact property information.
1. Add photo data (if any).
1. Save the contact as MSG or VCard format.

The following code snippet shows you how to create and save an Outlook contact:

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

### **Save Contacts in VCF Format Version 3**

To save a contact in VCF format Version 3, use the *version* property of the [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) class.

1. Create a new instance of the [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) class.
2. Set the version property of the VCardSaveOptions object to VCardVersion.V30. This sets the vCard version to 3.0.
3. Call the [save](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/#methods) method of the *MapiContact* object, passing the file name "contact.vcf" and the *VCardSaveOptions* object as parameters. This saves the contact as a vCard file with the specified file name and options. 

The following code snippet shows you how to save a contact in VCF format Version 3:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.version = ae.personalinfo.vcard.VCardVersion.V30
contact.save("contact.vcf", options)
```

### **Load Contacts from MSG or VCard Files**

The [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/#mapicontact-class) class can be used to load both Outlook MSG and VCard format contacts. 

To **load a contact from MSG**, use the code sample below:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}

To **load a contact from VCard**, use the following code sample:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCF-LoadingContactFromVCF.py" >}}

### **Load Contacts with Specified Encoding**

The following code snippet shows you how to load a contact from vcard with specified encoding.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.py" >}}

### **Save VCard Files with Custom Character Encoding**

When saving a vCard file, you can define the character encoding to ensure compatibility with non-ASCII characters. For instance, setting the *preferred_text_encoding* property of the [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) object to "utf-8" ensures proper encoding of non-ASCII text. This feature is particularly useful for handling multilingual contact data. Below is an example of how to configure and save a vCard file with custom character encoding:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.preferred_text_encoding = "utf-8"
contact.save("contact.vcf", options)
```

#### **Save VCard Files with Extended Properties**

In addition to standard vCard fields, you can enhance your vCard files by including extended properties. These are additional attributes not covered by the standard vCard specification, allowing greater customization. To enable this, set the *use_extensions* property of the [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) class to True. This is particularly beneficial for adding custom or application-specific metadata. Here’s how you can save a vCard file with extended properties enabled:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)
```

### **Read Multiple Contacts in VCard Format**

To retrieve all contacts from a VCard, you can use the following [methods](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardcontact/#methods):

- *is_multi_contacts* method determines if a stream has multiple contacts.
- *load_as_multiple(file_path)* method loads a list of all contacts from a VCard file.
- *load_as_multiple(stream)* method loads a list of all contacts from a VCard stream.

The code snippet below demonstrates the process of reading multiple contacts from a VCard file:

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

## **Render Contact Information to MHTML**

Outlook Contact can be converted to MHTML using Aspose.Email API. The following code sample demonstrates how to generate an MHTML file that contains detailed contact information originally from an MSG file: 

1. Load the MSG file as a [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) object.
2. Convert the message to EML format.
3. Prepare MHT save options:  
   - Enable body content encoding and preserve original boundaries.  
   - Set MHT format options to write headers and render vCard information.
4. Define fields to render in the MHT.
5. Save the EML as an MHTML file.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.py" >}}
