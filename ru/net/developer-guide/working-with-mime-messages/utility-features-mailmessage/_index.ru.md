---
title: "Утилитные функции - MailMessage"
url: /ru/net/utility-features-mailmessage/
weight: 50
type: docs
---

## **Шифрование и расшифровка сообщений**

Aspose.Email предоставляет возможность шифровать и расшифровывать электронные сообщения с использованием X509Certificates. В этой статье показано, как существующее или новое сообщение может быть загружено и зашифровано с использованием [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Методы [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/encrypt/#encrypt/) и [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/decrypt/#decrypt/) возвращают объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) для примененных эффектов, и с ними нужно обращаться с осторожностью при шифровании/расшифровке сообщений. Шифрование и расшифровка сообщений включает в себя следующие шаги:

1. Создайте новое сообщение или загрузите существующее
1. Загрузите сертификат шифрования с использованием объекта X509Certificate
1. Зашифруйте сообщение с использованием сертификата
1. Отправьте сообщение или сохраните его
1. Расшифруйте сообщение по мере необходимости

Следующий фрагмент кода показывает, как шифровать и расшифровывать сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}

### **Проверка сообщения на шифрование**

Класс Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) позволяет проверить, зашифровано сообщение или нет. Свойство [IsEncrypted](https://reference.aspose.com/email/net/aspose.email/mailmessage/isencrypted/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) позволяет проверить это, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}

## **Электронные сообщения с TNEF-вложениями**

Формат транспортной нейтральной инкапсуляции (TNEF) является проприетарным форматом вложений электронной почты, используемым Microsoft Outlook и Microsoft Exchange Server. API Aspose.Email позволяет читать электронные сообщения, которые имеют TNEF-вложения, и изменять содержимое вложения. Электронное сообщение затем может быть сохранено как обычное электронное письмо или в том же формате, сохраняя TNEF-вложения. Эта статья показывает различные примеры кода для работы с сообщениями, содержащими TNEF-вложения. Эта статья также показывает, как создавать TNEF EML файлы из Outlook MSG файлов.

### **Чтение сообщения с сохранением TNEF-вложений**

Следующий фрагмент кода показывает, как читать сообщение, сохраняя TNEF-вложения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}

### **Чтение сообщения без сохранения TNEF-вложений**

Следующий фрагмент кода показывает, как читать сообщение без сохранения TNEF-вложений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}

### **Обновление ресурсов в TNEF-вложении и сохранение формата TNEF**

Следующий фрагмент кода показывает, как обновить ресурсы в TNEF-вложении и сохранить формат TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}

### **Добавление новых вложений в основное сообщение, содержащее TNEF**

Следующий фрагмент кода показывает, как добавить новые вложения в основное сообщение, содержащее TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}

### **Создание TNEF EML из MSG**

MSG-файлы Outlook иногда содержат информацию, такую как таблицы и текстовые стили, которые могут нарушаться при конвертации в EML. Создание TNEF-сообщений из таких MSG-файлов позволяет сохранить форматирование и даже отправить такие сообщения через почтовые клиенты, сохраняя форматирование. Свойство [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/convertastnef/) используется для достижения этого. Следующий фрагмент кода показывает, как создать TNEF EML из MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}

Для создания TNEF можно использовать следующий образец кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}

### **Определение, является ли сообщение TNEF**

Следующий фрагмент кода показывает, как определить, является ли сообщение TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}

### **Проверка, является ли вложение в формате TNEF**

Свойство [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/#attachmentistnef-property) позволяет определить, является ли вложение сообщения вложением, оформленным в формате TNEF.

```cs
var eml = MailMessage.Load(fileName);

foreach (attachment in eml.Attachments)
{
    Console.WriteLine($"Является ли вложение TNEF?: {attachment.IsTnef}");
}
```

## **Обработка возвратных сообщений**

Очень часто сообщение, отправленное получателю, может быть возвратным по любой причине, такой как неверный адрес получателя. API Aspose.Email имеет возможность обрабатывать такое сообщение для проверки, является ли оно возвратным письмом или обычным электронным сообщением. Метод [CheckBounced](https://reference.aspose.com/email/net/aspose.email/mailmessage/checkbounced/#checkbounced) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) возвращает допустимый результат, если электронное сообщение является возвратным письмом. Эта статья показывает использование класса [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/), который предоставляет возможность проверки, является ли сообщение возвратным письмом. Она также предоставляет детальную информацию о получателях, действиях и причинах уведомления. Следующий фрагмент кода показывает, как обрабатывать возвратные сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckBouncedMessage-CheckBouncedMessage.cs" >}}

## **Байесовский анализатор спама**

Aspose.Email предоставляет фильтрацию электронной почты с использованием байесовского анализатора спама. Для этой цели предоставляет класс [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/). Эта статья показывает, как обучить фильтр различать спам и обычные электронные письма на основе базы слов.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-BayesianSpamAnalyzer-BayesianSpamAnalyzer.cs" >}}

## **Получение преамбулы и эпилога из сообщений EML**

Электронное сообщение может содержать некоторую скрытую информацию в виде обычного текста перед телом сообщения (т.е. преамбула) или после тела (т.е. эпилог). Обычно это какая-то дополнительная информация или контекст для получателя до или после того, как они прочитают основное содержимое электронной почты. Вы можете получить эту информацию с помощью свойств [MailMessage.Preamble](https://reference.aspose.com/email/net/aspose.email/mailmessage/preamble/) или/и [MailMessage.Epilogue](https://reference.aspose.com/email/net/aspose.email/mailmessage/epilogue/#mailmessageepilogue-property) соответственно.

Следующий фрагмент кода показывает, как получить тексты преамбулы и эпилога:

```cs
// Получает или задает текст преамбулы.
public string Preamble

// Получает или задает текст эпилога.
public string Epilogue
```