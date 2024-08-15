---
title: Creating an Outlook Contact
type: docs
weight: 70
url: /java/creating-an-outlook-contact/
---


{{% alert color="primary" %}} 

This migration tip shows how to create a Microsot Outlook contact using [Microsoft Office Automation](#office-automation) and [Aspose.Email](#asposeemail-for-java). The code sample shows how to set different information of a Contact such as Personal, Professional and Business information. Creating an Outlook contact consists of the following steps:

1. Creating a Contact object.
1. Populating or setting the property's various properties.
1. Saving the object.

{{% /alert %}} 
## **Office Automation**
To use Office Automation, Microsoft Outlook must be installed on the machine that the code runs on. A reference to Outlook.interop.dll is also required.
### **Programming Samples**
The following code snippet creates an Outlook contact in VCard format and saves it to disc using Office Automation.

**C#**

~~~cs

 Microsoft.Office.Interop.Outlook._Application OutlookObject = new Microsoft.Office.Interop.Outlook.Application();

//Create a new Contact Item

Microsoft.Office.Interop.Outlook.ContactItem contact = OutlookObject.CreateItem(

                        Microsoft.Office.Interop.Outlook.OlItemType.olContactItem);

//Set different properties of this Contact Item.

contact.FirstName = "Mellissa";

contact.LastName = "MacBeth";

contact.JobTitle = "Account Representative";

contact.CompanyName = "Contoso Ltd.";

contact.OfficeLocation = "36/2529";

contact.BusinessTelephoneNumber = "4255551212 x432";

contact.BusinessAddressStreet = "1 Microsoft Way";

contact.BusinessAddressCity = "Redmond";

contact.BusinessAddressState = "WA";

contact.BusinessAddressPostalCode = "98052";

contact.BusinessAddressCountry = "United States of America";

contact.Email1Address = "melissa@contoso.com";

contact.Email1AddressType = "SMTP";

contact.Email1DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Save the Contact to disc

contact.SaveAs("OutlookContact.vcf", OlSaveAsType.olVCard); 

~~~
## **Aspose.Email for Java**
The samples below use Aspose.Email to create the Outlook contact in VCard format and save it to disc. The example shows how to create a contact using the [MapiContact](https://apireference.aspose.com/email/java/com.aspose.email/MapiContact) class and setting the contact details in the object before saving the contact.
### **Programming Samples**

~~~Java

//Create a new MapiContact Object
MapiContact mapiContact = new MapiContact();

//Set different properties of this Contact object
mapiContact.setNameInfo(new MapiContactNamePropertySet("Mellissa", "", "MacBeth"));
mapiContact.getProfessionalInfo().setTitle("Account Representative");
mapiContact.getProfessionalInfo().setCompanyName("Contoso Ltd.");
mapiContact.getProfessionalInfo().setOfficeLocation("36/2529");
mapiContact.getTelephones().setBusinessTelephoneNumber("4255551212 x432");
mapiContact.getPhysicalAddresses().getWorkAddress().setStreet("1 Microsoft Way");
mapiContact.getPhysicalAddresses().getWorkAddress().setCity("Redmond");
mapiContact.getPhysicalAddresses().getWorkAddress().setStateOrProvince("WA");
mapiContact.getPhysicalAddresses().getWorkAddress().setPostalCode("98052");
mapiContact.getPhysicalAddresses().getWorkAddress().setCountry("United States of America");
mapiContact.getElectronicAddresses().getEmail1().setEmailAddress("milissa@contoso.com");
mapiContact.getElectronicAddresses().getEmail1().setAddressType("SMTP");
mapiContact.getElectronicAddresses().getEmail1().setDisplayName("Melissa MacBeth (mellissa@contoso.com)");

//Save the Contact object to disc
mapiContact.save("Contact.vcf", ContactSaveFormat.VCard);

~~~
