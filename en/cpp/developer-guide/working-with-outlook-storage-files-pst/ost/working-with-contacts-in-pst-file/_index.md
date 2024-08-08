---
title: Working with Contacts in PST File
type: docs
weight: 60
url: /cpp/working-with-contacts-in-pst-file/
---

## **Adding Contact to PST**
With Aspose.Email you can add a MapiContact to the Contacts subfolder of a PST file that you have created or loaded. Below are the steps to add MapiContact to a PST:

1. Create a MapiContact object.
1. Set the MapiContact properties using different constructors and methods.
1. Create a PST using the PersonalStorage.Create() method.
1. Create a pre-defined folder (Contacts) at the root of the PST file by accessing the root folder and then calling the AddMapiMessageItem() method.

The following code snippet shows you how to create a MapiContact and then add it to the contacts folder of a newly created PST file.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiContactAndAddToContactsSubfolder-CreateNewMapiContactAndAddToContactsSubfolder.cpp" >}}
## **Save contacts information from PST file in MSG Format**
This article explains how to access contact information from an Outlook PST file and save the contact to disk in MSG format. The PersonalStorage and MapiContact classes to get and display the contact information. The steps to get the contact information are:

1. Load the PST file in the PersonalStorage class.
1. Browse the Contacts folder.
1. Get the contents of the Contacts folder to get the message collection.
1. Loop through the message collection.
1. Call the PersonalStorage.ExtractContactInfo() method to get the contact information in the MapiContact class. Use the MapiContact class properties to access the contact information
1. Call the PersonalStorage.ExtractMessage() method to get the contact information in the MapiMessage class.
1. Call the MapiMessage.Save() method to save the contact to disk in MSG format.

The following code snippet shows you how to retrieve all the contact information from the PST file and save to disk in MSG format.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AccessContactInformation-AccessContactInformation.cpp" >}}
## **Save Contacts information from PST file in VCF Format**
This article shows how to access contact information from a Microsoft Outlook PST file and save the contact to disk in vCard (VCF) format. Use the PersonalStorage and MapiContact classes to get contact information from the PST file. To get the contact information:

1. Load the PST file in the PersonalStorage class.
1. Browse the Contacts folder.
1. Get the contents of the Contacts folder to get the message collection.
1. Loop through the message collection.
1. Call the PersonalStorage.ExtractMessage() method to get the contact information in the MapiContact class.
1. Use the MapiContact class different properties to access the contact information.

The program below loads a PST file from disk and saves all the contacts to vCard (VCF) format. The VCF files can then be used in any other program that can load the standard vCard contact file. If you open any VCF file in Microsoft Outlook, it looks like the one in the below screenshot.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
The following code snippet shows you how to export contacts from Outlook PST to vCard (VCF) format.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveContactInformation-SaveContactInformation.cpp" >}}
## **Working with Distribution Lists**
It is possible to create a Distribution list using Aspose.Email API that is a collection of multiple contacts. A distribution list can be saved to disc in Outlook MSG format and can be viewed/manipulated by opening it in MS Outlook.
### **Creating and Saving a Distribution List**
The following code snippet shows you how to create and save a distribution list.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cpp" >}}
### **Reading a Distribution List from a PST**
The following code snippet shows you how to read a distribution list from a PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingDistributionListFromPST-ReadingDistributionListFromPST.cpp" >}}
