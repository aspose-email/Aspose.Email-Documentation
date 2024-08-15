---
title: "Функции утилиты — MailMessage"
url: /ru/java/utility-features-mailmessage/
weight: 50
type: docs
---

## **Шифрование и дешифрование сообщений**

Aspose.Email предоставляет возможность шифрования и дешифрования сообщений электронной почты. В этом разделе показано, как можно загрузить и зашифровать существующее или новое сообщение с помощью [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). [encrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) and [decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt--) методы возвращают **MailMessage** объект для примененных эффектов, о котором необходимо позаботиться при шифровании/дешифровании сообщений. Шифрование и дешифрование сообщений включает следующие шаги:

1. Создайте новое сообщение или загрузите существующее
2. Зашифруйте сообщение с помощью файла сертификата
3. Отправьте сообщение или сохраните его
4. При необходимости расшифруйте сообщение

В следующем фрагменте кода показано, как шифровать и дешифровать сообщения.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.java" >}}

### **Проверка сообщения на шифрование**

Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) класс позволяет проверить сообщение, зашифровано оно или нет. [isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isEncrypted--) собственность **MailMessage** позволяет проверить это, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CheckMessageForEncryption-CheckMessageForEncryption.java" >}}

## **Шифрование сообщений с помощью сертификата X509**

Aspose.Email предоставляет API для работы с зашифрованными сообщениями с помощью X509Certificate:

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс имеет следующие методы для работы с шифрованием сообщений:

