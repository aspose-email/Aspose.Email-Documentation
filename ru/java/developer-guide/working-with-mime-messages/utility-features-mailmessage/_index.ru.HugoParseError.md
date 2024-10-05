---  
title: Утилитарные функции - MailMessage  
type: docs  
weight: 50  
url: /java/utility-features-mailmessage/  
---  
  
## **Шифрование и дешифрование сообщений**  
  
Aspose.Email предоставляет возможность шифрования и дешифрования электронных писем. Эта тема демонстрирует, как загружать и шифровать существующее или новое сообщение с использованием [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Методы [encrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) и [decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt--) возвращают объект **MailMessage** для примененных эффектов, с которыми нужно быть осторожным при шифровании/дешифровании сообщений. Шифрование и дешифрование сообщений включает в себя следующие шаги:  
  
1. Создайте новое сообщение или загрузите существующее  
2. Зашифруйте сообщение с использованием файла сертификата  
3. Отправьте сообщение или сохраните его  
4. Дешифруйте сообщение по необходимости  
  
Следующий фрагмент кода демонстрирует, как зашифровать и дешифровать сообщения.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.java" >}}  
  
### **Проверка сообщения на предмет шифрования**  
  
Класс Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) позволяет проверить сообщение на предмет того, зашифровано оно или нет. Свойство [isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isEncrypted--) объекта **MailMessage** позволяет делать это, как показано в следующем фрагменте кода.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CheckMessageForEncryption-CheckMessageForEncryption.java" >}}  
  
## **Шифрование сообщений с использованием X509Certificate**  
  
Aspose.Email предоставляет API для работы с зашифрованными сообщениями с использованием X509Certificate:  
  
Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) имеет следующие методы для работы с шифрованием сообщений:  
  
