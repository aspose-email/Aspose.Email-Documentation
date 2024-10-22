---
title: "Creando un Contacto de Outlook"
url: /es/java/creando-un-contacto-de-outlook/
weight: 70
type: docs
---


{{% alert color="primary" %}} 

Este consejo de migración muestra cómo crear un contacto de Microsoft Outlook usando [Microsoft Office Automation](#office-automation) y [Aspose.Email](#asposeemail-for-java). El ejemplo de código muestra cómo establecer diferente información de un contacto como información Personal, Profesional y Comercial. Crear un contacto de Outlook consiste en los siguientes pasos:

1. Crear un objeto Contacto.
1. Rellenar o establecer las diversas propiedades del objeto.
1. Guardar el objeto.

{{% /alert %}} 
## **Office Automation**
Para usar Office Automation, Microsoft Outlook debe estar instalado en la máquina donde se ejecuta el código. También se requiere una referencia a Outlook.interop.dll.
### **Ejemplos de Programación**
El siguiente fragmento de código crea un contacto de Outlook en formato VCard y lo guarda en disco utilizando Office Automation.

**C#**

~~~cs

 Microsoft.Office.Interop.Outlook._Application OutlookObject = new Microsoft.Office.Interop.Outlook.Application();

//Crear un nuevo elemento de contacto

Microsoft.Office.Interop.Outlook.ContactItem contact = OutlookObject.CreateItem(

                        Microsoft.Office.Interop.Outlook.OlItemType.olContactItem);

//Establecer diferentes propiedades de este elemento de contacto.

contact.FirstName = "Mellissa";

contact.LastName = "MacBeth";

contact.JobTitle = "Representante de Cuenta";

contact.CompanyName = "Contoso Ltd.";

contact.OfficeLocation = "36/2529";

contact.BusinessTelephoneNumber = "4255551212 x432";

contact.BusinessAddressStreet = "1 Microsoft Way";

contact.BusinessAddressCity = "Redmond";

contact.BusinessAddressState = "WA";

contact.BusinessAddressPostalCode = "98052";

contact.BusinessAddressCountry = "Estados Unidos de América";

contact.Email1Address = "melissa@contoso.com";

contact.Email1AddressType = "SMTP";

contact.Email1DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Guardar el contacto en disco

contact.SaveAs("OutlookContact.vcf", OlSaveAsType.olVCard); 

~~~
## **Aspose.Email for Java**
Los ejemplos a continuación utilizan Aspose.Email para crear el contacto de Outlook en formato VCard y guardarlo en disco. El ejemplo muestra cómo crear un contacto usando la clase [MapiContact](https://apireference.aspose.com/email/java/com.aspose.email/MapiContact) y establecer los detalles del contacto en el objeto antes de guardar el contacto.
### **Ejemplos de Programación**

~~~Java

//Crear un nuevo objeto MapiContact
MapiContact mapiContact = new MapiContact();

//Establecer diferentes propiedades de este objeto de contacto
mapiContact.setNameInfo(new MapiContactNamePropertySet("Mellissa", "", "MacBeth"));
mapiContact.getProfessionalInfo().setTitle("Representante de Cuenta");
mapiContact.getProfessionalInfo().setCompanyName("Contoso Ltd.");
mapiContact.getProfessionalInfo().setOfficeLocation("36/2529");
mapiContact.getTelephones().setBusinessTelephoneNumber("4255551212 x432");
mapiContact.getPhysicalAddresses().getWorkAddress().setStreet("1 Microsoft Way");
mapiContact.getPhysicalAddresses().getWorkAddress().setCity("Redmond");
mapiContact.getPhysicalAddresses().getWorkAddress().setStateOrProvince("WA");
mapiContact.getPhysicalAddresses().getWorkAddress().setPostalCode("98052");
mapiContact.getPhysicalAddresses().getWorkAddress().setCountry("Estados Unidos de América");
mapiContact.getElectronicAddresses().getEmail1().setEmailAddress("milissa@contoso.com");
mapiContact.getElectronicAddresses().getEmail1().setAddressType("SMTP");
mapiContact.getElectronicAddresses().getEmail1().setDisplayName("Melissa MacBeth (mellissa@contoso.com)");

//Guardar el objeto de contacto en disco
mapiContact.save("Contact.vcf", ContactSaveFormat.VCard);

~~~