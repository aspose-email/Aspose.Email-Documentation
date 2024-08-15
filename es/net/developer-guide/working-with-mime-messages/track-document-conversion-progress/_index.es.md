---
title: "Seguimiento del progreso de la conversión de documentos"
url: /es/net/track-document-conversion-progress/
weight: 60
type: docs
---


Aspose.Email ofrece la posibilidad de realizar un seguimiento del progreso de la conversión del documento. Para ello, la API proporciona [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/). que representa el método que gestiona los eventos de progreso. Los tipos de eventos de progreso se representan mediante [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) enumeración. La [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) la enumeración tiene los siguientes miembros.

- mimeStructureCreated: este evento informa que se ha creado la estructura mime.
- mimePartSaved: este evento informa que se ha terminado de guardar una parte mime.
- SavedToStream: este evento informa que todas las partes de mime se guardan para transmitir.

El siguiente código de ejemplo demuestra el uso de [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/) and [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) la enumeración rastrea el progreso de la conversión del documento.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-1.cs" >}}

El siguiente es el código de la clase personalizada utilizada en el ejemplo de código anterior.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-2.cs" >}}
