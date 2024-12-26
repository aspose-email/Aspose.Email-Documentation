---
title: Working with Outlook Contacts
ArticleTitle: Working with Outlook Contacts
type: docs
weight: 80
url: /java/working-with-outlook-contacts/
---

## **Create Outlook Contact**

Aspose.Email for Java supports creating Outlook contacts (VCards) using the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class. [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) contains many methods some of which are given below.

- [MapiContactElectronicAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) contains a set of [MapiContactElectronicAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/).
- [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--)
- [MapiContactNamePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--)
- [MapiContactPersonalInfoPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--)
- [MapiContactPhysicalAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) contains a set of [MapiContactPhysicalAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--).
- [MapiContactProfessionalPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
- [MapiContactTelephonePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--)
  
### **Contact Structure in Aspose.Email for Java**

Below is the hierarchy implemented for contacts in Aspose.Email for Java. The relevant class name is given against each property. Hyperlinks are provided to the online documentation for further reference.

1. [Contact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) (MapiContact)
   1. [Electronic Addresses](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) (MapiContactElectronicAddressPropertySet)
      1. [Email1](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/) (MapiContactElectronicAddress)
         1. Address Type
         1. Display Name
         1. Email Address
         1. Fax Number
      1. Email2
      1. Email3
      1. Home Fax
      1. Primary Fax
      1. Business Fax
   1. [Events](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) (MapiContactEventPropertySet)
      See below for an example of how to set events.
      1. Birthday
      1. Wedding Anniversary
   1. [Name Info](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--) (MapiContactNamePropertySet)
      1. Display Name
      1. Display Name Prefix
      1. File Under
      1. File Under ID
      1. Generation
      1. Given Name
      1. Initials
      1. Middle Name
      1. Nick Name
      1. Surname
   1. [Personal Info](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--) (MapiContactPersonalInfoPropertySet)
      1. Account
      1. Business Home Page
      1. Computer Network Name
      1. Customer ID
      1. Free Business Location
      1. FTP Site
      1. Gender
      1. Government ID Number
      1. Hobbies
      1. HTML
      1. Instant Messaging Address
      1. Language
      1. Location
      1. Notes
      1. Organizational ID Number
      1. Personal Home Page
      1. Referred by Name
      1. Spouse Name
   1. [Physical Address](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) (MapiContactPhysicalAddressPropertySet)
      1. [Home Address](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--) (MapiContactPhysicalAddress)
         1. Address
         1. City
         1. Country
         1. Country Code
         1. Postal Code
         1. Post Office Box
         1. State Or Province
      1. Other Address
      1. Work Address
   2. [Professional Info](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
      1. Assistant
      2. Company Name
      3. Depart Name
      4. Manager Name
      5. Office Location
      6. Profession
      7. Title
   3. [Telephones](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--) (MapiContactTelephonePropertySet)
      1. Assistant Telephone Number
      2. Business2 Telephone Number
      3. Business Telephone Number
      4. Callback Telephone Number
      5. Car Telephone Number
      6. Company Main Telephone Number
      7. Home2 Telephone Number
      8. Home Telephone Number
      9. ISDN Number
      10. Mobile Telephone Number
      11. Other Telephone Number
      12. Pager Telephone Number
      13. Primary Telephone Number
      14. Radio Telephone Number
      15. Telex Number
      16. TTY/TDD Phone Number

The following code uses Aspose.Email to create an Outlook contact and fills it with name, professional properties, physical address, and email. It also shows adding [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) to the contact.

|![todo:image_alt_text](https://i.imgur.com/D4jXgXo.png)|
| :- |
|**Figure: A Microsoft Outlook contact coded in with Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-CreateOutlookContact.java" >}}

### **Adding Contact Event Information to a MapiContact**

Microsoft Outlook lets users add event information to a contact. The event holds the birthday and wedding anniversary. Aspose.Email provides the [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/) class for adding this information to a contact. This is elaborated in the following example.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-AddingContactEventInformationToAMapiContact.java" >}}

## **Creating, Saving and Reading Outlook Contacts**

Aspose.Email allows developers to create Microsoft Outlook contacts as well as email messages. The [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class provides all contact properties required to create an Outlook contact. This article shows how to create, save and read an Outlook contact using the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.

### **Create and Save a MapiContact**

The following steps can be used to create and save a contact to disc:

1. Instantiate a new object of the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.
1. Enter information related to various properties of the contact.
1. Add photo data to the contact, if any.
1. Save the contact as MSG or VCard format.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-CreatingAndSavingAMapiContact.java" >}}

### **Save Contact in Version 3 VCF Format**

To save the contact in version 3 VCF format, use the [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) enumerable to set the [VCardSaveOptions.Version](https://reference.aspose.com/email/java/com.aspose.email/vcardsaveoptions/#getVersion--) property. The following sample code demonstrates the use of [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) enumerable to save the contact VCF version 3 format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateV30Contact-1.java" >}}

### **Read a MapiContact**

The [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class can be used to load both Microsoft Outlook MSG files as well as VCard format contacts. The following code samples show how to load Outlook contacts saved as MSG and VCF into [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

#### **Load a Contact from MSG**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromMSG.java" >}}

#### **Load a contact from VCard**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromVCard.java" >}}

#### **Load VCard Contact with specified Encoding**

Supported Method: [MapiContact.fromVCard(String, Encoding)](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/#fromVCard-java.lang.String-java.nio.charset.Charset-)

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingVCardContactWithSpecifiedEncoding.java" >}}

## **Rendering Contact Information to MHTML**

Outlook Contact can be converted to MHTML using Aspose.Email API. This example shows how a VCard is loaded into [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) and then converted to MHTML with the help of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) API.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.java" >}}
