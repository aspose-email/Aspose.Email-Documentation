---
title: "Tutorial por correo electrónico"
url: /es/net/email-tutorial/
weight: 5
type: docs
---

## **Formatos de archivo de correo electrónico más populares**

### MSG

**Mensaje de Microsoft Outlook (MSG)** es un formato de correo electrónico propietario utilizado por Microsoft Outlook para almacenar mensajes de correo electrónico individuales. Estos archivos contienen el contenido del correo electrónico y los metadatos, como el remitente, los destinatarios, el asunto y las marcas de tiempo. Admiten el formato enriquecido, los archivos adjuntos y funciones específicas de Outlook, como los indicadores, la importancia y la sensibilidad.

#### Características principales

- El archivo MSG representa un único mensaje de correo electrónico.
- Los archivos MSG se asocian con Microsoft Outlook y pueden abrirse con él.
- Los archivos MSG se suelen utilizar para archivar, hacer copias de seguridad e intercambiar elementos de Outlook entre diferentes instancias de Outlook u otros clientes de correo electrónico compatibles.

MSG está estrechamente relacionado en el contexto de Microsoft Outlook y **Interfaz de programación de aplicaciones de mensajería (MAPI)**. MAPI es una interfaz de programación que permite a las aplicaciones interactuar con los servicios de mensajería, principalmente Microsoft Exchange Server y Microsoft Outlook. Proporciona un conjunto de funciones y protocolos para enviar, recibir y administrar mensajes de correo electrónico, así como para acceder a otras funciones relacionadas con la mensajería, como calendarios, contactos y tareas. Microsoft Outlook usa MAPI para crear, manipular y administrar mensajes de correo electrónico. Cuando un usuario redacta o recibe un correo electrónico en Outlook, MAPI gestiona la comunicación subyacente con el servidor de correo y proporciona las funciones necesarias para administrar el contenido del mensaje.

#### Base técnica para el formato MSG

Los archivos MSG almacenan los datos de los mensajes usando **Propiedades de MAPI**, que son atributos que definen varios aspectos del mensaje. Estas propiedades incluyen atributos estándar, como el remitente, el destinatario, el asunto y las marcas de tiempo, así como propiedades personalizadas y atributos extendidos.
Las propiedades organizan el mensaje en una estructura jerárquica, con propiedades de nivel superior que definen los atributos generales del mensaje y propiedades anidadas que representan componentes específicos, como los destinatarios, los archivos adjuntos y los objetos incrustados. Los archivos MSG pueden contener varios flujos de propiedades, cada uno con un conjunto de propiedades de MAPI relacionadas. Estas secuencias se estructuran de acuerdo con la **Formato binario de archivos compuestos (CFBF)** y almacena tanto las propiedades estándar como las personalizadas.

### OFT

**Plantilla de archivo de Outlook (OFT)** son formatos de correo electrónico utilizados por Microsoft Outlook para crear mensajes estandarizados. A diferencia de los archivos MSG, los archivos OFT no contienen el contenido real de los mensajes, sino que sirven como plantillas con formato, diseño y marcadores de posición predefinidos para el contenido dinámico.

#### Características principales

 - Los archivos OFT agilizan la creación de correos electrónicos repetitivos al proporcionar plantillas prediseñadas para situaciones comunes, como boletines informativos, anuncios o respuestas.
 - Al usar plantillas OFT, las organizaciones garantizan la coherencia en la marca, el formato y los mensajes en todas las comunicaciones salientes.
 - Los usuarios pueden personalizar las plantillas OFT añadiendo o modificando el contenido antes de enviarlo, lo que permite personalizar los mensajes y, al mismo tiempo, mantener un formato estandarizado.

### EML

**EML** es uno de los formatos de archivo de correo electrónico más reconocidos y utilizados, diseñado principalmente para cumplir con los **MIME (extensiones de correo de Internet multipropósito)** estándar. Este formato es ampliamente compatible en varios clientes y sistemas de correo electrónico debido a su enfoque abierto y generalizado para el almacenamiento y la transmisión del correo electrónico.

#### Características principales

