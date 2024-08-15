---
title: "Trabajando con listas de distribución en un archivo PST"
url: /es/python-net/working-with-distribution-lists/
weight: 90
type: docs
---

Una lista de distribución es un grupo de contactos que puede manipularse mediante un software automatizado que permite al usuario enviar correos electrónicos a varios destinatarios simultáneamente.

El software Aspose.Email permite a los usuarios crear, administrar y manipular listas de distribución. Esto incluye crear y guardar miembros de la lista, leer las listas de distribución, actualizar las propiedades de las listas y otras operaciones relacionadas.

## **Creación y almacenamiento de listas de distribución**

Crea y guarda una lista de distribución como se muestra en el ejemplo de código siguiente:

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
distributionList.body = "Distribution List Body"
distributionList.subject = "Sample Distribution List using Aspose.Email"
# Add distribution list to PST
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

## **Lectura de listas de distribución de PST**

Para leer una lista de distribución de un PST, utilice el siguiente ejemplo de código:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

for msg in folder.enumerate_messages():
    # Check if the message has the "IPM.DistList" message class
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Now, you can work with the distribution list
        # (e.g., access its members, display its properties, or make modifications)
        for member in dist_list.members:
            print(f"{member.display_name}")
```

## **Actualización de listas de distribución en PST**

Para actualizar una lista de distribución en un archivo PST, por ejemplo, para agregar un nuevo miembro, usa el siguiente ejemplo de código:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

# add a new member to each distribution list in pst
for msg in folder.enumerate_messages():
    # Check if the message has the "IPM.DistList" message class
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Create new member to add
        member = ae.mapi.MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com")
        dist_list.members.append(member)
        # update DL in PST
        folder.update_message(msg.entry_id_string, dist_list)
```