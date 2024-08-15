---
title: "Conexión al servidor IMAP"
url: /es/net/connecting-to-imap-server/
weight: 10
type: docs
---


The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) La clase permite a las aplicaciones administrar los buzones IMAP mediante el protocolo IMAP. El [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) La clase se usa para conectarse a los servidores de correo IMAP y administrar los correos electrónicos en las carpetas de correo electrónico IMAP. Para conectarse a un servidor IMAP

1. Crea una instancia del [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Especifique el nombre de host, el nombre de usuario y la contraseña en el [Constructor IMAPClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor_8).

**Tenga en cuenta que las restricciones de contraseña deben cumplir los requisitos del servidor. El cliente de correo electrónico no añade restricciones de contraseña.**

Una vez que [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se inicia la instancia, la siguiente llamada a cualquier operación que utilice esta instancia se conectará al servidor. El siguiente fragmento de código muestra cómo conectarse a un servidor IMAP siguiendo los pasos anteriores.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");
```

## **Conexión con un servidor IMAP con SSL habilitado**

[Conexión con el servidor IMAP](/email/net/connecting-to-imap-server#connecting-with-imap-server) describió cómo conectarse a un servidor IMAP en cuatro sencillos pasos:

1. Crea una instancia del [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Especifique el nombre de host, el nombre de usuario y la contraseña.
1. Especifique el puerto.
1. Especifique las opciones de seguridad.

El proceso para conectarse a un servidor IMAP con SSL habilitado es similar, pero requiere que defina otras propiedades:

- Establezca las opciones de seguridad en SSLIplicit.

El siguiente fragmento de código muestra cómo

1. Establezca un nombre de usuario, una contraseña y un puerto.
1. Defina la opción de seguridad.


```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Crea una instancia del ImapClient class
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");
           
// Set the security mode to implicit
client.SecurityOptions = SecurityOptions.SSLImplicit;
```

## **Conexión al servidor mediante proxy**

Los servidores proxy se utilizan habitualmente para comunicarse con el mundo exterior. En estos casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección de proxy. Aspose.Email admite las versiones 4, 4a y 5 del protocolo de proxy SOCKS. Este artículo proporciona un ejemplo práctico de cómo acceder al buzón de correo mediante un servidor de correo proxy. Para acceder al buzón a través de un servidor proxy:

1. Initialize [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) con la información requerida, es decir, la dirección del proxy, el puerto y la versión de SOCKS.
1. Initialize [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) con la dirección del host, el nombre de usuario, la contraseña y cualquier otra configuración.
1. Configure el del cliente [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) propiedad del cliente a la [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) objeto creado anteriormente.

El siguiente fragmento de código muestra cómo recuperar el buzón de correo a través de un servidor proxy.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Connect and log in to IMAP and set SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.SecurityOptions = SecurityOptions.Auto;
           
string proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Set the proxy
client.Proxy = proxy;
          
try
{
    client.SelectFolder("Inbox");
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

## **Conexión al servidor mediante un proxy HTTP**

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
using (ImapClient client = new ImapClient("imap.domain.com", "username", "password"))
{
    client.Proxy = proxy;
    client.SelectFolder("Inbox");
}
```

## **Conexión al servidor en modo de solo lectura**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) la clase proporciona una [ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) propiedad que, cuando se establece en **true**, indica que no se deben realizar cambios en el estado permanente del buzón. El siguiente ejemplo de código demuestra el uso de [ImapClient.ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) propiedad. Obtiene el recuento de mensajes no leídos, luego recupera un mensaje y, a continuación, vuelve a obtener el recuento de mensajes no leídos en modo de solo lectura. El recuento de los mensajes no leídos sigue siendo el mismo, lo que indica que el estado permanente del buzón no se modificó.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
ImapClient imapClient = new ImapClient();
imapClient.Host = "<HOST>";
imapClient.Port = 993;
imapClient.Username = "<USERNAME>";
imapClient.Password = "<PASSWORD>";
imapClient.SupportedEncryption = EncryptionProtocols.Tls;
imapClient.SecurityOptions = SecurityOptions.SSLImplicit;

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.HasNoFlags(ImapMessageFlags.IsRead); /* get unread messages. */
MailQuery query = imapQueryBuilder.GetQuery();

imapClient.ReadOnly = true;
imapClient.SelectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.ListMessages(query);
Console.WriteLine("Initial Unread Count: " + messageInfoCol.Count());
if (messageInfoCol.Count() > 0)
{
    imapClient.FetchMessage(messageInfoCol[0].SequenceNumber);

    messageInfoCol = imapClient.ListMessages(query);
    // This count will be equal to the initial count
    Console.WriteLine("Updated Unread Count: " + messageInfoCol.Count());
}
else
{
    Console.WriteLine("No unread messages found");
}
```
## **Conexión al servidor mediante la autenticación CRAM-MD5**

Para una autenticación y un acceso seguros al servidor de correo electrónico, Aspose.Email for.NET ofrece un método de autenticación CRAM-MD5.
El siguiente fragmento de código le mostrará cómo funciona con el IMAPClient:

```cs
imapClient.AllowedAuthentication = ImapKnownAuthenticationType.CramMD5;
```

## **Cómo configurar el tiempo de espera para las operaciones de correo**

Cada operación de correo lleva algún tiempo dependiendo de muchos factores (retrasos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código que aparece a continuación muestra cómo hacerlo mediante el [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) propiedad. Nota: no debes establecer valores altos para evitar largas esperas en tu aplicación.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Cómo restringir el tiempo de espera de los saludos**

El cliente IMAP puede usar el modo automático para establecer una conexión. En este modo, el cliente IMAP revisa todos los parámetros de conexión posibles hasta que se establezca la conexión. En caso de que la conexión sea correcta, un servidor IMAP envía una cadena de saludo al cliente. Los servidores pueden iniciar la conexión SSL/TLS de forma implícita o explícita (START TLS). Si el modo de conexión no coincide (por ejemplo, el servidor espera una conexión SSL implícita pero el cliente intenta establecer una conexión SSL no segura o explícita), el servidor no enviará una cadena de saludo y el usuario esperará mucho tiempo hasta que se agote el tiempo de espera y el cliente pase a la siguiente opción de conexión. Para evitar este problema, se ha introducido la propiedad GreetingTimeout. Esta propiedad permite establecer el tiempo de espera de la cadena de saludo y reducir el tiempo de establecimiento automático de la conexión.

```cs
using (ImapClient client = new ImapClient("localhost", 993, "username", "password"))
{
    client.GreetingTimeout = 4000;
    client.SelectFolder(ImapFolderInfo.InBox);
}
```

## **Uso de protocolos criptográficos con el cliente IMAP**

Aspose.Email admite los protocolos criptográficos SSL (obsoletos) y TLS para brindar seguridad en las comunicaciones. Puede habilitar el cifrado criptográfico para proteger el intercambio de datos entre la aplicación y los servidores de correo.

> **_NOTE:_**  Debe establecer únicamente las versiones del protocolo compatibles con .NET Framework. Si su versión actual de .NET Framework no admite algunas versiones del protocolo criptográfico, se ignorarán y se omitirán. En este caso, no se generarán excepciones. Utilice, por favor [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) método si desea configurar los protocolos sin ninguna comprobación de compatibilidad.

El ejemplo de código siguiente muestra cómo configurar TLS 1.3 para [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) instancia de clase.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

En caso de que la versión actual de.NET Framework no admita un protocolo de cifrado especificado, la diferencia de comportamiento entre [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) método y [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) la propiedad es la siguiente:
- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) si se utiliza esta propiedad, el cliente de correo electrónico reduce el protocolo de cifrado a un nivel compatible.
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) si se utiliza este método, el cliente de correo electrónico lanza excepciones.
