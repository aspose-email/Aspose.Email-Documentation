---
title: "Утилитарные функции - SMTP клиент"
url: /ru/java/utility-features-smtp-client/
weight: 30
type: docs
---


## **Получение расширений сервера с использованием SmtpClient**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) позволяет извлечь поддерживаемые сервером расширения, такие как IDLE, UNSELECT, QUOTA и т.д. Это помогает определить доступность расширения перед использованием клиента для этой конкретной функции. Метод [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getCapabilities--) возвращает поддерживаемые типы расширений в виде массива строк.

### **Извлечение расширений сервера**

Следующий фрагмент кода показывает, как извлечь расширения сервера.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com",587,"username","password");
client.setSecurityOptions(SecurityOptions.Auto);
String[] caps = client.getCapabilities();
for (String str:caps)
	System.out.println(str);
~~~

## **Работа с подписанным сообщением**

API Aspose.Email предоставляет возможность создания подписанных сообщений с использованием сертификатов. Метод [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) может быть использован для подписи сообщения для сохранения или даже отправки его с использованием [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).

{{% alert color="primary" %}} 

Пожалуйста, обратите внимание, что API Aspose.Email для Java зависит от Bouncy Castle для криптографических функций.

{{% /alert %}} 

### **Зависимости Maven для Bouncy Castle**

~~~
<dependency>
<groupId>org.bouncycastle</groupId>
<artifactId>bcprov-jdk15on</artifactId>
<version>1.60</version>
</dependency>

<dependency>
<groupId>org.bouncycastle</groupId>
<artifactId>bcpkix-jdk15on</artifactId>
<version>1.60</version>
</dependency>
~~~

### **Включение провайдера безопасности Bouncy Castle**

~~~java
import java.security.Security;
import org.bouncycastle.jce.provider.BouncyCastleProvider;

if (Security.getProvider("BC") == null)
    Security.addProvider(new BouncyCastleProvider());
~~~

### **Подпись сообщения**

Следующий фрагмент кода показывает, как подписать сообщение.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java

byte[] privateCert = Files.readAllBytes(new File("sample.pfx").toPath());
byte[] publicCert = Files.readAllBytes(new File("sample.cer").toPath());

MailMessage msg = new MailMessage("userfrom@gmail.com", "userto@gmail.com", "Подписанное сообщение", "Тестовое тело подписанного сообщения");
MailMessage signed = msg.attachSignature(privateCert, "password");
MailMessage encrypted = signed.encrypt(publicCert, "password");
MailMessage decrypted = encrypted.decrypt(privateCert, "password");
MailMessage unsigned = decrypted.removeSignature();// Исходное сообщение с правильным телом
MapiMessage mapi = MapiMessage.fromMailMessage(unsigned);
~~~

### **Использование опции отдельного сертификата**

Веб-клиенты электронной почты могут не отображать содержимое тела подписанного сообщения. Это можно исправить, отделив сертификат перед отправкой его в веб-клиенты электронной почты. Флаг отсоединения в перегруженном методе [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) может быть использован для достижения этой цели. Если установить в **true**, сертификат будет отделен от электронной почты и наоборот. Чтобы видеть тело подписанного сообщения в веб-клиентах, необходимо создать [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) с отсоединенной подписью. Следующий фрагмент кода показывает, как использовать опцию отдельного сертификата.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java

MailMessage msg = new MailMessage("dr38445@gmail.com", "dr38445@gmail.com", "subject:Подписанное сообщение только от AE", "body:Тестовое тело подписанного сообщения от AE");
MailMessage signed = msg.attachSignature(privateCert, "password", true);
SmtpClient smtp = getSmtpClient(); //некоторый тестовый smtp клиент

smtp.send(signed);
~~~