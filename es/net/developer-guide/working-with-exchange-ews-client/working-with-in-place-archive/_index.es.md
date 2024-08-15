---
title: "Trabajando con In-Place Archive"
url: /es/net/working-with-in-place-archive/
weight: 150
type: docs
---


## **Archivos locales en Office 365**

Los archivos locales de Office 365 proporcionan a los usuarios espacio de almacenamiento adicional. Una vez activados los buzones de archivado, los usuarios pueden acceder a los mensajes y almacenarlos en su buzón de archivado mediante Microsoft Outlook y Outlook en la Web. Cuando el buzón con el archivado local habilitado se abre con Outlook, el buzón de archivo se muestra como un buzón independiente.

## **Mover elementos a un archivo local**

La API Aspose.Email se puede usar para mover elementos al buzón de archivo de los usuarios mediante el [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) method. [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) El método proporciona cuatro sobrecargas que se enumeran a continuación.

- [`ArchiveItem(string sourceFolderUri, Appointment appointment)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem)
- [`ArchiveItem(string sourceFolderUri, ExchangeTask task)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_1)
- [`ArchiveItem(string sourceFolderUri, MapiMessageItemBase item)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_2)
- [`ArchiveItem(string sourceFolderUri, string uniqueId)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_3)

El ejemplo de código que se muestra a continuación demuestra el uso de [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) método para mover un correo electrónico al buzón de archivo mediante el UniqueURI.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-MoveItemsToInPlaceArchive-MoveItemsToInPlaceArchive.cs" >}}
