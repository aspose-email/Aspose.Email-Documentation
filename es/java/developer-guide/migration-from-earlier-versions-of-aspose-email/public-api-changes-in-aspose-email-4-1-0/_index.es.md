---
title: "Cambios en la API pública en Aspose.Email 4.1.0"
url: /es/java/public-api-changes-in-aspose-email-4-1-0/
weight: 30
type: docs
---

{{% alert color="primary" %}}

La siguiente es una lista de los cambios realizados en la API pública, como [added](/email/java/public-api-changes-in-aspose-email-4-1-0/), renombrado, eliminado o [deprecated](/email/java/public-api-changes-in-aspose-email-4-1-0/) miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tiene dudas sobre algún cambio de la lista, hágalo saber en el foro de soporte de Aspose.Email.
## **Miembros de enumeración agregados**
### **`MhtFormatOptions` Enumeración con miembros `WriteCompleteEmailAddressToMht` and `HideExtraPrintHeader`**

Permite controlar si el encabezado superior está visible en la salida MHT. El [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, Boolean writeCompleteEmailAddress)` el método está marcado como obsoleto. Usa el [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, int formatOptions)` método en su lugar.
### **`MailMessageSaveOptions.HideExtraPrintHeader` Miembro de enumeración**
The [`MailMessageSaveOptions`](https://apireference.aspose.com/email/java/com.aspose.email/SaveOptions)`.HideExtraPrintHeader` El miembro de enumeración proporciona el control de la visibilidad del encabezado superior en la salida MHT.

{{% /alert %}}
