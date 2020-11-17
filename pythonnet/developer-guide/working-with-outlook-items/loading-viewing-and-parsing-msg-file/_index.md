---
title: Loading, Viewing and Parsing MSG file
type: docs
weight: 20
url: /pythonnet/loading-viewing-and-parsing-msg-file/
---


This topic explains how to load a Microsoft Outlook Messagefile (*.msg). The MapiMessage class is used to load MSG files, and provides several static loading functions for different scenarios. The following code snippet shows you how to load MSG files from file or from stream.
{{% alert %}}
**Try it out!**

Parse email files online with the free [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}
## **Loading MSG Files**
The following code snippet shows you how to load MSG files.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-LoadMSGFiles-LoadMSGFiles.cs" >}}
## **Loading from Stream**
The following code snippet shows you how to load file from stream.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-LoadingFromStream-LoadingFromStream.cs" >}}


## **Converting EML to MSG preserving embedded EML format**
EML files can be loaded into MapiMessage class by instantiating a MailMessage object and passing it to MapiMessage.FromMailMessage method. If the EML file contains embedded EML files, use MapiConversionOptions.PreserveEmbeddedMessageFormat to retain the format of embedded EML files. The below code snippet shows how to laod EML files into MapiMessage while preserving format of embedded EML files.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}
