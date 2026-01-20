---
title: Load, Parse Outlook MSG Files Using Aspose.Email for C++
ArticleTitle: Load & Parse Outlook MSG Files 
linktitle: Load, Parse Outlook MSG Files 
type: docs
weight: 20
url: /cpp/load-parse-outlook-msg-files/
description: Learn how to load and parse Outlook MSG files from a file or stream using the Aspose.Email for C++ library.
---

**Aspose.Email for C++** provides powerful tools for reading and analyzing Microsoft Outlook message files (.msg). The [MapiMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_message/) class is used to load and parse MSG files, giving access to message details such as subject, sender, body, recipients, and attachments. You can load messages directly from a file or from a memory stream, depending on your application needs.

{{% alert %}}
**Try it out!**

Parse email files with the free [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}

## **Load MSG Files from Disk**

The following example demonstrates how to load a .msg file from the local file system and access its basic properties such as subject, sender, body, and attachments.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadMSGFiles-LoadMSGFiles.cpp" >}}

## **Load MSG Files from Stream**

You can also load Outlook MSG files from a data stream, which is especially useful when working with in-memory data or email files stored in a database.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingFromStream-LoadingFromStream.cpp" >}}
