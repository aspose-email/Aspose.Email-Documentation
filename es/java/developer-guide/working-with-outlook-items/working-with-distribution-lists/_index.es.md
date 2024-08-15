---
title: "Trabajando con listas de distribución"
url: /es/java/working-with-distribution-lists/
weight: 130
type: docs
---


Es posible crear una lista de distribución utilizando la API Aspose.Email que es una colección de varios contactos. Una lista de distribución se puede guardar en el disco en formato MSG de Outlook y se puede ver o manipular abriéndola en MS Outlook.

## **Creación y almacenamiento de listas de distribución**

El siguiente fragmento de código muestra cómo crear y guardar una lista de distribución.

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

## **Guarde la lista de distribución de Mapi en un único archivo VCF de múltiples contactos**

The [void save (opciones String FileName, MapiDistributionListSaveOptions)](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/#save-java.lang.String-com.aspose.email.MapiDistributionListSaveOptions-) El método le permite guardar la lista de distribución de Mapi en un nombre de archivo específico mediante las opciones de almacenamiento proporcionadas. Puede proporcionar el nombre del archivo y una instancia del [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) clase como parámetros.
El [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) La clase contiene opciones para guardar la lista de distribución de Mapi. En este caso, puede especificar el formato de guardado como vCard (ContactSaveFormat.vCard) para guardar la lista de distribución como un archivo VCF con varios contactos.

El siguiente fragmento de código muestra cómo guardar una lista de distribución en un archivo VCF con varios contactos:

```java
MapiDistributionList dlist = (MapiDistributionList)msg.toMapiMessageItem();
MapiDistributionListSaveOptions options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.save("distribution_list.vcf", options);
```

## **Lectura de una lista de distribución desde un PST**

El siguiente fragmento de código muestra cómo leer una lista de distribución desde un archivo PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
MapiDistributionList dlist = (MapiDistributionList)message.toMapiMessageItem();
~~~
