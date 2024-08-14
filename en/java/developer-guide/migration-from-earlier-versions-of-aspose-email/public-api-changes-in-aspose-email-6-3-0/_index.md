---
title: Public API Changes in Aspose.Email 6.3.0
type: docs
weight: 240
url: /java/public-api-changes-in-aspose-email-6-3-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for Java. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.

The class `RecurrencePattern` renamed to `CalendarRecurrence` class.
The class `CalendarRecurrencePattern` renamed to `RecurrencePattern` class.
The class `CalendarRecurrencePattern` is obsolete and will be removed soon. Please, use `RecurrencePattern` class instead of it.
## **Added APIs**
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
