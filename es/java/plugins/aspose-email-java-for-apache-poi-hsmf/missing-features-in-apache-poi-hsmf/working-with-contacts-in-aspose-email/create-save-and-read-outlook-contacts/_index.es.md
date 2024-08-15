---
title: "Crear, guardar y leer contactos de Outlook"
url: /es/java/create-save-and-read-outlook-contacts/
weight: 10
type: docs
---

## **Aspose.Email - Crear, guardar y leer contactos de Outlook**
Se pueden seguir los pasos siguientes para crear y guardar un contacto en un disco:

1. Cree una instancia de un objeto nuevo de la clase MapiContact.
1. Introduzca la información relacionada con las distintas propiedades del contacto.
1. Agrega datos de fotos al contacto, si los hay.
1. Guarda el contacto en formato MSG o vCard.

**Java**

``` java

 MapiContact contact = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");

contact.setNameInfo(new MapiContactNamePropertySet("Bertha", "A.", "Buell"));

contact.setProfessionalInfo(new MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant"));

contact.getPersonalInfo().setPersonalHomePage("B2BTies.com");

contact.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT");

contact.getElectronicAddresses().setEmail1(new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"));

contact.setTelephones(new MapiContactTelephonePropertySet("06605045265"));

// Set Photo Data

File fi = new File(dataDir + "Aspose.jpg");

byte[] fileContent = Files.readAllBytes(fi.toPath());

MapiContactPhoto photo = new MapiContactPhoto(fileContent, MapiContactPhotoImageFormat.Jpeg);

contact.setPhoto(photo);

// Save as MSG

contact.save(dataDir + "contact.msg", ContactSaveFormat.Msg);

// Loading MSG

MapiMessage msg = MapiMessage.fromFile(dataDir + "contact.msg");

MapiContact mapiContact = (MapiContact)msg.toMapiMessageItem();

```
## **Descargar Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar código de muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)

{{% alert color="primary" %}}

Para obtener más información, visite [Crear, guardar y leer contactos de Outlook](/email/java/working-with-outlook-contacts/).

{{% /alert %}}
