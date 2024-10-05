---
title: "Изменения в публичном API Aspose.Email 4.1.0"
url: /ru/java/public-api-changes-in-aspose-email-4-1-0/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Ниже приведен список изменений, внесенных в публичный API, таких как [добавленные](/email/java/public-api-changes-in-aspose-email-4-1-0/), переименованные, удаленные или [устаревшие](/email/java/public-api-changes-in-aspose-email-4-1-0/) элементы, а также любые изменения, несовместимые с предыдущими версиями в Aspose.Email для Java. Если у вас есть вопросы по любому из перечисленных изменений, пожалуйста, поднимите их на форуме поддержки Aspose.Email.
## **Добавленные члены перечисления**
### **`MhtFormatOptions` перечисление с членами `WriteCompleteEmailAddressToMht` и `HideExtraPrintHeader`**

Предоставляет контроль над видимостью верхнего заголовка в выходных данных MHT. Метод [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, Boolean writeCompleteEmailAddress)` помечен как устаревший. Вместо этого используйте метод [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, int formatOptions)`.
### **Член перечисления `MailMessageSaveOptions.HideExtraPrintHeader`**
Член перечисления [`MailMessageSaveOptions`](https://apireference.aspose.com/email/java/com.aspose.email/SaveOptions)`.HideExtraPrintHeader` предоставляет контроль над видимостью верхнего заголовка в выходных данных MHT.

{{% /alert %}}