---
title: Read and Convert Outlook OST Files
ArticleTitle: Read and Convert Outlook OST Files
type: docs
weight: 20
url: /python-net/read-and-convert-outlook-ost-files/
---


Aspose.Email for .NET provides the API for reading Microsoft Outlook OST files. You can load an OST file from disk or a stream into an instance of the [Aspose.Email.Outlook.Pst.PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/) class and get information about its contents, for example, folders, subfolders and messages. Microsoft Outlook creates a PST file to store emails when using POP3 or IMAP mail servers for downloading messages, whereas an OST file is created when Microsoft Exchange is the mail server. OST files are designed to support larger file sizes compared to PST files.

## **Reading OST Files**

The process for reading an OST file with Aspose.Email is exactly the same as for reading a PST file. The same code can read both PST and OST files: just provide the correct file name to the [PersonalStorage.from_file()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method. The following code snippet shows you how to read OST files:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}

## **Convert OST to PST**

{{% alert %}}
**Try it out!**

Convert emails & message archives online with the free [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}
Aspose.Email makes it possible to convert an OST file to PST with a single line of code. Similarly, OST file can be created from PST file using the same line of code with the [FileFormat](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/fileformat/) enumerator. At present, the API supports converting OST formats to PST except OST 2013/2016. The following code snippet shows you how to convert OST to PST:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ConvertingOSTToPST-ConvertingOSTToPST.py" >}}

## **Convert PST to OST**

Conversion from PST to OST is not supported by Aspose.Email because OST is always created by the Outlook when adding an account and synchronizing with the mail server. The difference between PST and OST files is that PST is only available locally. OST content is also available on the e-mail server. So there is no need to convert PST to OST for local use. But you can import PST into an existing account using the Import/Export wizard in Outlook.

For performing other operations with OST files, please refer to the following pages:

- Read Outlook PST File and Get Folder and Subfolder Information
- Get Messages Information from an Outlook PST File
- Extract Messages from Outlook PST File and Save to Disk or Stream in MSG Format
- Access Contact Information from Outlook PST File and Save to Disk in MSG Format
