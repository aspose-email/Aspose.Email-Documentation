---
title: "Cambios en la API pública en Aspose.Email 6.3.0"
url: /es/java/public-api-changes-in-aspose-email-6-3-0/
weight: 240
type: docs
---

La siguiente es una lista de los cambios realizados en la API pública, como miembros añadidos, renombrados, eliminados o obsoletos, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tiene preocupaciones sobre algún cambio listado, por favor, comuníquese en el foro de soporte de Aspose.Email.

La clase `RecurrencePattern` fue renombrada a `CalendarRecurrence`.
La clase `CalendarRecurrencePattern` fue renombrada a `RecurrencePattern`.
La clase `CalendarRecurrencePattern` está obsoleta y será eliminada pronto. Por favor, use la clase `RecurrencePattern` en su lugar.
## **APIs Añadidas**
- Clase `FileFormatType`
- Clase `FileFormatInfo`
- Clase `FileFormatUtil`
- Método `FileFormatUtil.detectFileFormat(InputStream)`
- Método `FileFormatUtil.detectFileFormat(String)`

- Método `MailMessage.attachSignature(CmsSigner, boolean)`
- Método `MailMessage.attachSignature(X509Certificate2, boolean)`

- Clase `TimeoutException`
- Método `TimeoutException.#ctor`
- Método `TimeoutException.#ctor(String)`

- Propiedad `EmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Propiedad `HtmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Propiedad `MhtSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`