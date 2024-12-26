---
title: Reading Email Messages from Microsoft SharePoint Document Library
ArticleTitle: Reading Email Messages from Microsoft SharePoint Document Library
type: docs
weight: 110
url: /net/reading-email-messages-from-microsoft-sharepoint-document-library/
---


This article shows how to read email messages from a Microsoft SharePoint document library. To access files in a SharePoint document library, the SharePoint SDK must be installed on the system. The SDK provides the API necessary to log in and access files from the document library.
## **Reading Email Messages from SharePoint**
The programming samples below assumes that a Microsoft Outlook Message file (.msg) is already stored in the SharedDocument folder of the SharePoint Document Library. The SharePoint SDK is used to get the message file into a stream and then pass this stream to an instance of Aspose.Email's [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage) class. The MailMessage class loads the stream and parses the Outlook message file. After that, access the MailMessage class' properties, for example, subject, text body, HTML body etc. to use the information in a Visual Studio project. For information on how to install and configure Microsoft SharePoint Server and the SDK, please refer to the respective sections in MSDN library. The following code snippet shows you how to read email messages from SharePoint.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-ReadingEmailMessagesFromSharePoint-ReadingEmailMessagesFromSharePoint.cs" >}}
