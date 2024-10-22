---
title: "Conexión al Servidor IMAP"
url: /es/java/conexion-al-servidor-imap/
weight: 10
type: docs
---


La clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) permite a las aplicaciones gestionar buzones de correo IMAP utilizando el protocolo IMAP. La clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) se utiliza para conectarse a servidores de correo IMAP y gestionar correos electrónicos en las carpetas de correo IMAP. Para conectarse a un servidor IMAP

1. Cree una instancia de la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Especifique el nombre de host, el nombre de usuario y la contraseña en el [constructor de ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

Una vez que la instancia de [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) esté iniciada, la siguiente llamada a cualquier operación utilizando esta instancia se conectará al servidor. El siguiente fragmento de código le muestra cómo conectarse a un servidor IMAP usando los pasos anteriores.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Crear un imapclient con host, usuario y contraseña
ImapClient client = new ImapClient("localhost", "user", "password");
~~~

## **Conexión con Servidor IMAP Habilitado SSL**

[Conectarse con el Servidor IMAP](/email/java/conectarse-al-servidor-imap#conectarse-con-el-servidor-imap) describe cómo conectarse a un servidor IMAP en cuatro simples pasos:

1. Cree una instancia de la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Especifique el nombre de host, el nombre de usuario y la contraseña.
1. Especifique el puerto.
1. Especifique las [Opciones de Seguridad](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/).

El proceso para conectarse a un servidor IMAP habilitado SSL es similar, pero requiere que configure algunas propiedades adicionales:

- Establezca las [Opciones de Seguridad](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) en SSLImplicit.

El siguiente fragmento de código muestra cómo

1. Establecer un nombre de usuario, contraseña y puerto.
1. Establecer la opción de seguridad.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Crear una instancia de la clase ImapClient
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");

// Establecer el modo de seguridad en implícito
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~

## **Conexión al Servidor a través de Proxy**

Los servidores proxy se utilizan comúnmente para comunicarse con el mundo exterior. En tales casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección del proxy. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo proxy SOCKS. Este artículo proporciona un ejemplo funcional de acceso al buzón utilizando un servidor de correo proxy. Para acceder al buzón a través de un servidor proxy:

1. Inicialice [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) con la información requerida, es decir, dirección del proxy, puerto y versión SOCKS.
1. Inicialice [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) con la dirección del host, nombre de usuario, contraseña y cualquier otra configuración.
1. Establezca la propiedad [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) del cliente en el objeto [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) creado anteriormente.

El siguiente fragmento de código le muestra cómo recuperar el buzón a través de un servidor proxy.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
// Conectarse e iniciar sesión en IMAP y establecer SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);

String proxyAddress = "192.168.203.142"; // dirección del proxy
int proxyPort = 1080; // puerto del proxy
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Establecer el proxy
client.setProxy(proxy);

try {
    client.selectFolder("Inbox");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~ 

## **Conexión al Servidor a través de Proxy HTTP**

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
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

## **Personalizar Mecanismo de Autenticación**

Recupere la lista de mecanismos de autenticación que son soportados por el servidor IMAP utilizando el método [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getSupportedAuthentication--) de la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Este método permite al cliente determinar qué métodos de autenticación están disponibles para establecer una conexión segura con el servidor. Luego, utilizando el método [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setAllowedAuthentication-long-), que obtiene (o establece) la enumeración de los tipos de autenticación permitidos por el usuario, elija el mecanismo de autenticación más apropiado para la comunicación cliente-servidor. Esto permite establecer explícitamente el método de autenticación para el cliente de correo.

El siguiente ejemplo de código muestra cómo personalizar la autenticación del cliente de correo:

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.Plain);
```

## **Conexión al Servidor en Modo Solo Lectura**

La clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona una propiedad [ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) que, cuando se establece en **true**, indica que no se deben realizar cambios en el estado permanente del buzón. El siguiente ejemplo de código demuestra el uso de la propiedad [ImapClient.ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-). Obtiene el conteo de mensajes no leídos, luego recupera un mensaje y luego obtiene nuevamente el conteo de mensajes no leídos en modo solo lectura. El conteo de mensajes no leídos permanece igual, lo que indica que el estado permanente del buzón no ha cambiado.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.hasNoFlags(ImapMessageFlags.isRead()); /* obtener mensajes no leídos. */
MailQuery query = imapQueryBuilder.getQuery();

imapClient.setReadOnly(true);
imapClient.selectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.listMessages(query);
System.out.println("Conteo inicial de no leídos: " + messageInfoCol.size());
if (messageInfoCol.size() > 0) {
    imapClient.fetchMessage(messageInfoCol.get_Item(0).getSequenceNumber());

    messageInfoCol = imapClient.listMessages(query);
    // Este conteo será igual al conteo inicial
    System.out.println("Conteo actualizado de no leídos: " + messageInfoCol.size());
} else {
    System.out.println("No se encontraron mensajes no leídos");
}
~~~ 

## **Usar autenticación CRAM-MD5 para conectarse a un servidor**

Para asegurar la autenticación y comunicación seguras con el servidor IMAP, puede especificar y hacer cumplir el uso de CRAM-MD5 como el método de autenticación permitido para el cliente IMAP. El siguiente fragmento de código muestra cómo configurar el tipo de autenticación permitida para el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.CramMD5);
```

## **Validar Credenciales de Servidor de Correo Sin Enviar Correo**

A veces es necesario verificar credenciales sin enviar un correo electrónico. Aspose.Email proporciona el método [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#validateCredentials--) para realizar esta operación. Si la validación tiene éxito, el código dentro de la instrucción if se ejecuta, generalmente utilizado para realizar acciones adicionales o recuperar datos del servidor IMAP. El siguiente fragmento de código demuestra la validación de credenciales sin enviar un correo electrónico:

```java
try (ImapClient imapClient = new ImapClient(
        server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto)) {
    imapClient.setTimeout(4000);

    if (imapClient.validateCredentials()) {
        // realizar alguna acción
    }
}
```

## **Cómo Establecer Tiempo de Espera para Operaciones de Correo**

Cada operación de correo toma algo de tiempo dependiendo de muchos factores (retardos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El siguiente ejemplo de código le muestra cómo hacerlo utilizando la propiedad [Timeout](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setTimeout-int-). Nota: no debe establecer valores grandes para evitar largas esperas en su aplicación.

~~~Java
try (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.setTimeout(60000); // 60 segundos

    // algún código...
}
~~~ 

## **Cómo Restringir el Tiempo de Espera de Saludo**

El cliente IMAP puede usar el modo automático para establecer una conexión. En este modo, el cliente IMAP pasa por todos los parámetros de conexión posibles hasta que la conexión se establece. Un servidor IMAP en caso de conexión correcta envía una cadena de saludo al cliente. Los servidores pueden usar la iniciación de conexión SSL/TLS implícita o explícita (START TLS). Si el modo de conexión no coincide (por ejemplo, el servidor espera una conexión SSL implícita pero el cliente intenta establecer una conexión no segura o explícita SSL), el servidor no enviará una cadena de saludo y el usuario esperará mucho tiempo hasta que el tiempo de espera alcance una cadena de saludo, y el cliente pase a la siguiente opción de conexión. Para evitar este problema, se ha introducido GreetingTimeout. Esta propiedad le permite establecer el tiempo de espera para la cadena de saludo y reducir el tiempo de establecimiento de conexión automática.

```java
ImapClient imapClient = new ImapClient();
imapClient.setGreetingTimeout(4000);
```