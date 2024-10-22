---
title: "Trabajar con Listas de Distribución en Archivos PST"
url: /es/python-net/working-with-distribution-lists/
weight: 90
type: docs
---

Una lista de distribución es un grupo de contactos que puede ser manipulado por software automatizado, permitiendo al usuario enviar correos electrónicos a múltiples destinatarios simultáneamente.

El software Aspose.Email permite a los usuarios crear, gestionar y manipular listas de distribución. Esto incluye crear y guardar miembros de la lista, leer listas de distribución, actualizar propiedades de la lista y otras operaciones relacionadas.

## **Creando y Guardando Listas de Distribución**

Crea y guarda una lista de distribución como se muestra en el ejemplo de código a continuación:

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

distributionList = ae.mapi.MapiDistributionList("Lista de contactos", members)
distributionList.body = "Cuerpo de la lista de distribución"
distributionList.subject = "Lista de distribución de muestra utilizando Aspose.Email"
# Agregar lista de distribución a PST
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

one_off_members_list = ae.mapi.MapiDistributionList("Lista simple", one_off_members)
contact_folder.add_mapi_message_item(one_off_members_list)
```

## **Leyendo Listas de Distribución desde PST**

Para leer una lista de distribución de un PST, utiliza el siguiente ejemplo de código:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

for msg in folder.enumerate_messages():
    # Verificar si el mensaje tiene la clase de mensaje "IPM.DistList"
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Ahora, puedes trabajar con la lista de distribución
        # (por ejemplo, acceder a sus miembros, mostrar sus propiedades o hacer modificaciones)
        for member in dist_list.members:
            print(f"{member.display_name}")
```

## **Actualizando Listas de Distribución en PST**

Para actualizar una lista de distribución en un archivo PST, por ejemplo, para agregar un nuevo miembro, utiliza el siguiente ejemplo de código:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

# agregar un nuevo miembro a cada lista de distribución en pst
for msg in folder.enumerate_messages():
    # Verificar si el mensaje tiene la clase de mensaje "IPM.DistList"
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Crear nuevo miembro para agregar
        member = ae.mapi.MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com")
        dist_list.members.append(member)
        # actualizar DL en PST
        folder.update_message(msg.entry_id_string, dist_list)
```