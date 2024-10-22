---
title: "Conexión al servidor SMTP"
url: /es/java/conexion-al-servidor-smtp/
weight: 10
type: docs
---


Las siguientes propiedades deben configurarse al conectarse a un servidor SMTP con soporte SSL.

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Puerto

En los ejemplos a continuación mostramos cómo:

1. Establecer un nombre de usuario.
1. Establecer una contraseña.
1. Establecer el puerto.
1. Establecer la opción de seguridad.

El siguiente fragmento de código muestra cómo conectarse a un servidor SMTP habilitado para SSL.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com");

// Set username, password, port, and security options
client.setUsername("your.email@gmail.com");
client.setPassword("your.password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~

## **Conectar al servidor a través de un servidor proxy SOCKS**

A veces usamos servidores proxy para comunicarnos con el mundo exterior. En tales casos, los clientes de correo no pueden comunicarse a través de Internet sin especificar la dirección del proxy. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo proxy SOCKS. Este artículo proporciona un ejemplo funcional de envío de correo electrónico utilizando un servidor de correo proxy. Para enviar un correo electrónico a través de un servidor proxy:

1. Inicialice el proxy con la información requerida, es decir, dirección del proxy, puerto y versión SOCKS.
1. Inicialice [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) con la dirección del host, el nombre de usuario y la contraseña, y cualquier otra configuración.
1. Establezca la propiedad Proxy del cliente en el objeto [Proxy](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getProxy--) creado anteriormente.

El siguiente fragmento de código muestra cómo conectarse a un servidor a través de un servidor proxy.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.SSLImplicit);
String proxyAddress = "192.168.203.142"; // dirección del proxy
int proxyPort = 1080; // puerto del proxy
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Enviando correo electrónico a través del proxy",
        "Implementar el protocolo proxy SOCKS para las versiones 4, 4a, 5 (solo autenticación de nombre de usuario/contraseña)"));
~~~ 

## **Conectar al servidor a través de un servidor proxy HTTP**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (SmtpClient client = new SmtpClient("host", 587, "username", "password")) {
    client.setProxy(proxy);
    client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Enviando correo electrónico a través del proxy",
            "Implementar el protocolo proxy SOCKS para las versiones 4, 4a, 5 (solo autenticación de nombre de usuario/contraseña)"));
}
~~~ 

## **Personalizar mecanismo de autenticación**

Recupere la lista de mecanismos de autenticación que son compatibles con el servidor SMTP utilizando el método [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getSupportedAuthentication--) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Este método permite al cliente determinar qué métodos de autenticación están disponibles para establecer una conexión segura con el servidor. Luego, utilizando el método [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setAllowedAuthentication-long-) que obtiene (o establece) la enumeración de los tipos de autenticación permitidos por el usuario, elija el mecanismo de autenticación más apropiado para la comunicación cliente-servidor. Esto permite establecer el método de autenticación para el cliente de correo explícitamente.

El siguiente ejemplo de código muestra cómo personalizar la autenticación del cliente de correo electrónico:

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.Login);
```

## **Usar autenticación CRAM-MD5 para conectarse a un servidor**

Para asegurar la autenticación y comunicación seguras con el servidor SMTP, puede especificar y hacer cumplir el uso de CRAM-MD5 como el método de autenticación permitido para el cliente SMTP. El siguiente fragmento de código muestra cómo configurar el tipo de autenticación permitida para el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/):

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.CramMD5);
```

## **Vincular el cliente SMTP a una dirección IP específica en el host**

No se puede descartar la posibilidad de que un host tenga múltiples puertos disponibles para el envío de correos electrónicos. En tales casos, puede surgir la necesidad de vincular el cliente de envío de correo a un puerto específico en el host para enviar correos electrónicos. Esto se puede lograr con la API de Aspose.Email usando la propiedad [bindIPEndPoint](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#bindIPEndPoint-com.aspose.email.BindIPEndPointHandler-) de [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). La API [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) se puede configurar para usar una dirección IP específica en el host especificando el punto final IP específico. El siguiente fragmento de código muestra cómo vincular el cliente SMTP a una dirección IP específica en el host.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", // host
        587, // puerto
        "nombredeusuario", // nombre de usuario
        "contraseña", // contraseña
        SecurityOptions.Auto // Opciones de seguridad
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

## **Validar credenciales del servidor de correo sin enviar correo electrónico**

A veces es necesario verificar credenciales sin enviar un correo electrónico. Aspose.Email proporciona el método [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#validateCredentials--) para realizar esta operación. Si la validación es exitosa, se ejecuta el código dentro de la sentencia if, generalmente utilizado para realizar acciones adicionales o recuperar datos del servidor IMAP. El siguiente fragmento de código demuestra la validación de credenciales sin enviar un correo electrónico:

```java
try (SmtpClient smtpClient = new SmtpClient(
        server.SmtpUrl, server.SmtpPort, "nombredeusuario", "contraseña", SecurityOptions.Auto)) {
    smtpClient.setTimeout(4000);

    if (smtpClient.validateCredentials()) {
        // hacer algo
    }
}
```

## **Cómo establecer un tiempo de espera para operaciones de correo**

Cada operación de correo lleva algo de tiempo dependiendo de muchos factores (retrasos de red, tamaño de datos, rendimiento del servidor, etc.). Puede establecer un tiempo de espera para todas las operaciones de correo. El ejemplo de código a continuación muestra cómo hacerlo utilizando la propiedad [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getTimeout--). Nota: no debe establecer valores grandes para evitar esperas largas en su aplicación.

~~~Java
try (SmtpClient smtpClient = new SmtpClient("host", 587, "nombredeusuario", "contraseña", SecurityOptions.SSLExplicit))
{
    smtpClient.setTimeout(60000); // 60 segundos

    // algo de código...
}
~~~