- public MailMessage [attachSignature(X509Certificate2 certificate, boolean detached)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-boolean-) - Создает подписанное сообщение.  
- public MailMessage [attachSignature(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Создает подписанное сообщение.  
- public X509Certificate2[] [checkSignatureCert()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkSignatureCert--) - Проверяет подпись существующего MailMessage.  
- public MailMessage [decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)  
- public MailMessage [encrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)  
- public MailMessage [encrypt(X509Certificate2[] certificates)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2---)  
  
## **Настройка параметров локали для Aspose.Email**  
  
Вы можете использовать класс [LocaleOptions](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/) в случае неназнанной локали по умолчанию и установить наиболее подходящую локаль для библиотеки Aspose Email. Она предлагает следующие методы для выполнения этой задачи:  
  
- [getLocale()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#getLocale--) - Возвращает локаль по умолчанию для Aspose.Email.  
- [setLocale(Locale locale)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.util.Locale-) и [setLocale(String localeName)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.lang.String-) - Устанавливает локаль по умолчанию для Aspose.Email.  
- [clear()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#clear--) - Очищает локаль по умолчанию для Aspose.Email. Будет использоваться локаль по умолчанию для Java.  

Следующий фрагмент кода демонстрирует, как загрузить сообщение электронной почты из файла с использованием указанных параметров локали:  
  
```java  
final Locale locale = new Locale("en", "DE");  
Locale.setDefault(locale);  
  
// Установить локаль для библиотеки Aspose Email  
LocaleOptions.setLocale("en-US");  
// или  
//LocaleOptions.setLocale(new Locale("en", "US"));  
  
MailMessage.load("document.msg");  
```  
Этот код гарантирует, что приложение и библиотека Aspose.Email используют указанные локали для обработки языка, страны и культурных традиций.  
  
## **MailMessages, содержащие TNEF-вложения**  
  
Формат транспортного нейтрального инкапсулирования (TNEF) - это проприетарный формат вложений электронной почты, используемый Microsoft Outlook и Microsoft Exchange Server. API Aspose.Email позволяет читать электронные сообщения с TNEF-вложениями и изменять их содержимое. Затем электронное письмо может быть сохранено как обычное электронное письмо или в том же формате, сохраняя TNEF-вложения. Эта статья демонстрирует различные примеры кода для работы с сообщениями, содержащими TNEF-вложения.  
  
### **Чтение сообщения с сохранением TNEF-вложений**  
  
Следующий фрагмент кода демонстрирует, как читать сообщение, сохраняя TNEF-вложения.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.java" >}}  
  
### **Обновление ресурсов в TNEF-вложении и сохранение формата TNEF**  
  
Следующий фрагмент кода демонстрирует, как обновить ресурсы в TNEF-вложении и сохранить формат TNEF.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-UpdateTNEFAttachments-UpdateTNEFAttachments.java" >}}  
  
### **Добавление новых вложений в основное сообщение, содержащее TNEF**  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-AddNewAttachmentToMessageContainingTNEF.java" >}}  
  
### **Создание TNEF EML из MSG**  
  
Outlook MSG иногда содержит информацию, такую как таблицы и текстовые стили, которые могут быть нарушены, если их преобразовать в EML. Создание TNEF-сообщений из таких файлов MSG позволяет сохранить форматирование и даже отправить такие сообщения через почтовые клиенты, сохраняя форматирование.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreatingTNEFEMLFromMSG.java" >}}  
  
Чтобы создать TNEF, можно использовать следующий образец кода.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreateTNEF.java" >}}  
  
### **Определение, является ли сообщение TNEF**  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-DetectIfAMessageIsTNEF.java" >}}  
  
## **Обработка отклоненных сообщений**  
  
Довольно часто сообщение, отправленное получателю, может быть возвращено по любой причине, такой как некорректный адрес получателя. API Aspose.Email имеет возможность обрабатывать такое сообщение, проверяя, является ли оно отклоненной электронной почтой или обычным электронным сообщением. Метод [CheckBounced](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkBounced--) класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) возвращает действительный результат, если электронное сообщение является отклоненной электронной почтой.  
  
Эта статья демонстрирует использование класса [BounceResult](https://reference.aspose.com/email/java/com.aspose.email/bounceresult/), который предоставляет возможность проверять, является ли сообщение отклоненной электронной почтой. Она также предоставляет подробную информацию о получателях, предпринятых действиях и причине уведомления.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ProcessBouncedMessages-.java" >}}  
  
## **Игнорировать исключения**  
  
Библиотека предлагает класс [ExceptionManager](https://reference.aspose.com/email/java/com.aspose.email/exceptionmanager/) для реализации возможности игнорирования исключений в функциональности вашего приложения. Следующий фрагмент кода демонстрирует, как установить обратный вызов для обработки исключений:  
  
```java  
 ExceptionManager.setIgnoreExceptionsHandler( new IgnoreExceptionsCallback() {  
  
   //путь к исключению: {Module}\{Method}\{Action}\{GUID}  
  
   //пример: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598  
  
   public boolean invoke(AsposeException ex, String path) {  
  
       //Игнорировать все исключения на MailMessage.Load  
  
       return path.equals("MailMessage\\Load");  
  
   }  
  
});  
```  
Или используйте **альтернативу**:  
  
```java  
 ExceptionManager.setIgnoreAll(true);  
```  
Кроме того, вы можете установить обратный вызов для журнала игнорируемых **исключений**:  
  
```java  
ExceptionManager.setIgnoreExceptionsLogHandler( new IgnoreExceptionsLogCallback() {  
  
   public void invoke(String message) {  
  
        System.out.println("=== ИСКЛЮЧЕНИЕ ИГНОРИРОВАНО === " + message);  
  
   }  
  
});  
```  
Пользователь будет уведомлен, что исключение можно игнорировать, с помощью сообщения об ошибке. Например:  
  
Исключение в сообщении:  
  
```java  
AsposeArgumentException: свойства не должны быть пустыми.  
```  
  
Если вы хотите игнорировать исключение и продолжить выполнение, то вы можете использовать:  
```java  
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")  
  
Недопустимое TNEF-вложение будет интерпретировано как обычное вложение.  
```  
  
## **Байесовский анализатор спама**  
  
Aspose.Email предоставляет возможность фильтрации электронной почты с использованием байесовского анализатора спама. Для этой цели он предоставляет класс [SpamAnalyzer](https://reference.aspose.com/email/java/com.aspose.email/spamanalyzer/). Эта статья показывает, как обучить фильтр, чтобы различать спам и обычные электронные письма на основе базы слов.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-BayesianSpamAnalyzer-.java" >}}  
  
## **Получение преамбулы и эпилога из EML-сообщений**  
  
В формате MIME *преамбула* - это текст, который появляется после заголовков и перед первой многочастной границей. *Эпилог* - это текст, который появляется после последней границы и перед концом сообщения. Этот текст обычно не виден пользователям в почтовых клиентах, но некоторые реализации MIME могут использовать его для вставки заметок для получателей, читающих сообщение с помощью программ, не соответствующих стандартам MIME.  
  
Следующий фрагмент кода показывает, как получить преамбулу и эпилог из EML-сообщения, что можно сделать с помощью соответствующих методов класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/):  
  
- [setPreamble(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setPreamble-java.lang.String-) - Устанавливает или получает текст преамбулы.  
- [setEpilogue(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setEpilogue-java.lang.String-) - Устанавливает или получает текст эпилога.  
  
```java  
// Устанавливает или получает текст преамбулы.  
public String getPreamble, setPreamble  
  
// Устанавливает или получает текст эпилога.  
public String getEpilogue, setEpilogue  
```  