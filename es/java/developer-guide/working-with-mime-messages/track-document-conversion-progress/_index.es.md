---
title: "Seguimiento del Progreso de Conversión de Documentos"
url: /es/java/seguimiento-del-progreso-de-conversion-de-documentos/
weight: 60
type: docs
---

## **Seguimiento del Progreso de Conversión de Documentos**

Aspose.Email proporciona la facilidad de rastrear el progreso de la conversión de documentos. Para esto, la API proporciona [SaveOptions.CustomProgressHandler](https://reference.aspose.com/email/java/com.aspose.email/saveoptions/#getCustomProgressHandler--). que representa el método que maneja los eventos de progreso. Los tipos de eventos de progreso están representados por la [ProgressEventType](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/) enumeración. La enumeración **ProgressEventType** tiene los siguientes miembros.

- [MimeStructureCreated](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimeStructureCreated): Este evento informa que la estructura mime ha sido creada.
- [MimePartSaved](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#MimePartSaved): Este evento informa que se ha terminado de guardar una parte mime.
- [SavedToStream](https://reference.aspose.com/email/java/com.aspose.email/progresseventtype/#SavedToStream): Este evento informa que todas las partes mime han sido guardadas en el stream.

El siguiente código de muestra demuestra el uso de **SaveOptions.CustomProgressHandler** y **ProgressEventType** enumeración para rastrear el progreso de conversión de documentos.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-1.java" >}}

El siguiente es el código para la clase personalizada utilizada en el código de muestra dado arriba.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TrackDocumentConversionProgress-2.java" >}}