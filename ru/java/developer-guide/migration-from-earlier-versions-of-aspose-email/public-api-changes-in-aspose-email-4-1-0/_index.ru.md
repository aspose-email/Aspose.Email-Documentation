---
title: "Изменения в публичном API в Aspose.Email 4.1.0"
url: /ru/java/public-api-changes-in-aspose-email-4-1-0/
weight: 30
type: docs
---

{{% alert color="primary" %}}

Ниже приведен список любых изменений, внесенных в общедоступный API, таких как: [added](/email/java/public-api-changes-in-aspose-email-4-1-0/), переименован, удален или [deprecated](/email/java/public-api-changes-in-aspose-email-4-1-0/) участников, а также любые изменения, не совместимые с обратной совместимостью, внесенные в Aspose.Email для Java. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.
## **Добавлены участники перечисления**
### **`MhtFormatOptions` Перечисление с участием членов `WriteCompleteEmailAddressToMht` and `HideExtraPrintHeader`**

Обеспечивает контроль того, отображается ли верхний заголовок в выходных данных MHT. [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, Boolean writeCompleteEmailAddress)` метод отмечен как устаревший. Используйте [`MhtMessageFormatter`](https://apireference.aspose.com/email/java/com.aspose.email/MhtFormatOptions)`.format(`[`MailMessage`](https://apireference.aspose.com/email/java/com.aspose.email.class-use/MailMessage) `message, int formatOptions)` вместо этого метод.
### **`MailMessageSaveOptions.HideExtraPrintHeader` Участник переписи**
The [`MailMessageSaveOptions`](https://apireference.aspose.com/email/java/com.aspose.email/SaveOptions)`.HideExtraPrintHeader` элемент перечисления обеспечивает управление видимостью верхнего заголовка в выходных данных MHT.

{{% /alert %}}
