---
title: "Conectarse al servidor POP3"
url: /es/net/connect-to-pop3-server/
weight: 10
type: docs
---

## Conexión a un servidor POP3

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) La clase permite a las aplicaciones administrar los buzones de correo electrónico mediante el Protocolo de oficina de correos, versión 3 (POP3). Para conectarse a un servidor, utilice el [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) clase. El [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class es la entrada principal para los desarrolladores que desean agregar la administración de POP3 a sus aplicaciones.NET. En este artículo se explica cómo utilizarla. Para conectarse a un servidor POP3:

1. Crea una instancia del [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.
2. Especifique el host, el nombre de usuario y la contraseña en [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) instance.

El siguiente fragmento de código muestra cómo conectarse con el servidor POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ConnectingToPOP3-ConnectingToPOP3.cs" >}}

## **Conexión al servidor SSL**

[Conexión a un servidor POP3](#connecting-to-a-pop3-server) describió cómo conectarse a un servidor POP3 en dos sencillos pasos:

1. Crea una instancia del [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.
1. Especifique el host, el nombre de usuario y la contraseña.

El proceso para conectarse a un servidor POP3 con SSL habilitado es similar, pero requiere establecer otras propiedades:

- [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/)
- Port

Para conectarse a un servidor POP3 con SSL habilitado, utilice el [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) clase y establece el [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/) y propiedades portuarias. El siguiente fragmento de código muestra cómo conectarse a un servidor POP3 con SSL habilitado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.cs" >}}

## **Conexión con un servidor APOP**

POP son las siglas de Post Office Protocol. APOP son las siglas de Authenticated Post Office Protocol. APOP es una versión ampliada de la configuración del servidor POP3 que cifra el nombre de usuario y la contraseña y utiliza un mecanismo de autenticación diseñado para proteger la contraseña de la cuenta POP3 al revisar el correo electrónico. La autenticación APOP no requiere que la contraseña de la cuenta se envíe como texto sin formato al servidor de correo POP3.

## **Conexión al servidor mediante proxy**

Los servidores proxy son muy comunes para comunicarse con el mundo exterior. En estos casos, las direcciones proxy se utilizan para que los clientes de correo electrónico accedan a los buzones a través de Internet. Aspose.Email admite las versiones 4, 4a y 5 del protocolo de proxy SOCKS. Este artículo proporciona un ejemplo práctico de cómo recuperar correo electrónico mediante un servidor de correo proxy. Para recuperar el correo electrónico a través de un servidor proxy:

1. Initialize [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) con la información requerida, es decir, la dirección del proxy, el puerto y la versión de SOCKS.
1. Initialize [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) con la dirección del host, el nombre de usuario, la contraseña y cualquier otra configuración.
1. Establezca la propiedad Proxy de un cliente en [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) objeto creado anteriormente.

El siguiente fragmento de código muestra cómo recuperar el correo electrónico a través de un servidor proxy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveEmailViaProxyServer-RetrieveEmailViaProxyServer.cs" >}}

## **Conexión al servidor mediante un proxy HTTP**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-AccessMailboxViaHttpProxy-AccessPOP3MailboxViaHttpProxy.cs" >}}

## **Conexión al servidor mediante el mecanismo de autenticación CRAM-MD5**

Mediante la autenticación CRAM-MD5, Aspose.Email para.NET permite a los usuarios autenticar y acceder de forma segura a los servidores de correo electrónico que admiten este método de autenticación. El ejemplo de código que aparece a continuación muestra cómo utilizar el mecanismo en su proyecto:

```cs
popClient.AllowedAuthentication = Pop3KnownAuthenticationType.CramMD5;
```

## **Cómo configurar el tiempo de espera para las operaciones de correo**

Cada operación de correo lleva algún tiempo dependiendo de muchos factores (retrasos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código que aparece a continuación muestra cómo hacerlo mediante el [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) propiedad. Nota: no debes establecer valores altos para evitar largas esperas en tu aplicación.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Uso de protocolos criptográficos con un cliente POP3**

Aspose.Email admite los protocolos criptográficos SSL (obsoletos) y TLS para brindar seguridad en las comunicaciones. Puede habilitar el cifrado criptográfico para proteger el intercambio de datos entre la aplicación y los servidores de correo.

> **_NOTE:_**  Debe establecer únicamente las versiones del protocolo compatibles con .NET Framework. Si su versión actual de .NET Framework no admite algunas versiones del protocolo criptográfico, se ignorarán y se omitirán. En este caso, no se generarán excepciones. Utilice, por favor [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) método si desea configurar los protocolos sin ninguna comprobación de compatibilidad.

El ejemplo de código siguiente muestra cómo configurar TLS 1.3 para [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) instancia de clase.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

En caso de que la versión actual de.NET Framework no admita un protocolo de cifrado especificado, la diferencia de comportamiento entre [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) método y [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) la propiedad es la siguiente:

- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) si se utiliza esta propiedad, el cliente de correo electrónico reduce el protocolo de cifrado a un nivel compatible.
 
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) si se utiliza este método, el cliente de correo electrónico lanza excepciones.
