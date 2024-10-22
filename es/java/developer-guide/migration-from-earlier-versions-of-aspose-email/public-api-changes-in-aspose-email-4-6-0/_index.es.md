---
title: "Cambios en la API Pública en Aspose.Email 4.6.0"
url: /es/java/public-api-changes-in-aspose-email-4-6-0/
weight: 80
type: docs
---

La siguiente es una lista de los cambios realizados en la API pública, como miembros añadidos, renombrados, eliminados o descontinuados, así como cualquier cambio que no sea compatible hacia atrás realizado en Aspose.Email para Java. Si tiene inquietudes sobre algún cambio listado, comuníquelo en el foro de soporte de Aspose.Email.
## **APIs Añadidas**
- Clase `SpamAnalyzer`

- Campo/Enumeración `MapiPropertyTag.PR_BODY_HTML`
- Campo/Enumeración `MapiPropertyTag.PR_BODY_HTML_A`
- Campo/Enumeración `MapiPropertyTag.PR_BODY_HTML_W`

- Método `SpamAnalyzer.#ctor`
- Método `SpamAnalyzer.#ctor(InputStream stream)`
- Método `SpamAnalyzer.#ctor(String filePath)`
- Método `SpamAnalyzer.loadDatabase(InputStream stream)`
- Método `SpamAnalyzer.loadDatabase(String filePath)`
- Método `SpamAnalyzer.reset`
- Método `SpamAnalyzer.saveDatabase(OutputStream stream)`
- Método `SpamAnalyzer.saveDatabase(String filePath)`
- Método `SpamAnalyzer.test(MailMessage message)`
- Método `SpamAnalyzer.trainFilter(String text, boolean isSpam)`
- Método `SpamAnalyzer.trainFilter(MailMessage[] ham, MailMessage[] spam)`
- Método `SpamAnalyzer.trainFilter(MailMessage message, boolean isSpam)`

- Propiedad `OleDocumentFormat.getMicrosoftPhotoEditor`
- Propiedad `OleDocumentFormat.detPictureMetafile`