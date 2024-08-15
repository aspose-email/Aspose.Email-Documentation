---
title: "Работа с локальным архивом"
url: /ru/net/working-with-in-place-archive/
weight: 150
type: docs
---


## **Местные архивы в Office 365**

Местовые архивы в Office 365 предоставляют пользователям дополнительное пространство для хранения. После включения архивных почтовых ящиков пользователи могут получать доступ к сообщениям и хранить их в своем архивном почтовом ящике с помощью Microsoft Outlook и Outlook в Интернете. Если почтовый ящик с включенной архивацией на месте открывается в Outlook, архивный почтовый ящик отображается как отдельный почтовый ящик.

## **Переместить элементы в локальный архив**

Aspose.Email API можно использовать для перемещения элементов в архивный почтовый ящик пользователей с помощью [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) method. [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) Метод обеспечивает четыре перегрузки, которые перечислены ниже.

- [`ArchiveItem(string sourceFolderUri, Appointment appointment)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem)
- [`ArchiveItem(string sourceFolderUri, ExchangeTask task)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_1)
- [`ArchiveItem(string sourceFolderUri, MapiMessageItemBase item)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_2)
- [`ArchiveItem(string sourceFolderUri, string uniqueId)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_3)

Приведенный ниже пример кода демонстрирует использование [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) метод перемещения электронной почты в архивный почтовый ящик с помощью uniqueURI.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-MoveItemsToInPlaceArchive-MoveItemsToInPlaceArchive.cs" >}}
