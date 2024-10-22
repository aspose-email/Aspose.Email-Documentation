---
title: "Conectar a un Servidor POP3"
url: /es/net/connect-to-pop3-server/
weight: 10
type: docs
---

## Conectando a un Servidor POP3

La clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) permite a las aplicaciones gestionar buzones de correo utilizando el Protocolo de Oficina de Correos, Versión 3 (POP3). Para conectarse a un servidor, use la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). La clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) es la principal entrada para los desarrolladores que desean agregar gestión POP3 a sus aplicaciones .NET. Este artículo explica cómo utilizarla. Para conectarse a un servidor POP3:

1. Cree una instancia de la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Especifique el host, nombre de usuario y contraseña en la instancia de [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

El siguiente fragmento de código muestra cómo conectarse al servidor POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ConnectingToPOP3-ConnectingToPOP3.cs" >}}

## **Conectando a un servidor SSL**

[Conectando a un Servidor POP3](#connecting-to-a-pop3-server) describe cómo conectarse a un servidor POP3 en dos pasos simples:

1. Cree una instancia de la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Especifique el host, nombre de usuario y contraseña.

El proceso para conectarse a un servidor POP3 habilitado para SSL es similar, pero requiere que configure algunas propiedades adicionales:

- [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/)
- Puerto

Para conectarse a un servidor POP3 habilitado para SSL, use la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) y establezca las propiedades [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/) y Puerto. El siguiente fragmento de código muestra cómo conectarse a un servidor POP3 habilitado para SSL.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.cs" >}}

## **Conectando con un Servidor APOP**

POP significa Protocolo de Oficina de Correos. APOP significa Protocolo de Oficina de Correos Autenticado. APOP es una versión extendida de la configuración del servidor POP3 que encripta su nombre de usuario y contraseña y utiliza un mecanismo de autenticación diseñado para proteger la contraseña de su cuenta POP3 al verificar el correo electrónico. La autenticación APOP no requiere que se envíe la contraseña de la cuenta como texto plano al servidor de correo POP3.

## **Conectando a un Servidor a través de Proxy**

Los servidores proxy son muy comunes para comunicarse con el exterior. En tales casos, se utilizan direcciones proxy para que los clientes de correo accedan a los buzones a través de Internet. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo de proxy SOCKS. Este artículo proporciona un ejemplo funcional de recuperación de correo electrónico utilizando un servidor de correo proxy. Para recuperar correo electrónico a través de un servidor proxy:

1. Inicialice [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) con la información requerida, es decir, dirección proxy, puerto y versión de SOCKS.
1. Inicialice [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) con la dirección del host, nombre de usuario, contraseña y cualquier otra configuración.
1. Establezca la propiedad Proxy de un cliente al objeto [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) creado anteriormente.

El siguiente fragmento de código muestra cómo recuperar correo electrónico a través de un servidor proxy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveEmailViaProxyServer-RetrieveEmailViaProxyServer.cs" >}}

## **Conectando a un servidor a través de un Proxy HTTP**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-AccessMailboxViaHttpProxy-AccessPOP3MailboxViaHttpProxy.cs" >}}

## **Conectando al servidor mediante el mecanismo de autenticación CRAM-MD5**

Usando la autenticación CRAM-MD5, Aspose.Email para .NET permite a los usuarios autenticar y acceder de manera segura a servidores de correo electrónico que soportan este método de autenticación. El siguiente ejemplo de código muestra cómo utilizar el mecanismo en su proyecto:

```cs
popClient.AllowedAuthentication = Pop3KnownAuthenticationType.CramMD5;
```

## **Cómo Establecer el Tiempo de Espera para Operaciones de Correo**

Cada operación de correo toma algún tiempo dependiendo de muchos factores (retardos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código a continuación muestra cómo hacerlo utilizando la propiedad [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Nota: no debe establecer valores grandes para evitar esperas prolongadas en su aplicación.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.Timeout = 60000; // 60 segundos

    // algún código...
}
```

## **Usando Protocolos Criptográficos con el Cliente POP3**

Aspose.Email soporta SSL (obsoleto) y protocolos criptográficos TLS para proporcionar seguridad en las comunicaciones. Puede habilitar la encriptación criptográfica para proteger el intercambio de datos entre su aplicación y los servidores de correo.

> **_NOTA:_** Debe establecer solo aquellas versiones del protocolo que son soportadas por .NET Framework. Si algunas versiones del protocolo criptográfico no son soportadas por su versión actual de .NET Framework, serán ignoradas y omitidas. En este caso, no se generarán excepciones. Utilice el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) si desea establecer los protocolos sin ninguna verificación de compatibilidad.

El siguiente ejemplo de código muestra cómo establecer TLS 1.3 para la instancia de la clase [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.SupportedEncryption = EncryptionProtocols.Tls13;

    // algún código...
}
```

En caso de que un protocolo de encriptación especificado no sea soportado en la versión actual de .NET Framework, la diferencia en el comportamiento entre el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) y la propiedad [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) es la siguiente:

- Si se utiliza la propiedad [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/), el cliente de correo degradará el protocolo de encriptación a un nivel soportado.
  
- Si se utiliza el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), el cliente de correo lanzará excepciones.