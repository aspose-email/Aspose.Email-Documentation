---
title: Creating an Outlook Contact
type: docs
weight: 70
url: /net/creating-an-outlook-contact/
---


{{% alert color="primary" %}} 

This migration tip shows how to create a Microsot Outlook contact using [Microsoft Office Automation](#office-automation) and [Aspose.Email](#asposeemail-for-net). The code sample shows how to set different information of a Contact such as Personal, Professional and Business information. Creating an Outlook contact consists of the following steps:

1. Creating a Contact object.
1. Populating or setting the property's various properties.
1. Saving the object.

{{% /alert %}} 
## **Office Automation**
To use Office Automation, Microsoft Outlook must be installed on the machine that the code runs on. A reference to Outlook.interop.dll is also required.
### **Programming Samples**
The following code snippet creates an Outlook contact in VCard format and saves it to disc using Office Automation.

**C#**

``` cs

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

```
## **Aspose.Email for .NET**
The samples below use Aspose.Email to create the Outlook contact in VCard format and save it to disc. The example shows how to create a contact using the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/index) class and setting the contact details in the object before saving the contact.
### **Programming Samples**
**C#**

``` cs

 //Create a new MapiContact Object

MapiContact mapiContact = new MapiContact();

//Set different properties of this Contact object

mapiContact.NameInfo = new MapiContactNamePropertySet("Mellissa", "", "MacBeth");

mapiContact.ProfessionalInfo.Title = "Account Representative";

mapiContact.ProfessionalInfo.CompanyName = "Contoso Ltd.";

mapiContact.ProfessionalInfo.OfficeLocation = "36/2529";

mapiContact.Telephones.BusinessTelephoneNumber = "4255551212 x432";

mapiContact.PhysicalAddresses.WorkAddress.Street = "1 Microsoft Way";

mapiContact.PhysicalAddresses.WorkAddress.City = "Redmond";

mapiContact.PhysicalAddresses.WorkAddress.StateOrProvince = "WA";

mapiContact.PhysicalAddresses.WorkAddress.PostalCode = "98052";

mapiContact.PhysicalAddresses.WorkAddress.Country = "United States of America";

mapiContact.ElectronicAddresses.Email1.EmailAddress = "milissa@contoso.com";

mapiContact.ElectronicAddresses.Email1.AddressType = "SMTP";

mapiContact.ElectronicAddresses.Email1.DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Save the Contact object to disc

mapiContact.Save("Contact.vcf", ContactSaveFormat.VCard);

```
