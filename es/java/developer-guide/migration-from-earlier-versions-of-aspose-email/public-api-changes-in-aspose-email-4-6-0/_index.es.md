---
title: "Cambios en la API pública en Aspose.Email 4.6.0"
url: /es/java/public-api-changes-in-aspose-email-4-6-0/
weight: 80
type: docs
---

La siguiente es una lista de todos los cambios realizados en la API pública, como la adición, el cambio de nombre, la eliminación o la desaprobación de miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tienes dudas sobre algún cambio de la lista, comunícalo en el foro de soporte de Aspose.Email.
## **API añadidas**
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
