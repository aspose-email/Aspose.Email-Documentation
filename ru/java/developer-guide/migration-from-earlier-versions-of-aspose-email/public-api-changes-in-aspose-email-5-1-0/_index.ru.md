---
title: "Изменения в публичном API в Aspose.Email 5.1.0"
url: /ru/java/public-api-changes-in-aspose-email-5-1-0/
weight: 120
type: docs
---

Следующий список содержит изменения в публичном API, включая добавленные, переименованные, удаленные или устаревшие элементы, а также любые несовместимые изменения в Aspose.Email для .NET. Если у вас есть вопросы по любому из перечисленных изменений, пожалуйста, задайте их на форуме поддержки Aspose.Email.

## **Добавленные API**
- Класс `BaseTokenProvider`
- Класс `OutlookTokenProvider`

- Метод `HeaderCollection.getDecodedValue(String)`

- Метод `BaseTokenProvider.getAccessToken()`
- Метод `BaseTokenProvider.getAccessToken(boolean)`
- Метод `OutlookTokenProvider.getInstance(String,String,String)`

- Свойство `MailMessage.getHtmlBodyText`
- Свойство `BaseTokenProvider.getClientId()`
- Свойство `BaseTokenProvider.getClientSecret()`
- Свойство `BaseTokenProvider.getRefreshToken()`
- Свойство `MapiConversionOptions.getPreserveOriginalAddresses(), MapiConversionOptions.setPreserveOriginalAddresses(boolean)`

## **Удаленные API**

- Метод `GoogleTokenProvider.getAccessToken()`
- Метод `GoogleTokenProvider.getAccessToken(boolean)`
- Метод `AppointmentMailMessageInterpretor.loadMessageHeader(MailMessage,MapiMessage)`
- Свойство `GoogleTokenProvider.getClientId()`
- Свойство `GoogleTokenProvider.getClientSecret()`
- Свойство `GoogleTokenProvider.getRefreshToken()`