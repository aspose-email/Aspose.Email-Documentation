---
title: Working with Distribution Lists
ArticleTitle: Working with Distribution Lists
type: docs
weight: 130
url: /java/working-with-distribution-lists/
---


It is possible to create a Distribution list using Aspose.Email API that is a collection of multiple contacts. A distribution list can be saved to disk in Outlook MSG format and can be viewed/manipulated by opening it in MS Outlook.

## **Creating and Saving Distribution Lists**

The following code snippet shows you how to create and save a distribution list.

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

## **Save Mapi Distribution List to a Single Multi Contact VCF File**

The [void save(String fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/#save-java.lang.String-com.aspose.email.MapiDistributionListSaveOptions-) method allows you to save the Mapi Distribution List to a specified file name using the provided save options. You can provide the file name and an instance of the [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) class as parameters.
The [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) class contains options for saving the Mapi Distribution List. In this case, you can specify the save format as VCard (ContactSaveFormat.VCard) to save the distribution list as a multi-contact VCF file.

The following code snippet demonstrates how to save a distribution list to a multi-contact VCF file:

```java
MapiDistributionList dlist = (MapiDistributionList)msg.toMapiMessageItem();
MapiDistributionListSaveOptions options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.save("distribution_list.vcf", options);
```

## **Reading a Distribution List from a PST**

The following code snippet shows you how to read a distribution list from a PST file.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
MapiDistributionList dlist = (MapiDistributionList)message.toMapiMessageItem();
~~~
