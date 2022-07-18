---
title: Utility Features - SMTP Client
type: docs
weight: 30
url: /java/utility-features-smtp-client/
---


## **Listing Extension Servers using Smtp Client**
Aspose.Email's [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient) lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT, QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/EmailClient#getCapabilities\(\)) method returns the supported extension types in the form of a string array.
### **Retrieving Server Extensions**
The following code snippet shows you how to retrieve server extensions.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com",587,"username","password");
client.setSecurityOptions(SecurityOptions.Auto);
String[] caps = client.getCapabilities();
for (String str:caps)
	System.out.println(str);
~~~
## **Working with Signed Message**
Aspose.Email API provides the capability to create Signed messages using certificates. The [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#attachSignature\(byte[],%20java.lang.String\)) method of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage) class can be used to sign a message for saving or even sending it using the [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient).

{{% alert color="primary" %}} 

Please note that the Aspose.Email for Java API depends on Bouncy Castle for cryptography features.

{{% /alert %}} 

### **Bouncy Castle Maven Dependencies**



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
### **Enable Bouncy Castle Security Provider**



~~~java
import java.security.Security;
import org.bouncycastle.jce.provider.BouncyCastleProvider;

if (Security.getProvider("BC") == null)
    Security.addProvider(new BouncyCastleProvider());
~~~

### **Sign a Message**
The following code snippet shows you how to Sign a Message.


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
### **Using Detached Certificate Option**
Web-based email clients may not be able to display body contents of a Signed message. This can be taken care of by detaching the certificate before sending it to web-based email clients. The detached flag in the overloaded method of [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#attachSignature\(byte[],%20java.lang.String\)) can be used to achieve this. If set to **true**, the certificate is detached from the email and vice versa. To see Signed Message body in Web-based clients, you need to create [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage) with detached signature. The following code snippet shows you how to use detached certificate option.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

MailMessage msg = new MailMessage("dr38445@gmail.com", "dr38445@gmail.com", "subject:Signed message only by AE", "body:Test Body of signed message by AE");
MailMessage signed = msg.attachSignature(privateCert, "password", true);
SmtpClient smtp = getSmtpClient(); //some test smtp client

smtp.send(signed);
~~~
