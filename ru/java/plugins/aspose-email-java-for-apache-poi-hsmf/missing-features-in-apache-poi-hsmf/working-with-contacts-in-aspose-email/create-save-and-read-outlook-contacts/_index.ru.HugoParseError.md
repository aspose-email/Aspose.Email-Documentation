---
title: Создание, сохранение и чтение контактов Outlook
type: docs
weight: 10
url: /java/create-save-and-read-outlook-contacts/
---

## **Aspose.Email - Создание, сохранение и чтение контактов Outlook**
Для создания и сохранения контакта на диск можно использовать следующие шаги:

1. Создайте новый объект класса MapiContact.
1. Введите информацию, связанную с различными свойствами контакта.
1. Добавьте данные фотографии к контакту, если таковые имеются.
1. Сохраните контакт в формате MSG или VCard.

**Java**

``` java

 MapiContact contact = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");

contact.setNameInfo(new MapiContactNamePropertySet("Bertha", "A.", "Buell"));

contact.setProfessionalInfo(new MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant"));

contact.getPersonalInfo().setPersonalHomePage("B2BTies.com");

contact.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT");

contact.getElectronicAddresses().setEmail1(new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"));

contact.setTelephones(new MapiContactTelephonePropertySet("06605045265"));

// Установить данные фотографии

File fi = new File(dataDir + "Aspose.jpg");

byte[] fileContent = Files.readAllBytes(fi.toPath());

MapiContactPhoto photo = new MapiContactPhoto(fileContent, MapiContactPhotoImageFormat.Jpeg);

contact.setPhoto(photo);

// Сохранить как MSG

contact.save(dataDir + "contact.msg", ContactSaveFormat.Msg);

// Загрузка MSG

MapiMessage msg = MapiMessage.fromFile(dataDir + "contact.msg");

MapiContact mapiContact = (MapiContact)msg.toMapiMessageItem();

```
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)

{{% alert color="primary" %}} 

Для получения дополнительных сведений посетите страницу [Создание, сохранение и чтение контактов Outlook](/email/java/working-with-outlook-contacts/).

{{% /alert %}}