- публичное почтовое сообщение [Прикрепить подпись (сертификат X509 Certificate2, отдельное логическое значение)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-boolean-) - Создает подписанное сообщение.
- публичное почтовое сообщение [Прикрепите подпись (сертификат X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Создает подписанное сообщение.
- публичный сертификат X509 [2] [checkSignatureCert()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkSignatureCert--) - Проверяет подпись существующего MailMessage.
- публичное почтовое сообщение [расшифровать (сертификат X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- публичное почтовое сообщение [зашифровать (сертификат X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- публичное почтовое сообщение [зашифровать (сертификат X509 2 [] сертификата)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2---)


## **Настройка параметров локали для Aspose.Email**

Вы можете использовать [LocaleOptions](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/) класс в случае нераспознанной локали по умолчанию и установите наиболее подходящую локаль для Aspose Email lib. Он предлагает следующие методы выполнения задачи:

- [getLocale()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#getLocale--) - Возвращает локаль по умолчанию для Aspose.Email.
- [setLocale (локальная локаль)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.util.Locale-) and [SetLocale (строковое локальное имя)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.lang.String-) - Установите локаль по умолчанию, связанную с Aspose.Email.
- [clear()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#clear--) - Очищает локаль по умолчанию для Aspose.Email. Будет использоваться локаль по умолчанию для Java.

В следующем примере кода показано, как загрузить почтовое сообщение из файла, используя указанные настройки локали:

```java
final Locale locale = new Locale("en", "DE");
Locale.setDefault(locale);

// set Locale for Aspose Email lib
LocaleOptions.setLocale("en-US");
// or
//LocaleOptions.setLocale(new Locale("en", "US"));

MailMessage.load("document.msg");
```
Этот код гарантирует, что приложение и библиотека Aspose.Email используют указанные локали для обработки языковых, национальных и культурных конвенций.

## **Почтовые сообщения, содержащие вложения в формате TNEF**

Транспортный нейтральный формат инкапсуляции (TNEF) — это собственный формат вложений электронной почты, используемый Microsoft Outlook и Microsoft Exchange Server. API Aspose.Email позволяет читать сообщения электронной почты, содержащие вложения в формате TNEF, и изменять их содержимое. Затем письмо можно сохранить как обычное электронное письмо или в том же формате, сохранив вложения в формате TNEF. В этой статье приведены различные примеры кода для работы с сообщениями, содержащими вложения в формате TNEF.

### **Чтение сообщения путем сохранения вложений TNEF**

В следующем фрагменте кода показано, как прочитать сообщение, сохранив вложения в формате TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.java" >}}

### **Обновление ресурсов во вложении TNEF и сохранение формата TNEF**

В следующем фрагменте кода показано, как обновить ресурсы во вложении TNEF и сохранить формат TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-UpdateTNEFAttachments-UpdateTNEFAttachments.java" >}}

### **Добавление новых вложений к основному сообщению, содержащему TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-AddNewAttachmentToMessageContainingTNEF.java" >}}

### **Создание EML TNEF из MSG**

Иногда файлы MSG Outlook содержат такую информацию, как таблицы и текстовые стили, которые могут быть нарушены при преобразовании в формат EML. Создание сообщений TNEF из таких файлов MSG позволяет нам сохранять форматирование и даже отправлять такие сообщения через почтовые клиенты с сохранением форматирования. 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreatingTNEFEMLFromMSG.java" >}}

Для создания TNEF можно использовать следующий пример кода.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreateTNEF.java" >}}

### **Определите, соответствует ли сообщение TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-DetectIfAMessageIsTNEF.java" >}}

## **Обработка возвращенных сообщений**

Очень часто сообщение, отправленное получателю, может возвращаться по любой причине, например из-за неправильного адреса получателя. API Aspose.Email имеет возможность обрабатывать такое сообщение для проверки того, является ли оно отведенным письмом или обычным сообщением электронной почты. [CheckBounced](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkBounced--) метод [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс возвращает действительный результат, если сообщение электронной почты было возвращено.

В этой статье показано использование [BounceResult](https://reference.aspose.com/email/java/com.aspose.email/bounceresult/) класс, который позволяет проверить, является ли сообщение возвращенным письмом. В нем также содержится подробная информация о получателях, предпринятых действиях и причине уведомления.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ProcessBouncedMessages-.java" >}}

## **Игнорировать исключения**

Библиотека предлагает [ExceptionManager](https://reference.aspose.com/email/java/com.aspose.email/exceptionmanager/) класс для реализации возможности игнорирования исключений в функциональность вашего приложения. В приведенном ниже фрагменте кода показано, как настроить обратный вызов для обработки исключений:

```java
 ExceptionManager.setIgnoreExceptionsHandler( new IgnoreExceptionsCallback() {

   //exception path: {Module}\{Method}\{Action}\{GUID}

   //example: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598

   public boolean invoke(AsposeException ex, String path) {

       //Ignore all exceptions on MailMessage.Load

       return path.equals("MailMessage\\Load");

   }

});
```
Или используйте **alternative**:

```java
 ExceptionManager.setIgnoreAll(true);
```
Кроме того, вы можете установить обратный вызов для игнорируемых **журнал исключений**:

```java
ExceptionManager.setIgnoreExceptionsLogHandler( new IgnoreExceptionsLogCallback() {

   public void invoke(String message) {

        System.out.println("=== EXCEPTION IGNORED === " + message);

   }

});
```
Пользователь будет уведомлен о том, что исключение может быть проигнорировано сообщением об ошибке. Например:

Исключение в сообщении:

```java
AsposeArgumentException: properties should not be empty.
```

Если вы хотите проигнорировать исключение и продолжить, вы можете использовать:
```java
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")

Invalid TNEF Attachment will be interpreted as regular attachment.
```

## **Байесовский анализатор спама**

Aspose.Email предоставляет возможность фильтрации электронной почты с помощью анализатора спама Bayes. Он предоставляет [SpamAnalyzer](https://reference.aspose.com/email/java/com.aspose.email/spamanalyzer/) класс для этой цели. В этой статье показано, как научить фильтр отличать спам от обычных писем на основе базы слов.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-BayesianSpamAnalyzer-.java" >}}

## **Получение преамбулы и эпилога из сообщений EML**

В формате MIME *preamble* это текст, который появляется после заголовков и перед первой составной границей. *epilogue* это текст, который появляется после последней границы и перед концом сообщения. Этот текст обычно не виден пользователям в программах чтения почты, но в некоторых реализациях MIME он может использоваться для вставки заметок получателям, прочитавшим сообщение с помощью программ, не совместимых с MIME.

В следующем фрагменте кода показано, как получить преамбулу и эпилог из сообщения EML, что может быть достигнуто с помощью соответствующих методов [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class:

- [setPreamble (строковое значение)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setPreamble-java.lang.String-) - Получает или задает текст преамбулы.
- [setEpiLogue (строковое значение)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setEpilogue-java.lang.String-) - Получает или задает текст эпилога.

```java
// Gets or sets a preamble text.
public String getPreamble, setPreamble

// Gets or sets an epilogue text.
public String getEpilogue, setEpilogue
```

