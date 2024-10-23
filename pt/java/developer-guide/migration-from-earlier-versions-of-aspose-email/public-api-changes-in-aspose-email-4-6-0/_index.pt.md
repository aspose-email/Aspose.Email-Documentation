---
title: "Mudanças na API Pública no Aspose.Email 4.6.0"
url: /pt/java/public-api-changes-in-aspose-email-4-6-0/
weight: 80
type: docs
---

A seguir está uma lista de quaisquer mudanças feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como qualquer mudança não compatível com versões anteriores feita no Aspose.Email para Java. Se você tiver preocupações sobre alguma mudança listada, por favor, levante no fórum de suporte do Aspose.Email.
## **APIs Adicionadas**
- Classe `SpamAnalyzer`

- Campo/Enum `MapiPropertyTag.PR_BODY_HTML`
- Campo/Enum `MapiPropertyTag.PR_BODY_HTML_A`
- Campo/Enum `MapiPropertyTag.PR_BODY_HTML_W`

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

- Propriedade `OleDocumentFormat.getMicrosoftPhotoEditor`
- Propriedade `OleDocumentFormat.detPictureMetafile`