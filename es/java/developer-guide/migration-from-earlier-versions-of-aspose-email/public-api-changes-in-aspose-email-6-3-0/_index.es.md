---
title: "Cambios en la API pública en Aspose.Email 6.3.0"
url: /es/java/public-api-changes-in-aspose-email-6-3-0/
weight: 240
type: docs
---

La siguiente es una lista de todos los cambios realizados en la API pública, como la adición, el cambio de nombre, la eliminación o la desaprobación de miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tienes dudas sobre algún cambio de la lista, comunícalo en el foro de soporte de Aspose.Email.

La clase `RecurrencePattern` renombrado a `CalendarRecurrence` clase.
La clase `CalendarRecurrencePattern` renombrado a `RecurrencePattern` clase.
La clase `CalendarRecurrencePattern` está obsoleto y se eliminará pronto. Por favor, utilice `RecurrencePattern` clase en lugar de ella.
## **API añadidas**
- Class `FileFormatType`
- Class `FileFormatInfo`
- Class `FileFormatUtil`
- Method `FileFormatUtil.detectFileFormat(InputStream)`
- Method `FileFormatUtil.detectFileFormat(String)`

- Method `MailMessage.attachSignature(CmsSigner, boolean)`
- Method `MailMessage.attachSignature(X509Certificate2, boolean)`

- Class `TimeoutException`
- Method `TimeoutException.#ctor`
- Method `TimeoutException.#ctor(String)`

- Property `EmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Property `HtmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Property `MhtSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
