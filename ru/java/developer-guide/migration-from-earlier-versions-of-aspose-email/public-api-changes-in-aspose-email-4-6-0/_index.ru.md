---
title: "Изменения в публичном API Aspose.Email 4.6.0"
url: /ru/java/public-api-changes-in-aspose-email-4-6-0/
weight: 80
type: docs
---

Следующее является списком изменений, внесенных в публичный API, таких как добавленные, переименованные, удаленные или устаревшие члены, а также любые изменения, не совместимые с предыдущими версиями, внесенные в Aspose.Email для Java. Если у вас есть опасения по поводу какого-либо перечисленного изменения, пожалуйста, поднимите этот вопрос на форуме поддержки Aspose.Email.
## **Добавленные API**
- Класс `SpamAnalyzer`

- Поле/Перечисление `MapiPropertyTag.PR_BODY_HTML`
- Поле/Перечисление `MapiPropertyTag.PR_BODY_HTML_A`
- Поле/Перечисление `MapiPropertyTag.PR_BODY_HTML_W`

- Метод `SpamAnalyzer.#ctor`
- Метод `SpamAnalyzer.#ctor(InputStream stream)`
- Метод `SpamAnalyzer.#ctor(String filePath)`
- Метод `SpamAnalyzer.loadDatabase(InputStream stream)`
- Метод `SpamAnalyzer.loadDatabase(String filePath)`
- Метод `SpamAnalyzer.reset`
- Метод `SpamAnalyzer.saveDatabase(OutputStream stream)`
- Метод `SpamAnalyzer.saveDatabase(String filePath)`
- Метод `SpamAnalyzer.test(MailMessage message)`
- Метод `SpamAnalyzer.trainFilter(String text, boolean isSpam)`
- Метод `SpamAnalyzer.trainFilter(MailMessage[] ham, MailMessage[] spam)`
- Метод `SpamAnalyzer.trainFilter(MailMessage message, boolean isSpam)`

- Свойство `OleDocumentFormat.getMicrosoftPhotoEditor`
- Свойство `OleDocumentFormat.detPictureMetafile`