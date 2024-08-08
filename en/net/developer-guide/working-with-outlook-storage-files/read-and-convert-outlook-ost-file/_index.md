---
title: Read and Convert Outlook OST File
type: docs
weight: 20
url: /net/read-and-convert-outlook-ost-file/
---


Aspose.Email for .NET provides an API for reading Microsoft Outlook OST files. You can load an OST file from a disk or a stream into an instance of the [Aspose.Email.Outlook.Pst.PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class and get information about its contents, for example, folders, subfolders, and messages. Microsoft Outlook creates a PST file to store emails when POP3 or IMAP mail servers are used for downloading messages. It creates an OST file when Microsoft Exchange is the mail server. OST supports larger file sizes than PST files.

## **Reading OST Files**

The process for reading an OST file with Aspose.Email is exactly the same as for reading a PST file. The same code can read both PST and OST files: just provide the correct file name to the [PersonalStorage.FromFile()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile/) method. The following code snippet shows you how to read OST files.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cs" >}}

## **Converting OST to PST**

{{% alert %}}
**Try it out!**

Convert emails & message archives online with the free [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}
Aspose.Email makes it possible to convert an OST file to PST with a single line of code. Similarly, the OST file can be created from PST file using the same line of code with the [FileFormat](https://reference.aspose.com/email/net/aspose.email.storage.pst/fileformat/) enumerator. At present, the API supports converting OST formats to PST except 2013/2016/2019/2021 and future versions. The following code snippet shows you how to Convert OST to PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cs" >}}

For performing other operations with OST files, please refer to the following pages:

- [Read Outlook PST File and Get Folder and Subfolder Information](https://docs.aspose.com/email/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Get Messages Information from an Outlook PST File](https://docs.aspose.com/email/net/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Extract Messages from Outlook PST File and Save to Disk or Stream in MSG Format](https://docs.aspose.com/email/net/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Access Contact Information from Outlook PST File and Save to Disk in MSG Format](https://docs.aspose.com/email/net/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Converting PST to OST**

Conversion from PST to OST is not supported by Aspose.Email because OST is always created by the Outlook when adding an account and synchronizing with the mail server.
The difference between PST and OST files is that PST is only available locally. OST content is also available on the e-mail server.
So there is no need to convert PST to OST for local use.
But you can import PST into an existing account using the Import/Export wizard in Outlook.
