---
title: Conectando al Servidor SMTP
type: docs
weight: 10
url: /net/conectando-al-servidor-smtp/
---

Al trabajar con clientes de correo electrónico, ciertas operaciones pueden tardar un tiempo considerable en ejecutarse. Para evitar que estas operaciones se ejecuten indefinidamente, los usuarios pueden hacer uso de la propiedad [EmailClient.Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Es importante tener en cuenta que los valores asignados a esta propiedad deben tener intervalos lo suficientemente largos para acomodar operaciones extensas.

Sin embargo, confiar únicamente en la propiedad Timeout puede hacer que el establecimiento de la conexión tarde más de lo esperado. Esto puede ocurrir cuando el cliente de correo electrónico utiliza el modo automático para el establecimiento de conexión. En este modo, el cliente cicla a través de varios parámetros de conexión hasta que se establece una conexión.

Al conectarse a servidores SMTP, IMAP y POP3, se envía una cadena de saludo al cliente al establecer la conexión con éxito. Los servidores pueden usar una iniciación de conexión SSL/TLS implícita o explícita (START TLS). En casos donde el modo de conexión no coincide (por ejemplo, el servidor espera una conexión SSL implícita mientras el cliente intenta establecer una conexión no asegurada o explícita SSL), el servidor no enviará una cadena de saludo.

Como resultado, el usuario puede esperar un período prolongado hasta que se alcance el tiempo de espera y el cliente pase a la siguiente opción de conexión.

Para abordar este problema, se ha introducido la propiedad [GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/). Esta propiedad permite a los usuarios establecer un tiempo de espera para la cadena de saludo, reduciendo el tiempo que toma establecer una conexión automática. Al implementar la **propiedad GreetingTimeout**, los usuarios pueden optimizar el rendimiento de su cliente de correo electrónico y evitar tiempos de espera prolongados durante el establecimiento de la conexión.

El siguiente ejemplo de código muestra cómo establecer la propiedad [EmailClient.GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/):

```cs
using (SmtpClient client = new SmtpClient("localhost", 25, "username", "password"))
{
    client.GreetingTimeout = 4000;
}
```

## **Conectándose al Servidor a través de un Servidor Proxy Socks**

A veces usamos servidores proxy para comunicarnos con el mundo exterior. En tales casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección del proxy. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo proxy SOCKS. Este artículo proporciona un ejemplo funcional de envío de correo electrónico utilizando un servidor de correo proxy. Para enviar un correo electrónico a través de un servidor proxy:

1. Inicializa el Proxy con la información requerida, es decir, dirección del proxy, puerto y versión de SOCKS.
1. Inicializa [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) con la dirección del host, nombre de usuario y contraseña, y cualquier otra configuración.
1. Establece la propiedad Proxy del cliente al objeto [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) creado anteriormente.

El siguiente fragmento de código muestra cómo conectarse a un servidor a través de un servidor proxy.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaProxyServer-SendEmailViaProxyServer.cs" >}}

## **Conectándose al Servidor a través de un Servidor Proxy HTTP**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaHttpProxy-SendEmailViaHttpProxy.cs" >}}

## **Conectándose al Servidor utilizando el Método de Autenticación Soportado**

Aspose.Email para .NET ofrece propiedades que permiten verificar qué métodos de autenticación se pueden utilizar para establecer una conexión segura con el servidor SMTP antes de enviar un correo electrónico:

-   la propiedad [SmtpClient.SupportedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/supportedauthentication/) devuelve una lista de métodos de autenticación soportados por el servidor SMTP.
-   la propiedad [SmtpClient.AllowedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/allowedauthentication/) devuelve una lista de métodos de autenticación definidos por el usuario.

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.Login;
```

## **Cargando Información de Autenticación SMTP desde un Archivo CONFIG**

La clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) permite a las aplicaciones leer información de autenticación como nombre de usuario y contraseña, así como la dirección del host y el número de puerto directamente desde un archivo de configuración. Utilizar la etiqueta de configuración nativa de .NET, como se muestra a continuación, permite que la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) lea esta información a través del Administrador de Configuración también disponible en el marco de .NET. Para que Aspose.Email pueda leer un archivo de configuración, debe estar en el formato correcto. A continuación, mostramos un ejemplo de archivo de configuración XML seguido del código que lo lee. El siguiente fragmento de código muestra cómo cargar la información de autenticación SMTP desde un archivo CONFIG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "LoadingAuthenticationInformationFromAFile.xml" >}}

Una vez que se definen las configuraciones, carga estas configuraciones directamente en una instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) utilizando uno de sus constructores sobrecargados. El siguiente fragmento de código demuestra la lectura de configuraciones desde el archivo de configuración y su carga directamente en la instancia de la [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-LoadSmtpConfigFile-LoadSmtpConfigFile.cs" >}}

## **Vinculando el Cliente SMTP a una Dirección IP Específica en el Host**

No se puede descartar la posibilidad de que un host tenga múltiples puertos disponibles para enviar correos electrónicos. En tales casos, puede surgir la necesidad de vincular el cliente de envío de correos electrónicos a un puerto específico en el host para enviar correos electrónicos. Esto también se puede lograr con la API de Aspose.Email utilizando la propiedad [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) [BindIPEndPoint](https://apireference.aspose.com/email/net/aspose.email.clients/emailclient/events/bindipendpoint). La [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) de la API se puede configurar para usar una dirección IP específica en el host especificando el Endpoint IP específico. El siguiente fragmento de código muestra cómo vincular el Cliente SMTP a una Dirección IP Específica en el Host.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SetSpecificIpAddress-SetSpecificIpAddress.cs" >}}

## **Cómo Establecer el Tiempo de Espera para Operaciones de Correo**

Cada operación de correo toma algo de tiempo dependiendo de muchos factores (retrasos de red, tamaño de los datos, rendimiento del servidor, etc.). Puedes establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código a continuación muestra cómo hacerlo utilizando la propiedad [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Nota: no debes establecer valores grandes para evitar largas esperas en tu aplicación.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.Timeout = 60000; // 60 segundos

    // algún código...
}
```

## **Usando Protocolos Criptográficos con el Cliente SMTP**

Aspose.Email soporta SSL (obsoleto) y protocolos criptográficos TLS para proporcionar seguridad en las comunicaciones. Puedes habilitar la encriptación criptográfica para proteger el intercambio de datos entre tu aplicación y los servidores de correo.

> **_NOTA:_** Debes establecer solo aquellas versiones del protocolo que son soportadas por el Marco de .NET. Si algunas versiones del protocolo criptográfico no son soportadas por tu versión actual del Marco de .NET, serán ignoradas y omitidas. En este caso, no se generarán excepciones. Por favor usa el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) si deseas establecer los protocolos sin verificaciones de compatibilidad.

El ejemplo de código a continuación muestra cómo establecer TLS 1.3 para la instancia de la clase [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // algún código...
}
```

En el caso de que un protocolo de encriptación especificado no sea soportado en la versión actual del Marco de .NET, la diferencia de comportamiento entre el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) y la propiedad [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) es la siguiente:

-   Si se utiliza la propiedad [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/), el cliente de correo electrónico degrada el protocolo de encriptación a un nivel soportado.
-   Si se utiliza el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), el cliente de correo electrónico lanza excepciones.

## **Usando el Mecanismo CRAM-MD5 para Autenticación**

El mecanismo de autenticación CRAM-MD5 de Aspose.Email para .NET proporciona una capa adicional de seguridad al acceder al servidor. El siguiente fragmento de código muestra cómo implementar esta característica en tu proyecto:

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.CramMD5;
```

