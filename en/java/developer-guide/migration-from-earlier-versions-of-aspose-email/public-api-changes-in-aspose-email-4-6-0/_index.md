---
title: Public API Changes in Aspose.Email 4.6.0
type: docs
weight: 80
url: /java/public-api-changes-in-aspose-email-4-6-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for Java. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added APIs**
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
