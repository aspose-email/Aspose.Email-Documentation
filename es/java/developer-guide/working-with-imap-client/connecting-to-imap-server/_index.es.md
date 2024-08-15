---
title: "Conexión al servidor IMAP"
url: /es/java/connecting-to-imap-server/
weight: 10
type: docs
---


The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) La clase permite a las aplicaciones administrar los buzones IMAP mediante el protocolo IMAP. El [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) La clase se usa para conectarse a los servidores de correo IMAP y administrar los correos electrónicos en las carpetas de correo electrónico IMAP. Para conectarse a un servidor IMAP

1. Crea una instancia del [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Especifique el nombre de host, el nombre de usuario y la contraseña en el [Constructor IMAPClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

Una vez que [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) se inicia la instancia, la siguiente llamada a cualquier operación que utilice esta instancia se conectará al servidor. El siguiente fragmento de código muestra cómo conectarse a un servidor IMAP siguiendo los pasos anteriores.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");
~~~

## **Conexión con un servidor IMAP con SSL habilitado**

[Conexión con el servidor IMAP](/email/java/connecting-to-imap-server#connecting-with-imap-server) describió cómo conectarse a un servidor IMAP en cuatro sencillos pasos:

1. Crea una instancia del [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Especifique el nombre de host, el nombre de usuario y la contraseña.
1. Especifique el puerto.
1. Especifique el [Opciones de seguridad](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/).

El proceso para conectarse a un servidor IMAP con SSL habilitado es similar, pero requiere que defina otras propiedades:

- Set [Opciones de seguridad](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) a SSSImplicit.

El siguiente fragmento de código muestra cómo

1. Establezca un nombre de usuario, una contraseña y un puerto.
1. Defina la opción de seguridad.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Crea una instancia del ImapClient class
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");

// Set the security mode to implicit
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~

## **Conexión al servidor mediante proxy**

Los servidores proxy se utilizan habitualmente para comunicarse con el mundo exterior. En estos casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección de proxy. Aspose.Email admite las versiones 4, 4a y 5 del protocolo de proxy SOCKS. Este artículo proporciona un ejemplo práctico de cómo acceder al buzón de correo mediante un servidor de correo proxy. Para acceder al buzón a través de un servidor proxy:

1. Initialize [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) con la información requerida, es decir, la dirección del proxy, el puerto y la versión de SOCKS.
1. Initialize [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) con la dirección del host, el nombre de usuario, la contraseña y cualquier otra configuración.
1. Configurar el cliente [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) propiedad a la [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) objeto creado anteriormente.

El siguiente fragmento de código muestra cómo recuperar el buzón de correo a través de un servidor proxy.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP and set SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);

String proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Set the proxy
client.setProxy(proxy);

try {
    client.selectFolder("Inbox");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Conexión al servidor mediante un proxy HTTP**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
final ImapClient client = new ImapClient("imap.domain.com", "username", "password");
try {
    client.setProxy(proxy);
    client.selectFolder("Inbox");
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Personalice el mecanismo de autenticación**

Recupere la lista de mecanismos de autenticación que admite el servidor IMAP mediante el [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getSupportedAuthentication--) método del [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) clase. Este método permite al cliente determinar qué métodos de autenticación están disponibles para establecer una conexión segura con el servidor. A continuación, utilizando el [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setAllowedAuthentication-long-) método que obtiene (o establece) la enumeración de los tipos de autenticación permitidos por el usuario, elija el mecanismo de autenticación más apropiado para la comunicación entre el cliente y el servidor. Esto le permite establecer el método de autenticación para el cliente de correo de forma explícita.

El siguiente ejemplo de código muestra cómo personalizar la autenticación del cliente de correo electrónico:

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.Plain);
```

## **Conexión al servidor en modo de solo lectura**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) la clase proporciona una [ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) propiedad que, cuando se establece en **true**, indica que no se deben realizar cambios en el estado permanente del buzón. El siguiente ejemplo de código demuestra el uso de [ImapClient.ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) propiedad. Obtiene el recuento de mensajes no leídos, luego recupera un mensaje y, a continuación, vuelve a obtener el recuento de mensajes no leídos en modo de solo lectura. El recuento de los mensajes no leídos sigue siendo el mismo, lo que indica que el estado permanente del buzón no se modificó.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.hasNoFlags(ImapMessageFlags.isRead()); /* get unread messages. */
MailQuery query = imapQueryBuilder.getQuery();

imapClient.setReadOnly(true);
imapClient.selectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.listMessages(query);
System.out.println("Initial Unread Count: " + messageInfoCol.size());
if (messageInfoCol.size() > 0) {
    imapClient.fetchMessage(messageInfoCol.get_Item(0).getSequenceNumber());

    messageInfoCol = imapClient.listMessages(query);
    // This count will be equal to the initial count
    System.out.println("Updated Unread Count: " + messageInfoCol.size());
} else {
    System.out.println("No unread messages found");
}
~~~

## **Uso de la autenticación CRAM-MD5 para conectarse a un servidor**

Para garantizar la autenticación y la comunicación seguras con el servidor IMAP, puede especificar y hacer cumplir el uso del CRAM-MD5 como método de autenticación permitido para el cliente IMAP. El siguiente fragmento de código muestra cómo configurar el tipo de autenticación permitido para el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.CramMD5);
```
## **Valide las credenciales del servidor de correo sin enviar correo electrónico**

A veces es necesario verificar las credenciales sin enviar un correo electrónico. Aspose.Email proporciona la [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#validateCredentials--) método para realizar esta operación. Si la validación se realiza correctamente, se ejecuta el código incluido en la sentencia if, que normalmente se utiliza para realizar otras acciones o recuperar datos del servidor IMAP. El siguiente fragmento de código muestra la validación de las credenciales sin enviar un correo electrónico:

```java
try (ImapClient imapClient = new ImapClient(
        server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto)) {
    imapClient.setTimeout(4000);

    if (imapClient.validateCredentials()) {
        // to do something
    }
}
```

## **Cómo configurar el tiempo de espera para las operaciones de correo**

Cada operación de correo lleva algún tiempo dependiendo de muchos factores (retrasos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código que aparece a continuación muestra cómo hacerlo mediante el [Timeout](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setTimeout-int-) propiedad. Nota: no debes establecer valores altos para evitar largas esperas en tu aplicación.

~~~Java
try (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~

## **Cómo restringir el tiempo de espera de los saludos**

El cliente IMAP puede usar el modo automático para establecer una conexión. En este modo, el cliente IMAP revisa todos los parámetros de conexión posibles hasta que se establezca la conexión. En caso de que la conexión sea correcta, un servidor IMAP envía una cadena de saludo al cliente. Los servidores pueden iniciar la conexión SSL/TLS de forma implícita o explícita (START TLS). Si el modo de conexión no coincide (por ejemplo, el servidor espera una conexión SSL implícita pero el cliente intenta establecer una conexión SSL no segura o explícita), el servidor no enviará una cadena de saludo y el usuario esperará mucho tiempo hasta que se agote el tiempo de espera y el cliente pase a la siguiente opción de conexión. Para evitar este problema, se ha introducido el GreetingTimeout. Esta propiedad permite establecer el tiempo de espera de la cadena de saludo y reducir el tiempo de establecimiento automático de la conexión.

```java
ImapClient imapClient = new ImapClient();
imapClient.setGreetingTimeout(4000);
```
