---
title: "Creando un contacto de Outlook en Aspose.Email"
url: /es/net/creando-un-contacto-de-outlook-en-aspose-email/
weight: 80
type: docs
---

Este consejo de migración muestra cómo crear un contacto de Microsoft Outlook utilizando Microsoft Office Automation y Aspose.Email. El ejemplo de código muestra cómo establecer diferentes informaciones de un contacto, como información personal, profesional y empresarial. Crear un contacto de Outlook consiste en los siguientes pasos:

1. Crear un objeto Contacto.
1. Población o establecimiento de las diversas propiedades del objeto.
1. Guardar el objeto.
## **VSTO**
``` cs

 //Crear un nuevo objeto MapiContact

MapiContact mapiContact = new MapiContact();

//Establecer diferentes propiedades de este objeto Contacto

mapiContact.NameInfo = new MapiContactNamePropertySet("Mellissa", "", "MacBeth");

mapiContact.ProfessionalInfo.Title = "Representante de Cuenta";

mapiContact.ProfessionalInfo.CompanyName = "Contoso Ltd.";

mapiContact.ProfessionalInfo.OfficeLocation = "36/2529";

mapiContact.Telephones.BusinessTelephoneNumber = "4255551212 x432";

mapiContact.PhysicalAddresses.WorkAddress.Street = "1 Microsoft Way";

mapiContact.PhysicalAddresses.WorkAddress.City = "Redmond";

mapiContact.PhysicalAddresses.WorkAddress.StateOrProvince = "WA";

mapiContact.PhysicalAddresses.WorkAddress.PostalCode = "98052";

mapiContact.PhysicalAddresses.WorkAddress.Country = "Estados Unidos de América";

mapiContact.ElectronicAddresses.Email1.EmailAddress = "milissa@contoso.com";

mapiContact.ElectronicAddresses.Email1.AddressType = "SMTP";

mapiContact.ElectronicAddresses.Email1.DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Guardar el objeto Contacto en disco

mapiContact.Save("Contact.vcf", ContactSaveFormat.VCard);

```
## **Aspose.Email**
``` cs

 //Crear un nuevo objeto MapiContact

MapiContact mapiContact = new MapiContact();

//Establecer diferentes propiedades de este objeto Contacto

mapiContact.NameInfo = new MapiContactNamePropertySet("Mellissa", "", "MacBeth");

mapiContact.ProfessionalInfo.Title = "Representante de Cuenta";

mapiContact.ProfessionalInfo.CompanyName = "Contoso Ltd.";

mapiContact.ProfessionalInfo.OfficeLocation = "36/2529";

mapiContact.Telephones.BusinessTelephoneNumber = "4255551212 x432";

mapiContact.PhysicalAddresses.WorkAddress.Street = "1 Microsoft Way";

mapiContact.PhysicalAddresses.WorkAddress.City = "Redmond";

mapiContact.PhysicalAddresses.WorkAddress.StateOrProvince = "WA";

mapiContact.PhysicalAddresses.WorkAddress.PostalCode = "98052";

mapiContact.PhysicalAddresses.WorkAddress.Country = "Estados Unidos de América";

mapiContact.ElectronicAddresses.Email1.EmailAddress = "milissa@contoso.com";

mapiContact.ElectronicAddresses.Email1.AddressType = "SMTP";

mapiContact.ElectronicAddresses.Email1.DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Guardar el objeto Contacto en disco

mapiContact.Save("Contact.vcf", ContactSaveFormat.VCard);

```
## **Descargar código de ejemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772939)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Creating.an.Outlook.Contact.Aspose.Email.zip)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Creating%20an%20Outlook%20Contact%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Creating%20an%20Outlook%20Contact%20\(Aspose.Email\).zip)