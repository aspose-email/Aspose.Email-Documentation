---
title: "Создание контакта в Outlook"
url: /ru/java/creating-an-outlook-contact/
weight: 70
type: docs
---


{{% alert color="primary" %}} 

Этот совет по миграции показывает, как создать контакт Microsoft Outlook с использованием [Microsoft Office Automation](#office-automation) и [Aspose.Email](#asposeemail-for-java). Пример кода показывает, как задать различную информацию о контакте, такую как личная, профессиональная и деловая информация. Создание контакта в Outlook состоит из следующих шагов:

1. Создание объекта контакта.
1. Заполнение или установка различных свойств объекта.
1. Сохранение объекта.

{{% /alert %}} 
## **Office Automation**
Для использования Office Automation необходимо установить Microsoft Outlook на машину, на которой выполняется код. Также требуется ссылка на Outlook.interop.dll.
### **Примеры программирования**
Следующий фрагмент кода создает контакт Outlook в формате VCard и сохраняет его на диск с использованием Office Automation.

**C#**

~~~cs

 Microsoft.Office.Interop.Outlook._Application OutlookObject = new Microsoft.Office.Interop.Outlook.Application();

//Создать новый элемент контакта

Microsoft.Office.Interop.Outlook.ContactItem contact = OutlookObject.CreateItem(

                        Microsoft.Office.Interop.Outlook.OlItemType.olContactItem);

//Задать разные свойства этого элемента контакта.

contact.FirstName = "Мелисса";

contact.LastName = "Макбет";

contact.JobTitle = "Представитель по работе с клиентами";

contact.CompanyName = "Contoso Ltd.";

contact.OfficeLocation = "36/2529";

contact.BusinessTelephoneNumber = "4255551212 x432";

contact.BusinessAddressStreet = "1 Microsoft Way";

contact.BusinessAddressCity = "Редмонд";

contact.BusinessAddressState = "WA";

contact.BusinessAddressPostalCode = "98052";

contact.BusinessAddressCountry = "Соединенные Штаты Америки";

contact.Email1Address = "melissa@contoso.com";

contact.Email1AddressType = "SMTP";

contact.Email1DisplayName = "Мелисса Макбет (mellissa@contoso.com)";

//Сохранить контакт на диск

contact.SaveAs("OutlookContact.vcf", OlSaveAsType.olVCard); 

~~~
## **Aspose.Email для Java**
Примеры ниже используют Aspose.Email для создания контакта Outlook в формате VCard и его сохранения на диск. В примере показано, как создать контакт с использованием класса [MapiContact](https://apireference.aspose.com/email/java/com.aspose.email/MapiContact) и установить детали контакта в объекте перед его сохранением.
### **Примеры программирования**

~~~Java

//Создать новый объект MapiContact
MapiContact mapiContact = new MapiContact();

//Задать разные свойства этого объекта контакта
mapiContact.setNameInfo(new MapiContactNamePropertySet("Мелисса", "", "Макбет"));
mapiContact.getProfessionalInfo().setTitle("Представитель по работе с клиентами");
mapiContact.getProfessionalInfo().setCompanyName("Contoso Ltd.");
mapiContact.getProfessionalInfo().setOfficeLocation("36/2529");
mapiContact.getTelephones().setBusinessTelephoneNumber("4255551212 x432");
mapiContact.getPhysicalAddresses().getWorkAddress().setStreet("1 Microsoft Way");
mapiContact.getPhysicalAddresses().getWorkAddress().setCity("Редмонд");
mapiContact.getPhysicalAddresses().getWorkAddress().setStateOrProvince("WA");
mapiContact.getPhysicalAddresses().getWorkAddress().setPostalCode("98052");
mapiContact.getPhysicalAddresses().getWorkAddress().setCountry("Соединенные Штаты Америки");
mapiContact.getElectronicAddresses().getEmail1().setEmailAddress("milissa@contoso.com");
mapiContact.getElectronicAddresses().getEmail1().setAddressType("SMTP");
mapiContact.getElectronicAddresses().getEmail1().setDisplayName("Мелисса Макбет (mellissa@contoso.com)");

//Сохранить объект контакта на диск
mapiContact.save("Contact.vcf", ContactSaveFormat.VCard);

~~~