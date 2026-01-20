---
title: Working with Distribution Lists
ArticleTitle: Working with Distribution Lists
type: docs
weight: 40
url: /python-net/working-with-distribution-lists/
---


It is possible to create a Distribution list using Aspose.Email API that is a collection of multiple contacts. A distribution list can be saved to disc in Outlook MSG format and can be viewed/manipulated by opening it in MS Outlook.

## **Create and Save Distribution Lists**

The following code snippet shows you how to create and save a distribution list.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}

## **Read Distribution Lists from PST Files**

The following code snippet shows you how to read a distribution list from a PST file.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file( "your_pst_file.pst")
folder = pst.root_folder.get_sub_folder("Contacts")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    dlist = msg.to_mapi_message_item()
    if isinstance(dlist, ae.mapi.MapiDistributionList):
        for member in dlist.members:
            print("Member Display Name:", member.display_name)
            print("Member Email Address:", member.email_address)
```

## **Update Distribution Lists in PST Files**

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