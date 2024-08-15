---
title: "Изменения в публичном API в Aspose.Email 6.3.0"
url: /ru/java/public-api-changes-in-aspose-email-6-3-0/
weight: 240
type: docs
---

Ниже приведен список всех изменений, внесенных в общедоступный API, таких как добавление, переименование, удаление или устаревание членов, а также любых изменений, не совместимых с обратной совместимостью, внесенных в Aspose.Email для Java. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.

Класс `RecurrencePattern` переименован в `CalendarRecurrence` класс.
Класс `CalendarRecurrencePattern` переименован в `RecurrencePattern` класс.
Класс `CalendarRecurrencePattern` устарела и скоро будет удалена. Пожалуйста, используйте `RecurrencePattern` класс вместо него.
## **Добавлены API**
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
