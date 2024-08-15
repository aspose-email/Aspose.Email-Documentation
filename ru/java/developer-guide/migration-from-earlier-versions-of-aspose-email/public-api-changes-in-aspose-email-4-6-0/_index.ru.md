---
title: "Изменения в публичном API в Aspose.Email 4.6.0"
url: /ru/java/public-api-changes-in-aspose-email-4-6-0/
weight: 80
type: docs
---

Ниже приведен список всех изменений, внесенных в общедоступный API, таких как добавление, переименование, удаление или устаревание членов, а также любых изменений, не совместимых с обратной совместимостью, внесенных в Aspose.Email для Java. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.
## **Добавлены API**
- Class `SpamAnalyzer`

- Field/Enum `MapiPropertyTag.PR_BODY_HTML`
- Field/Enum `MapiPropertyTag.PR_BODY_HTML_A`
- Field/Enum `MapiPropertyTag.PR_BODY_HTML_W`

- Method `SpamAnalyzer.#ctor`
- Method `SpamAnalyzer.#ctor(InputStream stream)`
- Method `SpamAnalyzer.#ctor(String filePath)`
- Method `SpamAnalyzer.loadDatabase(InputStream stream)`
- Method `SpamAnalyzer.loadDatabase(String filePath)`
- Method `SpamAnalyzer.reset`
- Method `SpamAnalyzer.saveDatabase(OutputStream stream)`
- Method `SpamAnalyzer.saveDatabase(String filePath)`
- Method `SpamAnalyzer.test(MailMessage message)`
- Method `SpamAnalyzer.trainFilter(String text, boolean isSpam)`
- Method `SpamAnalyzer.trainFilter(MailMessage[] ham, MailMessage[] spam)`
- Method `SpamAnalyzer.trainFilter(MailMessage message, boolean isSpam)`

- Property `OleDocumentFormat.getMicrosoftPhotoEditor`
- Property `OleDocumentFormat.detPictureMetafile`
