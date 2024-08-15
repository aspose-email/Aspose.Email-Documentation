---
title: "Создание контакта Outlook в Aspose.Email"
url: /ru/net/creating-an-outlook-contact-in-aspose-email/
weight: 80
type: docs
---


В этом совете по миграции показано, как создать контакт Microsoft Outlook с помощью Microsoft Office Automation и Aspose.Email. В примере кода показано, как настроить различную информацию о контакте, например личные, профессиональные и деловые сведения. Создание контакта Outlook состоит из следующих шагов:

1. Создание объекта Contact.
1. Заполнение или настройка различных свойств свойства.
1. Сохранение объекта.
## **VSTO**
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
## **Aspose.Email**
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
## **Загрузить образец кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772939)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Creating.an.Outlook.Contact.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Creating%20an%20Outlook%20Contact%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Creating%20an%20Outlook%20Contact%20\(Aspose.Email\).zip)
