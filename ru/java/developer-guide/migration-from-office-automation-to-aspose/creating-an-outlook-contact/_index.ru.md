---
title: "Создание контакта Outlook"
url: /ru/java/creating-an-outlook-contact/
weight: 70
type: docs
---


{{% alert color="primary" %}}

В этом совете по миграции показано, как создать контакт Microsoft Outlook с помощью [Автоматизация работы Microsoft Office](#office-automation) and [Aspose.Email](#asposeemail-for-java). В примере кода показано, как настроить различную информацию о контакте, например личную, профессиональную и деловую информацию. Создание контакта Outlook состоит из следующих шагов:

1. Создание объекта Contact.
1. Заполнение или настройка различных свойств свойства.
1. Сохранение объекта.

{{% /alert %}}
## **Автоматизация делопроизводства**
Чтобы использовать Автоматизация делопроизводства, Microsoft Outlook должен быть установлен на компьютере, на котором работает код. Также требуется ссылка на Outlook.Interop.dll.
### **Примеры программирования**
Следующий фрагмент кода создает контакт Outlook в формате vCard и сохраняет его на диске с помощью Автоматизация делопроизводства.

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
## **Aspose.Электронная почта для Java**
В приведенных ниже примерах используется Aspose.Email для создания контакта Outlook в формате vCard и сохранения его на диске. В примере показано, как создать контакт с помощью [MapiContact](https://apireference.aspose.com/email/java/com.aspose.email/MapiContact) класс и настройка контактных данных в объекте перед сохранением контакта.
### **Примеры программирования**

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
