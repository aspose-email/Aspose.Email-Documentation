---
title: "Conectarse al servidor POP3"
url: /es/python-net/connect-to-pop3-server/
weight: 10
type: docs
---

## **Conectándose al servidor POP3**
La clase Pop3Client permite a las aplicaciones gestionar bandejas de correo utilizando el Protocolo de Oficina de Correos, Versión 3 (POP3). Para conectarse a un servidor, utilice la clase Pop3Client. La clase Pop3Client es la principal entrada para los desarrolladores que desean agregar gestión de POP3 a sus aplicaciones .NET. Este artículo explica cómo utilizarla. Para conectarse a un servidor POP3:

1. Cree una instancia de la clase Pop3Client como cliente.
1. Especifique el host, el nombre de usuario y la contraseña en la instancia de Pop3Client.

El siguiente fragmento de código le muestra cómo conectarse con el servidor POP3.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ConnectingToPOP3-ConnectingToPOP3.py" >}}
## **Conectándose a un servidor SSL**
Conectarse a un servidor POP3 se describió cómo conectarse a un servidor POP3 en tres simples pasos:

1. Cree una instancia de la clase Pop3Client.
1. Especifique el host, el nombre de usuario y la contraseña.

El proceso para conectarse a un servidor POP3 habilitado para SSL es similar, pero requiere que establezca algunas propiedades adicionales:

- SecurityOptions
- Port

Para conectarse a un servidor POP3 habilitado para SSL, utilice la clase Aspose.Email.Pop3.Pop3Client y establezca las propiedades SecurityOptions y Port. El siguiente fragmento de código le muestra cómo conectarse a un servidor POP3 habilitado para SSL.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.py" >}}

## **Conectándose con un servidor APOP**

APOP o Protocolo de Oficina de Correos Autenticado es una extensión del Protocolo de Oficina de Correos (POP) tradicional, que proporciona un método seguro para la autenticación del cliente durante el proceso de recuperación de correo electrónico. La principal ventaja de APOP es que la contraseña real nunca se transmite a través de la red. El acceso a la bandeja de entrada del usuario se concede como resultado de un intercambio exitoso de valores hash entre un servidor y un cliente.

### **Conectándose al servidor a través de un proxy**

Los servidores proxy son muy comunes para comunicarse con el mundo exterior. En tales casos, se utilizan direcciones proxy para que los clientes de correo accedan a las bandejas de entrada a través de Internet. Aspose.Email proporciona soporte para las versiones 4, 4a y 5 del protocolo proxy SOCKS. Su clase [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) permite a las aplicaciones acceder y manipular mensajes utilizando el Protocolo de Oficina de Correos Versión 3 (POP3). El método 'get_mailbox_info()' de la clase recupera información sobre la bandeja de entrada, como el número de mensajes, el tamaño total, etc. El siguiente ejemplo de código demuestra el proceso de recuperación de correo electrónico utilizando un servidor de correo proxy:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
# Establecer la dirección proxy, el puerto y el proxy
proxy_address = "192.168.203.142"
proxy_port = 1080
proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Conectándose al servidor a través de un proxy HTTP**

Existen varios tipos de proxies, incluidos los proxies HTTP, proxies SOCKS, y más, cada uno con diferentes propósitos y niveles de funcionalidad. Los pasos específicos y configuraciones pueden variar según el tipo de proxy que se esté utilizando. El siguiente ejemplo de código demuestra cómo configurar el POP3Client con la configuración adicional de un proxy HTTP y obtener información sobre la bandeja de entrada:

```py
import aspose.email as ae

proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Conectándose al servidor a través del mecanismo de autenticación CRAM-MD5**

CRAM-MD5 (Mecanismo de Autenticación de Respuesta de Desafío con MD5) se utiliza comúnmente en protocolos de correo electrónico como POP3 e IMAP, donde la autenticación segura es importante. Ofrece un nivel de seguridad más fuerte en comparación con la transmisión de contraseñas en texto plano. Aspose.Email para .NET permite a los usuarios autenticarse de forma segura y acceder a servidores de correo electrónico que admiten este método de autenticación.

```py
client.allowed_authentication = ae.clients.pop3.Pop3KnownAuthenticationType.CRAM_MD5
```
## **Cómo establecer un tiempo de espera para las operaciones de correo**

Aspose.Email proporciona la propiedad 'timeout' de la clase [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para obtener o establecer el tiempo de espera para las operaciones de correo con el fin de prevenir bloqueos, manejar problemas de red o servidor, mejorar la capacidad de respuesta y garantizar una gestión eficiente de los recursos. El siguiente ejemplo de código muestra cómo implementar la propiedad en un proyecto:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
#  60 segundos
client.timeout = 60000
```
## **Usando protocolos criptográficos con cliente POP3**

Aspose.Email admite protocolos criptográficos SSL (obsoleto) y TLS para proporcionar seguridad en las comunicaciones. Puede habilitar la encriptación criptográfica para proteger el intercambio de datos entre su aplicación y servidores de correo.

```
NOTA: Es importante saber que solo puede configurar las versiones de protocolo soportadas por el .NET Framework. Si la versión actual de su .NET Framework no soporta ciertas versiones de protocolo, esas versiones no soportadas serán ignoradas y omitidas. Esto podría resultar en una posible disminución en el nivel de seguridad TLS, y es crucial tener en cuenta que no se generarán excepciones en esta situación. Los desarrolladores deben tener cuidado para garantizar que el nivel de seguridad TLS deseado se mantenga en función de los protocolos soportados en su entorno .NET Framework.
```
El siguiente ejemplo de código demuestra cómo configurar un cliente POP3 con configuraciones para el protocolo de encriptación TLS 1.3 para una comunicación segura:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
En caso de que un protocolo de encriptación específico no sea soportado en la versión actual del .NET Framework, la diferencia de comportamiento entre el método 'SetSupportedEncryptionUnsafe' y la propiedad 'SupportedEncryption' es la siguiente:

Si se utiliza la propiedad 'SupportedEncryption', el cliente de correo electrónico reduce el protocolo de encriptación a un nivel soportado.

Si se utiliza el método 'SetSupportedEncryptionUnsafe', el cliente de correo electrónico lanza excepciones.