---
title: "Mudanças na API Pública no Aspose.Email 6.3.0"
url: /pt/java/public-api-changes-in-aspose-email-6-3-0/
weight: 240
type: docs
---

A seguir está uma lista de quaisquer mudanças feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como qualquer mudança não compatível com versões anteriores feita no Aspose.Email para Java. Se você tiver preocupações sobre alguma mudança listada, por favor, reporte-a no fórum de suporte do Aspose.Email.

A classe `RecurrencePattern` foi renomeada para a classe `CalendarRecurrence`.
A classe `CalendarRecurrencePattern` foi renomeada para a classe `RecurrencePattern`.
A classe `CalendarRecurrencePattern` está obsoleta e será removida em breve. Por favor, use a classe `RecurrencePattern` em seu lugar.
## **APIs Adicionadas**
- Classe `FileFormatType`
- Classe `FileFormatInfo`
- Classe `FileFormatUtil`
- Método `FileFormatUtil.detectFileFormat(InputStream)`
- Método `FileFormatUtil.detectFileFormat(String)`

- Método `MailMessage.attachSignature(CmsSigner, boolean)`
- Método `MailMessage.attachSignature(X509Certificate2, boolean)`

- Classe `TimeoutException`
- Método `TimeoutException.#ctor`
- Método `TimeoutException.#ctor(String)`

- Propriedade `EmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Propriedade `HtmlSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`
- Propriedade `MhtSaveOptions.getCheckBodyContentEncoding, setCheckBodyContentEncoding`