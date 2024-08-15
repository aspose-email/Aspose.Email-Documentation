---
title: "Работа со списками рассылки"
url: /ru/java/working-with-distribution-lists/
weight: 130
type: docs
---


С помощью Aspose.Email API можно создать список рассылки, который представляет собой набор из нескольких контактов. Список рассылки можно сохранить на диск в формате Outlook MSG и просматривать и изменять его, открывая его в MS Outlook.

## **Создание и сохранение списков рассылки**

В следующем фрагменте кода показано, как создать и сохранить список рассылки.

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

## **Сохранить список рассылки Mapi в один многоконтактный файл VCF**

The [void save (строковое имя файла, параметры сохранения списка рассылки MAPI)](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/#save-java.lang.String-com.aspose.email.MapiDistributionListSaveOptions-) Метод позволяет сохранить список рассылки Mapi под указанным именем файла, используя предоставленные опции сохранения. Вы можете указать имя файла и экземпляр [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) класс в качестве параметров. [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) класс содержит опции для сохранения списка рассылки Mapi. В этом случае вы можете указать формат сохранения как vCard (ContactSaveFormat.vCard), чтобы сохранить список рассылки в виде многоконтактного файла VCF.

В следующем фрагменте кода показано, как сохранить список рассылки в многоконтактный файл VCF:

```java
MapiDistributionList dlist = (MapiDistributionList)msg.toMapiMessageItem();
MapiDistributionListSaveOptions options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.save("distribution_list.vcf", options);
```

## **Чтение списка рассылки из PST**

В следующем фрагменте кода показано, как читать список рассылки из файла PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
MapiDistributionList dlist = (MapiDistributionList)message.toMapiMessageItem();
~~~
