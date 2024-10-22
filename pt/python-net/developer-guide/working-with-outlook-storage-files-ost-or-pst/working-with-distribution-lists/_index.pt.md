---
title: "Trabalhando com Listas de Distribuição em Arquivo PST"
url: /pt/python-net/trabalhando-com-listas-de-distribuicao/
weight: 90
type: docs
---

Uma lista de distribuição é um grupo de contatos que pode ser manipulada por software automatizado, permitindo ao usuário enviar e-mails para múltiplos destinatários simultaneamente.

O software Aspose.Email permite aos usuários criar, gerenciar e manipular listas de distribuição. Isso inclui criar e salvar membros da lista, ler listas de distribuição, atualizar propriedades da lista e outras operações relacionadas.

## **Criando e Salvando Listas de Distribuição**

Crie e salve uma lista de distribuição, conforme mostrado no exemplo de código abaixo:

```py
import aspose.email as ae

displayName1 = "Sebastian Wright"
email1 = "SebastianWright@dayrep.com"

displayName2 = "Wichert Kroos"
email2 = "WichertKroos@teleworm.us"

pst = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)

contactFolder = pst.create_predefined_folder("Contacts", ae.storage.pst.StandardIpmFolder.CONTACTS)

strEntryId1 = contactFolder.add_mapi_message_item(ae.mapi.MapiContact(displayName1, email1))
strEntryId2 = contactFolder.add_mapi_message_item(ae.mapi.MapiContact(displayName2, email2))

member1 = ae.mapi.MapiDistributionListMember(displayName1, email1)
member1.entry_id_type = ae.mapi.MapiDistributionListEntryIdType.CONTACT
member1.entry_id = strEntryId1.encode()

member2 = ae.mapi.MapiDistributionListMember(displayName2, email2)
member2.entry_id_type = ae.mapi.MapiDistributionListEntryIdType.CONTACT
member2.entry_id = strEntryId2.encode()

members = ae.mapi.MapiDistributionListMemberCollection()
members.append(member1)
members.append(member2)

distributionList = ae.mapi.MapiDistributionList("Lista de Contatos", members)
distributionList.body = "Corpo da Lista de Distribuição"
distributionList.subject = "Lista de Distribuição de Exemplo usando Aspose.Email"
# Adicionar lista de distribuição ao PST
contactFolder.add_mapi_message_item(distributionList)
```

```py
import aspose.email as ae

displayName1 = "Sebastian Wright"
email1 = "SebastianWright@dayrep.com"

displayName2 = "Wichert Kroos"
email2 = "WichertKroos@teleworm.us"

pst = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)

contact_folder = pst.create_predefined_folder("Contacts", ae.storage.pst.StandardIpmFolder.CONTACTS)

one_off_members = ae.mapi.MapiDistributionListMemberCollection()
one_off_members.append(ae.mapi.MapiDistributionListMember("John R. Patrick", "JohnRPatrick@armyspy.com"))
one_off_members.append(ae.mapi.MapiDistributionListMember("Tilly Bates", "TillyBates@armyspy.com"))

one_off_members_list = ae.mapi.MapiDistributionList("Lista Simples", one_off_members)
contact_folder.add_mapi_message_item(one_off_members_list)
```

## **Lendo Listas de Distribuição do PST**

Para ler uma lista de distribuição de um PST, use o seguinte exemplo de código:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

for msg in folder.enumerate_messages():
    # Verifique se a mensagem tem a classe de mensagem "IPM.DistList"
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Agora, você pode trabalhar com a lista de distribuição
        # (por exemplo, acessar seus membros, exibir suas propriedades ou fazer modificações)
        for member in dist_list.members:
            print(f"{member.display_name}")
```

## **Atualizando Listas de Distribuição no PST**

Para atualizar uma lista de distribuição em um arquivo PST, por exemplo, para adicionar um novo membro, use o seguinte exemplo de código:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

# adicionar um novo membro a cada lista de distribuição no pst
for msg in folder.enumerate_messages():
    # Verifique se a mensagem tem a classe de mensagem "IPM.DistList"
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Criar novo membro para adicionar
        member = ae.mapi.MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com")
        dist_list.members.append(member)
        # atualizar DL no PST
        folder.update_message(msg.entry_id_string, dist_list)
```