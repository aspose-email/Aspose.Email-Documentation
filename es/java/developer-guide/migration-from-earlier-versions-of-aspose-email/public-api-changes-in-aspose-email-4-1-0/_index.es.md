---
title: "Cambios en la API Pública en Aspose.Email 4.1.0"
url: /es/java/public-api-changes-in-aspose-email-4-1-0/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

La siguiente es una lista de cualquier cambio realizado en la API pública, como miembros [agregados](/email/java/public-api-changes-in-aspose-email-4-1-0/), renombrados, eliminados o miembros [obsoletos](/email/java/public-api-changes-in-aspose-email-4-1-0/), así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tiene inquietudes sobre algún cambio listado, por favor infórmelo en el foro de soporte de Aspose.Email.
## **Miembros de Enumeración Agregados**
### **Enumeración `MhtFormatOptions` con Miembros `WriteCompleteEmailAddressToMht` y `HideExtraPrintHeader`**

Proporciona control sobre si el encabezado superior es visible en la salida MHT. El método [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, Boolean writeCompleteEmailAddress)` está marcado como obsoleto. Use el método [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, int formatOptions)` en su lugar.
### **Miembro de Enumeración `MailMessageSaveOptions.HideExtraPrintHeader`**
El miembro de enumeración [`MailMessageSaveOptions`](https://apireference.aspose.com/email/java/com.aspose.email/SaveOptions)`.HideExtraPrintHeader` proporciona control sobre la visibilidad del encabezado superior en la salida MHT.

{{% /alert %}}