---
title: "Работа с архивом в месте"
url: /ru/net/working-with-in-place-archive/
weight: 150
type: docs
---


## **Архивы в месте в Office 365**

Архивы в месте в Office 365 предоставляют пользователям дополнительное место для хранения. После включения архивных почтовых ящиков пользователи могут получать доступ и хранить сообщения в своем архивном почтовом ящике с помощью Microsoft Outlook и Outlook в Интернете. Когда почтовый ящик с включенной функцией архивации в месте открывается в Outlook, архивный почтовый ящик отображается как отдельный почтовый ящик.

## **Перемещение элементов в архив в месте**

API Aspose.Email может быть использован для перемещения элементов в архивный почтовый ящик пользователей с помощью метода [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/). Метод [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) предоставляет четыре перегрузки, которые перечислены ниже.

- [`ArchiveItem(string sourceFolderUri, Appointment appointment)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem)
- [`ArchiveItem(string sourceFolderUri, ExchangeTask task)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_1)
- [`ArchiveItem(string sourceFolderUri, MapiMessageItemBase item)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_2)
- [`ArchiveItem(string sourceFolderUri, string uniqueId)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_3)

Пример кода, приведенный ниже, демонстрирует использование метода [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) для перемещения электронного письма в архивный почтовый ящик с использованием UniqueUri.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-MoveItemsToInPlaceArchive-MoveItemsToInPlaceArchive.cs" >}}