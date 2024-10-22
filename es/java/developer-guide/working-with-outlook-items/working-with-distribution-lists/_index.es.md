---
title: "Trabajando con Listas de Distribución"
url: /es/java/trabajando-con-listas-de-distribucion/
weight: 130
type: docs
---


Es posible crear una lista de distribución utilizando la API de Aspose.Email, que es una colección de múltiples contactos. Una lista de distribución se puede guardar en disco en formato MSG de Outlook y se puede ver/manipular abriéndola en MS Outlook.

## **Creando y Guardando Listas de Distribución**

El siguiente fragmento de código muestra cómo crear y guardar una lista de distribución.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
String dataDir = "outlook/";

String displayName1 = "Sebastian Wright";
String email1 = "SebastianWright@dayrep.com";

String displayName2 = "Wichert Kroos";
String email2 = "WichertKroos@teleworm.us";

String strEntryId1;
String strEntryId2;

// Crear lista de distribución a partir de contactos
try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CreateDistributionListInPST_out.pst", FileFormatVersion.Unicode)) {
    // Agregar la carpeta de contactos al pst
    FolderInfo contactFolder = personalStorage.createPredefinedFolder("Contacts", StandardIpmFolder.Contacts);

    // Crear contactos
    strEntryId1 = contactFolder.addMapiMessageItem(new MapiContact(displayName1, email1));
    strEntryId2 = contactFolder.addMapiMessageItem(new MapiContact(displayName2, email2));

    // Crear lista de distribución en base a los contactos creados
    MapiDistributionListMember member1 = new MapiDistributionListMember(displayName1, email1);
    member1.setEntryIdType(MapiDistributionListEntryIdType.Contact);
    member1.setEntryId(Base64.getDecoder().decode(strEntryId1));

    MapiDistributionListMember member2 = new MapiDistributionListMember(displayName2, email2);
    member2.setEntryIdType(MapiDistributionListEntryIdType.Contact);
    member2.setEntryId(Base64.getDecoder().decode(strEntryId2));

    MapiDistributionListMemberCollection members = new MapiDistributionListMemberCollection();
    members.add(member1);
    members.add(member2);

    MapiDistributionList distributionList = new MapiDistributionList("Lista de contactos", members);
    distributionList.setBody("Cuerpo de la lista de distribución");
    distributionList.setSubject("Lista de distribución de muestra usando Aspose.Email");

    // Agregar lista de distribución al PST
    contactFolder.addMapiMessageItem(distributionList);
}

// Crear miembros de lista de distribución temporales (para los cuales no se crearon contactos separados)
try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CreateDistributionListInPST_OneOffmembers_out.pst", FileFormatVersion.Unicode)) {
    // Agregar la carpeta de contactos al pst
    FolderInfo contactFolder = personalStorage.createPredefinedFolder("Contacts", StandardIpmFolder.Contacts);

    MapiDistributionListMemberCollection oneOffmembers = new MapiDistributionListMemberCollection();
    oneOffmembers.add(new MapiDistributionListMember("John R. Patrick", "JohnRPatrick@armyspy.com"));
    oneOffmembers.add(new MapiDistributionListMember("Tilly Bates", "TillyBates@armyspy.com"));

    MapiDistributionList oneOffMembersList = new MapiDistributionList("Lista simple", oneOffmembers);
    contactFolder.addMapiMessageItem(oneOffMembersList);
}
~~~

## **Guardar Lista de Distribución Mapi en un Solo Archivo VCF de Múltiples Contactos**

El [void save(String fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/#save-java.lang.String-com.aspose.email.MapiDistributionListSaveOptions-) método te permite guardar la Lista de Distribución Mapi en un nombre de archivo especificado utilizando las opciones de guardado proporcionadas. Puedes proporcionar el nombre del archivo y una instancia de la clase [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) como parámetros.
La clase [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) contiene opciones para guardar la Lista de Distribución Mapi. En este caso, puedes especificar el formato de guardado como VCard (ContactSaveFormat.VCard) para guardar la lista de distribución como un archivo VCF de múltiples contactos.

El siguiente fragmento de código demuestra cómo guardar una lista de distribución en un archivo VCF de múltiples contactos:

```java
MapiDistributionList dlist = (MapiDistributionList)msg.toMapiMessageItem();
MapiDistributionListSaveOptions options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.save("distribution_list.vcf", options);
```

## **Leer una Lista de Distribución desde un PST**

El siguiente fragmento de código muestra cómo leer una lista de distribución desde un archivo PST.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de Archivos.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
MapiDistributionList dlist = (MapiDistributionList)message.toMapiMessageItem();
~~~