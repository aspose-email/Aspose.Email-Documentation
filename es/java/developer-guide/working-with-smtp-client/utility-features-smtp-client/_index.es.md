---
title: "Características de Utilidad - Cliente SMTP"
url: /es/java/utility-features-smtp-client/
weight: 30
type: docs
---


## **Listando Servidores de Extensión usando el Cliente Smtp**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) te permite recuperar las extensiones que un servidor soporta, tales como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El método [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getCapabilities--) devuelve los tipos de extensión soportados en forma de un arreglo de cadenas.

### **Recuperando Extensiones del Servidor**

El siguiente fragmento de código te muestra cómo recuperar las extensiones del servidor.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com",587,"username","password");
client.setSecurityOptions(SecurityOptions.Auto);
String[] caps = client.getCapabilities();
for (String str:caps)
	System.out.println(str);
~~~

## **Trabajando con Mensajes Firmados**

La API de Aspose.Email proporciona la capacidad de crear mensajes firmados utilizando certificados. El método [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) puede ser utilizado para firmar un mensaje para guardarlo o incluso enviarlo utilizando el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).

{{% alert color="primary" %}} 

Ten en cuenta que la API Aspose.Email para Java depende de Bouncy Castle para las características de criptografía.

{{% /alert %}} 

### **Dependencias de Maven de Bouncy Castle**

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

### **Habilitar el Proveedor de Seguridad Bouncy Castle**

~~~java
import java.security.Security;
import org.bouncycastle.jce.provider.BouncyCastleProvider;

if (Security.getProvider("BC") == null)
    Security.addProvider(new BouncyCastleProvider());
~~~

### **Firmar un Mensaje**

El siguiente fragmento de código te muestra cómo firmar un mensaje.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java

byte[] privateCert = Files.readAllBytes(new File("sample.pfx").toPath());
byte[] publicCert = Files.readAllBytes(new File("sample.cer").toPath());

MailMessage msg = new MailMessage("userfrom@gmail.com", "userto@gmail.com", "Mensaje firmado únicamente", "Cuerpo de prueba del mensaje firmado");
MailMessage signed = msg.attachSignature(privateCert, "password");
MailMessage encrypted = signed.encrypt(publicCert, "password");
MailMessage decrypted = encrypted.decrypt(privateCert, "password");
MailMessage unsigned = decrypted.removeSignature();// El mensaje original con el cuerpo adecuado
MapiMessage mapi = MapiMessage.fromMailMessage(unsigned);
~~~

### **Utilizando la Opción de Certificado Separado**

Los clientes de correo electrónico basados en la web pueden no ser capaces de mostrar el contenido del cuerpo de un mensaje firmado. Esto puede manejarse separando el certificado antes de enviarlo a clientes de correo electrónico basados en la web. La bandera detach en el método sobrecargado de [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) puede ser utilizada para lograr esto. Si se establece en **true**, el certificado se separa del correo electrónico y viceversa. Para ver el cuerpo del Mensaje Firmado en clientes basados en la web, necesitas crear un [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) con firma separada. El siguiente fragmento de código te muestra cómo usar la opción de certificado separado.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java

MailMessage msg = new MailMessage("dr38445@gmail.com", "dr38445@gmail.com", "asunto:Mensaje firmado únicamente por AE", "cuerpo:Prueba del cuerpo del mensaje firmado por AE");
MailMessage signed = msg.attachSignature(privateCert, "password", true);
SmtpClient smtp = getSmtpClient(); // algún cliente smtp de prueba

smtp.send(signed);
~~~