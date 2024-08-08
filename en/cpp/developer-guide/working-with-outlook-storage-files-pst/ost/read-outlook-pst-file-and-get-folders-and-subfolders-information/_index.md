---
title: Read Outlook PST File and Get Folders and SubFolders Information
type: docs
weight: 30
url: /cpp/read-outlook-pst-file-and-get-folders-and-subfolders-information/
---

## **Read Outlook PST File and Get Folder and Subfolder Information**
Aspose.Email for C++ provides an API for reading Microsoft Outlook PST files. You can load a PST file from disk or stream into an instance of the PersonalStorage class and get the information about its contents, for example folders, subfolders and messages. The API also provides the capability to include search folders while traversing for messages from the PST folders.
### **Loading a PST File**
An Outlook PST file can be loaded in an instance of the PersonalStorage class. The following code snippet shows you how to load the PST file.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cpp" >}}
### **Displaying Folders Information**
After loading the PST file in the PersonalStorage class, you can get the information about the file display name, root folder, subfolders and messages count. The following code snippet shows you how to display the name of PST file, folders and number of messages in the folders.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cpp" >}}
### **Retrieving Parent Folder Information from MessageInfo**
The following code snippet shows you how to retrieve parent folder information from MessageInfo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetreiveParentFolderInformationFromMessageInfo-RetreiveParentFolderInformationFromMessageInfo.cpp" >}}
