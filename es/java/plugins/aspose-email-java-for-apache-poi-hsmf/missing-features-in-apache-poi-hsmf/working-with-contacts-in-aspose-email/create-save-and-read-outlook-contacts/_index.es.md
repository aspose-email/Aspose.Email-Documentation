---
title: "Crear, Guardar y Leer Contactos de Outlook"
url: /es/java/create-save-and-read-outlook-contacts/
weight: 10
type: docs
---

## **Aspose.Email - Crear, Guardar y Leer Contactos de Outlook**
Los siguientes pasos se pueden utilizar para crear y guardar un contacto en disco:

1. Instanciar un nuevo objeto de la clase MapiContact.
1. Ingresar información relacionada con varias propiedades del contacto.
1. Agregar datos de foto al contacto, si los hay.
1. Guardar el contacto en formato MSG o VCard.

**Java**

``` java

 MapiContact contact = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");

contact.setNameInfo(new MapiContactNamePropertySet("Bertha", "A.", "Buell"));

contact.setProfessionalInfo(new MapiContactProfessionalPropertySet("Awthentikz", "Asistente de trabajo social"));

contact.getPersonalInfo().setPersonalHomePage("B2BTies.com");

contact.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT");

contact.getElectronicAddresses().setEmail1(new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"));

contact.setTelephones(new MapiContactTelephonePropertySet("06605045265"));

// Establecer datos de la foto

File fi = new File(dataDir + "Aspose.jpg");

byte[] fileContent = Files.readAllBytes(fi.toPath());

MapiContactPhoto photo = new MapiContactPhoto(fileContent, MapiContactPhotoImageFormat.Jpeg);

contact.setPhoto(photo);

// Guardar como MSG

contact.save(dataDir + "contact.msg", ContactSaveFormat.Msg);

// Cargando MSG

MapiMessage msg = MapiMessage.fromFile(dataDir + "contact.msg");

MapiContact mapiContact = (MapiContact)msg.toMapiMessageItem();

```
## **Descargar Código en Ejecución**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Descargar Código de Muestra**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)

{{% alert color="primary" %}} 

Para más detalles, visita [Creación, Guardado y Lectura de Contactos de Outlook](/email/java/working-with-outlook-contacts/).

{{% /alert %}}