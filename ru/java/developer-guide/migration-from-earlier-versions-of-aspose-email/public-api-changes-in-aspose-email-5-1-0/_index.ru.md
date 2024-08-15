---
title: "Изменения в публичном API в Aspose.Email 5.1.0"
url: /ru/java/public-api-changes-in-aspose-email-5-1-0/
weight: 120
type: docs
---

Ниже приведен список любых изменений, внесенных в общедоступный API, таких как добавление, переименование, удаление или устаревание участников, а также любых изменений, не совместимых с обратной совместимостью, внесенных в Aspose.Email for .NET. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.

## **Добавлены API**
- Class `BaseTokenProvider`
- Class `OutlookTokenProvider`

- Method `HeaderCollection.getDecodedValue(String)`

- Method `BaseTokenProvider.getAccessToken()`
- Method `BaseTokenProvider.getAccessToken(boolean)`
- Method `OutlookTokenProvider.getInstance(String,String,String)`

- Property `MailMessage.getHtmlBodyText`
- Property `BaseTokenProvider.getClientId()`
- Property `BaseTokenProvider.getClientSecret()`
- Property `BaseTokenProvider.getRefreshToken()`
- Property `MapiConversionOptions.getPreserveOriginalAddresses(), MapiConversionOptions.setPreserveOriginalAddresses(boolean)`

## **Удаленные API**

- Method `GoogleTokenProvider.getAccessToken()`
- Method `GoogleTokenProvider.getAccessToken(boolean)`
- Method `AppointmentMailMessageInterpretor.loadMessageHeader(MailMessage,MapiMessage)`
- Property `GoogleTokenProvider.getClientId()`
- Property `GoogleTokenProvider.getClientSecret()`
- Property `GoogleTokenProvider.getRefreshToken()`
