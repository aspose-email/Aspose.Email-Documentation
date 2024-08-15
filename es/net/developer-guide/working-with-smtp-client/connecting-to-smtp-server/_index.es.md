---
title: "Conexión al servidor SMTP"
url: /es/net/connecting-to-smtp-server/
weight: 10
type: docs
---

Cuando se trabaja con clientes de correo electrónico, algunas operaciones pueden tardar un tiempo considerable en ejecutarse. Para evitar que estas operaciones se ejecuten indefinidamente, los usuarios pueden utilizar el [EmailClient.Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) propiedad. Es importante tener en cuenta que los valores asignados a esta propiedad deben tener intervalos lo suficientemente largos como para permitir operaciones prolongadas.

Sin embargo, confiar únicamente en la propiedad Timeout puede provocar que el establecimiento de la conexión demore más de lo esperado. Esto puede ocurrir cuando el cliente de correo electrónico usa el modo automático para establecer la conexión. En este modo, el cliente recorre varios parámetros de conexión hasta que se establezca una conexión.

Al conectarse a servidores SMTP, IMAP y POP3, se envía una cadena de saludo al cliente al establecer la conexión correctamente. Los servidores pueden iniciar una conexión SSL/TLS implícita o explícita (START TLS). En los casos en que el modo de conexión no coincida (por ejemplo, si el servidor espera una conexión SSL implícita mientras el cliente intenta establecer una conexión SSL no segura o explícita), el servidor no enviará una cadena de saludo.

Como resultado, el usuario puede esperar un período prolongado hasta que se agote el tiempo de espera y el cliente pase a la siguiente opción de conexión.

Para abordar este problema, el [GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/) se ha introducido la propiedad. Esta propiedad permite a los usuarios establecer un tiempo de espera para la cadena de saludo, lo que reduce el tiempo necesario para establecer una conexión automática. Al implementar el **Propiedad GreetingTimeout**, los usuarios pueden optimizar el rendimiento de su cliente de correo electrónico y evitar largos tiempos de espera durante el establecimiento de la conexión.

El siguiente ejemplo de código muestra cómo configurar el [EmailClient.GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/) property:

```cs
using (SmtpClient client = new SmtpClient("localhost", 25, "username", "password"))
{
    client.GreetingTimeout = 4000;
}
```

## **Conexión al servidor a través de Socks Proxy Sever**

A veces utilizamos servidores proxy para comunicarnos con el mundo exterior. En estos casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección de proxy. Aspose.Email admite las versiones 4, 4a y 5 del protocolo proxy SOCKS. Este artículo proporciona un ejemplo práctico del envío de correos electrónicos mediante un servidor de correo proxy. Para enviar un correo electrónico a través de un servidor proxy:

1. Inicialice el proxy con la información requerida, es decir, la dirección del proxy, el puerto y la versión de SOCKS.
1. Initialize [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) con la dirección del host, el nombre de usuario y la contraseña y cualquier otra configuración.
1. Establezca la propiedad Proxy del cliente en [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) objeto creado anteriormente.

El siguiente fragmento de código muestra cómo conectarse a un servidor mediante un servidor proxy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaProxyServer-SendEmailViaProxyServer.cs" >}}

## **Conexión al servidor mediante un servidor proxy HTTP**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaHttpProxy-SendEmailViaHttpProxy.cs" >}}

## **Conexión al servidor mediante el método de autenticación compatible**

Aspose.Email para.NET ofrece propiedades que permiten comprobar qué métodos de autenticación se pueden utilizar para establecer una conexión segura con el servidor SMTP antes de enviar un correo electrónico:
- the [SmtpClient.SupportedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/supportedauthentication/) La propiedad devuelve una lista de los métodos de autenticación admitidos por el servidor SMTP.
- the [SmtpClient.AllowedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/allowedauthentication/) La propiedad devuelve una lista de los métodos de autenticación definidos por el usuario.

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.Login;
```

## **Carga de la información de autenticación SMTP desde el archivo CONFIG**

The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) La clase permite a las aplicaciones leer la información de autenticación, como el nombre de usuario y la contraseña y la dirección del host y el número de puerto, directamente desde un archivo de configuración. El uso de la etiqueta de configuración nativa de.NET, como se muestra a continuación, habilita la [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase para leer esta información a través del Configuration Manager, también disponible en.NET Framework. Para que Aspose.Email pueda leer un archivo de configuración, debe estar en el formato correcto. A continuación, mostramos un ejemplo de archivo de configuración XML seguido del código que lo lee. El siguiente fragmento de código muestra cómo cargar la información de autenticación SMTP desde el archivo CONFIG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "LoadingAuthenticationInformationFromAFile.xml" >}}

Una vez definidos los ajustes de configuración, cárguelos directamente en una instancia del [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase que utiliza uno de sus constructores sobrecargados. En el siguiente fragmento de código se muestra cómo leer los valores de configuración del archivo de configuración y cómo cargarlos directamente en la instancia del [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-LoadSmtpConfigFile-LoadSmtpConfigFile.cs" >}}

## **Vincular el cliente SMTP a una dirección IP específica en el host**

No se puede descartar la posibilidad de que un host tenga varios puertos disponibles para enviar correos electrónicos. En tales casos, puede surgir la necesidad de vincular el cliente de envío de correo electrónico a un puerto específico del host para enviar correos electrónicos. Esto también se puede lograr con la API Aspose.Email utilizando la [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) [BindIPEndPoint](https://apireference.aspose.com/email/net/aspose.email.clients/emailclient/events/bindipendpoint) propiedad. Las API [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) se puede configurar para usar una dirección IP específica en el host especificando el punto final IP específico. El siguiente fragmento de código muestra cómo vincular el cliente SMTP a una dirección IP específica del host.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SetSpecificIpAddress-SetSpecificIpAddress.cs" >}}

## **Cómo configurar el tiempo de espera para las operaciones de correo**

Cada operación de correo lleva algún tiempo dependiendo de muchos factores (retrasos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código que aparece a continuación muestra cómo hacerlo mediante el [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) propiedad. Nota: no debes establecer valores altos para evitar largas esperas en tu aplicación.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Uso de protocolos criptográficos con un cliente SMTP**

Aspose.Email admite los protocolos criptográficos SSL (obsoletos) y TLS para brindar seguridad en las comunicaciones. Puede habilitar el cifrado criptográfico para proteger el intercambio de datos entre la aplicación y los servidores de correo.

> **_NOTE:_**  Debe establecer únicamente las versiones del protocolo compatibles con .NET Framework. Si su versión actual de .NET Framework no admite algunas versiones del protocolo criptográfico, se ignorarán y se omitirán. En este caso, no se generarán excepciones. Utilice, por favor [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) método si desea configurar los protocolos sin ninguna comprobación de compatibilidad.

El ejemplo de código siguiente muestra cómo configurar TLS 1.3 para [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) instancia de clase.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

En caso de que la versión actual de.NET Framework no admita un protocolo de cifrado especificado, la diferencia de comportamiento entre [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) método y [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) la propiedad es la siguiente:
- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) si se utiliza esta propiedad, el cliente de correo electrónico reduce el protocolo de cifrado a un nivel compatible.
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) si se utiliza este método, el cliente de correo electrónico lanza excepciones.

##  **Uso del mecanismo CRAM-MD5 para la autenticación**

El mecanismo de autenticación CRAM-MD5 de Aspose.Email para.NET proporciona una capa adicional de seguridad al acceder al servidor. El siguiente fragmento de código muestra cómo implementar esta función en su proyecto:

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.CramMD5;
```