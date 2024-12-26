---
title: Create, Save and Read Outlook Contacts
ArticleTitle: Create, Save and Read Outlook Contacts
type: docs
weight: 10
url: /java/create-save-and-read-outlook-contacts/
---

## **Aspose.Email - Create, Save and Read Outlook Contacts**
The following steps can be used to create and save a contact to disc:

1. Instantiate a new object of the MapiContact class.
1. Enter information related to various properties of the contact.
1. Add photo data to the contact, if any.
1. Save the contact as MSG or VCard format.

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
## **Download Running Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download Sample Code**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)

{{% alert color="primary" %}} 

For more details, visit [Creating, Saving and Reading Outlook Contacts](/email/java/working-with-outlook-contacts/).

{{% /alert %}}
