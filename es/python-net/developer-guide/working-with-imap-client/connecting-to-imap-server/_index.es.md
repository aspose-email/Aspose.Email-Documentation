---
title: "Conexión al servidor IMAP"
url: /es/python-net/connecting-to-imap-server/
weight: 10
type: docs
---

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) La clase en Aspose.Email para Python sirve como un componente para interactuar con las cuentas de correo electrónico mediante el protocolo IMAP. El IMAP (Protocolo de acceso a mensajes de Internet) es un protocolo estándar para acceder y administrar los mensajes de correo electrónico almacenados en un servidor de correo.

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) La clase proporciona funcionalidades para conectarse a un servidor de correo electrónico a través de IMAP, autenticar usuarios, recuperar correos electrónicos, administrar carpetas y realizar diversas operaciones, como leer, mover, eliminar o actualizar mensajes de correo electrónico. Básicamente, esta clase permite a los desarrolladores integrar la funcionalidad IMAP en sus aplicaciones de Python, lo que les permite interactuar con las cuentas de correo electrónico de una manera estandarizada y compatible con los protocolos.

Para conectarse al servidor IMAP, siga tres sencillos pasos. El ejemplo de código que aparece a continuación muestra cómo conectarse al servidor IMAP mediante programación.

1. Crea una instancia de la clase ImapClient.
2. Especifique el nombre de host, el puerto, el nombre de usuario y la contraseña.
3. Especifique las opciones de seguridad.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
```
## **Conexión a un servidor IMAP con SSL habilitado**

El proceso para conectarse a un servidor IMAP con SSL habilitado es similar al descrito anteriormente, pero requiere que defina otra propiedad:

- Establezca las opciones de seguridad en SSLIplicit.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

# Set the security mode to implicit
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
```
## **Conexión al servidor mediante proxy**

El servidor proxy actúa como intermediario entre el dispositivo de un usuario e Internet. Se puede usar por varios motivos, como mejorar el rendimiento de la red, aumentar la seguridad y la privacidad, eludir las restricciones geográficas y almacenar en caché el contenido web para reducir el uso del ancho de banda. Los servidores proxy también se pueden usar para filtrar y monitorear el uso de Internet en una organización o para proporcionar anonimato a los usuarios. Aspose.Email admite las versiones 4, 4a y 5 del protocolo de proxy SOCKS. El ejemplo de código y los pasos siguientes muestran cómo configurar un cliente IMAP para que se conecte a un servidor IMAP a través de un servidor proxy SOCKS para una comunicación segura y privada con el servidor de correo.

1. Crea una instancia del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) y defina los detalles del servidor IMAP.
2. Establezca las opciones de seguridad en automáticas para el cliente IMAP.
3. Defina los detalles del servidor proxy, como la dirección IP y el puerto.
4. Cree un objeto SocksProxy con la dirección de proxy y el puerto definidos, con la versión 5 de SOCKS.
5. Configure el proxy creado como el proxy del cliente IMAP.
6. Conéctese al servidor IMAP y seleccione la carpeta «Bandeja de entrada» utilizando el proxy para la comunicación.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.AUTO
proxy_address = "192.168.203.142"
proxy_port = 1080

proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = proxy
client.select_folder("Inbox")
```
## **Conexión al servidor mediante un proxy HTTP**

Aspose.Email también proporciona la funcionalidad de acceder a un buzón mediante el proxy HTTP. El ejemplo de código siguiente muestra cómo configurar un cliente IMAP para que se conecte a un servidor IMAP a través de un servidor proxy HTTP para una comunicación segura y privada con el servidor de correo.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")
client.proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client.select_folder("Inbox")
```
## **Conexión al servidor en modo de solo lectura**

La implementación de una funcionalidad de modo de solo lectura para un buzón implica proporcionar la capacidad de controlar y restringir las modificaciones al estado permanente del buzón, garantizando la integridad de los datos, el cumplimiento y la experiencia del usuario. Un valor True establecido en esta propiedad indica que no se permiten los cambios. El siguiente ejemplo de código muestra cómo usar esta propiedad en un proyecto:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
client.read_only = True
```
## **Conexión al servidor mediante la autenticación CRAM-MD5**

El uso de la autenticación CRAM-MD5 proporciona una forma segura de autenticarse con un servidor de correo. Con Aspose.Email puede implementar fácilmente esta capacidad en su proyecto de Python.

El siguiente ejemplo de código muestra cómo configurar el cliente para que acepte CRAM-MD5 como uno de los métodos de autenticación compatibles para conectarse a un servidor IMAP:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.allowed_authentication = ae.clients.imap.ImapKnownAuthenticationType.CRAM_MD5
```
## **Cómo configurar el tiempo de espera para las operaciones de correo**

La propiedad de «tiempo de espera» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) La clase evita que el cliente espere indefinidamente una respuesta cuando se comunica con el servidor de correo y permite gestionar posibles retrasos en la conexión, problemas de red o latencia. El tiempo de espera se calcula en milisegundos. El siguiente fragmento de código muestra cómo establecer un período de tiempo de espera de 60 000 milisegundos (60 segundos) para que el cliente espere la respuesta del servidor:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)
#  60 seconds
client.timeout = 60000
```
## **Cómo restringir el tiempo de espera de los saludos**

Establecer un tiempo de espera para la operación de saludo entre un cliente y un servidor permite al cliente limitar el tiempo que espera una respuesta del servidor durante el proceso inicial de apretón de manos. Esto es importante porque si el servidor no responde o hay problemas de red, el cliente no debe esperar indefinidamente para recibir una respuesta.

La API proporciona la propiedad 'greeting_timeout' del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) clase para establecer un tiempo de espera en la operación de saludo. El siguiente fragmento de código muestra cómo restringir el tiempo de espera del saludo: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

client.greeting_timeout = 4000
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
```
## **Uso de protocolos criptográficos con el cliente IMAP**

Aspose.Email admite los protocolos criptográficos SSL (obsoletos) y TLS para brindar seguridad en las comunicaciones. La propiedad «supported_encryption» de [EmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients/emailclient/#emailclient-class) La clase define las versiones de los protocolos de cifrado SSL/TLS que se utilizarán.

> **_NOTE:_** solo puede configurar las versiones del protocolo compatibles con .net framework. Si su versión actual de.NET Framework no admite algunas versiones del protocolo, se ignorarán y se omitirán. Esto puede llevar a una degradación del nivel de seguridad de TLS. En este caso, no se generarán excepciones. Utilice el método 'set_supported_encryption_unsafe (value) 'si desea configurar los protocolos sin ninguna comprobación de compatibilidad.

El ejemplo de código siguiente muestra cómo configurar TLS 1.3 para [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) instancia de clase.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
Si la versión actual de.NET Framework no admite un protocolo de cifrado específico, la diferencia de comportamiento entre el método 'set_supported_encryption_unsafe (value) 'y la propiedad' supported_encryption 'es la siguiente:

Si se utiliza la propiedad «supported_encryption», el cliente de correo electrónico reduce el protocolo de cifrado a un nivel compatible.
Si se utiliza el método 'set_supported_encryption_unsafe (value) ', el cliente de correo electrónico generará excepciones.