---
title: "Criar, Salvar e Ler Contatos do Outlook"
url: /pt/java/create-save-and-read-outlook-contacts/
weight: 10
type: docs
---

## **Aspose.Email - Criar, Salvar e Ler Contatos do Outlook**
Os seguintes passos podem ser usados para criar e salvar um contato no disco:

1. Instanciar um novo objeto da classe MapiContact.
1. Inserir informações relacionadas a várias propriedades do contato.
1. Adicionar dados da foto ao contato, se houver.
1. Salvar o contato no formato MSG ou VCard.

**Java**

``` java

 MapiContact contact = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");

contact.setNameInfo(new MapiContactNamePropertySet("Bertha", "A.", "Buell"));

contact.setProfessionalInfo(new MapiContactProfessionalPropertySet("Awthentikz", "Assistente de trabalho social"));

contact.getPersonalInfo().setPersonalHomePage("B2BTies.com");

contact.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT");

contact.getElectronicAddresses().setEmail1(new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"));

contact.setTelephones(new MapiContactTelephonePropertySet("06605045265"));

// Definir Dados da Foto

File fi = new File(dataDir + "Aspose.jpg");

byte[] fileContent = Files.readAllBytes(fi.toPath());

MapiContactPhoto photo = new MapiContactPhoto(fileContent, MapiContactPhotoImageFormat.Jpeg);

contact.setPhoto(photo);

// Salvar como MSG

contact.save(dataDir + "contact.msg", ContactSaveFormat.Msg);

// Carregando MSG

MapiMessage msg = MapiMessage.fromFile(dataDir + "contact.msg");

MapiContact mapiContact = (MapiContact)msg.toMapiMessageItem();

```
## **Código em Execução para Download**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Código de Exemplo para Download**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/msgfiles/readwriteoutlookcontacts/AsposeReadWriteOutlookContact.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Criando, Salvando e Lendo Contatos do Outlook](/email/java/working-with-outlook-contacts/).

{{% /alert %}}