---
title: "Cambios en la API Pública en Aspose.Email 5.1.0"
url: /es/java/cambios-en-la-api-publica-en-aspose-email-5-1-0/
weight: 120
type: docs
---

La siguiente es una lista de los cambios realizados en la API pública, como miembros añadidos, renombrados, eliminados o desaprobados, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para .NET. Si tiene preocupaciones sobre algún cambio listado, por favor infórmelo en el foro de soporte de Aspose.Email.

## **APIs Añadidas**
- Clase `BaseTokenProvider`
- Clase `OutlookTokenProvider`

- Método `HeaderCollection.getDecodedValue(String)`

- Método `BaseTokenProvider.getAccessToken()`
- Método `BaseTokenProvider.getAccessToken(boolean)`
- Método `OutlookTokenProvider.getInstance(String,String,String)`

- Propiedad `MailMessage.getHtmlBodyText`
- Propiedad `BaseTokenProvider.getClientId()`
- Propiedad `BaseTokenProvider.getClientSecret()`
- Propiedad `BaseTokenProvider.getRefreshToken()`
- Propiedad `MapiConversionOptions.getPreserveOriginalAddresses(), MapiConversionOptions.setPreserveOriginalAddresses(boolean)`

## **APIs Eliminadas**

- Método `GoogleTokenProvider.getAccessToken()`
- Método `GoogleTokenProvider.getAccessToken(boolean)`
- Método `AppointmentMailMessageInterpretor.loadMessageHeader(MailMessage,MapiMessage)`
- Propiedad `GoogleTokenProvider.getClientId()`
- Propiedad `GoogleTokenProvider.getClientSecret()`
- Propiedad `GoogleTokenProvider.getRefreshToken()`