---
title: "Características de la utilidad: cliente SMTP"
url: /es/net/utility-features-smtp-client/
weight: 30
type: docs
---

# Características de la utilidad: cliente SMTP

## **Listado de servidores de extensión que utilizan un cliente SMTP**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) permite recuperar las extensiones de servidor que admite un servidor, como IDLE, UNSELECT, QUOTA, etc. Esto ayuda a identificar la disponibilidad de una extensión antes de usar el cliente para esa funcionalidad en particular. El [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) El método devuelve los tipos de extensión admitidos en forma de una matriz de cadenas.

### **Recuperación de extensiones de servidor**

El siguiente fragmento de código muestra cómo recuperar las extensiones de servidor.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-RetreiveServerExtensions-RetreiveSMTPServerExtensions.cs" >}}

## **Trabajando con mensajes firmados**

La API Aspose.Email ofrece la capacidad de crear mensajes firmados mediante certificados. La [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) método del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) la clase se puede usar para firmar un mensaje para guardarlo o incluso enviarlo usando el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

### **Firma un mensaje**

El siguiente fragmento de código muestra cómo firmar un mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SignAMessage-SignAMessage.cs" >}}

### **Uso de la opción de certificado independiente**

Es posible que los clientes de correo electrónico basados en la web no puedan mostrar el contenido del cuerpo de un mensaje firmado. Esto puede solucionarse separando el certificado antes de enviarlo a los clientes de correo electrónico basados en la web. La marca separada en el método sobrecargado de [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) se puede utilizar para lograr esto. Si se establece en **true**, el certificado se separa del correo electrónico y viceversa. Para ver el cuerpo del mensaje firmado en los clientes basados en la web, debe crear [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) con firma independiente. El siguiente fragmento de código muestra cómo utilizar la opción de certificado independiente.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-UsingDetachedCertificate-UsingDetachedCertificate.cs" >}}

## **Valide las credenciales del servidor de correo sin enviar correo electrónico**

La API Aspose.Email ofrece la capacidad de validar las credenciales del servidor de correo sin enviar un correo electrónico. Esto se puede lograr con el [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentials/) método que se encarga de verificar la autenticidad y exactitud de las credenciales de correo electrónico proporcionadas, que normalmente se utilizan para la autenticación al conectarse al servidor.

Verifica que las credenciales de correo electrónico proporcionadas, como el nombre de usuario y la contraseña, sean válidas y que el cliente pueda establecer una conexión correcta con el servidor. Esta verificación de las credenciales ayuda a garantizar que el cliente pueda acceder a la cuenta de correo electrónico de forma segura y realizar diversas operaciones, como enviar correos electrónicos.

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

También hay una versión del método [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentialsasync/)  para realizar una operación asincrónica. 