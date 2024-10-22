---
title: "Conectando al servidor IMAP"
url: /es/python-net/conectando-al-servidor-imap/
weight: 10
type: docs
---

La clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) en Aspose.Email para Python sirve como un componente para interactuar con cuentas de correo electrónico utilizando el protocolo IMAP. IMAP (Protocolo de Acceso a Mensajes de Internet) es un protocolo estándar para acceder y gestionar mensajes de correo electrónico almacenados en un servidor de correo.

La clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) proporciona funcionalidades para conectarse a un servidor de correo electrónico a través de IMAP, autenticar usuarios, recuperar correos electrónicos, gestionar carpetas y realizar diversas operaciones como leer, mover, eliminar o actualizar mensajes de correo electrónico. Esta clase permite a los desarrolladores integrar la funcionalidad IMAP en sus aplicaciones de Python, permitiéndoles interactuar con cuentas de correo electrónico de manera estandarizada y conforme al protocolo.

Para conectarse al servidor IMAP, siga tres pasos simples. El siguiente ejemplo de código muestra cómo conectarse al servidor IMAP programáticamente.

1. Cree una instancia de la clase ImapClient.
2. Especifique el nombre del host, puerto, nombre de usuario y contraseña.
3. Especifique las opciones de seguridad.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd")
```
## **Conectando a un servidor IMAP habilitado para SSL**

El proceso para conectarse a un servidor IMAP habilitado para SSL es similar al descrito anteriormente pero requiere que establezca otra propiedad:

- Establezca las opciones de seguridad en SSLImplicit.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd")

# Establecer el modo de seguridad en implícito
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
```
## **Conectando al servidor a través de un proxy**

El servidor proxy actúa como un intermediario entre el dispositivo de un usuario y el internet. Puede usarse por diversas razones, como mejorar el rendimiento de la red, aumentar la seguridad y privacidad, sortear restricciones geográficas y almacenar en caché el contenido web para reducir el uso de ancho de banda. Los servidores proxy también pueden ser utilizados para filtrar y monitorear el uso del internet en una organización o proporcionar anonimato a los usuarios. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo de proxy SOCKS. El siguiente ejemplo de código y pasos demuestran cómo configurar un cliente IMAP para conectarse a un servidor IMAP a través de un servidor proxy SOCKS para una comunicación segura y privada con el servidor de correo.

1. Cree una instancia de la [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) y establezca los detalles del servidor IMAP.
2. Establezca las opciones de seguridad en automático para el cliente IMAP.
3. Defina los detalles del servidor proxy, como la dirección IP y el puerto.
4. Cree un objeto SocksProxy con la dirección y el puerto del proxy definidos, utilizando SOCKS versión 5.
5. Establezca el proxy creado como el proxy para el cliente IMAP.
6. Conéctese al servidor IMAP y seleccione la carpeta "Bandeja de entrada" utilizando el proxy para la comunicación.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", "nombredeusuario", "contraseña")

client.security_options = ae.clients.SecurityOptions.AUTO
proxy_address = "192.168.203.142"
proxy_port = 1080

proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = proxy
client.select_folder("Bandeja de entrada")
```
## **Conectando al servidor a través de un proxy HTTP**

Aspose.Email también proporciona la funcionalidad para acceder a un buzón utilizando el proxy HTTP. El siguiente ejemplo de código demuestra cómo configurar un cliente IMAP para conectarse a un servidor IMAP a través de un servidor proxy HTTP para una comunicación segura y privada con el servidor de correo.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", "nombredeusuario", "contraseña")
client.proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client.select_folder("Bandeja de entrada")
```
## **Conectando al servidor en modo de solo lectura**

Implementar una funcionalidad de modo de solo lectura para un buzón implica proporcionar la capacidad de controlar y restringir las modificaciones al estado permanente del buzón, asegurando la integridad de los datos, el cumplimiento y la experiencia del usuario. Un valor True establecido en esta propiedad indica que no se permiten cambios. El siguiente ejemplo de código muestra cómo usar esta propiedad en un proyecto:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd")
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
client.read_only = True
```
## **Conectando al servidor utilizando autenticación CRAM-MD5**

Usar la autenticación CRAM-MD5 proporciona una forma segura de autenticar con un servidor de correo. Con Aspose.Email, puede implementar esta capacidad en su proyecto de Python fácilmente.

El siguiente ejemplo de código demuestra cómo configurar el cliente para aceptar CRAM-MD5 como uno de los métodos de autenticación admitidos para conectarse a un servidor IMAP:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd")
client.allowed_authentication = ae.clients.imap.ImapKnownAuthenticationType.CRAM_MD5
```
## **Cómo establecer un tiempo de espera para operaciones de correo**

La propiedad 'timeout' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) evita que el cliente espere indefinidamente por una respuesta al comunicarse con el servidor de correo y permite manejar posibles retrasos de conexión, problemas de red o latencia. El tiempo de espera se calcula en milisegundos. El siguiente fragmento de código muestra cómo establecer un período de tiempo de espera de 60,000 milisegundos (60 segundos) para que el cliente espere la respuesta del servidor:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)
#  60 segundos
client.timeout = 60000
```
## **Cómo restringir el tiempo de espera de saludo**

Establecer un tiempo de espera en la operación de saludo entre un cliente y un servidor permite al cliente limitar la cantidad de tiempo que espera por una respuesta del servidor durante el proceso inicial de negociación. Esto es importante porque si el servidor no responde o hay problemas de red, el cliente no debería esperar indefinidamente una respuesta.

La API proporciona la propiedad 'greeting_timeout' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para establecer un tiempo de espera en la operación de saludo. El siguiente fragmento de código muestra cómo restringir el tiempo de espera de saludo:  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd")

client.greeting_timeout = 4000
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
```
## **Usando protocolos criptográficos con el cliente IMAP**

Aspose.Email admite los protocolos criptográficos SSL (obsoleto) y TLS para proporcionar seguridad en las comunicaciones. La propiedad 'supported_encryption' de la clase [EmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients/emailclient/#emailclient-class) define las versiones de los protocolos de cifrado SSL/TLS que se deben utilizar.

> **_NOTA:_** solo puede establecer aquellas versiones de protocolo que son compatibles con .net framework. Si algunas versiones de protocolo no son compatibles con su versión actual de .NET framework, se ignorarán y se omitirá. Esto puede llevar a una reducción del nivel de seguridad TLS. En este caso, no se generarán excepciones. Utilice el método 'set_supported_encryption_unsafe(value)' si desea establecer los protocolos sin comprobaciones de compatibilidad.

El siguiente ejemplo de código muestra cómo establecer TLS 1.3 para la instancia de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class).

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
En caso de que un protocolo de cifrado específico no sea compatible en la versión actual del .NET Framework, la diferencia en el comportamiento entre el método 'set_supported_encryption_unsafe(value)' y la propiedad 'supported_encryption' es la siguiente:

Si se utiliza la propiedad 'supported_encryption', el cliente de correo electrónico reduce el protocolo de cifrado a un nivel compatible.
Si se utiliza el método 'set_supported_encryption_unsafe(value)', el cliente de correo electrónico genera excepciones.