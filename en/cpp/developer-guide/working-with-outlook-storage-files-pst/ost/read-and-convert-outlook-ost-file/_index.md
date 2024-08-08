---
title: Read and Convert Outlook OST File
type: docs
weight: 20
url: /cpp/read-and-convert-outlook-ost-file/
---

## **Read and Convert Outlook OST File**
Aspose.Email for C++ provides an API for reading Microsoft Outlook OST files. You can load an OST file from disk or stream into an instance of the Aspose.Email.Outlook.Pst.PersonalStorage class and get information about its contents, for example, folders, subfolders and messages. Microsoft Outlook creates a PST file to store emails in when POP3 or IMAP mail servers are used for downloading messages. It creates an OST file when Microsoft Exchange is the mail server. OST supports larger file sizes than PST files.
### **Reading OST Files**
The process for reading an OST file with Aspose.Email is exactly the same as for reading a PST file. The same code can read both PST and OST files: just provide the correct file name to the PersonalStorage.FromFile() method. The following code snippet shows you how to read OST files.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cpp" >}}
### **Converting OST to PST**
Aspose.Email makes it possible to convert an OST file to PST with a single line of code. Similarly, OST file can be created from PST file using the same line of code with the FileFormat enumerator. At present, the API supports converting OST formats to PST except OST 2013/2016. The following code snippet shows you how to Convert OST to PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cpp" >}}



