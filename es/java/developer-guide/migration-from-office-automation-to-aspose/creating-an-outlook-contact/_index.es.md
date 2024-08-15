---
title: "Creación de un contacto de Outlook"
url: /es/java/creating-an-outlook-contact/
weight: 70
type: docs
---


{{% alert color="primary" %}}

Este consejo de migración muestra cómo crear un contacto de Microsoft Outlook mediante [Automatización de Microsoft Office](#office-automation) and [Aspose.Email](#asposeemail-for-java). El ejemplo de código muestra cómo configurar diferentes datos de un contacto, como la información personal, profesional y empresarial. La creación de un contacto de Outlook consiste en los siguientes pasos:

1. Creación de un objeto de contacto.
1. Rellenar o configurar las distintas propiedades de la propiedad.
1. Guardar el objeto.

{{% /alert %}}
## **Automatización de oficinas**
Para usar Automatización de oficinas, Microsoft Outlook debe estar instalado en la máquina en la que se ejecuta el código. También es necesaria una referencia a Outlook.Interop.dll.
### **Ejemplos de programación**
El siguiente fragmento de código crea un contacto de Outlook en formato vCard y lo guarda en un disco mediante Automatización de oficinas.

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
## **Aspose.Email para Java**
Los ejemplos siguientes utilizan Aspose.Email para crear el contacto de Outlook en formato vCard y guardarlo en un disco. El ejemplo muestra cómo crear un contacto mediante el [MapiContact](https://apireference.aspose.com/email/java/com.aspose.email/MapiContact) clase y configuración de los detalles de contacto en el objeto antes de guardar el contacto.
### **Ejemplos de programación**

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
