---
title: Working with Contacts in PST File
type: docs
weight: 40
url: /java/working-with-contacts-in-pst-file/
---

## **Adding Contact to PST**
[Create New PST, Add Sub-folders and Messages](java/create-new-pst-add-sub-folders-and-messages/) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add a [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) to the Contacts subfolder of a PST file that you have created or loaded. Below are the steps to add [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) to a PST:

1. Create a [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) object.
1. Set the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) properties using different constructors and methods.
1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#create\(java.lang.String,%20int\)) method.
1. Create a pre-defined folder (Contacts) at the root of the PST file by accessing the root folder and then calling the [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMapiMessageItem\(com.aspose.email.IMapiMessageItem\)) method.

The code snippet below shows how to create a [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) and then add it to the Contacts folder of a newly created PST file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiContactToPST-.java" >}}
## **Save contacts information from PST file in MSG Format**
This article shows how to access contact information from a Microsoft Outlook PST file and save contacts to disk in MSG format. To do so, use the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) and [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) classes to get and display the contact information.

To get a contact's information:

1. Load the PST file in the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) class.
1. Browse the Contacts folder.
1. Get the contents of the Contacts folder to get the message collection.
1. Loop through the message collection.
1. Call [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractMessage\(com.aspose.email.MessageInfo\)) and then [toMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#toMapiMessageItem\(\)) method to get the contact information in the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class.
1. Use [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) properties to access the contact information
1. Call the [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractMessage\(com.aspose.email.MessageInfo\)) method to get the contact information in the [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) class.
1. Call the [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage#save\(java.lang.String\)) method to save the contact to disk in MSG format.

Below is a sample code that retrieves all the contacts information from the PST file and saves it to disk in MSG format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AccessContactInformationFromPSTFile-.java" >}}
## **Save Contacts Information from Outlook PST to Disk in vCard format**
This article shows how to access contact information from a Microsoft Outlook PST file and save the contact to disk in vCard (VCF) format. It uses the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) and [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) classes to get the contact information.

Below are the steps to get the contacts information:

1. Load the PST file in [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage) class.
1. Browse the Contacts folder.
1. Get the contents of the Contacts folder to get the message collection.
1. Loop through the message collection.
1. Call the [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#extractMessage\(com.aspose.email.MessageInfo\)) method to get the contact information in the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class.
1. Use the properties of the [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/MapiContact) class to access the contact information.

The program below loads a PST file from disk and saves all the contacts in vCard (VCF) format. The VCF files can then be used in any other program that can load the standard vCard contact file. If you open any VCF file in Microsoft Outlook, it will look like the one in the below screenshot.

|![todo:image_alt_text](https://i.imgur.com/EFt3p1Z.png)|
| :- |
|**Figure: A vCard saved with Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveContactsInformationFromOutlookPSTToDiskInvCardFormat-.java" >}}
