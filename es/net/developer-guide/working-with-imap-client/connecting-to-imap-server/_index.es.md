---
title: "Conectar al Servidor IMAP"
url: /es/net/conectando-al-servidor-imap/
weight: 10
type: docs
---

La clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) permite a las aplicaciones gestionar buzones de correo IMAP utilizando el protocolo IMAP. La clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se utiliza para conectarse a servidores de correo IMAP y gestionar correos electrónicos en las carpetas de correo IMAP. Para conectarse a un servidor IMAP

1. Cree una instancia de la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
1. Especifique el nombre de host, el nombre de usuario y la contraseña en el [constructor de ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor_8).

**Nota: las restricciones de contraseña deben cumplir con los requisitos del servidor. El cliente de correo no añade restricciones de contraseña.**

Una vez que la instancia de [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) está iniciada, la siguiente llamada a cualquier operación utilizando esta instancia se conectará al servidor. El siguiente fragmento de código le muestra cómo conectarse a un servidor IMAP utilizando los pasos anteriores.

```csharp
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear un imapclient con host, usuario y contraseña
ImapClient client = new ImapClient("localhost", "user", "password");
```

## **Conectando con Servidor IMAP con SSL Activado**

[Conectando con Servidor IMAP](/email/net/connecting-to-imap-server#connecting-with-imap-server) describió cómo conectarse a un servidor IMAP en cuatro simples pasos:

1. Cree una instancia de la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
1. Especifique el nombre de host, el nombre de usuario y la contraseña.
1. Especifique el puerto.
1. Especifique las Opciones de Seguridad.

El proceso para conectarse a un servidor IMAP habilitado para SSL es similar, pero requiere que establezca algunas propiedades más:

- Establecer Opciones de Seguridad a SSLImplicit.

El siguiente fragmento de código muestra cómo

1. Establecer un nombre de usuario, contraseña y puerto.
1. Establecer opción de seguridad.

```csharp
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear una instancia de la clase ImapClient
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");
            
// Establecer el modo de seguridad a implícito
client.SecurityOptions = SecurityOptions.SSLImplicit;
```

## **Conectando al Servidor a través de Proxy**

Los servidores proxy se utilizan comúnmente para comunicarse con el exterior. En tales casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección del proxy. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo SOCKS. Este artículo proporciona un ejemplo funcional de acceso al buzón utilizando un servidor de correo proxy. Para acceder al buzón a través de un servidor proxy:

1. Inicialice [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) con la información requerida, es decir, dirección proxy, puerto y versión SOCKS.
1. Inicialice [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) con la dirección del host, nombre de usuario, contraseña y cualquier otra configuración.
1. Establezca la propiedad [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) del cliente al objeto [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) creado anteriormente.

El siguiente fragmento de código le muestra cómo recuperar el buzón a través de un servidor proxy.

```csharp
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-.NET
// Conectar e iniciar sesión en IMAP y establecer opciones de seguridad
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.SecurityOptions = SecurityOptions.Auto;
            
string proxyAddress = "192.168.203.142"; // dirección proxy
int proxyPort = 1080; // puerto proxy
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Establecer el proxy
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

## **Conectando al Servidor a través de Proxy HTTP**

```csharp
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-.NET
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
using (ImapClient client = new ImapClient("imap.domain.com", "username", "password"))
{
    client.Proxy = proxy;
    client.SelectFolder("Inbox");
}
```

## **Conectando al Servidor en Modo de Solo Lectura**

La clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona una propiedad [ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) que, cuando se establece en **true**, indica que no se deben realizar cambios en el estado permanente del buzón. El siguiente ejemplo de código demuestra el uso de la propiedad [ImapClient.ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/). Obtiene el conteo de mensajes no leídos, luego recupera un mensaje y después obtiene el conteo de mensajes no leídos nuevamente en modo de solo lectura. El conteo de los mensajes no leídos permanece igual, indicando que el estado permanente del buzón no ha sido cambiado.

```csharp
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-.NET
ImapClient imapClient = new ImapClient();
imapClient.Host = "<HOST>";
imapClient.Port = 993;
imapClient.Username = "<USERNAME>";
imapClient.Password = "<PASSWORD>";
imapClient.SupportedEncryption = EncryptionProtocols.Tls;
imapClient.SecurityOptions = SecurityOptions.SSLImplicit;

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.HasNoFlags(ImapMessageFlags.IsRead); /* obtener mensajes no leídos. */
MailQuery query = imapQueryBuilder.GetQuery();

imapClient.ReadOnly = true;
imapClient.SelectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.ListMessages(query);
Console.WriteLine("Conteo Inicial de No Leídos: " + messageInfoCol.Count());
if (messageInfoCol.Count() > 0)
{
    imapClient.FetchMessage(messageInfoCol[0].SequenceNumber);

    messageInfoCol = imapClient.ListMessages(query);
    // Este conteo será igual al conteo inicial
    Console.WriteLine("Conteo Actualizado de No Leídos: " + messageInfoCol.Count());
}
else
{
    Console.WriteLine("No se encontraron mensajes no leídos");
}
```
## **Conectando al Servidor utilizando autenticación CRAM-MD5**

Para autenticación segura y acceso al servidor de correo, Aspose.Email para .NET ofrece un método de autenticación CRAM-MD5.
El siguiente fragmento de código le mostrará cómo funciona con el ImapClient:

```cs
imapClient.AllowedAuthentication = ImapKnownAuthenticationType.CramMD5;
```

## **Cómo Establecer Timeout para Operaciones de Correo**

Cada operación de correo toma algún tiempo dependiendo de muchos factores (retrasos de red, tamaño de datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código a continuación muestra cómo hacerlo utilizando la propiedad [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/). Nota: no debe establecer valores grandes para evitar esperas prolongadas en su aplicación.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.Timeout = 60000; // 60 segundos

    // algún código...
}
```

## **Cómo Restringir el Timeout de Saludo**

El cliente IMAP puede utilizar el modo automático para establecer una conexión. En este modo, el cliente IMAP pasa por todos los parámetros de conexión posibles hasta que se establece la conexión. Un servidor IMAP en caso de una conexión correcta envía una cadena de saludo al cliente. Los servidores pueden utilizar la iniciación de conexión SSL/TLS implícita o explícita (START TLS). Si el modo de conexión no coincide (por ejemplo, el servidor espera una conexión SSL implícita pero el cliente intenta establecer una conexión no segura o explícita de SSL), el servidor no enviará una cadena de saludo y el usuario esperará mucho tiempo hasta que el tiempo de espera alcance la cadena de saludo, y el cliente pase a la siguiente opción de conexión. Para evitar este problema, se ha introducido la propiedad GreetingTimeout. Esta propiedad le permite establecer el tiempo de espera para la cadena de saludo y reducir el tiempo de establecimiento de conexión automática.

```cs
using (ImapClient client = new ImapClient("localhost", 993, "username", "password"))
{
    client.GreetingTimeout = 4000;
    client.SelectFolder(ImapFolderInfo.InBox);
}
```

## **Usando Protocolos Criptográficos con el Cliente IMAP**

Aspose.Email admite SSL (obsoleto) y protocolos criptográficos TLS para proporcionar seguridad en las comunicaciones. Puede habilitar la encriptación criptográfica para proteger el intercambio de datos entre su aplicación y los servidores de correo.

> **_NOTA:_** Debe establecer solo aquellas versiones del protocolo que sean compatibles con el .NET Framework. Si algunas versiones del protocolo criptográfico no son compatibles con su versión actual de .NET Framework, serán ignoradas y omitidas. En este caso, no se generarán excepciones. Utilice el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) si desea establecer los protocolos sin ninguna verificación de compatibilidad.

El ejemplo de código a continuación muestra cómo establecer TLS 1.3 para la instancia de la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // algún código...
}
```

En caso de que un protocolo de encriptación especificado no sea compatible en la versión actual del .NET Framework, la diferencia de comportamiento entre el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) y la propiedad [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) es la siguiente:
- Si se utiliza la propiedad [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/), el cliente de correo degradará el protocolo de encriptación a un nivel compatible.
- Si se utiliza el método [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe), el cliente de correo lanzará excepciones.