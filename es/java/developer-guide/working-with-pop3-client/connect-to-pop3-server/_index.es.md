---
title: "Conectarse al servidor POP3"
url: /es/java/connect-to-pop3-server/
weight: 10
type: docs
---


The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) La clase permite a las aplicaciones administrar los buzones de correo electrónico mediante el Protocolo de oficina de correos, versión 3 (POP3). Para conectarse a un servidor, utilice el [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) clase. El [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class es la entrada principal para los desarrolladores que desean agregar la administración de POP3 a sus aplicaciones.NET. En este artículo se explica cómo utilizarla. Para conectarse a un servidor POP3:

1. Crea una instancia del [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.
1. Especifique el host, el nombre de usuario y la contraseña en [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) instance.

El siguiente fragmento de código muestra cómo conectarse con el servidor POP3.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Crea una instancia del Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Connected to POP3 server.");
~~~

## **Conexión al servidor SSL**

[Conexión a un servidor POP3](#connecting-to-pop3-server) describió cómo conectarse a un servidor POP3 en tres sencillos pasos:

1. Crea una instancia del [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.
1. Especifique el host, el nombre de usuario y la contraseña.

El proceso para conectarse a un servidor POP3 con SSL habilitado es similar, pero requiere establecer otras propiedades:

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Port

Para conectarse a un servidor POP3 con SSL habilitado, utilice el [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) clase y establece el [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) y propiedades portuarias. El siguiente fragmento de código muestra cómo conectarse a un servidor POP3 con SSL habilitado.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Crea una instancia del Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username and password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Connecting to POP3 server using SSL.");
~~~

## **Conexión con un servidor APOP**

POP son las siglas de Post Office Protocol. APOP son las siglas de Authenticated Post Office Protocol. APOP es una versión ampliada de la configuración del servidor POP3 que cifra el nombre de usuario y la contraseña y utiliza un mecanismo de autenticación diseñado para proteger la contraseña de la cuenta POP3 al revisar el correo electrónico. La autenticación APOP no requiere que la contraseña de la cuenta se envíe como texto sin formato al servidor de correo POP3.

## **Conexión al servidor mediante proxy**

Los servidores proxy son muy comunes para comunicarse con el mundo exterior. En estos casos, las direcciones proxy se utilizan para que los clientes de correo electrónico accedan a los buzones a través de Internet. Aspose.Email admite las versiones 4, 4a y 5 del protocolo de proxy SOCKS. Este artículo proporciona un ejemplo práctico de cómo recuperar correo electrónico mediante un servidor de correo proxy. Para recuperar el correo electrónico a través de un servidor proxy:

1. Initialize [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) con la información requerida, es decir, la dirección del proxy, el puerto y la versión de SOCKS.
1. Initialize [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) con la dirección del host, el nombre de usuario, la contraseña y cualquier otra configuración.
2. Establezca la propiedad Proxy del cliente en [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) objeto creado anteriormente.

El siguiente fragmento de código muestra cómo recuperar correos electrónicos a través de un servidor proxy.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Crea una instancia del Pop3Client class
Pop3Client client = new Pop3Client("pop.domain.com", "username", "password");

// Set proxy address, Port and Proxy
String proxyAddress = "192.168.203.142";
int proxyPort = 1080;
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
~~~

## **Conexión a un servidor mediante un proxy HTTP**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (Pop3Client client = new Pop3Client("imap.domain.com", "username", "password")) {
    client.setProxy(proxy);
    Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
}
~~~

## **Personalice el mecanismo de autenticación**

Recupere la lista de mecanismos de autenticación que admite el servidor POP3 mediante el [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getSupportedAuthentication--) método del [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) clase. Este método permite al cliente determinar qué métodos de autenticación están disponibles para establecer una conexión segura con el servidor. A continuación, utilizando el [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setAllowedAuthentication-long-) método que obtiene (o establece) la enumeración de los tipos de autenticación permitidos por el usuario, elija el mecanismo de autenticación más apropiado para la comunicación entre el cliente y el servidor. Esto le permite establecer el método de autenticación para el cliente de correo de forma explícita.

El siguiente ejemplo de código muestra cómo personalizar la autenticación del cliente de correo electrónico:

```java
pop3Client.setAllowedAuthentication(Pop3KnownAuthenticationType.Plain);
```

## **Soporte del protocolo OAuth 2.0 para la autorización**

OAuth 2.0 proporciona autorización

Pop3Client es compatible con OAuth 2.0 y proporciona formas de autorización específicas para las aplicaciones. Los siguientes constructores se utilizan para inicializar POP3Client mediante OAuth:

```java
public Pop3Client(

            String host, /*The host name*/

            int port, /*The port number*/

            String username, /*The user name*/

            ITokenProvider tokenProvider, /*TokenProvider allowing to retrieve access token*/

            /*SecurityOptions*/int securityOptions) /*Security mode for a mail client*/



public Pop3Client(

            String host, /*The host name*/

            int port, /*The port number*/

            String username, /*The user name*/

            String authInfo, /*The user password or XOAUTH2 access token*/

            boolean useOAuth, /*Defines whether SASL XOAUTH2 mechanism is used to login to the server*/

            /*SecurityOptions*/int securityOptions) /*Security mode for a mail client*/
```

## **Valide las credenciales del servidor de correo sin enviar correo electrónico**

A veces es necesario verificar las credenciales sin enviar un correo electrónico. Aspose.Email proporciona la [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#validateCredentials--) método para realizar esta operación. Si la validación se realiza correctamente, se ejecuta el código incluido en la sentencia if, que normalmente se utiliza para realizar otras acciones o recuperar datos del servidor IMAP. El siguiente fragmento de código muestra la validación de las credenciales sin enviar un correo electrónico:

```java
try (Pop3Client pop3Client = new Pop3Client(
        server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto)) {
    pop3Client.setTimeout(4000);

    if (pop3Client.validateCredentials()) {
        // to do something
    }
}
```

## **Uso de la autenticación CRAM-MD5 para conectarse a un servidor**

Para garantizar la autenticación y la comunicación seguras con el servidor POP3, puede especificar y hacer cumplir el uso de CRAM-MD5 como método de autenticación permitido para el cliente POP3. El siguiente fragmento de código muestra cómo configurar el tipo de autenticación permitido para [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/):

```java
popClient.setAllowedAuthentication(Pop3KnownAuthenticationType.CramMD5);
```
## **Cómo configurar el tiempo de espera para las operaciones de correo**

Cada operación de correo lleva algún tiempo dependiendo de muchos factores (retrasos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código que aparece a continuación muestra cómo hacerlo mediante el [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setTimeout-int-) propiedad. Nota: no debes establecer valores altos para evitar largas esperas en tu aplicación.

~~~Java
try (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.setTimeout(60000); // 60 seconds

    // some code...
}
~~~