---
title: "Conexión al servidor SMTP"
url: /es/java/connecting-to-smtp-server/
weight: 10
type: docs
---


Es necesario establecer las siguientes propiedades al conectarse a un servidor SMTP compatible con SSL.

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Port

En los ejemplos siguientes mostramos cómo:

1. Establece un nombre de usuario.
1. Establece una contraseña.
1. Configure el puerto.
1. Defina la opción de seguridad.

El siguiente fragmento de código muestra cómo conectar un servidor SMTP con SSL habilitado.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com");

// Set username, password, port, and security options
client.setUsername("your.email@gmail.com");
client.setPassword("your.password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~

## **Conexión al servidor a través de Socks Proxy Sever**

A veces utilizamos servidores proxy para comunicarnos con el mundo exterior. En estos casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección de proxy. Aspose.Email admite las versiones 4, 4a y 5 del protocolo proxy SOCKS. Este artículo proporciona un ejemplo práctico del envío de correos electrónicos mediante un servidor de correo proxy. Para enviar un correo electrónico a través de un servidor proxy:

1. Inicialice el proxy con la información requerida, es decir, la dirección del proxy, el puerto y la versión de SOCKS.
1. Initialize [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) con la dirección del host, el nombre de usuario y la contraseña y cualquier otra configuración.
1. Establezca la propiedad Proxy del cliente en [Proxy](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getProxy--) objeto creado anteriormente.

El siguiente fragmento de código muestra cómo conectarse a un servidor mediante un servidor proxy.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.SSLImplicit);
String proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy",
        "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"));
~~~

## **Conexión al servidor mediante un servidor proxy HTTP**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (SmtpClient client = new SmtpClient("host", 587, "username", "password")) {
    client.setProxy(proxy);
    client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy",
            "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"));
}
~~~

## **Personalice el mecanismo de autenticación**

Recupere la lista de mecanismos de autenticación que admite el servidor SMTP mediante el [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getSupportedAuthentication--) método del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase. Este método permite al cliente determinar qué métodos de autenticación están disponibles para establecer una conexión segura con el servidor. A continuación, utilizando el [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setAllowedAuthentication-long-) método que obtiene (o establece) la enumeración de los tipos de autenticación permitidos por el usuario, elija el mecanismo de autenticación más apropiado para la comunicación entre el cliente y el servidor. Esto le permite establecer el método de autenticación para el cliente de correo de forma explícita.

El siguiente ejemplo de código muestra cómo personalizar la autenticación del cliente de correo electrónico:

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.Login);
```
## **Uso de la autenticación CRAM-MD5 para conectarse a un servidor**

Para garantizar la autenticación y la comunicación seguras con el servidor SMTP, puede especificar y hacer cumplir el uso de CRAM-MD5 como método de autenticación permitido para el cliente SMTP. El siguiente fragmento de código muestra cómo configurar el tipo de autenticación permitido para [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/):

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.CramMD5);
```

## **Vincular el cliente SMTP a una dirección IP específica en el host**

No se puede descartar la posibilidad de que un host tenga varios puertos disponibles para enviar correos electrónicos. En tales casos, puede surgir la necesidad de vincular el cliente de envío de correo electrónico a un puerto específico del host para enviar correos electrónicos. Esto también se puede lograr con la API Aspose.Email utilizando la [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) [bindIPEndPoint](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#bindIPEndPoint-com.aspose.email.BindIPEndPointHandler-) propiedad. La API [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) se puede configurar para usar una dirección IP específica en el host especificando el punto final IP específico. El siguiente fragmento de código muestra cómo vincular el cliente SMTP a una dirección IP específica del host.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", // host
        587, // port
        "username", // username
        "password", // password
        SecurityOptions.Auto // Security Options
);
try {
    client.bindIPEndPoint(new BindIPEndPointHandler() {
        public InetSocketAddress invoke(InetSocketAddress remoteEndPoint) {
            return new InetSocketAddress(0);
        }
    });
    client.noop();
} finally {
    client.dispose();
}
~~~

## **Valide las credenciales del servidor de correo sin enviar correo electrónico**

A veces es necesario verificar las credenciales sin enviar un correo electrónico. Aspose.Email proporciona la [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#validateCredentials--) método para realizar esta operación. Si la validación se realiza correctamente, se ejecuta el código incluido en la sentencia if, que normalmente se utiliza para realizar otras acciones o recuperar datos del servidor IMAP. El siguiente fragmento de código muestra la validación de las credenciales sin enviar un correo electrónico:

```java
try (SmtpClient smtpClient = new SmtpClient(
        server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto)) {
    smtpClient.setTimeout(4000);

    if (smtpClient.validateCredentials()) {
        // to do something
    }
}
```

## **Cómo configurar el tiempo de espera para las operaciones de correo**

Cada operación de correo lleva algún tiempo dependiendo de muchos factores (retrasos en la red, tamaño de los datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código que aparece a continuación muestra cómo hacerlo mediante el [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getTimeout--) propiedad. Nota: no debes establecer valores altos para evitar largas esperas en tu aplicación.

~~~Java
try (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~