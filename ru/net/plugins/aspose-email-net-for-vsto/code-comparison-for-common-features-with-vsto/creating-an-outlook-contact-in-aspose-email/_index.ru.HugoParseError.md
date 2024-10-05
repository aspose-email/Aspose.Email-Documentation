---
title: Создание контакта Outlook в Aspose.Email
type: docs
weight: 80
url: /net/creating-an-outlook-contact-in-aspose-email/
---


Этот совет по миграции показывает, как создать контакт Microsoft Outlook с помощью автоматизации Microsoft Office и Aspose.Email. Пример кода демонстрирует, как задать различную информацию о контакте, такую как Личная, Профессиональная и Деловая информация. Создание контакта Outlook включает в себя следующие шаги:

1. Создание объекта контакта.
1. Заполнение или установка различных свойств объекта.
1. Сохранение объекта.
## **VSTO**
``` cs

 //Создать новый объект MapiContact

MapiContact mapiContact = new MapiContact();

//Установить различные свойства этого объекта контакта

mapiContact.NameInfo = new MapiContactNamePropertySet("Mellissa", "", "MacBeth");

mapiContact.ProfessionalInfo.Title = "Представитель по аккаунтам";

mapiContact.ProfessionalInfo.CompanyName = "Contoso Ltd.";

mapiContact.ProfessionalInfo.OfficeLocation = "36/2529";

mapiContact.Telephones.BusinessTelephoneNumber = "4255551212 x432";

mapiContact.PhysicalAddresses.WorkAddress.Street = "1 Microsoft Way";

mapiContact.PhysicalAddresses.WorkAddress.City = "Редмонд";

mapiContact.PhysicalAddresses.WorkAddress.StateOrProvince = "WA";

mapiContact.PhysicalAddresses.WorkAddress.PostalCode = "98052";

mapiContact.PhysicalAddresses.WorkAddress.Country = "Соединенные Штаты Америки";

mapiContact.ElectronicAddresses.Email1.EmailAddress = "milissa@contoso.com";

mapiContact.ElectronicAddresses.Email1.AddressType = "SMTP";

mapiContact.ElectronicAddresses.Email1.DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Сохранить объект контакта на диск

mapiContact.Save("Contact.vcf", ContactSaveFormat.VCard);

```
## **Aspose.Email**
``` cs

 //Создать новый объект MapiContact

MapiContact mapiContact = new MapiContact();

//Установить различные свойства этого объекта контакта

mapiContact.NameInfo = new MapiContactNamePropertySet("Mellissa", "", "MacBeth");

mapiContact.ProfessionalInfo.Title = "Представитель по аккаунтам";

mapiContact.ProfessionalInfo.CompanyName = "Contoso Ltd.";

mapiContact.ProfessionalInfo.OfficeLocation = "36/2529";

mapiContact.Telephones.BusinessTelephoneNumber = "4255551212 x432";

mapiContact.PhysicalAddresses.WorkAddress.Street = "1 Microsoft Way";

mapiContact.PhysicalAddresses.WorkAddress.City = "Редмонд";

mapiContact.PhysicalAddresses.WorkAddress.StateOrProvince = "WA";

mapiContact.PhysicalAddresses.WorkAddress.PostalCode = "98052";

mapiContact.PhysicalAddresses.WorkAddress.Country = "Соединенные Штаты Америки";

mapiContact.ElectronicAddresses.Email1.EmailAddress = "milissa@contoso.com";

mapiContact.ElectronicAddresses.Email1.AddressType = "SMTP";

mapiContact.ElectronicAddresses.Email1.DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Сохранить объект контакта на диск

mapiContact.Save("Contact.vcf", ContactSaveFormat.VCard);

```
## **Скачать образец кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772939)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Creating.an.Outlook.Contact.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Creating%20an%20Outlook%20Contact%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Creating%20an%20Outlook%20Contact%20\(Aspose.Email\).zip)