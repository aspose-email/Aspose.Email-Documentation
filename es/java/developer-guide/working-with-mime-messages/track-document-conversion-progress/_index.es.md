---
title: "Seguimiento del progreso de la conversión de documentos"
url: /es/java/track-document-conversion-progress/
weight: 60
type: docs
---

## **Seguimiento del progreso de la conversión de documentos**

Aspose.Email ofrece la posibilidad de realizar un seguimiento del progreso de la conversión del documento. Para ello, la API proporciona [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/#getCustomProgressHandler--). que representa el método que gestiona los eventos de progreso. Los tipos de eventos de progreso se representan mediante [ProgressEventType](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/) enumeración. La **ProgressEventType** la enumeración tiene los siguientes miembros.

- [MimeStructureCreated](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimeStructureCreated): Este evento informa que se ha creado la estructura mime.
- [MimePartSaved](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimePartSaved): Este evento informa de que ha finalizado el almacenamiento de una parte de mime.
- [SavedToStream](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#SavedToStream): Este evento informa de que todas las partes de mimo se guardan para su transmisión.

El siguiente código de ejemplo demuestra el uso de **SaveOptions.CustomProgressHandler** and **ProgressEventType** la enumeración rastrea el progreso de la conversión del documento.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-1.java" >}}

El siguiente es el código de la clase personalizada utilizada en el ejemplo de código anterior.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-2.java" >}}
