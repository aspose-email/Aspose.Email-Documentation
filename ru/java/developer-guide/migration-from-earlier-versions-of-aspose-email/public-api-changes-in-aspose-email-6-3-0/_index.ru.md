---
title: "Изменения публичного API в Aspose.Email 6.3.0"
url: /ru/java/public-api-changes-in-aspose-email-6-3-0/
weight: 240
type: docs
---

Следующий список содержит изменения, внесенные в публичный API, такие как добавленные, переименованные, удаленные или устаревшие члены, а также любые изменения, несовместимые с предыдущими версиями, внесенные в Aspose.Email для Java. Если у вас есть опасения по поводу любого из перечисленных изменений, пожалуйста, озвучьте их на форуме поддержки Aspose.Email.

Класс `RecurrencePattern` переименован в класс `CalendarRecurrence`.
Класс `CalendarRecurrencePattern` переименован в класс `RecurrencePattern`.
Класс `CalendarRecurrencePattern` устарел и будет скоро удален. Пожалуйста, используйте класс `RecurrencePattern` вместо него.
## **Добавленные API**
- Класс `FileFormatType`
- Класс `FileFormatInfo`
- Класс `FileFormatUtil`
- Метод `FileFormatUtil.detectFileFormat(InputStream)`
- Метод `FileFormatUtil.detectFileFormat(String)`

- Метод `MailMessage.attachSignature(CmsSigner, boolean)`
- Метод `MailMessage.attachSignature(X509Certificate2, boolean)`

- Класс `TimeoutException`
- Метод `TimeoutException.#ctor`
- Метод `TimeoutException.#ctor(String)`

- Свойство `EmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Свойство `HtmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Свойство `MhtSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`