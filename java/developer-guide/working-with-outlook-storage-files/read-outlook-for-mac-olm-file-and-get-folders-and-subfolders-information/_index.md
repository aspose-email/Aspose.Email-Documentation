---
title: Read Outlook for Mac OLM File and Get Folders and SubFolders Information
type: docs
weight: 130
url: /java/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
---

{{% alert color="primary" %}} 

Aspose.Email for Java lets you read Outlook for Mac OLM files. You can load an OLM file from disk into an instance of the [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/OlmStorage) class and get the information about its contents, for example, folders, subfolders, and messages.

{{% /alert %}} 
## **Read Outlook for Mac OLM File and Get Folder and Subfolder Information**
Aspose.Email for Java provides an API for reading Outlook for Mac data files in OLM format. An OLM file can be loaded into an instance of the [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/OlmStorage) class. After loading the OLM file into the [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/OlmStorage) class, you can get the information about the file display name, root folder, subfolders and messages count.
### **Read OLM file**
The following code snippet shows you how to load the OLM file and get its content.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-LoadAndReadOLMFile.java" >}}
### **Get Folder Path**
You may also get the folder path of folders in the OML file. Aspose.Email provides [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/OlmFolder#getPath\(\)) property which returns the folder path. The following code snippet demonstrates the use of [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/OlmFolder#getPath\(\)) property to get the folder paths in the OML file.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-GetFolderPathInOLM-1.java" >}}
### **Count the number of items in the folder**
You may also count the number of items in the folder. Aspose.Email provides [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/OlmFolder#getMessageCount\(\)) property which returns the number of items in the folder. The following code snippet demonstrates the use of [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/OlmFolder#getMessageCount\(\)) property to get the number of items in the folders of the OML file.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-CountItemsInOLMFolder-1.java" >}}
