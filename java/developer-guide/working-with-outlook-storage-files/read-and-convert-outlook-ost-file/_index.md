---
title: Read and Convert Outlook OST File
type: docs
weight: 20
url: /java/read-and-convert-outlook-ost-file/
---

{{% alert color="primary" %}} 

Microsoft Outlook creates a PST file for email storage when you use POP3 or IMAP mail servers to download messages. It creates an OST file when you use Microsoft Exchange as your mail server. OST supports larger file sizes compared to PST.

{{% /alert %}} 

Aspose.Email provides an API for reading Microsoft Outlook OST files. You can load an OST file into an instance of [PersonalStorage](https://apireference.aspose.com/java/email/com.aspose.email/PersonalStorage) class and get the information about its contents, for example, folders and subfolders.
## **Reading OST Files**
Reading an OST file with Aspose.Email is exactly similar to reading a PST file. The same code can read both PST and OST files: just provide the correct file name to the [PersonalStorage.fromFile()](https://apireference.aspose.com/java/email/com.aspose.email/PersonalStorage#fromFile\(java.lang.String\)) method.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ReadAnOSTFile.java" >}}
## **Converting OST to PST**
Aspose.Email makes it possible to convert an OST file to PST with a single line of code. Similarly, the OST file can be created from the PST file using the same line of code with the [FileFormat](https://apireference.aspose.com/java/email/com.aspose.email/FileFormat) enumerator.

{{% alert color="primary" %}} 

At present, the API supports converting OST formats to PST except OST 2013/2016.

{{% /alert %}} 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ConvertOSTToPST.java" >}}

{{% alert %}}
**Try it out!**

Convert emails & message archives online with the free [**Aspose.Email Conversion App**](https://products.aspose.app/email/Conversion).
{{% /alert %}}
