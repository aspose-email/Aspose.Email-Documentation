---
title: "Функции утилиты — SMTP-клиент"
url: /ru/java/utility-features-smtp-client/
weight: 30
type: docs
---


## **Список серверов расширений с использованием клиента Smtp**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getCapabilities--) метод возвращает поддерживаемые типы расширений в виде строкового массива.

### **Получение серверных расширений**

В следующем фрагменте кода показано, как извлекать серверные расширения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com",587,"username","password");
client.setSecurityOptions(SecurityOptions.Auto);
String[] caps = client.getCapabilities();
for (String str:caps)
	System.out.println(str);
~~~

## **Работа с подписанным сообщением**

Aspose.Email API предоставляет возможность создавать подписанные сообщения с использованием сертификатов. [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) метод [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс можно использовать для подписи сообщения для сохранения или даже отправки его с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).

{{% alert color="primary" %}}

Обратите внимание, что API Aspose.Email для Java зависит от Bouncy Castle в том, что касается функций криптографии.

{{% /alert %}}

### **Зависимости Баунси Касл Мейвен**

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

### **Включить поставщика услуг безопасности Bouncy Castle**

~~~java
import java.security.Security;
import org.bouncycastle.jce.provider.BouncyCastleProvider;

if (Security.getProvider("BC") == null)
    Security.addProvider(new BouncyCastleProvider());
~~~

### **Подпишите сообщение**

В следующем фрагменте кода показано, как подписать сообщение.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

byte[] privateCert = Files.readAllBytes(new File("sample.pfx").toPath());
byte[] publicCert = Files.readAllBytes(new File("sample.cer").toPath());

MailMessage msg = new MailMessage("userfrom@gmail.com", "userto@gmail.com", "Signed message only", "Test Body of signed message");
MailMessage signed = msg.attachSignature(privateCert, "password");
MailMessage encrypted = signed.encrypt(publicCert, "password");
MailMessage decrypted = encrypted.decrypt(privateCert, "password");
MailMessage unsigned = decrypted.removeSignature();// The original message with proper body
MapiMessage mapi = MapiMessage.fromMailMessage(unsigned);
~~~

### **Использование опции «Отдельный сертификат»**

Веб-клиенты электронной почты могут не отображать основное содержимое подписанного сообщения. Эту проблему можно решить, отсоединив сертификат перед отправкой почтовым веб-клиентам. Отключенный флаг в перегруженном методе [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) могут быть использованы для достижения этой цели. Если установлено значение **true**, сертификат отделяется от электронного письма и наоборот. Чтобы увидеть текст подписанного сообщения в веб-клиентах, вам необходимо создать [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) с отдельной подписью. В следующем фрагменте кода показано, как использовать опцию отдельного сертификата.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

MailMessage msg = new MailMessage("dr38445@gmail.com", "dr38445@gmail.com", "subject:Signed message only by AE", "body:Test Body of signed message by AE");
MailMessage signed = msg.attachSignature(privateCert, "password", true);
SmtpClient smtp = getSmtpClient(); //some test smtp client

smtp.send(signed);
~~~
