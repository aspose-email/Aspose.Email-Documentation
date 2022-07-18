---
title: Working with Contacts in PST File
type: docs
weight: 40
url: /net/working-with-contacts-in-pst-file/
---


## **Adding Contact to PST**
[Create a New PST File and Add Subfolders](/email/net/create-new-pst-file-and-add-subfolders/#creating-a-new-pst-file-and-add-subfolders) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add a MapiContact to the Contacts subfolder of a PST file that you have created or loaded. Below are the steps to add MapiContact to a PST:

1. Create a [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) object.
1. Set the [MapiContact properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/properties/index) using different constructors and methods.
1. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/methods/create/index) method.
1. Create a pre-defined folder (Contacts) at the root of the PST file by accessing the root folder and then calling the [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/methods/addmapimessageitem) method.

The following code snippet shows you how to create a MapiContact and then add it to the contacts folder of a newly created PST file.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-CreateNewMapiContactAndAddToContactsSubfolder-CreateNewMapiContactAndAddToContactsSubfolder.cs" >}}
## **Save contacts information from PST file in MSG Format**
This article explains how to access contact information from an Outlook PST file and save the contact to disk in MSG format. The [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage) and [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) classes to get and display the contact information. The steps to get the contact information are:

1. Load the PST file in the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage) class.
1. Browse the Contacts folder.
1. Get the contents of the Contacts folder to get the message collection.
1. Loop through the message collection.
1. Call the PersonalStorage.ExtractContactInfo() method to get the contact information in the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) class. Use the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) class properties to access the contact information
1. Call the [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/methods/extractmessage/index) method to get the contact information in the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) class.
1. Call the MapiMessage.Save() method to save the contact to disk in MSG format.

The following code snippet shows you how to retrieve all the contact information from the PST file and save to disk in MSG format.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-AccessContactInformation-AccessContactInformation.cs" >}}
## **Save Contacts information from PST file in VCF Format**
This article shows how to access contact information from a Microsoft Outlook PST file and save the contact to disk in vCard (VCF) format. Use the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage) and [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) classes to get contact information from the PST file. To get the contact information:

1. Load the PST file in the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage) class.
1. Browse the Contacts folder.
1. Get the contents of the Contacts folder to get the message collection.
1. Loop through the message collection.
1. Call the PersonalStorage.ExtractMessage() method to get the contact information in the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) class.
1. Use the [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact) class different properties to access the contact information.

The program below loads a PST file from disk and saves all the contacts to vCard (VCF) format. The VCF files can then be used in any other program that can load the standard vCard contact file. If you open any VCF file in Microsoft Outlook, it looks like the one in the below screenshot.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
The following code snippet shows you how to export contacts from Outlook PST to vCard (VCF) format.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SaveContactInformation-SaveContactInformation.cs" >}}

See also: [Working with Distribution Lists](/email//net/working-with-distribution-lists-in-pst/)
