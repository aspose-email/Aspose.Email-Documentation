---
title: "Функции утилиты — MailMessage"
url: /ru/net/utility-features-mailmessage/
weight: 50
type: docs
---


## **Шифрование и дешифрование сообщений**

Aspose.Email предоставляет возможность шифрования и дешифрования сообщений электронной почты с помощью сертификатов X509Certificates. В этой статье показано, как можно загрузить и зашифровать существующее или новое сообщение с помощью [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/encrypt/#encrypt/) and [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/decrypt/#decrypt/) методы возвращают [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) объект для примененных эффектов, о котором необходимо позаботиться при шифровании/расшифровке сообщений. Шифрование и дешифрование сообщений включает следующие шаги:

1. Создайте новое сообщение или загрузите существующее
1. Загрузите сертификат шифрования с помощью объекта X509Certificate
1. Зашифруйте сообщение с помощью сертификата
1. Отправьте сообщение или сохраните его
1. При необходимости расшифруйте сообщение

В следующем фрагменте кода показано, как шифровать и дешифровать сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}

### **Проверьте сообщение на шифрование**

Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс позволяет проверить, зашифровано ли сообщение или нет. [IsEncrypted ](https://reference.aspose.com/email/net/aspose.email/mailmessage/isencrypted/)собственность [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) позволяет проверить это, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}

## **Сообщения электронной почты, содержащие вложения TNEF**

Транспортный нейтральный формат инкапсуляции (TNEF) — это собственный формат вложений электронной почты, используемый Microsoft Outlook и Microsoft Exchange Server. API Aspose.Email позволяет читать сообщения электронной почты, содержащие вложения в формате TNEF, и изменять содержимое вложения. Затем письмо можно сохранить как обычное электронное письмо или в том же формате, сохранив вложения TNEF. В этой статье приведены различные примеры кода для работы с сообщениями, содержащими вложения в формате TNEF. В этой статье также показано, как создавать файлы TNEF EML из файлов Outlook MSG.

### **Прочитайте сообщение с сохранением вложений TNEF**

В следующем фрагменте кода показано, как прочитать сообщение с сохранением вложений в формате TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}

### **Чтение сообщения без сохранения вложений TNEF**

В следующем фрагменте кода показано, как прочитать сообщение без сохранения вложений в формате TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}

### **Обновление ресурсов во вложении TNEF и сохранение формата TNEF**

В следующем фрагменте кода показано, как обновить ресурсы во вложении TNEF и сохранить формат TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}

### **Добавление новых вложений к основному сообщению, содержащему TNEF**

В следующем фрагменте кода показано, как добавить новые вложения к основному сообщению, содержащему TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}

### **Создание EML TNEF из MSG**

Иногда файлы MSG Outlook содержат такую информацию, как таблицы и текстовые стили, которые могут быть нарушены при преобразовании в формат EML. Создание сообщений TNEF из таких файлов MSG позволяет сохранить форматирование и даже отправлять такие сообщения через почтовые клиенты с сохранением форматирования. [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/convertastnef/) свойство используется для достижения этой цели. В следующем фрагменте кода показано, как создать TNEF EML из MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}

Для создания TNEF можно использовать следующий пример кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}

### **Определите, соответствует ли сообщение TNEF**

В следующем фрагменте кода показано, как определить, является ли сообщение TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}

### **Проверьте, имеет ли вложение формат TNEF**

The [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/#attachmentistnef-property) свойство позволяет определить, является ли вложенное сообщение сообщением в формате TNEF.

```cs
var eml = MailMessage.Load(fileName);

foreach (attachment in eml.Attachments)
{
    Console.WriteLine($"Is Attachment TNEF?: {attachment.IsTnef}");
}
```

## **Обработка возвращенных сообщений**

Очень часто сообщение, отправленное получателю, может возвращаться по любой причине, например из-за неправильного адреса получателя. API Aspose.Email имеет возможность обрабатывать такое сообщение для проверки того, является ли оно отведенным письмом или обычным сообщением электронной почты. [CheckBounced](https://reference.aspose.com/email/net/aspose.email/mailmessage/checkbounced/#checkbounced) метод [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс возвращает действительный результат, если сообщение электронной почты было возвращено. В этой статье показано использование [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/) класс, который позволяет проверить, является ли сообщение возвращенным письмом. В нем также содержится подробная информация о получателях, предпринятых действиях и причине уведомления. В следующем фрагменте кода показано, как обрабатывать возвращенные сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckBouncedMessage-CheckBouncedMessage.cs" >}}


## **Байесовский анализатор спама**

Aspose.Email обеспечивает фильтрацию электронной почты с помощью байесовского спам-анализатора. Он предоставляет [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) класс для этой цели. В этой статье показано, как научить фильтр отличать спам от обычных писем на основе базы слов.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-BayesianSpamAnalyzer-BayesianSpamAnalyzer.cs" >}}

## **Получение преамбулы и эпилога из eml-сообщений**

Сообщение электронной почты может содержать скрытую информацию в виде обычного текста перед текстом сообщения (например, преамбула) или после текста (например, эпилог). Обычно это дополнительная информация или контекст, предоставляемые получателю до или после прочтения основного содержания письма. Вы можете получить эту информацию, используя [MailMessage.Preamble](https://reference.aspose.com/email/net/aspose.email/mailmessage/preamble/) or/and [MailMessage.Epilogue](https://reference.aspose.com/email/net/aspose.email/mailmessage/epilogue/#mailmessageepilogue-property) свойства соответственно.

В следующем фрагменте кода показано, как получить тексты преамбулы и эпилога:

```cs
// Gets or sets a preamble text.
public string Preamble

// Gets or sets an epilogue text.
public string Epilogue
```
