---
title: "Seguimiento del Progreso de Conversión de Documentos"
url: /es/net/track-document-conversion-progress/
weight: 60
type: docs
---


Aspose.Email proporciona la facilidad para rastrear el progreso de conversión de documentos. Para esto, la API ofrece [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/), que representa el método que maneja los eventos de progreso. Los tipos de eventos de progreso están representados por la [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) enumeración. La enumeración [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) tiene los siguientes miembros.

- MimeStructureCreated: Este evento informa que la estructura MIME ha sido creada.
- MimePartSaved: Este evento informa que se ha terminado de guardar una parte MIME.
- SavedToStream: Este evento informa que todas las partes MIME se han guardado en el flujo.

El siguiente código de ejemplo demuestra el uso de [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/net/aspose.email/saveoptions/customprogresshandler/) y la enumeración [ProgressEventType](https://reference.aspose.com/email/net/aspose.email/progresseventtype/) para rastrear el progreso de conversión de documentos.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-1.cs" >}}

Lo siguiente es el código para la clase personalizada utilizada en el código de ejemplo dado anteriormente.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-TrackDocumentConversionProgress-2.cs" >}}