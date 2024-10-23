---
title: "Trabalhando com Listas de Distribuição"
url: /pt/java/trabalhando-com-listas-de-distribuicao/
weight: 130
type: docs
---


É possível criar uma lista de distribuição usando a API Aspose.Email, que é uma coleção de múltiplos contatos. Uma lista de distribuição pode ser salva no disco no formato MSG do Outlook e pode ser visualizada/manipulada ao abri-la no MS Outlook.

## **Criando e Salvando Listas de Distribuição**

O seguinte trecho de código mostra como criar e salvar uma lista de distribuição.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

String displayName1 = "Sebastian Wright";
String email1 = "SebastianWright@dayrep.com";

String displayName2 = "Wichert Kroos";
String email2 = "WichertKroos@teleworm.us";

String strEntryId1;
String strEntryId2;

// Criar lista de distribuição a partir dos contatos
try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CreateDistributionListInPST_out.pst", FileFormatVersion.Unicode)) {
    // Adicionar a pasta de contatos ao pst
    FolderInfo contactFolder = personalStorage.createPredefinedFolder("Contacts", StandardIpmFolder.Contacts);

    // Criar contatos
    strEntryId1 = contactFolder.addMapiMessageItem(new MapiContact(displayName1, email1));
    strEntryId2 = contactFolder.addMapiMessageItem(new MapiContact(displayName2, email2));

    // Criar lista de distribuição com base nos contatos criados
    MapiDistributionListMember member1 = new MapiDistributionListMember(displayName1, email1);
    member1.setEntryIdType(MapiDistributionListEntryIdType.Contact);
    member1.setEntryId(Base64.getDecoder().decode(strEntryId1));

    MapiDistributionListMember member2 = new MapiDistributionListMember(displayName2, email2);
    member2.setEntryIdType(MapiDistributionListEntryIdType.Contact);
    member2.setEntryId(Base64.getDecoder().decode(strEntryId2));

    MapiDistributionListMemberCollection members = new MapiDistributionListMemberCollection();
    members.add(member1);
    members.add(member2);

    MapiDistributionList distributionList = new MapiDistributionList("Lista de Contatos", members);
    distributionList.setBody("Corpo da Lista de Distribuição");
    distributionList.setSubject("Exemplo de Lista de Distribuição usando Aspose.Email");

    // Adicionar lista de distribuição ao PST
    contactFolder.addMapiMessageItem(distributionList);
}

// Criar membros de lista de distribuição única (para os quais nenhum contato separado foi criado)
try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CreateDistributionListInPST_OneOffmembers_out.pst", FileFormatVersion.Unicode)) {
    // Adicionar a pasta de contatos ao pst
    FolderInfo contactFolder = personalStorage.createPredefinedFolder("Contacts", StandardIpmFolder.Contacts);

    MapiDistributionListMemberCollection oneOffmembers = new MapiDistributionListMemberCollection();
    oneOffmembers.add(new MapiDistributionListMember("John R. Patrick", "JohnRPatrick@armyspy.com"));
    oneOffmembers.add(new MapiDistributionListMember("Tilly Bates", "TillyBates@armyspy.com"));

    MapiDistributionList oneOffMembersList = new MapiDistributionList("Lista Simples", oneOffmembers);
    contactFolder.addMapiMessageItem(oneOffMembersList);
}
~~~

## **Salvar Lista de Distribuição Mapi em um Único Arquivo VCF Multi Contato**

O [void save(String fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/#save-java.lang.String-com.aspose.email.MapiDistributionListSaveOptions-) permite salvar a Lista de Distribuição Mapi com um nome de arquivo específico usando as opções de salvamento fornecidas. Você pode fornecer o nome do arquivo e uma instância da classe [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) como parâmetros.
A classe [MapiDistributionListSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistsaveoptions/) contém opções para salvar a Lista de Distribuição Mapi. Neste caso, você pode especificar o formato de salvamento como VCard (ContactSaveFormat.VCard) para salvar a lista de distribuição como um arquivo VCF de múltiplos contatos.

O seguinte trecho de código demonstra como salvar uma lista de distribuição em um arquivo VCF de múltiplos contatos:

```java
MapiDistributionList dlist = (MapiDistributionList)msg.toMapiMessageItem();
MapiDistributionListSaveOptions options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.save("distribution_list.vcf", options);
```

## **Lendo uma Lista de Distribuição de um PST**

O seguinte trecho de código mostra como ler uma lista de distribuição de um arquivo PST.

~~~Java
// Para exemplos completos e arquivos de dados, por favor, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);
MapiDistributionList dlist = (MapiDistributionList)message.toMapiMessageItem();
~~~