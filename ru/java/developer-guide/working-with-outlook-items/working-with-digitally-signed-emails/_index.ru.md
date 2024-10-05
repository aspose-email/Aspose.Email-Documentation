---
title: "Управление цифровыми подписями сообщений"
url: /ru/java/working-with-outlook-notes/
weight: 100
type: docs
---

Aspose.Email реализует полный алгоритм объекта электронной почты S/MIME. Это дает API полную возможность добавлять цифровые подписи к электронным сообщениям, сохранять их при конвертации сообщений между форматами, удалять их и т.д.

## **Прикрепить подпись к электронному сообщению**

Метод [SecureEmailManager.attachSignature](https://reference.aspose.com/email/java/com.aspose.email/secureemailmanager/#attachSignature-com.aspose.email.MapiMessage-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-com.aspose.email.SignatureOptions-) позволяет прикреплять цифровые подписи к электронным сообщениям. После прикрепления подписи проверьте результаты через такие свойства, как [IsSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--), [MessageClass](https://reference.aspose.com/email/java/com.aspose.email/knownpropertylist/#MESSAGE-CLASS) и детали вложения.

Вы можете предоставить MailMessage или MapiMessage, приватный сертификат и параметры подписи, чтобы настроить процесс прикрепления подписи с помощью класса [SignatureOptions](https://reference.aspose.com/email/java/com.aspose.email/signatureoptions/), который позволяет пользователям задавать различные параметры для прикрепления подписи, включая отделенные или неотделенные подписи.

Следующий пример кода покажет вам, как загрузить сообщение из файла, прикрепить отделенную и неотделенную цифровую подпись с использованием приватного сертификата, а затем проверить, были ли подписи успешно прикреплены.

```java
String fileName = "message.msg";
String privateCertFile = "certFile.pfx";
X509Certificate2 privateCert = new X509Certificate2(privateCertFile, "password");

MapiMessage msg = MapiMessage.load(fileName);

SignatureOptions opt = new SignatureOptions();
opt.setDetached(true);
MapiMessage signedDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedDetached.isSigned()) {
    System.out.println("Отделенная подпись успешно прикреплена.");
}

opt.setDetached(false);
MapiMessage signedNonDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedNonDetached.isSigned()) {
    System.out.println("Неотделенная подпись успешно прикреплена.");
}
```

## **Сохранение подписи при конвертации из EML в MSG**

Aspose.Email сохраняет цифровую подпись при конвертации из EML в MSG. Следующий фрагмент кода показывает, как конвертировать из EML в MSG.

~~~Java
// Для полного примера и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "outlook/";

// Загрузка электронного сообщения
MailMessage message = MailMessage.load(dataDir + "Message.eml", new EmlLoadOptions());
// Сохранение как MSG
message.save(dataDir + "ConvertEMLToMSG_out.msg", SaveOptions.getDefaultMsgUnicode());
~~~
## **Удаление подписи из файла сообщения Outlook**

Если вам необходимо удалить подпись из сообщения в формате MAPI, например, для обеспечения совместимости, Aspose.Email предлагает метод [MapiMessage.removeSignature](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#removeSignature--) и свойство [MapiMessage.isSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--).

Следующий фрагмент кода показывает, как загрузить сообщение MAPI из файла, проверить, имеет ли оно цифровую подпись, и, если да, создать новое сообщение без цифровой подписи:

```java
MapiMessage msg = MapiMessage.load(fileName);

if (msg.isSigned()) {
    MapiMessage unsignedMsg = msg.removeSignature();
}
```
## **Конвертация S/MIME сообщений из MSG в EML**

Aspose.Email сохраняет цифровую подпись при конвертации из MSG в EML, как показано в следующем фрагменте кода.

~~~Java
// Для полного примера и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "outlook/";

MailMessage msg = MailMessage.load(dataDir + "message.eml");
MapiMessage mapi = MapiMessage.fromMailMessage(msg, new MapiConversionOptions(OutlookMessageFormat.Unicode));
// Сохранение файла на диск
mapi.save(dataDir + "ConvertMIMEMessagesFromMSGToEML_out.msg");
~~~

## **Расшифровка файла MSG с помощью сертификата**

Если у вас есть зашифрованные сообщения MAPI и необходимо расшифровать их, используя приватный ключ, хранящийся в сертификате, следующие функции Aspose.Email могут быть полезны:

- [MapiMessage.isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isEncrypted--) - Получает значение, указывающее, зашифровано ли сообщение.
- [MapiMessage.decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt--) - Расшифровывает это сообщение (метод ищет соответствующий сертификат и приватный ключ текущего пользователя и компьютера в хранилищах My).
- [MapiMessage.decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Расшифровывает это сообщение с использованием сертификата.

Следующий фрагмент кода показывает, как работать с зашифрованными сообщениями MAPI:

```java
X509Certificate2 privateCert = new X509Certificate2("privateCertFile", "password");
MapiMessage msg = MapiMessage.load("encrypted.msg");

if (msg.isEncrypted()) {
    MapiMessage decryptedMsg = msg.decrypt(privateCert);
    //MapiMessage decryptedMsg = msg.decrypt(/*byte[]*/rawPrivateCert, "password");
}
```