- Cada archivo EML encapsula un único mensaje de correo electrónico junto con sus metadatos asociados, como el remitente, los destinatarios, el asunto y las marcas de tiempo.
- Los archivos EML admiten formatos enriquecidos, archivos adjuntos y elementos incrustados, y cumplen con el estándar MIME, que permite una representación versátil del contenido del correo electrónico.
-  A diferencia de los formatos propietarios como MSG (Microsoft Outlook Message), que están estrechamente vinculados a un software específico (Outlook y MAPI), los archivos EML ofrecen un enfoque más universal compatible con varios programas de correo electrónico en diferentes plataformas. Los archivos EML son compatibles con multitud de clientes de correo electrónico, incluidos, entre otros, Microsoft Outlook, Mozilla Thunderbird, Apple Mail y muchos servicios de correo electrónico basados en la web.

#### Base técnica del formato EML

El formato de archivo EML está intrínsecamente vinculado al estándar MIME, que es una especificación para el formato de los cuerpos de los mensajes de Internet. MIME amplía el formato de correo electrónico básico para admitir texto en conjuntos de caracteres distintos del ASCII, así como archivos adjuntos de contenido multimedia.

**Estructura MIME:**

   - Un archivo EML comienza con la sección de encabezado, que contiene información como los encabezados Desde, Para, Asunto, Fecha y otros encabezados. Los encabezados adicionales pueden incluir Content-Type, Content-Transfer-Encoding, etc.
   - Tras los encabezados, se presenta el cuerpo de un archivo EML. Esta sección puede contener texto sin formato, HTML o contenido en varias partes, lo que permite combinar diferentes tipos de contenido en un solo mensaje.
   - Un archivo EML puede incluir archivos adjuntos codificados en base64, lo que permite la transferencia de datos binarios por correo electrónico. Estos archivos adjuntos se definen dentro de sus propias partes MIME con los encabezados apropiados que indican el tipo de archivo y la codificación.

**Tipos de MIME:**

El contenido de un archivo EML se divide en varios tipos de MIME para diferenciar el texto, el HTML y otros tipos de medios. Entre los tipos de MIME más comunes que se encuentran en un archivo EML se incluyen los siguientes:

- `text/plain` para mensajes de texto sin formato.
- `text/html` para mensajes con formato HTML.
- `multipart/mixed` para correos electrónicos que incluyen tanto el contenido del mensaje como los archivos adjuntos.
- `application/octet-stream` para archivos adjuntos binarios.

### TNEF

**Formato de encapsulación neutral para el transporte (TNEF)** es un formato de correo electrónico propietario que utilizan Microsoft Outlook y Microsoft Exchange Server para encapsular las propiedades del correo electrónico y el contenido de texto enriquecido que pueden no ser compatibles con los protocolos de correo electrónico estándar.
Los clientes de correo electrónico de Microsoft lo utilizan principalmente para codificar y transmitir formatos de texto enriquecido, objetos incrustados y otras funciones de correo electrónico patentadas, lo que garantiza que el contenido complejo del correo electrónico, como el formato, los archivos incrustados y los eventos del calendario, se conserve cuando se envíen correos electrónicos entre diferentes clientes de correo electrónico de Microsoft.

#### Características principales

- TNEF puede encapsular una amplia gama de propiedades de MAPI, un formato de texto enriquecido específico de Microsoft y propiedades especiales que no se pueden transmitir a través de correos electrónicos de texto plano o MIME estándar.
- Los elementos de Outlook, como el calendario, los contactos, las tareas y las notas, se pueden encapsular en el formato TNEF.
- Es posible que los clientes de correo electrónico que no son de Microsoft no entiendan o procesen correctamente los archivos adjuntos de TNEF, lo que a menudo resulta en `winmail.dat` archivo. Esto suele ocurrir porque no pueden decodificar el formato propietario codificado en TNEF.

#### Base técnica del formato TNEF

- TNEF encapsula el contenido del correo electrónico en un archivo adjunto binario especial. Este archivo adjunto normalmente lleva un `.dat` extensión de archivo, más comúnmente denominada `winmail.dat`.
- Los datos TNEF se asocian con frecuencia al tipo MIME `application/ms-tnef`.
- El formato TNEF representa una jerarquía de propiedades del mensaje como una estructura plana, que se puede ver como un flujo de datos secuencial. El formato típico de una propiedad específica de la secuencia incluye un identificador con información sobre el tipo de datos, el tamaño (si no está definido por el tipo) y los datos.

