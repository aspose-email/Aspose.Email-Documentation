---
title: Managing Outlook Contacts in PST Files
ArticleTitle: Managing Outlook Contacts in PST Files
type: docs
weight: 60
url: /python-net/managing-outlook-contacts-in-pst-files/
---


## **Add Outlook Contacts to PST Files**

[Create New PST File and Add Subfolders](https://docs.aspose.com/email/python-net/create-new-pst-file-and-add-subfolders/) demonstrates how to create a PST file and include subfolders within it. With Aspose.Email you can add a MapiContact to the Contacts subfolder of a PST file that you have created or loaded. Below are the steps to add a MapiContact to a PST file:

1. Create a [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/) object.
1. Set the MapiContact properties such as name, gender, email addresses, telephone numbers, physical addresses, and professional information using different constructors and methods.
1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method.
1. Create a pre-defined folder (Contacts) at the root of the PST file by accessing the root folder and then calling the [add_mapi_message_item()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method.

The following code snippet shows you how to create a MAPI contact and then add it to the Contacts folder of a newly created PST file:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiContactsAndAddToContactsSubFolder-CreateNewMapiContactsAndAddToContactsSubFolder.py" >}}

## **Save Outlook Contacts as MSG Files**

To access contact information from an Outlook PST file and save the contact to disk in MSG format, Aspose.Email provides the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) and the [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/) classes. The code snippet below shows you how to retrieve all the contact information from a PST file and save it to disk in MSG format:

1. Load the PST file in the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.
1. Browse the Contacts folder.
1. Get the contents of the Contacts folder to get the message collection.
1. Loop through the message collection.
1. Call the [PersonalStorage.extract_message()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method to get the contact information in the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/) class.
1. Call the [MapiMessage.save()](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods) method to save the contact to disk in MSG format.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AccessContactInformation-AccessContactInformation.py" >}}

## **Export Outlook Contacts as VCF Files**

To access contact information from a Microsoft Outlook PST file and save the contact to disk in vCard (VCF) format, use the [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) and [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/) classes. The code below loads a PST file from disk and saves all the contacts to vCard (VCF) format. The VCF files can then be used in any other program that can load the standard vCard contact file. If you open any VCF file in Microsoft Outlook, it looks like the one in the below screenshot.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |

The following code snippet shows you how to export contacts from Outlook PST to vCard (VCF) format:

1. Use [PersonalStorage.from_file](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) to open the PST file. 
1. Access the Contacts folder using the [get_sub_folder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods).
1. Loop Through Contacts:
   - Use [get_contents()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) to get all message info in the folder.
   - Iterate through [message_info_collection](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messageinfocollection/) with a loop.
1. Extract each contact using [pst.extract_message(message_info)](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) and store it as a MAPI message item.
1. Print the name and entry ID of every contact.
1. Save the contact as a VCF file using [contact.save](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/#methods).

```py
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import ContactSaveFormat

# Load the Outlook PST file
pst = PersonalStorage.from_file("my.pst")

# Get the Contacts folder
folder_info = pst.root_folder.get_sub_folder("Contacts")

# Loop through all the contacts in this folder
message_info_collection = folder_info.get_contents()
for message_info in message_info_collection:
    # Get the contact information
    contact = pst.extract_message(message_info).to_mapi_message_item()

    # Display some contents on screen
    print("Name: " + contact.name_info.display_name + " - " + message_info.entry_id_string)

    # Save to disk in vCard VCF format
    contact.save("D:\\" + contact.name_info.display_name + ".vcf", ContactSaveFormat.V_CARD)
```

## **Managing Outlook Distribution Lists in PST Files**

Aspose.Email for Python API makes it possible to create a distribution list - a collection of multiple contacts. A distribution list can be saved to disc in Outlook MSG format and can be viewed/manipulated by opening it in MS Outlook.

### **Create and Save Distribution Lists**

The code snippet below demonstrates how to create a PST file and add a distribution list. It also involves creating and adding contacts to the distribution list within the PST file.

1. Define contact details - set displayName and email for each contact.
2. Create a new PST file using [PersonalStorage.create()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) with UNICODE format.
3. Create Contacts folder using [create_predefined_folder()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods).
4. Instantiate [MapiContact](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicontact/#mapicontact-class) objects with the display name and email, then add contacts to the folder using [add_mapi_message_item()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods).
5. Create distribution list members by instantiating [MapiDistributionListMember](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapidistributionlistmember/) for each contact and setting entry_id with base64 decoding.
6. Add members to [MapiDistributionListMemberCollection](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapidistributionlistmembercollection/).
7. Create a distribution list by instantiating [MapiDistributionList](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapidistributionlist/), setting its body and subject.
8. Use [add_mapi_message_item()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) to add the distribution list to the contact folder.

```py
displayName1 = "Sebastian Wright"
email1 = "SebastianWright@dayrep.com"

displayName2 = "Wichert Kroos"
email2 = "WichertKroos@teleworm.us"

personalStorage = PersonalStorage.create(dataDir + "CreateDistributionListInPST_out.pst", FileFormatVersion.UNICODE)

contactFolder = personalStorage.create_predefined_folder("Contacts", StandardIpmFolder.CONTACTS)

   # Create contacts
   strEntryId1 = contactFolder.add_mapi_message_item(MapiContact(displayName1, email1))
   strEntryId2 = contactFolder.add_mapi_message_item( MapiContact(displayName2, email2))

   member1 = MapiDistributionListMember(displayName1, email1)
   member1.entry_id_type = MapiDistributionListEntryIdType.CONTACT
   member1.entry_id = base64.b64decode( bytes(strEntryId1, "utf-8") )

   member2 = MapiDistributionListMember(displayName2, email2)
   member2.entry_id_type = MapiDistributionListEntryIdType.CONTACT
   member2.entry_id = base64.b64decode( bytes(strEntryId1, "utf-8") )

   members = MapiDistributionListMemberCollection()
   members.append(member1)
   members.append(member2)

   distribution_list = MapiDistributionList("Contact list", members)
   distribution_list.body = "Distribution List Body"
   distribution_list.subject = "Sample Distribution List using Aspose.Email"     
                    
   # Add distribution list to PST 
   contactFolder.add_mapi_message_item(distribution_list);
```

### **Read Distribution Lists from PST Files**

The following code snippet shows you how to read a distribution list from a PST file:

```py
from aspose.email.mapi import MapiMessage

# Load the MAPI message from file
message = MapiMessage.load("dl.msg")

# Convert the message to MAPI distribution list
dlist = message.to_mapi_message_item()
```

### **Update Distribution Lists in Outlook PST Files**

To update a distribution list in a PST file, for example to add a new member, use the following code sample:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.CONTACTS)

# Add a new member to each distribution list in pst
for msg in folder.enumerate_messages():
    # Check if the message has the "IPM.DistList" message class
    if msg.message_class == "IPM.DistList":
        dist_list = pst.extract_message(msg).to_mapi_message_item()
        # Create a new member to add
        member = ae.mapi.MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com")
        dist_list.members.append(member)
        # Update DL in PST
        folder.update_message(msg.entry_id_string, dist_list)
```