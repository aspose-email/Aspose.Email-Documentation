---
title: Managing Outlook Distribution Lists in PST Files
ArticleTitle: Managing Outlook Distribution Lists in PST Files
type: docs
weight: 90
url: /python-net/managing-distribution-lists-in-pst-files/
---

A distribution list is a group of contacts that can be manipulated by automated software enabling the user to send emails to multiple recipients simultaneously.

Aspose.Email for Python API allows users to create, manage, and manipulate distribution lists. This includes creating and saving members from the list, reading distribution lists, updating list properties, and other related operations.

## **Create and Save Distribution Lists in PST Files**

### **Add a Distribution List with Existing PST Contacts**

The code snippet below demonstrates how to create a distribution list containing contacts that are already stored in a PST file.

1. Create a new PST file using [PersonalStorage.create()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) with UNICODE format.
2. Create a predefined "Contacts" folder, and add two contact entries (Sebastian Wright and Wichert Kroos) to this folder.
3. Add contacts to the distribution list:
    - Each contact is added to the distribution list as a [MapiDistributionListMember](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapidistributionlistmember/).
    - Each member's *entry_id* is linked to the corresponding PST contact using the encoded *strEntryId*.
4. Create a distribution list named "Contact list" which includes the added contacts as members, and add it to the PST file.


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

## **Add a Distribution List with One-Off Members**

One-off members are suitable when the contacts are not part of the Outlook address book but still need to be included in the distribution list. The following code sample demonstrates how to create a distribution list with one-off members — contacts that are not stored in the PST file.

1. Create a new PST file using [PersonalStorage.create()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) with UNICODE format.
2. Instead of linking contacts from the PST, define new contact entries (John R. Patrick and Tilly Bates) directly as one-off members.
3. Add the one-off members to a distribution list.
4. Create a distribution list, named "Simple list", and add it to the "Contacts" folder in the PST file.

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

## **Read Distribution Lists from PST Files**

To read a distribution list from a PST, use the following code sample:

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

## **Update Distribution Lists in Outlook PST Files**

To update a distribution list in a PST file, for example to add a new member, use the following code sample:

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