## **Formatos comunes de almacenamiento de correo electrónico**

### MBOX

**MBOX (abreviatura de Mailbox)** es un formato de almacenamiento de correo electrónico ampliamente utilizado que ha prevalecido durante varias décadas. Se usa para almacenar una colección de mensajes de correo electrónico en un solo archivo, con cada mensaje concatenado y demarcado por una línea separadora.

MBOX se desarrolló por primera vez en la década de 1970 y desde entonces ha visto varias versiones e implementaciones a lo largo de los años. Se ha implementado en numerosos clientes de correo electrónico, como Unix Mail, Mozilla Thunderbird, Eudora y más.

#### Características principales

- MBOX es compatible con una amplia gama de plataformas, incluidas Unix, Linux y macOS.
- Los clientes como Mozilla Thunderbird, Apple Mail y muchos otros pueden leer y escribir archivos MBOX.
- La naturaleza de texto plano del formato facilita el análisis y el procesamiento mediante herramientas de manipulación de texto.
- Debido a su estructura simple, MBOX se usa popularmente para archivar y hacer copias de seguridad.
- Dado que todos los correos electrónicos se almacenan en un solo archivo, el archivo puede llegar a ser bastante grande con el tiempo, lo que genera ineficiencias.
#### Variantes de MBOX

MBOX viene en varias variantes, cada una con ligeras diferencias en la forma en que gestionan los mensajes:

- **MBOXO:** El formato original en el que las líneas «De» del cuerpo del correo electrónico están entre comillas con un carácter >.
- **MBOXRD:** Una variante de MBOXO que amplía aún más el método de cotización de las líneas «Desde».
- **MBOXCL:** Introducido por la variante «clásica» de MBOX, en la que cada línea «De» se entrecomilla con una cadena de origen.
- **MBOXCL2:** Una variante de MBOXCL en la que las líneas «De» se duplican para distinguirlas.

#### Base técnica del formato MBOX

**Estructura de archivos:**
  - Un archivo MBOX es un archivo de texto sin formato que contiene una serie de mensajes EML.
  - Cada mensaje comienza con una línea «De» (un espacio después de la palabra «De») que normalmente incluye la dirección de correo electrónico del remitente y la marca de tiempo en la que se recibió el mensaje.
  - Cada mensaje va seguido de una línea en blanco para separarlo del siguiente mensaje.
 
    **Example:**
   
    ```
    From user@example.com Fri Jan 01 00:00:00 2021
    (Headers)
   
    (Body)
   
    From user2@example.com Fri Jan 01 00:01:00 2021
    (Headers)
   
    (Body)
    ```

### PST/OST

 **Mesa de almacenamiento personal (PST)** and **Tabla de almacenamiento sin conexión (OST)** son formatos de archivo utilizados por Microsoft Outlook para almacenar copias de correos electrónicos, eventos del calendario y otros elementos.

#### Características principales

- Los archivos PST se utilizan para almacenar información personal y, por lo general, se utilizan para archivar correos electrónicos y datos antiguos. Los utilizan principalmente usuarios domésticos y pequeñas organizaciones para el almacenamiento local de mensajes de correo electrónico, contactos y eventos del calendario.
- Los archivos OST se utilizan para el almacenamiento sin conexión y la sincronización de correos electrónicos y otros datos con el servidor de Exchange. Lo utilizan principalmente los usuarios que acceden a Microsoft Exchange Server u Office 365.
- Se almacena localmente en el ordenador del usuario. Se puede acceder a él incluso cuando el usuario no está conectado al servidor de correo electrónico.
- Los archivos PST se pueden respaldar fácilmente y transferir a otras computadoras. Los usuarios pueden transferir archivos PST entre diferentes sistemas o versiones de Outlook.
- Los archivos OST no están diseñados para realizar copias de seguridad o transferencias manuales, ya que son copias sincronizadas de los datos del servidor. Los archivos OST están vinculados a perfiles específicos y no se pueden mover fácilmente a diferentes sistemas.

### OLM

 **Archivo de archivo de Outlook para Mac (OLM)** es un formato de archivo utilizado por Microsoft Outlook para Mac para almacenar mensajes de correo electrónico, eventos del calendario, contactos, tareas y otros elementos.

