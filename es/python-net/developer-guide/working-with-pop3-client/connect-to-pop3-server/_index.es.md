---
title: "Conectarse al servidor POP3"
url: /es/python-net/connect-to-pop3-server/
weight: 10
type: docs
---

## **Conexión al servidor POP3**
La clase Pop3Client permite a las aplicaciones administrar los buzones de correo electrónico mediante el Protocolo de oficina de correos, versión 3 (POP3). Para conectarse a un servidor, utilice la clase Pop3Client. La clase Pop3Client es la entrada principal para los desarrolladores que desean agregar la administración de POP3 a sus aplicaciones.NET. En este artículo se explica cómo utilizarla. Para conectarse a un servidor POP3:

1. Crea una instancia de la clase Pop3Client como cliente.
1. Especifique el host, el nombre de usuario y la contraseña en la instancia de Pop3Client.

El siguiente fragmento de código muestra cómo conectarse al servidor POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ConnectingToPOP3-ConnectingToPOP3.py" >}}
## **Conexión al servidor SSL**
Conexión a un servidor POP3 describió cómo conectarse a un servidor POP3 en tres sencillos pasos:

1. Crea una instancia de la clase Pop3Client.
1. Especifique el host, el nombre de usuario y la contraseña.

El proceso para conectarse a un servidor POP3 con SSL habilitado es similar, pero requiere establecer otras propiedades:

- SecurityOptions
- Port

Para conectarse a un servidor POP3 con SSL habilitado, utilice la clase Aspose.Email.Pop3.Pop3Client y defina las propiedades SecurityOptions y Port. El siguiente fragmento de código muestra cómo conectarse a un servidor POP3 con SSL habilitado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.py" >}}

## **Conexión con un servidor APOP**

El APOP o Protocolo de Oficina Postal Autenticada es una extensión del Protocolo de Oficina Postal (POP) tradicional, que proporciona un método seguro para la autenticación del cliente durante el proceso de recuperación del correo electrónico. La principal ventaja del APOP es que la contraseña real nunca se transmite a través de la red. El acceso al buzón de correo del usuario se concede como resultado de un intercambio exitoso de valores hash entre un servidor y un cliente.

### **Conexión al servidor mediante proxy**

Los servidores proxy son muy comunes para comunicarse con el mundo exterior. En estos casos, las direcciones proxy se utilizan para que los clientes de correo electrónico accedan a los buzones a través de Internet. Aspose.Email admite las versiones 4, 4a y 5 del protocolo de proxy SOCKS. Su [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) La clase permite a las aplicaciones acceder a los mensajes y manipularlos mediante la versión 3 del Protocolo de oficina de correos (POP3). El método 'get_mailbox_info () 'de la clase recupera información sobre el buzón, como el número de mensajes, el tamaño total, etc. El siguiente ejemplo de código muestra el proceso de recuperación de correo electrónico mediante un servidor de correo proxy:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
# Set proxy address, Port and Proxy
proxy_address = "192.168.203.142"
proxy_port = 1080
proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Conexión al servidor mediante un proxy HTTP**

Hay varios tipos de proxies, incluidos los proxies HTTP, los proxies SOCKS y más, cada uno de los cuales sirve para diferentes propósitos y proporciona diferentes niveles de funcionalidad. Los pasos y configuraciones específicos pueden variar según el tipo de proxy que se utilice. El ejemplo de código que aparece a continuación muestra cómo configurar el POP3Client con la configuración adicional de un proxy HTTP y cómo obtener información sobre el buzón:

```py
import aspose.email as ae

proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Conexión al servidor mediante el mecanismo de autenticación CRAM-MD5**

El CRAM-MD5 (mecanismo de autenticación desafío-respuesta con MD5) se usa comúnmente en protocolos de correo electrónico como POP3 e IMAP, donde la autenticación segura es importante. Proporciona un mayor nivel de seguridad en comparación con la transmisión de contraseñas en texto plano. Aspose.Email para .NET permite a los usuarios autenticarse y acceder de forma segura a los servidores de correo electrónico que admiten este método de autenticación.

```py
client.allowed_authentication = ae.clients.pop3.Pop3KnownAuthenticationType.CRAM_MD5
```
## **Cómo configurar el tiempo de espera para las operaciones de correo**

Aspose.Email proporciona la propiedad de «tiempo de espera» del [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) clase para obtener o establecer el tiempo de espera de las operaciones de correo a fin de evitar bloqueos o bloqueos, gestionar los problemas de red o servidor, mejorar la capacidad de respuesta y garantizar una administración eficiente de los recursos. El siguiente ejemplo de código muestra cómo implementar la propiedad en un proyecto:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
#  60 seconds
client.timeout = 60000
```
## **Uso de protocolos criptográficos con un cliente POP3**

Aspose.Email admite los protocolos criptográficos SSL (obsoletos) y TLS para brindar seguridad en las comunicaciones. Puede habilitar el cifrado criptográfico para proteger el intercambio de datos entre la aplicación y los servidores de correo.

```
NOTE: It's important to know that you can only configure protocol versions supported by the .NET Framework. If your current .NET Framework version does not support certain protocol versions, those unsupported versions will be disregarded and skipped. This could result in a potential downgrade in TLS security level, and it's crucial to be aware that no exceptions will be raised in this situation. Developers should exercise caution to ensure the desired TLS security level is maintained based on the supported protocols in their .NET Framework environment.
```
El siguiente ejemplo de código muestra cómo configurar un cliente POP3 con configuraciones para el protocolo de cifrado TLS 1.3 para una comunicación segura:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
En caso de que la versión actual de .NET Framework no admita un protocolo de cifrado especificado, la diferencia de comportamiento entre el método 'setSupportedEncryptionUnsafe' y la propiedad 'SupportedEncryption' es la siguiente:

Si se utiliza la propiedad «SupportedEncryption», el cliente de correo electrónico reduce el protocolo de cifrado a un nivel compatible.

Si se usa el método 'setSupportedEncryptionUnsafe', el cliente de correo electrónico lanza excepciones.