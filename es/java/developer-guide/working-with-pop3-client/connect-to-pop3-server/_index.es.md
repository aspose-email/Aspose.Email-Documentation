---
title: "Conectar a un servidor POP3"
url: /es/java/connect-to-pop3-server/
weight: 10
type: docs
---


La clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) permite a las aplicaciones gestionar buzones de correo utilizando el Protocolo de Oficina de Correos, Versión 3 (POP3). Para conectarse a un servidor, utilice la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). La clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) es la entrada principal para los desarrolladores que desean agregar gestión POP3 a sus aplicaciones .NET. Este artículo explica cómo usarla. Para conectarse a un servidor POP3:

1. Cree una instancia de la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Especifique el host, el nombre de usuario y la contraseña en la instancia [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

El siguiente fragmento de código le muestra cómo conectarse al servidor POP3.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java

// Cree una instancia de la clase Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nombre de usuario, contraseña, Puerto y SecurityOptions para su cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Conectado al servidor POP3.");
~~~

## **Conectando a un servidor SSL**

[Conectarse a un servidor POP3](#connecting-to-pop3-server) describió cómo conectarse a un servidor POP3 en tres pasos simples:

1. Cree una instancia de la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Especifique el host, el nombre de usuario y la contraseña.

El proceso para conectarse a un servidor POP3 habilitado para SSL es similar, pero requiere que establezca algunas propiedades adicionales:

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Puerto

Para conectarse a un servidor POP3 habilitado para SSL, utilice la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) y establezca las propiedades [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) y Puerto. El siguiente fragmento de código le muestra cómo conectarse a un servidor POP3 habilitado para SSL.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java

// Cree una instancia de la clase Pop3Client
Pop3Client client = new Pop3Client();

// Especifique host, nombre de usuario y contraseña, Puerto y SecurityOptions para su cliente
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Conectando al servidor POP3 usando SSL.");
~~~

## **Conectando con un servidor APOP**

POP significa Protocolo de Oficina de Correos. APOP significa Protocolo de Oficina de Correos Autenticado. APOP es una versión extendida de la configuración del servidor POP3 que cifra su nombre de usuario y contraseña y utiliza un mecanismo de autenticación diseñado para proteger la contraseña de su cuenta POP3 al revisar el correo electrónico. La autenticación APOP no requiere que la contraseña de la cuenta se envíe en texto plano al servidor de correo POP3.

## **Conectando al servidor a través de un proxy**

Los servidores proxy son muy comunes para comunicarse con el mundo exterior. En tales casos, se utilizan direcciones proxy para que los clientes de correo electrónico accedan a los buzones a través de Internet. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo proxy SOCKS. Este artículo proporciona un ejemplo funcional de cómo recuperar correos electrónicos utilizando un servidor de correo proxy. Para recuperar correos electrónicos a través de un servidor proxy:

1. Inicialice [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) con la información requerida, es decir, dirección proxy, puerto y versión de SOCKS.
1. Inicialice [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) con la dirección del host, nombre de usuario, contraseña y cualquier otra configuración.
2. Establezca la propiedad Proxy del cliente al objeto [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) creado anteriormente.

El siguiente fragmento de código le muestra cómo recuperar correos electrónicos a través de un servidor proxy.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java

// Cree una instancia de la clase Pop3Client
Pop3Client client = new Pop3Client("pop.domain.com", "username", "password");

// Establezca la dirección del proxy, el Puerto y el Proxy
String proxyAddress = "192.168.203.142";
int proxyPort = 1080;
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
~~~

## **Conectando a un servidor a través de un proxy HTTP**

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (Pop3Client client = new Pop3Client("imap.domain.com", "username", "password")) {
    client.setProxy(proxy);
    Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
}
~~~

## **Personalizar el mecanismo de autenticación**

Recupere la lista de mecanismos de autenticación que son compatibles con el servidor POP3 utilizando el método [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getSupportedAuthentication--) de la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). Este método permite al cliente determinar qué métodos de autenticación están disponibles para establecer una conexión segura con el servidor. Luego, usando el método [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setAllowedAuthentication-long-), que obtiene (o establece) la enumeración de los tipos de autenticación permitidos por el usuario, elija el mecanismo de autenticación más apropiado para la comunicación cliente-servidor. Esto le permite establecer explícitamente el método de autenticación para el cliente de correo.

El siguiente ejemplo de código muestra cómo personalizar la autenticación del cliente de correo electrónico:

```java
pop3Client.setAllowedAuthentication(Pop3KnownAuthenticationType.Plain);
```

## **Soporte del protocolo OAuth 2.0 para autorización**

OAuth 2.0 proporciona autorización

Pop3Client admite OAuth 2.0 proporcionando formas específicas de autorización para aplicaciones. Los siguientes constructores se utilizan para inicializar POP3Client utilizando OAuth:

```java
public Pop3Client(

            String host, /*El nombre del host*/

            int port, /*El número del puerto*/ 

            String username, /*El nombre de usuario*/

            ITokenProvider tokenProvider, /*TokenProvider que permite recuperar el token de acceso*/

            /*SecurityOptions*/int securityOptions) /*Modo de seguridad para un cliente de correo*/



public Pop3Client(

            String host, /*El nombre del host*/

            int port, /*El número del puerto*/

            String username, /*El nombre de usuario*/

            String authInfo, /*La contraseña del usuario o token de acceso XOAUTH2*/

            boolean useOAuth, /*Define si se usa el mecanismo SASL XOAUTH2 para iniciar sesión en el servidor*/

            /*SecurityOptions*/int securityOptions) /*Modo de seguridad para un cliente de correo*/
```

## **Validar credenciales del servidor de correo sin enviar correo electrónico**

A veces es necesario verificar las credenciales sin enviar un correo electrónico. Aspose.Email proporciona el método [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#validateCredentials--) para realizar esta operación. Si la validación tiene éxito, se ejecuta el código dentro de la declaración if, generalmente utilizado para realizar acciones adicionales o recuperar datos del servidor IMAP. El siguiente fragmento de código demuestra la validación de credenciales sin enviar un correo electrónico:

```java
try (Pop3Client pop3Client = new Pop3Client(
        server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto)) {
    pop3Client.setTimeout(4000);

    if (pop3Client.validateCredentials()) {
        // hacer algo
    }
}
```

## **Usar autenticación CRAM-MD5 para conectarse a un servidor**

Para garantizar una autenticación y comunicación seguras con el servidor POP3, puede especificar y hacer cumplir el uso de CRAM-MD5 como el método de autenticación permitido para el cliente POP3. El siguiente fragmento de código muestra cómo configurar el tipo de autenticación permitida para el [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/):

```java
popClient.setAllowedAuthentication(Pop3KnownAuthenticationType.CramMD5);
```
## **Cómo establecer un tiempo de espera para las operaciones de correo**

Cada operación de correo toma algún tiempo dependiendo de muchos factores (retardos de red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código a continuación le muestra cómo hacer eso utilizando la propiedad [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setTimeout-int-). Nota: no debe establecer valores grandes para evitar largas esperas en su aplicación.

~~~Java
try (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.setTimeout(60000); // 60 segundos

    // algún código...
}
~~~