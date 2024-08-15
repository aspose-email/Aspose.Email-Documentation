---
title: "Управление сообщениями с цифровой подписью"
url: /ru/java/working-with-outlook-notes/
weight: 100
type: docs
---

Aspose.Email реализует полный алгоритм объекта электронной почты S/MIME. Это дает API полную возможность добавлять цифровые подписи к сообщениям электронной почты, сохранять их при преобразовании сообщений между форматами, удалять их и т. д.

## **Прикрепите подпись к электронному письму**

The [SecureEmailManager.attachSignature](https://reference.aspose.com/email/java/com.aspose.email/secureemailmanager/#attachSignature-com.aspose.email.MapiMessage-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-com.aspose.email.SignatureOptions-) метод позволяет прикреплять цифровые подписи к сообщениям электронной почты. После прикрепления подписи проверьте результаты с помощью таких свойств, как [IsSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--), [MessageClass](https://reference.aspose.com/email/java/com.aspose.email/knownpropertylist/#MESSAGE-CLASS), а также сведения о креплении.

Вы можете предоставить MailMessage или MapiMessage, частный сертификат и параметры подписи, чтобы настроить процесс вложения подписи с помощью [SignatureOptions](https://reference.aspose.com/email/java/com.aspose.email/signatureoptions/) класс, который позволяет пользователям указывать различные параметры вложения подписи, включая отдельные или неотделимые подписи.

В следующем примере кода показано, как загрузить сообщение из файла, прикрепить отсоединенную и неотделимую цифровую подпись с помощью частного сертификата, а затем проверить, успешно ли прикреплены подписи.

```java
String fileName = "message.msg";
String privateCertFile = "certFile.pfx";
X509Certificate2 privateCert = new X509Certificate2(privateCertFile, "password");

MapiMessage msg = MapiMessage.load(fileName);

SignatureOptions opt = new SignatureOptions();
opt.setDetached(true);
MapiMessage signedDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedDetached.isSigned()) {
    System.out.println("Detached Signature Attached Successfully.");
}

opt.setDetached(false);
MapiMessage signedNonDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedNonDetached.isSigned()) {
    System.out.println("Non-Detached Signature Attached Successfully.");
}
```

## **Сохранение подписи при преобразовании из EML в MSG**

Aspose.Email сохраняет цифровую подпись при преобразовании из EML в MSG. В следующем фрагменте кода показано, как конвертировать из EML в MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Load mail message
MailMessage message = MailMessage.load(dataDir + "Message.eml", new EmlLoadOptions());
// Save as MSG
message.save(dataDir + "ConvertEMLToMSG_out.msg", SaveOptions.getDefaultMsgUnicode());
~~~
## **Удалить подпись из файла сообщений Outlook**

Если вы столкнулись с необходимостью удалить подпись из сообщения в формате MAPI, например, в целях совместимости, Aspose.Email предлагает [MapiMessage.removeSignature](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#removeSignature--) метод и [MapiMessage.isSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--) property.

В следующем фрагменте кода показано, как загрузить сообщение MAPI из файла, проверить, подписано ли оно цифровой подписью, и, если да, создать новое сообщение без цифровой подписи:

```java
MapiMessage msg = MapiMessage.load(fileName);

if (msg.isSigned()) {
    MapiMessage unsignedMsg = msg.removeSignature();
}
```
## **Преобразование сообщений S/MIME из MSG в EML**

Aspose.Email сохраняет цифровую подпись при преобразовании из MSG в EML, как показано в следующем фрагменте кода.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage msg = MailMessage.load(dataDir + "message.eml");
MapiMessage mapi = MapiMessage.fromMailMessage(msg, new MapiConversionOptions(OutlookMessageFormat.Unicode));
// Save File to disk
mapi.save(dataDir + "ConvertMIMEMessagesFromMSGToEML_out.msg");
~~~

## **Расшифруйте файл MSG с помощью сертификата**

Если у вас есть зашифрованные сообщения MAPI и вам нужно расшифровать их с помощью закрытого ключа, хранящегося в сертификате, вам могут пригодиться следующие функции Aspose.Email:

- [MapiMessage.isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isEncrypted--) - Получает значение, указывающее, зашифровано ли сообщение.
- [MapiMessage.decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt--) - Расшифровывает это сообщение (метод ищет у текущего пользователя и компьютера My stores соответствующий сертификат и закрытый ключ).
- [Сообщение MAPI. Расшифровка (сертификат X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Расшифровывает это сообщение с помощью сертификата.

В следующем фрагменте кода показано, как работать с зашифрованными сообщениями MAPI:

```java
X509Certificate2 privateCert = new X509Certificate2("privateCertFile", "password");
MapiMessage msg = MapiMessage.load("encrypted.msg");

if (msg.isEncrypted()) {
    MapiMessage decryptedMsg = msg.decrypt(privateCert);
    //MapiMessage decryptedMsg = msg.decrypt(/*byte[]*/rawPrivateCert, "password");
}
```
