---
title: Automate Email Archiving in Exchange Servers Using C# and EWS API
ArticleTitle: Archiving Exchange Emails Using EWS API
type: docs
weight: 130
url: /net/archive-exchange-emails-using-ews-api/
---


Aspose.Email for .NET offers a comprehensive API to manage and process emails on an Exchange Server. This guide demonstrates how to list emails in the Inbox folder of an Exchange mailbox and archive them programmatically using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface. The [IEWSClient.ArchiveItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) method of the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface allows you to move items into users archive mailbox. It provides four overloads which are listed below:

- [ArchiveItem(string sourceFolderUri, Appointment appointment)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem)
- [ArchiveItem(string sourceFolderUri, ExchangeTask task)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_1)
- [ArchiveItem(string sourceFolderUri, MapiMessageItemBase item)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_2)
- [ArchiveItem(string sourceFolderUri, string uniqueId)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_3)


The following code sample demonstrates how to use Aspose.Email to connect to the Exchange server, list messages, and archive them with the [IEWSClient.ArchiveItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) method. Storing emails is achieved by moving each item to the Archive Mailbox using the UniqueUri.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-MoveItemsToInPlaceArchive-MoveItemsToInPlaceArchive.cs" >}}






