---
title: "Conectando al Servidor SMTP"
url: /es/python-net/conectando-al-servidor-smtp/
weight: 10
type: docs
---


## **Conectando a un Servidor SMTP Habilitado para SSL**
Las siguientes propiedades deben configurarse al conectarse a un servidor SMTP con soporte para SSL.

- SecurityOptions
- Port

En los ejemplos a continuación mostramos cómo:

1. Establecer un nombre de usuario.
1. Establecer una contraseña.
1. Establecer el puerto.
1. Establecer la opción de seguridad.

El siguiente fragmento de código muestra cómo conectarse a un servidor SMTP habilitado para SSL.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SSLEnabledSMTPServer-SSLEnabledSMTPServer.py" >}}

### **Establecer un Tiempo de Espera para la Respuesta de Saludo del Servidor**

Para mejorar la eficiencia de las operaciones del cliente de correo electrónico, los desarrolladores a menudo confían en la propiedad de tiempo de espera para limitar la duración de procesos prolongados. Sin embargo, especificar intervalos excesivamente largos para esta propiedad puede obstaculizar operaciones que requieren tiempos de procesamiento extendidos. Un escenario notable es durante el establecimiento de una conexión, donde depender únicamente de la propiedad de Timeout puede resultar en tiempos de conexión prolongados.

En casos específicos, el cliente de correo electrónico puede emplear un modo automático para el establecimiento de la conexión, ciclando sistemáticamente a través de varios parámetros de conexión hasta que se establezca una conexión exitosa. Los servidores SMTP, IMAP y POP3, al iniciar una conexión exitosa, envían una cadena de saludo al cliente. Notablemente, los servidores pueden emplear métodos de inicio de conexión SSL/TLS implícitos o explícitos (START TLS).

Un desafío potencial surge cuando el modo de conexión no coincide entre el servidor y el cliente. Por ejemplo, si el servidor espera una conexión SSL implícita mientras que el cliente intenta establecer una conexión no asegurada o explícitamente SSL, el servidor se abstiene de enviar una cadena de saludo. Como resultado, los usuarios experimentan tiempos de espera prolongados hasta que se alcanza el tiempo de espera, lo que lleva al cliente a pasar a la siguiente opción de conexión.

Para abordar este problema, los desarrolladores pueden aprovechar la propiedad 'greeting_timeout' de la clase [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class). Esta propiedad permite especificar un tiempo de espera (en milisegundos) específicamente para la cadena de saludo, minimizando el tiempo requerido para el establecimiento automático de la conexión. Al incorporar la propiedad 'greeting_timeout', los desarrolladores pueden optimizar los procesos de conexión y asegurar una experiencia de cliente de correo electrónico más responsiva y eficiente.

El siguiente ejemplo de código demuestra cómo implementar la propiedad en un proyecto:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("localhost", 25, "username", "password")
client.greeting_timeout = 4000
```
## **Enviar un Correo Electrónico a través de un Servidor Proxy Socks**

Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo proxy SOCKS. El siguiente ejemplo de código demuestra cómo enviar un correo electrónico utilizando SMTP con un proxy SOCKS: 

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("smtp.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.SSL_IMPLICIT
# dirección del proxy
proxy_address = "192.168.203.142"
# puerto del proxy
proxy_port = 1080
socks_proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = socks_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Enviando Correo Electrónico a través de proxy", "Implementar protocolo proxy socks para versiones 4, 4a, 5 (solo autenticación por Nombre de Usuario/Contraseña)"))
```

## **Conectarse al Servidor a través de un Servidor Proxy HTTP**

El siguiente ejemplo de código demuestra el uso de un proxy HTTP para enviar un correo electrónico a través de un servidor SMTP: 

```py
import aspose.email as ae

http_proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.smtp.SmtpClient("host", 587, "username", "password")
client.proxy = http_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Enviando Correo Electrónico a través de proxy", "Cuerpo"))
```

## **Conectarse al Servidor utilizando un Método de Autenticación Soportado**

Para establecer una conexión segura y exitosa al servidor para enviar correos electrónicos, un cliente puede seleccionar un método de autenticación soportado basado en las capacidades del servidor. Aspose.Email proporciona propiedades que devuelven listas de métodos de autenticación soportados: 

- La propiedad 'supported_authentication' obtiene la enumeración de tipos de autenticación soportados por el servidor 
- La propiedad 'allowed_authentication' obtiene o establece la enumeración de tipos de autenticación permitidos por el usuario 

Usando estas propiedades, los desarrolladores pueden asegurar que el cliente SMTP y el servidor son compatibles en términos de métodos de autenticación soportados y establecer una conexión con un servidor SMTP. El siguiente fragmento de código proporciona un ejemplo de uso de la propiedad 'allowed_authentication' en un proyecto:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.LOGIN
```

## **Cómo Establecer un Tiempo de Espera para Operaciones de Correo**

Establecer un tiempo de espera puede ser importante para manejar la comunicación de red de manera eficiente. La propiedad 'timeout' de la clase [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) se utiliza para especificar el tiempo máximo (en milisegundos) para esperar una respuesta del servidor SMTP. Esta propiedad permite al usuario controlar la duración que el cliente esperará para que el servidor responda a una operación particular, como una conexión o el envío de un comando. Si el servidor tarda más que el tiempo especificado en responder, el cliente lanzará una excepción, indicando un error de tiempo de espera. Esto ayuda a gestionar el comportamiento del cliente al interactuar con el servidor, asegurando que el cliente no quede atascado indefinidamente si el servidor no responde de manera oportuna. Utilice el siguiente fragmento de código para establecer el tiempo de espera para la respuesta del servidor:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
# 60 segundos
client.timeout = 60000
```

## **Usando Protocolos Criptográficos con el Cliente SMTP**

Aspose.Email soporta los protocolos criptográficos SSL (obsoleto) y TLS para proporcionar seguridad en las comunicaciones. Puede habilitar la encriptación criptográfica para proteger el intercambio de datos entre su aplicación y los servidores de correo.

```
NOTA: Debe establecer solo aquellas versiones del protocolo que son soportadas por el Framework de Python. Si algunas versiones del protocolo criptográfico no son soportadas por su versión actual del Framework de Python, serán ignoradas y omitidas. En este caso, no se generarán excepciones. Utilice el método 'set_supported_encryption_unsafe(value)' de la clase SmtpClient si desea establecer los protocolos sin ninguna comprobación de compatibilidad.
```
El siguiente ejemplo de código le muestra cómo establecer TLS 1.3 para la instancia de la clase SmtpClient.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```

## **Usando el Mecanismo CRAM-MD5 para Autenticación**

El mecanismo de autenticación CRAM-MD5 de Aspose.Email para Python proporciona una capa adicional de seguridad al acceder al servidor. El siguiente fragmento de código muestra cómo implementar esta característica en su proyecto:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.CRAM_MD5
```