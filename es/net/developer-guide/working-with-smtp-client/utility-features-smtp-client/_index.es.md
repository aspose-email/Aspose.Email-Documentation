---
title: "Características de Utilidad - Cliente SMTP"
url: /es/net/utility-features-smtp-client/
weight: 30
type: docs
---

# Características de Utilidad - Cliente SMTP

## **Listando Servidores de Extensión usando el Cliente SMTP**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) te permite recuperar las extensiones del servidor que un servidor soporta, tales como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad particular. El método [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) devuelve los tipos de extensiones soportados en forma de un array de cadenas.

### **Recuperando Extensiones del Servidor**

El siguiente fragmento de código te muestra cómo recuperar extensiones del servidor.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-RetreiveServerExtensions-RetreiveSMTPServerExtensions.cs" >}}

## **Trabajando con Mensajes Firmados**

La API de Aspose.Email proporciona la capacidad de crear mensajes firmados usando certificados. El método [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) puede ser utilizado para firmar un mensaje para guardarlo o incluso enviarlo usando el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

### **Firmar un Mensaje**

El siguiente fragmento de código te muestra cómo firmar un mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SignAMessage-SignAMessage.cs" >}}

### **Usando la Opción de Certificado Desligado**

Los clientes de correo electrónico basados en la web pueden no ser capaces de mostrar el contenido del cuerpo de un mensaje firmado. Esto se puede solucionar desligando el certificado antes de enviarlo a clientes de correo electrónico basados en la web. La bandera de desligado en el método sobrecargado de [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) puede ser utilizada para lograr esto. Si se establece en **true**, el certificado se desprende del correo electrónico y viceversa. Para ver el cuerpo del mensaje firmado en clientes basados en la web, necesitas crear un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) con la firma desligada. El siguiente fragmento de código te muestra cómo usar la opción de certificado desligado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-UsingDetachedCertificate-UsingDetachedCertificate.cs" >}}

## **Validar Credenciales del Servidor de Correo Sin Enviar un Correo Electrónico**

La API de Aspose.Email proporciona la capacidad de validar credenciales del servidor de correo sin enviar un correo electrónico. Esto se puede lograr con el método [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentials/) que es responsable de verificar la autenticidad y corrección de las credenciales de correo electrónico proporcionadas, que normalmente se usan para autenticación al conectarse al servidor.

Verifica que las credenciales de correo electrónico proporcionadas, tales como nombre de usuario y contraseña, son válidas, y que el cliente puede establecer una conexión exitosa al servidor. Esta verificación de credenciales ayuda a asegurar que el cliente pueda acceder a la cuenta de correo electrónico de forma segura y realizar diversas operaciones, tales como enviar correos electrónicos.

```cs
using (SmtpClient client = new SmtpClient(server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

También hay una versión del método [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentialsasync/) para realizar una operación asíncrona.