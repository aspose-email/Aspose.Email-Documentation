---
title: "Trabajando con el Archivo In-Place"
url: /es/net/working-with-in-place-archive/
weight: 150
type: docs
---

## **Archivos In-Place en Office 365**

Los Archivos In-Place en Office 365 proporcionan a los usuarios espacio adicional de almacenamiento. Después de que los buzones de archivo estén activados, los usuarios pueden acceder y almacenar mensajes en su Buzón de Archivo utilizando Microsoft Outlook y Outlook en la Web. Cuando el buzón con la archivación In-Place activada se abre con Outlook, el buzón de archivo se muestra como un buzón separado.

## **Mover elementos al Archivo In-Place**

La API Aspose.Email se puede utilizar para mover elementos al buzón de archivo de los usuarios utilizando el método [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/). El método [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) tiene cuatro sobrecargas que se enumeran a continuación.

- [`ArchiveItem(string sourceFolderUri, Appointment appointment)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem)
- [`ArchiveItem(string sourceFolderUri, ExchangeTask task)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_1)
- [`ArchiveItem(string sourceFolderUri, MapiMessageItemBase item)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_2)
- [`ArchiveItem(string sourceFolderUri, string uniqueId)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem_3)

El ejemplo de código dado a continuación demuestra el uso del método [`IEWSClient.ArchiveItem`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/archiveitem/#archiveitem/) para mover un correo electrónico al Buzón de Archivo utilizando el UniqueUri.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-MoveItemsToInPlaceArchive-MoveItemsToInPlaceArchive.cs" >}}