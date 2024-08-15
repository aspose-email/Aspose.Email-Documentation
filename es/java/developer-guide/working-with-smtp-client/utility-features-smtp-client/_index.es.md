---
title: "Características de la utilidad: cliente SMTP"
url: /es/java/utility-features-smtp-client/
weight: 30
type: docs
---


## **Listado de servidores de extensión que utilizan un cliente SMTP**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getCapabilities--) El método devuelve los tipos de extensión admitidos en forma de una matriz de cadenas.

### **Recuperación de extensiones de servidor**

El siguiente fragmento de código muestra cómo recuperar las extensiones de servidor.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com",587,"username","password");
client.setSecurityOptions(SecurityOptions.Auto);
String[] caps = client.getCapabilities();
for (String str:caps)
	System.out.println(str);
~~~

## **Trabajando con mensajes firmados**

La API Aspose.Email ofrece la capacidad de crear mensajes firmados mediante certificados. La [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) método del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) la clase se puede usar para firmar un mensaje para guardarlo o incluso enviarlo usando el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).

{{% alert color="primary" %}}

Tenga en cuenta que la API Aspose.Email para Java depende de Bouncy Castle para las funciones de criptografía.

{{% /alert %}}

### **Dependencias de Bouncy Castle Maven**

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

### **Habilitar el proveedor de seguridad de Bouncy Castle**

~~~java
import java.security.Security;
import org.bouncycastle.jce.provider.BouncyCastleProvider;

if (Security.getProvider("BC") == null)
    Security.addProvider(new BouncyCastleProvider());
~~~

### **Firma un mensaje**

El siguiente fragmento de código muestra cómo firmar un mensaje.

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

### **Uso de la opción de certificado independiente**

Es posible que los clientes de correo electrónico basados en la web no puedan mostrar el contenido del cuerpo de un mensaje firmado. Esto puede solucionarse separando el certificado antes de enviarlo a los clientes de correo electrónico basados en la web. La marca separada en el método sobrecargado de [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) se puede utilizar para lograr esto. Si se establece en **true**, el certificado se separa del correo electrónico y viceversa. Para ver el cuerpo del mensaje firmado en los clientes basados en la web, debe crear [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) con firma independiente. El siguiente fragmento de código muestra cómo utilizar la opción de certificado independiente.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

MailMessage msg = new MailMessage("dr38445@gmail.com", "dr38445@gmail.com", "subject:Signed message only by AE", "body:Test Body of signed message by AE");
MailMessage signed = msg.attachSignature(privateCert, "password", true);
SmtpClient smtp = getSmtpClient(); //some test smtp client

smtp.send(signed);
~~~
