---
title: "Работа с Распределительными Списками в PST Файле"
url: /ru/python-net/working-with-distribution-lists/
weight: 90
type: docs
---

Распределительный список - это группа контактов, с которыми можно взаимодействовать с помощью автоматизированного программного обеспечения, позволяющего пользователю отправлять электронные письма нескольким получателям одновременно.

Программное обеспечение Aspose.Email позволяет пользователям создавать, управлять и изменять распределительные списки. Это включает в себя создание и сохранение участников из списка, чтение распределительных списков, обновление свойств списка и другие связанные операции.

## **Создание и Сохранение Распределительных Списков**

Создайте и сохраните распределительный список, как показано в примере кода ниже:

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

distributionList = ae.mapi.MapiDistributionList("Contact list", members)
distributionList.body = "Текст Распределительного Списка"
distributionList.subject = "Пример Распределительного Списка с использованием Aspose.Email"
# Добавить распределительный список в PST
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

one_off_members_list = ae.mapi.MapiDistributionList("Simple list", one_off_members)
contact_folder.add_mapi_message_item(one_off_members_list)
```

## **Чтение Распределительных Списков из PST**

Чтобы прочитать распределительный список из PST, используйте следующий пример кода:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

for msg in folder.enumerate_messages():
    # Проверьте, имеет ли сообщение класс "IPM.DistList"
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Теперь вы можете работать с распределительным списком
        # (например, получать доступ к его участникам, отображать его свойства или вносить изменения)
        for member in dist_list.members:
            print(f"{member.display_name}")
```

## **Обновление Распределительных Списков в PST**

Чтобы обновить распределительный список в файле PST, например, чтобы добавить нового участника, используйте следующий пример кода:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

# добавьте нового участника в каждый распределительный список в pst
for msg in folder.enumerate_messages():
    # Проверьте, имеет ли сообщение класс "IPM.DistList"
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Создайте нового участника для добавления
        member = ae.mapi.MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com")
        dist_list.members.append(member)
        # обновите DL в PST
        folder.update_message(msg.entry_id_string, dist_list)
```