#### Características principales

- Los archivos OLM se utilizan principalmente para archivar y hacer copias de seguridad de correos electrónicos y otros elementos de Outlook en sistemas Mac.
- Los archivos OLM se almacenan localmente en el Mac del usuario.
- Los archivos OLM se pueden abrir y acceder a ellos a través de Microsoft Outlook para Mac. No son directamente compatibles con Outlook para Windows sin conversión.
- Microsoft no impone un límite de tamaño fijo para los archivos OLM, pero pueden producirse problemas de rendimiento si el archivo es muy grande. Los usuarios suelen gestionar el tamaño creando varios archivos más pequeños en lugar de un archivo OLM grande.
- Copia de seguridad: dado que los archivos OLM se almacenan localmente, se pueden hacer copias de seguridad o copiar en dispositivos de almacenamiento externos.

### TGZ

**TGZ**  (utilizado por Zimbra para el archivo de respaldo de buzones) es un formato de archivo utilizado para archivar y comprimir datos, comúnmente asociado con los sistemas Unix y Linux. El término «TGZ» hace referencia a una combinación de dos utilidades: «tar» (Tape Archive) y «gzip». El formato de archivo.tar agrupa varios archivos y directorios en un único archivo de almacenamiento. Conserva la información del sistema de archivos, como las estructuras de directorios, los permisos de los archivos y las marcas de tiempo. El formato de archivo.gz comprime los datos, lo que hace que el archivo tar sea más pequeño y fácil de administrar o transferir. La naturaleza comprimida del TGZ lo hace adecuado para transferir archivos de correo electrónico a través de Internet o moverlos de un sistema a otro.

### NSF

 **Instalación de almacenamiento de notas (NSF)** es un formato de archivo propietario utilizado principalmente por IBM Lotus Notes (ahora HCL Notes) para almacenar varios tipos de datos, incluidos el correo electrónico, los eventos del calendario, las tareas y otros datos de aplicaciones. Los archivos NSF utilizan un modelo de base de datos NoSQL basado en documentos. Cada base de datos se almacena como un único archivo NSF con la extensión.nsf. La extensión representa un formato de base de datos utilizado por IBM Notes y Domino Server. Cada correo electrónico, entrada de calendario o tarea se almacena como un documento que puede contener varios tipos de datos, como texto, archivos adjuntos, enlaces, formato de texto enriquecido e incluso metadatos.

## **Protocolos de correo**

### SMTP

