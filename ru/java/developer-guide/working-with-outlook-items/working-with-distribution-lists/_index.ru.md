---
title: "Работа с Распространительными Списками"
url: /ru/java/working-with-distribution-lists/
weight: 130
type: docs
---


Можно создать Распространительный список с использованием Aspose.Email API, который является коллекцией нескольких контактов. Распространительный список можно сохранить на диск в формате Outlook MSG и его можно просматривать/изменять, открыв в MS Outlook.

## **Создание и Сохранение Распространительных Списков**

Следующий фрагмент кода показывает, как создать и сохранить распространительный список.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

String displayName1 = "Sebastian Wright";
String email1 = "SebastianWright@dayrep.com";

String displayName2 = "Wichert Kroos";
String email2 = "WichertKroos@teleworm.us";

String strEntryId1;
String strEntryId2;

// Create distribution list from contacts
try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CreateDistributionListInPST_out.pst", FileFormatVersion.Unicode)) {
    // Add the contact folder to pst
    FolderInfo contactFolder = personalStorage.createPredefinedFolder("Contacts", StandardIpmFolder.Contacts);

    // Create contacts
    strEntryId1 = contactFolder.addMapiMessageItem(new MapiContact(displayName1, email1));
    strEntryId2 = contactFolder.addMapiMessageItem(new MapiContact(displayName2, email2));

    // Create distribution list on the base of the created contacts
    MapiDistributionListMember member1 = new MapiDistributionListMember(displayName1, email1);
    member1.setEntryIdType(MapiDistributionListEntryIdType.Contact);
    member1.setEntryId(Base64.getDecoder().decode(strEntryId1));

    MapiDistributionListMember member2 = new MapiDistributionListMember(displayName2, email2);
    member2.setEntryIdType(MapiDistributionListEntryIdType.Contact);
    member2.setEntryId(Base64.getDecoder().decode(strEntryId2));

    MapiDistributionListMemberCollection members = new MapiDistributionListMemberCollection();
    members.add(member1);
    members.add(member2);

    MapiDistributionList distributionList = new MapiDistributionList("Contact list", members);
    distributionList.setBody("Distribution List Body");
    distributionList.setSubject("Sample Distribution List using Aspose.Email");

    // Add distribution list to PST
    contactFolder.addMapiMessageItem(distributionList);
}

// Create one-off distribution list members (for which no separate contacts were created)
try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CreateDistributionListInPST_OneOffmembers_out.pst", FileFormatVersion.Unicode)) {
    // Add the contact folder to pst
    FolderInfo contactFolder = personalStorage.createPredefinedFolder("Contacts", StandardIpmFolder.Contacts);

    MapiDistributionListMemberCollection oneOffmembers = new MapiDistributionListMemberCollection();
    oneOffmembers.add(new MapiDistributionListMember("John R. Patrick", "JohnRPatrick@armyspy.com"));
    oneOffmembers.add(new MapiDistributionListMember("Tilly Bates", "TillyBates@armyspy.com"));

    MapiDistributionList oneOffMembersList = new MapiDistributionList("Simple list", oneOffmembers);
    contactFolder.addMapiMessageItem(oneOffMembersList);
}
~~~

## **Сохранение Mapi Распространительного Списка в Один Много контактный VCF Файл**

Метод [void save(String fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/#save-java.lang.String-com.aspose.email.MapiDistributionListSaveOptions-) позволяет сохранить Mapi Распространительный Список в указанное имя файла с использованием предоставленных параметров сохранения. Вы можете указать имя файла и экземпляр класса [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) в качестве параметров.
Класс [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) содержит параметры для сохранения Mapi Распространительного Списка. В этом случае вы можете указать формат сохранения как VCard (ContactSaveFormat.VCard), чтобы сохранить распространительный список в качестве много контактного VCF файла.

Следующий фрагмент кода демонстрирует, как сохранить распространительный список в много контактный VCF файл:

```java
MapiDistributionList dlist = (MapiDistributionList)msg.toMapiMessageItem();
MapiDistributionListSaveOptions options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.save("distribution_list.vcf", options);
```

## **Чтение Распространительного Списка из PST**

Следующий фрагмент кода показывает, как прочитать распространительный список из PST файла.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
MapiDistributionList dlist = (MapiDistributionList)message.toMapiMessageItem();
~~~