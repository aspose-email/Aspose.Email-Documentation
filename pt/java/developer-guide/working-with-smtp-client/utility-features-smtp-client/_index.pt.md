---
title: "Recursos de Utilidade - Cliente SMTP"
url: /pt/java/utility-features-smtp-client/
weight: 30
type: docs
---


## **Listando Extensões de Servidores usando o Cliente SMTP**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) permite recuperar as extensões de servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getCapabilities--) retorna os tipos de extensão suportados na forma de um array de strings.

### **Recuperando Extensões de Servidor**

O seguinte trecho de código mostra como recuperar as extensões de servidor.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com",587,"username","password");
client.setSecurityOptions(SecurityOptions.Auto);
String[] caps = client.getCapabilities();
for (String str:caps)
	System.out.println(str);
~~~

## **Trabalhando com Mensagem Assinada**

A API Aspose.Email fornece a capacidade de criar mensagens assinadas usando certificados. O método [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) pode ser usado para assinar uma mensagem para salvá-la ou até mesmo enviá-la usando o [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).

{{% alert color="primary" %}} 

Observe que a API Aspose.Email para Java depende do Bouncy Castle para recursos de criptografia.

{{% /alert %}} 

### **Dependências do Bouncy Castle no Maven**

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

### **Habilitar o Provedor de Segurança Bouncy Castle**

~~~java
import java.security.Security;
import org.bouncycastle.jce.provider.BouncyCastleProvider;

if (Security.getProvider("BC") == null)
    Security.addProvider(new BouncyCastleProvider());
~~~

### **Assinar uma Mensagem**

O seguinte trecho de código mostra como assinar uma mensagem.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java

byte[] privateCert = Files.readAllBytes(new File("sample.pfx").toPath());
byte[] publicCert = Files.readAllBytes(new File("sample.cer").toPath());

MailMessage msg = new MailMessage("userfrom@gmail.com", "userto@gmail.com", "Mensagem assinada apenas", "Corpo de teste da mensagem assinada");
MailMessage signed = msg.attachSignature(privateCert, "password");
MailMessage encrypted = signed.encrypt(publicCert, "password");
MailMessage decrypted = encrypted.decrypt(privateCert, "password");
MailMessage unsigned = decrypted.removeSignature();// A mensagem original com o corpo correto
MapiMessage mapi = MapiMessage.fromMailMessage(unsigned);
~~~

### **Usando a Opção de Certificado Destacado**

Clientes de email baseados na web podem não conseguir exibir o conteúdo do corpo de uma mensagem assinada. Isso pode ser resolvido destacando o certificado antes de enviá-lo para clientes de email baseados na web. A flag detached no método sobrecarregado de [attachSignature](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) pode ser usada para isso. Se definido como **true**, o certificado é destacado do email e vice-versa. Para ver o corpo da Mensagem Assinada em clientes baseados na web, você precisa criar [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) com assinatura destacada. O seguinte trecho de código mostra como usar a opção de certificado destacado.

~~~Java
// Para exemplos completos e arquivos de dados, por favor acesse https://github.com/aspose-email/Aspose.Email-for-Java

MailMessage msg = new MailMessage("dr38445@gmail.com", "dr38445@gmail.com", "assunto:Mensagem assinada apenas por AE", "corpo:Corpo de teste da mensagem assinada por AE");
MailMessage signed = msg.attachSignature(privateCert, "password", true);
SmtpClient smtp = getSmtpClient(); // algum cliente smtp de teste

smtp.send(signed);
~~~