---
title: "Mudanças na API Pública no Aspose.Email 5.1.0"
url: /pt/java/public-api-changes-in-aspose-email-5-1-0/
weight: 120
type: docs
---

A seguir, está uma lista de quaisquer mudanças feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como qualquer alteração não compatível com versões anteriores feita no Aspose.Email para .NET. Se você tiver preocupações sobre qualquer mudança listada, por favor, levante-a no fórum de suporte do Aspose.Email.

## **APIs Adicionadas**
- Classe `BaseTokenProvider`
- Classe `OutlookTokenProvider`

- Método `HeaderCollection.getDecodedValue(String)`

- Método `BaseTokenProvider.getAccessToken()`
- Método `BaseTokenProvider.getAccessToken(boolean)`
- Método `OutlookTokenProvider.getInstance(String,String,String)`

- Propriedade `MailMessage.getHtmlBodyText`
- Propriedade `BaseTokenProvider.getClientId()`
- Propriedade `BaseTokenProvider.getClientSecret()`
- Propriedade `BaseTokenProvider.getRefreshToken()`
- Propriedade `MapiConversionOptions.getPreserveOriginalAddresses(), MapiConversionOptions.setPreserveOriginalAddresses(boolean)`

## **APIs Removidas**

- Método `GoogleTokenProvider.getAccessToken()`
- Método `GoogleTokenProvider.getAccessToken(boolean)`
- Método `AppointmentMailMessageInterpretor.loadMessageHeader(MailMessage,MapiMessage)`
- Propriedade `GoogleTokenProvider.getClientId()`
- Propriedade `GoogleTokenProvider.getClientSecret()`
- Propriedade `GoogleTokenProvider.getRefreshToken()`