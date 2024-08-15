---
title: "Cambios en la API pública en Aspose.Email 5.1.0"
url: /es/java/public-api-changes-in-aspose-email-5-1-0/
weight: 120
type: docs
---

La siguiente es una lista de todos los cambios realizados en la API pública, como la adición, el cambio de nombre, la eliminación o la desaprobación de miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email for.NET. Si tienes dudas sobre algún cambio de la lista, comunícalo en el foro de soporte de Aspose.Email.

## **API añadidas**
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

## **API eliminadas**

- Method `GoogleTokenProvider.getAccessToken()`
- Method `GoogleTokenProvider.getAccessToken(boolean)`
- Method `AppointmentMailMessageInterpretor.loadMessageHeader(MailMessage,MapiMessage)`
- Property `GoogleTokenProvider.getClientId()`
- Property `GoogleTokenProvider.getClientSecret()`
- Property `GoogleTokenProvider.getRefreshToken()`
