---
title: Working with In-Place Archive
type: docs
weight: 150
url: /net/working-with-in-place-archive/
---


## **In-Place Archives in Office 365**
In-Place Archives in Office 365 provides users with additional storage space. After the archive mailboxes are turned on, users can access and store messages in their Archive Mailbox by using Microsoft Outlook and Outlook on the Web. When the mailbox with In-Place archiving enabled is opened with Outlook, the archive mailbox is shown as a separate mailbox.
## **Move Items to In-Place Archive**
Aspose.Email API can be used to move items into users archive mailbox by using the [IEWSClient.ArchiveItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/archiveitem/index) method. [IEWSClient.ArchiveItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/archiveitem/index) method provides four overloads which are listed below.

- [ArchiveItem(string sourceFolderUri, Appointment appointment)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/archiveitem)
- [ArchiveItem(string sourceFolderUri, ExchangeTask task)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/archiveitem/methods/1)
- [ArchiveItem(string sourceFolderUri, MapiMessageItemBase item)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/archiveitem/methods/2)
- [ArchiveItem(string sourceFolderUri, string uniqueId)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.iewsclient/archiveitem/methods/3)

The code example given below demonstrates the use of [IEWSClient.ArchiveItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/archiveitem/index) method to move an email to the Archive Mailbox by using the UniqueUri.



{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-MoveItemsToInPlaceArchive-MoveItemsToInPlaceArchive.cs" >}}
