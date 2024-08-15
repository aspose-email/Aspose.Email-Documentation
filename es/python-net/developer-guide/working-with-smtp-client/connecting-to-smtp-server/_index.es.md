---
title: "Conexión al servidor SMTP"
url: /es/python-net/connecting-to-smtp-server/
weight: 10
type: docs
---


## **Conexión de un servidor SMTP habilitado para SSL**
Es necesario establecer las siguientes propiedades al conectarse a un servidor SMTP compatible con SSL.

- SecurityOptions
- Port

En los ejemplos siguientes mostramos cómo:

1. Establece un nombre de usuario.
1. Establece una contraseña.
1. Configure el puerto.
1. Defina la opción de seguridad.

El siguiente fragmento de código muestra cómo conectar un servidor SMTP con SSL habilitado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SSLEnabledSMTPServer-SSLEnabledSMTPServer.py" >}}

### **Establezca un tiempo de espera para la respuesta de saludo del servidor**

Para mejorar la eficiencia de las operaciones de los clientes de correo electrónico, los desarrolladores suelen confiar en la propiedad de tiempo de espera para limitar la duración de los procesos prolongados. Sin embargo, especificar intervalos excesivamente largos para esta propiedad puede dificultar las operaciones que requieren tiempos de procesamiento prolongados. Un escenario notable es durante el establecimiento de una conexión, en el que confiar únicamente en la propiedad Timeout puede provocar tiempos de conexión prolongados.

En casos específicos, el cliente de correo electrónico puede emplear un modo automático para el establecimiento de la conexión, recorriendo sistemáticamente varios parámetros de conexión hasta que se establezca una conexión exitosa. Cuando la conexión se inicia correctamente, los servidores SMTP, IMAP y POP3 envían una cadena de saludo al cliente. En particular, los servidores pueden emplear métodos de inicio de conexión SSL/TLS implícitos o explícitos (START TLS).

Un posible desafío surge cuando el modo de conexión no coincide entre el servidor y el cliente. Por ejemplo, si el servidor prevé una conexión SSL implícita mientras el cliente intenta establecer una conexión SSL no segura o explícita, el servidor se abstiene de enviar una cadena de saludo. En consecuencia, los usuarios experimentan tiempos de espera prolongados hasta que se agota el tiempo de espera, lo que hace que el cliente pase a la siguiente opción de conexión.

Para solucionar este problema, los desarrolladores pueden aprovechar la propiedad 'greeting_timeout' de [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) clase. Esta propiedad permite especificar un tiempo de espera (en milisegundos) específico para la cadena de saludo, lo que minimiza el tiempo necesario para el establecimiento automático de la conexión. Al incorporar la propiedad 'greeting_timeout', los desarrolladores pueden optimizar los procesos de conexión y garantizar una experiencia de cliente de correo electrónico más eficiente y con mayor capacidad de respuesta.

El siguiente ejemplo de código muestra cómo implementar la propiedad en un proyecto:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("localhost", 25, "username", "password")
client.greeting_timeout = 4000
```
## **Enviar un correo electrónico a través del servidor proxy de Socks**

Aspose.Email admite las versiones 4, 4a y 5 del protocolo de proxy SOCKS. El siguiente ejemplo de código muestra cómo enviar un correo electrónico mediante SMTP con el proxy SOCKS:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("smtp.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.SSL_IMPLICIT
# proxy address
proxy_address = "192.168.203.142"
#proxy port
proxy_port = 1080
socks_proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = socks_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy", "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"))
```

## **Conexión al servidor mediante un servidor proxy HTTP**

El ejemplo de código siguiente muestra el uso de un proxy HTTP para enviar un correo electrónico a través de un servidor SMTP:

```py
import aspose.email as ae

http_proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.smtp.SmtpClient("host", 587, "username", "password")
client.proxy = http_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy", "Body"))
```

## **Conexión al servidor mediante el método de autenticación compatible**

Para establecer una conexión segura y exitosa con el servidor para enviar correos electrónicos, el cliente puede seleccionar un método de autenticación compatible en función de las capacidades del servidor. Aspose.Email proporciona propiedades que devuelven listas de los métodos de autenticación compatibles:

- La propiedad 'supported_authentication' obtiene la enumeración de los tipos de autenticación admitidos por el servidor
- La propiedad 'allowed_authentication' obtiene o establece la enumeración de los tipos de autenticación permitidos por el usuario

Con estas propiedades, los desarrolladores pueden asegurarse de que el cliente y el servidor SMTP sean compatibles en cuanto a los métodos de autenticación admitidos y establecer una conexión con un servidor SMTP. El siguiente fragmento de código proporciona un ejemplo del uso de la propiedad 'allowed_authentication' en un proyecto:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.LOGIN
```

## **Cómo configurar el tiempo de espera para las operaciones de correo**

Establecer un tiempo de espera puede ser importante para gestionar la comunicación de red de forma eficiente. La propiedad de «tiempo de espera» del [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) La clase se usa para especificar el tiempo máximo (en milisegundos) para esperar una respuesta del servidor SMTP. Esta propiedad permite al usuario controlar el tiempo que el cliente esperará a que el servidor responda a una operación concreta, como una conexión o el envío de un comando. Si el servidor tarda más del tiempo especificado en responder, el cliente emitirá una excepción que indicará un error de tiempo de espera. Esto ayuda a gestionar el comportamiento del cliente cuando interactúa con el servidor, garantizando que el cliente no se quede indefinidamente si el servidor no responde de manera oportuna. Utilice el siguiente fragmento de código para establecer el tiempo de espera de la respuesta del servidor:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
# 60 seconds
client.timeout = 60000
```

## **Uso de protocolos criptográficos con un cliente SMTP**

Aspose.Email admite los protocolos criptográficos SSL (obsoletos) y TLS para brindar seguridad en las comunicaciones. Puede habilitar el cifrado criptográfico para proteger el intercambio de datos entre la aplicación y los servidores de correo.

```
NOTE: You should set only those versions of the protocol, which are supported by Python Framework. If some versions of the cryptographic protocol are not supported by your current version of Python Framework, they will be ignored and skipped. In this case, exceptions won't be generated. Please use 'set_supported_encryption_unsafe(value)' method of the SmtpClient class if you want to set the protocols without any compatibility checks.
```
El ejemplo de código siguiente muestra cómo configurar TLS 1.3 para la instancia de clase SmtpClient.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```

## **Uso del mecanismo CRAM-MD5 para la autenticación**

El mecanismo de autenticación CRAM-MD5 de Aspose.Email para Python proporciona una capa adicional de seguridad al acceder al servidor. El siguiente fragmento de código muestra cómo implementar esta función en su proyecto:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.CRAM_MD5
```
