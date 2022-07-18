---
title: Working with Outlook Contacts
type: docs
weight: 80
url: /java/working-with-outlook-contacts/
---

## **Create Outlook Contact**
Aspose.Email for Java supports creating Outlook contacts (VCards) using the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class. [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) contains many methods some of which are given below.

- [MapiContactElectronicAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContactelectronicaddresspropertyset) contains a set of [MapiContactElectronicAddress](https://reference.aspose.com/email/java/com.aspose.email/MapiContactelectronicaddress).
- [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContacteventpropertyset)
- [MapiContactNamePropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContactNamePropertySet)
- [MapiContactPersonalInfoPropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContactPersonalInfoPropertySet)
- [MapiContactPhysicalAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContactPhysicalAddressPropertySet) contains a set of [MapiContactPhysicalAddress](https://reference.aspose.com/email/java/com.aspose.email/MapiContactPhysicalAddress).
- [MapiContactProfessionalPropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContactProfessionalPropertySet)
- [MapiContactTelephonePropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContactTelephonePropertySet)
### **Contact Structure in Aspose.Email for Java**
Below is the hierarchy implemented for contacts in Aspose.Email for Java. The relevant class name is given against each property. Hyperlinks are provided to the online documentation for further reference.

1. [Contact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) (MapiContact)
   1. [Electronic Addresses](https://reference.aspose.com/email/java/com.aspose.email/MapiContactElectronicAddressPropertySet) (MapiContactElectronicAddressPropertySet)
      1. [Email1](https://reference.aspose.com/email/java/com.aspose.email/MapiContactElectronicAddress) (MapiContactElectronicAddress)
         1. Address Type
         1. Display Name
         1. Email Address
         1. Fax Number
      1. Email2
      1. Email3
      1. Home Fax
      1. Primary Fax
      1. Business Fax
   1. [Events](https://reference.aspose.com/email/java/com.aspose.email/MapiContactEventPropertySet) (MapiContactEventPropertySet)
      See below for an example of how to set events.
      1. Birthday
      1. Wedding Anniversary
   1. [Name Info](https://reference.aspose.com/email/java/com.aspose.email/MapiContactNamePropertySet) (MapiContactNamePropertySet)
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
   1. [Personal Info](https://reference.aspose.com/email/java/com.aspose.email/MapiContactPersonalInfoPropertySet) (MapiContactPersonalInfoPropertySet)
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
   1. [Physical Address](https://reference.aspose.com/email/java/com.aspose.email/MapiContactPhysicalAddressPropertySet) (MapiContactPhysicalAddressPropertySet)
      1. [Home Address](https://reference.aspose.com/email/java/com.aspose.email/MapiContactPhysicalAddress) (MapiContactPhysicalAddress)
         1. Address
         1. City
         1. Country
         1. Country Code
         1. Postal Code
         1. Post Office Box
         1. State Or Province
      1. Other Address
      1. Work Address
   1. [Professional Info](https://reference.aspose.com/email/java/com.aspose.email/MapiContactProfessionalPropertySet) (MapiContactProfessionalPropertySet)
      1. Assistant
      1. Company Name
      1. Depart Name
      1. Manager Name
      1. Office Location
      1. Profession
      1. Title
   1. [Telephones](https://reference.aspose.com/email/java/com.aspose.email/MapiContactTelephonePropertySet) (MapiContactTelephonePropertySet)
      1. Assistant Telephone Number
      1. Business2 Telephone Number
      1. Business Telephone Number
      1. Callback Telephone Number
      1. Car Telephone Number
      1. Company Main Telephone Number
      1. Home2 Telephone Number
      1. Home Telephone Number
      1. ISDN Number
      1. Mobile Telephone Number
      1. Other Telephone Number
      1. Pager Telephone Number
      1. Primary Telephone Number
      1. Radio Telephone Number
      1. Telex Number
      1. TTY/TDD Phone Number

The following code uses Aspose.Email to create an Outlook contact and fills it with name, professional properties, physical address, and email. It also shows adding [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContacteventpropertyset) to the contact.

|![todo:image_alt_text](https://i.imgur.com/D4jXgXo.png)|
| :- |
|**Figure: A Microsoft Outlook contact coded in with Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-CreateOutlookContact.java" >}}
### **Adding Contact Event Information to a MapiContact**
Microsoft Outlook lets users add event information to contact. The event holds the birthday and wedding anniversary. Aspose.Email provides the [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/MapiContacteventpropertyset) class for adding this information to a contact. This is elaborated in the following example.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-AddingContactEventInformationToAMapiContact.java" >}}
## **Creating, Saving and Reading Outlook Contacts**
Aspose.Email allows developers to create Microsoft Outlook contacts as well as email messages. The [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class provides all contact properties required to create an Outlook contact. This article shows how to create, save and read an Outlook contact using the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class.
### **Create and Save a MapiContact**
The following steps can be used to create and save a contact to disc:

1. Instantiate a new object of the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class.
1. Enter information related to various properties of the contact.
1. Add photo data to the contact, if any.
1. Save the contact as MSG or VCard format.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-CreatingAndSavingAMapiContact.java" >}}
### **Save Contact in Version 3 VCF Format**
To save the contact in version 3 VCF format, use the [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/VCardVersion) enumerable to set the [VCardSaveOptions.Version](https://reference.aspose.com/email/java/com.aspose.email/VCardSaveOptions#setVersion\(int\)) property. The following sample code demonstrates the use of [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/VCardVersion) enumerable to save the contact VCF version 3 format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateV30Contact-1.java" >}}
### **Read a MapiContact**
The [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class can be used to load both Microsoft Outlook MSG files as well as VCard format contacts. The following code samples show how to load Outlook contacts saved as MSG and VCF into [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact).
#### **Load a Contact from MSG**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromMSG.java" >}}


#### **Load a contact from VCard**
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromVCard.java" >}}
#### **Load VCard Contact with specified Encoding**
Supported Method: [MapiContact.fromVCard(String, Encoding)](https://reference.aspose.com/email/java/com.aspose.email/MapiContact#fromVCard\(java.lang.String,%20java.nio.charset.Charset\))

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingVCardContactWithSpecifiedEncoding.java" >}}
## **Rendering Contact Information to MHTML**
Outlook Contact can be converted to MHTML using Aspose.Email API. This example shows how a VCard is loaded into [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) and then converted to MHTML with the help of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage) API.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.java" >}}