**SMTP (Protocolo simple de transferencia de correo)** es un protocolo que se utiliza para enviar y recibir mensajes de correo electrónico a través de Internet. Es una parte crucial del proceso de comunicación por correo electrónico y es el principal responsable de transferir los correos electrónicos del servidor de correo del remitente al servidor de correo del destinatario, así como de enviar los correos electrónicos de un cliente a un servidor. El puerto predeterminado para SMTP es 25 para la comunicación entre servidores de correo. Los puertos 587 y 465 también se utilizan para SMTP: el 587 se utiliza habitualmente para el envío de correo y el 465 para SMTP a través de SSL (SMTPS). El SMTP se define por [Versión RFC 5321](https://datatracker.ietf.org/doc/html/rfc5321).

#### Características principales

- Admite mecanismos de autenticación (por ejemplo, SMTP AUTH) para garantizar que solo los usuarios autorizados puedan enviar correos electrónicos a través del servidor.
- SMTP puede usar SSL/TLS para cifrar la conexión entre el cliente y el servidor, garantizando así que los datos del correo electrónico se transmitan de forma segura.
- Proporciona mensajes de error y códigos de estado detallados para indicar si la transmisión del correo electrónico se ha realizado correctamente o no.
- SMTP puede gestionar mensajes de varias partes, lo que permite la inclusión de archivos adjuntos y varios tipos de contenido en un correo electrónico.
- SMTP es un protocolo estandarizado y ampliamente aceptado, que garantiza la compatibilidad entre diferentes sistemas y clientes de correo electrónico (por ejemplo, Microsoft Outlook y Mozilla Thunderbird utilizan SMTP para enviar correos electrónicos salientes). Los sistemas y aplicaciones automatizados utilizan SMTP para enviar notificaciones, alertas y otros correos electrónicos automatizados.

### IMAP

**Protocolo de acceso a mensajes de Internet (IMAP)** es un protocolo estándar que utilizan los clientes de correo electrónico para acceder, recuperar y administrar los mensajes de correo electrónico de un servidor de correo. Entre los clientes compatibles se encuentran Microsoft Outlook, Mozilla Thunderbird, Apple Mail y muchos servicios de correo web como Gmail, Yahoo Mail y Outlook.com. La versión más utilizada es IMAP4, definida por [RFC 3501](https://datatracker.ietf.org/doc/html/rfc3501). A diferencia de **POP (Protocolo de oficina de correos)**, que descarga los correos electrónicos a un dispositivo local, IMAP almacena los correos electrónicos en el servidor. La capacidad de ver y administrar los mensajes de correo electrónico directamente en el servidor de correo proporciona flexibilidad para acceder a ellos desde varios dispositivos y ubicaciones, lo que reduce el riesgo de pérdida de datos en caso de pérdida o daño del dispositivo. IMAP sincroniza el cliente de correo electrónico con el servidor, lo que garantiza que los cambios realizados en un cliente (como leer o eliminar un correo electrónico) se reflejen en todos los demás clientes. IMAP suele utilizar el puerto 143 para las comunicaciones no cifradas y el puerto 993 para las comunicaciones cifradas (SSL/TLS).

#### Características principales

- Administración de carpetas. IMAP permite a los usuarios crear, eliminar y cambiar el nombre de las carpetas del servidor de correo. Admite estructuras jerárquicas de carpetas para organizar los correos electrónicos.
- IMAP rastrea el estado de cada correo electrónico (por ejemplo, leído, no leído, marcado, respondido). Estos indicadores de estado se almacenan en el servidor, por lo que son coherentes en todos los dispositivos.
- IMAP puede recuperar partes específicas de un correo electrónico, como encabezados o partes del cuerpo, lo que puede resultar útil para obtener una vista previa de los correos electrónicos o gestionar archivos adjuntos de gran tamaño.
- IMAP admite la búsqueda y el filtrado de correos electrónicos en el lado del servidor según varios criterios, lo que permite a los clientes recuperar mensajes específicos sin descargar todos los correos electrónicos.
- Varios clientes pueden acceder al mismo buzón de correo simultáneamente. IMAP gestiona el acceso simultáneo y actualiza el estado de los correos electrónicos en tiempo real.
- Dependencia del servidor. Dado que los correos electrónicos se almacenan en el servidor, es necesaria una conexión a Internet confiable para acceder y administrar los correos electrónicos. El tiempo de inactividad del servidor puede afectar a la disponibilidad del correo electrónico.
- IMAP puede usar SSL/TLS para cifrar la conexión entre el cliente y el servidor, garantizando así que los datos del correo electrónico se transmitan de forma segura.
- IMAP admite varios métodos de autenticación, incluido OAuth, para verificar las identidades de los usuarios de forma segura.

#### Extensiones de protocolo

- **IMAP INACTIVO:** Una extensión que permite al servidor notificar al cliente sobre nuevos mensajes o cambios en tiempo real, lo que reduce la necesidad de sondeos frecuentes.
- **CUOTA IMAP:** Una extensión que proporciona mecanismos para administrar y reportar las cuotas de almacenamiento, lo que ayuda a los usuarios a administrar el tamaño de sus buzones.
- **MOVIMIENTO IMAP:** Una extensión que optimiza el proceso de mover mensajes entre carpetas del servidor, mejorando el rendimiento.

### POP3

 **Protocolo de oficina de correos versión 3 (POP3)** es un protocolo que utilizan los clientes de correo electrónico como Microsoft Outlook, Mozilla Thunderbird y Apple Mail para recuperar el correo electrónico de un servidor de correo. Es uno de los protocolos más antiguos y sencillos de recuperación de correo electrónico, diseñado para descargar correos electrónicos a un dispositivo local y, opcionalmente, eliminarlos del servidor.

#### Características principales

- Dado que los correos electrónicos se descargan en el dispositivo local, los usuarios pueden acceder a sus correos electrónicos sin conexión sin necesidad de una conexión a Internet constante.
- POP3 es fácil de configurar y usar, por lo que es accesible para los usuarios que necesitan una recuperación básica del correo electrónico sin funciones avanzadas.
- POP3 no sincroniza el correo electrónico en varios dispositivos. Una vez que se descarga un correo electrónico en un dispositivo, deja de estar disponible en el servidor de forma predeterminada.
- POP3 proporciona capacidades limitadas de administración del lado del servidor. No se admiten funciones avanzadas como la administración de carpetas, la búsqueda en el servidor y los indicadores de estado de los mensajes.
- Dado que los correos electrónicos se almacenan localmente, los usuarios deben asegurarse de hacer copias de seguridad de sus datos de correo electrónico para evitar pérdidas en caso de fallo del dispositivo.
- Los usuarios pueden configurar los ajustes de POP3 para eliminar los correos electrónicos del servidor inmediatamente después de la descarga, después de un período específico o cuando se eliminan del cliente local.
- POP3 puede usar SSL/TLS para cifrar la conexión entre el cliente y el servidor, garantizando así que los datos del correo electrónico se transmitan de forma segura.

#### Versiones y extensiones de protocolo

- **POP3 a través de SSL (POP3S)** es una versión de POP3 que funciona a través de una conexión SSL/TLS y proporciona una comunicación cifrada entre el cliente y el servidor.
- **APOP (protocolo de oficina de correos autenticado)** es una extensión que proporciona un método de autenticación más seguro mediante el uso de contraseñas con hash.

## **API para acceder a los servicios de correo**

### Exchange Web Dav (ha quedado oficialmente obsoleto)

**Exchange WebDAV (creación y control de versiones distribuidos en la web)** era una extensión de protocolo utilizada por Microsoft Exchange Server para permitir a los clientes acceder y manipular el correo, el calendario y los elementos de contacto almacenados en el servidor a través de HTTP. Aunque ha quedado oficialmente obsoleta, desempeñó un papel importante en el desarrollo del acceso remoto y basado en la web a los datos de Exchange.

### EWS

**Servicios web de Exchange (EWS)** es una API proporcionada por Microsoft para interactuar con Microsoft Exchange Server. Permite a los desarrolladores acceder a los datos de Exchange, como correos electrónicos, eventos del calendario, contactos y tareas, y manipularlos mediante programación. EWS se introdujo para reemplazar los protocolos más antiguos, como WebDAV, y proporciona una forma más sólida y eficiente de trabajar con los datos de Exchange.

Utiliza el SOAP (Protocolo simple de acceso a objetos) a través de HTTP y HTTPS para enviar y recibir mensajes entre el cliente y el servidor de Exchange. La naturaleza basada en SOAP de EWS puede resultar compleja de implementar y depurar en comparación con las API RESTful. Microsoft está optando gradualmente por la API Graph de Microsoft, que proporciona un enfoque más moderno y REST para acceder a los datos de Microsoft 365, incluido Exchange Online.

### Microsoft Graph

**Microsoft Graph** es una potente API que proporciona un punto final unificado para acceder a una amplia gama de datos y servicios del ecosistema de Microsoft 365. Permite a los desarrolladores interactuar con una variedad de servicios de Microsoft, incluidos Office 365, Azure Active Directory, SharePoint, OneDrive, Outlook, Microsoft Teams y más. Sirve como puerta de entrada a los datos y la información de Microsoft 365.

#### Características principales

- La URL base de la API es https://graph.microsoft.com.
- Utiliza OAuth 2.0 para la autenticación y la autorización.
- Aprovecha las capacidades de inteligencia artificial y aprendizaje automático de Microsoft para obtener información mejorada sobre los datos.

### API de Gmail

**API de Gmail** es una API RESTful proporcionada por Google que permite a los desarrolladores interactuar mediante programación con los buzones de Gmail y realizar diversas operaciones con los datos del correo electrónico (leer, enviar, eliminar y organizar los mensajes de correo electrónico). Ofrece una alternativa más flexible y potente a los protocolos IMAP y SMTP tradicionales, ya que permite a los desarrolladores acceder y gestionar los mensajes, los hilos, las etiquetas, los borradores de Gmail y mucho más. Está disponible a través de Google Cloud Platform.

#### Características principales

- Realice varias solicitudes de API en una sola llamada HTTP para mejorar la eficiencia y reducir la cantidad de solicitudes de red.
- Utiliza OAuth 2.0 para una autenticación y autorización seguras, lo que garantiza que las aplicaciones solo accedan a los datos para los que los usuarios han otorgado permiso de forma explícita.
- Proporciona varios alcances de permisos, lo que permite a las aplicaciones solicitar solo el nivel de acceso que necesitan (por ejemplo, acceso de solo lectura, acceso total).
- Todas las interacciones de la API se producen a través de HTTPS para garantizar una comunicación segura entre la aplicación y los servidores de Google.

## **Tecnologías avanzadas**

### S/MIME

**Extensiones de correo de Internet seguras y multipropósito (S/MIME)** es un estándar muy utilizado para proteger la comunicación por correo electrónico. Proporciona un método para enviar y recibir mensajes de correo electrónico firmados y cifrados, lo que garantiza la integridad, la autenticidad y la confidencialidad de los mensajes.

#### Características principales

- S/MIME garantiza que solo el destinatario previsto pueda leer el contenido del correo electrónico. Utiliza una combinación de algoritmos de cifrado simétricos (para la velocidad) y asimétricos (para el intercambio de claves). Los algoritmos más utilizados son el RSA (utilizado para el cifrado asimétrico), el AES o el estándar de cifrado avanzado (uno de los algoritmos simétricos) y el triple DES.
- Confirma la identidad del remitente.
- Verifica que el contenido del correo electrónico no se haya manipulado durante el tránsito. Impide que el remitente niegue la autoría del correo electrónico.
- Usa la clave privada del remitente para crear una firma y el cliente del destinatario usa la clave pública del remitente para verificarla.
- S/MIME se basa en una infraestructura de clave pública (PKI) para la administración y el intercambio de claves. Los certificados digitales, emitidos por las autoridades de certificación (CA), vinculan las claves públicas a las identidades individuales. Los certificados suelen seguir el estándar X.509.

### DKIM

**Correo identificado con claves de dominio (DKIM)** es un mecanismo de autenticación de correo electrónico diseñado para detectar direcciones de remitentes falsificadas, una técnica común que se utiliza en la suplantación de identidad y la suplantación de correo electrónico. Permite a una organización asumir la responsabilidad de un correo electrónico durante su tránsito asociando un nombre de dominio al mensaje, garantizando así su autenticidad e integridad. DKIM verifica que un correo electrónico que supuestamente proviene de un dominio específico haya sido autorizado por el propietario del dominio, centrándose principalmente en la autenticidad de la dirección de correo electrónico «De». Esto se logra permitiendo al remitente firmar electrónicamente su correo electrónico con una clave privada, mientras que el destinatario verifica esta firma mediante una clave pública publicada en los registros DNS del remitente.

#### Características principales

- DKIM añade un encabezado «DKIM-Signature» al correo electrónico que contiene la firma digital y varios parámetros clave. El cuerpo del correo electrónico y los encabezados seleccionados se codifican mediante un algoritmo de hash como el SHA-256. A continuación, este hash se cifra con la clave privada del remitente para generar la firma digital.
- El remitente publica la clave pública en sus registros DNS. El servidor de correo electrónico del destinatario busca la clave pública del remitente en el DNS para verificar la firma digital.

### Correo electrónico de AMP

**Páginas móviles aceleradas (AMP)** for Email es un marco de código abierto diseñado para crear experiencias de correo electrónico dinámicas, interactivas y atractivas. Está diseñado para hacer que los correos electrónicos sean más dinámicos y funcionales, transformando un medio que tradicionalmente ha sido estático y pasivo.

#### Características principales

- Permite a los usuarios realizar acciones directamente desde el correo electrónico, como confirmar su asistencia a los eventos, rellenar formularios o interactuar con carruseles de productos.
- Los correos electrónicos pueden ofrecer contenido dinámico que se actualiza en el momento de la apertura. Esto garantiza que los usuarios vean la información más actualizada, ya sean los precios más recientes, el estado de las existencias o las actualizaciones de noticias.
- Los correos electrónicos de AMP son compatibles con varios de los principales clientes de correo electrónico, incluidos Gmail, Yahoo Mail y Outlook.com. Cada cliente de correo electrónico que admite correos electrónicos de AMP mantiene su propio conjunto de requisitos y reglas de representación.
- Los correos electrónicos de AMP deben enviarse en un formato MIME de varias partes que contenga una versión de texto sin formato para una accesibilidad básica, una versión HTML para un contenido rico y visualmente atractivo y una versión AMP para elementos dinámicos e interactivos, lo que garantiza la compatibilidad y una experiencia de usuario mejorada en varios clientes de correo electrónico.
- Solo los remitentes verificados pueden enviar correos electrónicos AMP, lo que garantiza que los correos electrónicos sean seguros y confiables.

### AntiSpam

El antispam se refiere a una variedad de técnicas, tecnologías y estrategias diseñadas para detectar, prevenir y mitigar los mensajes de correo electrónico no solicitados y, a menudo, dañinos, comúnmente conocidos como correo no deseado.

#### Técnicas antispam

1. **Métodos de filtrado**
   - Filtrado basado en el contenido: analiza el contenido del correo electrónico en busca de indicadores de spam comunes.
   - Listas negras: listas de direcciones IP o dominios de spam conocidos que se bloquean automáticamente.
   - Listas blancas: listas de remitentes aprobados a los que siempre se permite el acceso.
   - Filtrado heurístico: utiliza reglas y algoritmos para detectar el spam en función de patrones.
   - Filtrado bayesiano: utiliza métodos estadísticos para identificar el spam basándose en datos históricos.
   - Lista gris: rechaza temporalmente los correos electrónicos de remitentes desconocidos y los acepta si se vuelven a enviar después de un retraso.
   - Aprendizaje automático: utiliza modelos complejos entrenados en grandes conjuntos de datos para identificar el spam.

2. **Métodos de autenticación**
   - SPF (Sender Policy Framework): verifica que la dirección IP del remitente esté autorizada para enviar correos electrónicos para el dominio.
   - DKIM (DomainKeys Identified Mail): utiliza firmas digitales para verificar que el correo electrónico no se haya modificado durante el tránsito y que, de hecho, pertenezca al dominio que afirma ser.
   - DMARC (autenticación, informes y conformidad de mensajes basados en el dominio): se basa en SPF y DKIM para proporcionar un método estandarizado para que los remitentes de correo electrónico indiquen que sus mensajes están protegidos y cómo los servidores receptores deben gestionar los errores de autenticación.

### Rebotes de correo electrónico

#### Tipos de rebotes de correo electrónico

1. **Rebotes duros.** Fallos de entrega permanentes que indican que el correo electrónico no se puede entregar a la dirección del destinatario previsto.
   - Causas comunes:
     - Direcciones de correo electrónico no válidas o inexistentes.
     - El dominio del destinatario no existe.
     - Problemas permanentes con el servidor por parte del destinatario.
     - Errores tipográficos o de formato en la dirección de correo electrónico.

2. **Rebotes suaves.** Fallos de entrega temporales que indican que el correo electrónico no se pudo entregar en ese momento, pero que puede tener éxito si se vuelve a intentar más tarde.
   - Causas comunes:
     - El buzón del destinatario está lleno.
     - Problemas temporales con el servidor por parte del destinatario.
     - El servidor de correo electrónico del destinatario está inactivo o desconectado.
     - Los correos electrónicos son demasiado grandes para el sistema de correo electrónico del destinatario.

Los servidores de correo electrónico suelen devolver códigos de rebote que pueden ayudar a diagnosticar el motivo de un rebote.

### Enhebrado de correo electrónico

El subprocesamiento de correos electrónicos es un método que utilizan los clientes y aplicaciones de correo electrónico para agrupar correos electrónicos relacionados según su asunto o conversación, lo que facilita a los usuarios seguir y administrar los intercambios de correo electrónico.

#### Características principales

- **Encabezados de respuesta y referencias**. Encabezados de correo electrónico que apuntan a mensajes anteriores del hilo, lo que ayuda al cliente de correo electrónico a vincular las respuestas y los reenvíos al correo electrónico original.
- Líneas de asunto. A menudo se usa para agrupar correos electrónicos en hilos. Los correos electrónicos con el mismo asunto, normalmente con el prefijo «Re:» (respuesta) o «Fwd:» (reenviar), se agrupan.
- Los usuarios pueden expandir o reducir los hilos, centrándose solo en las partes relevantes de una conversación.
