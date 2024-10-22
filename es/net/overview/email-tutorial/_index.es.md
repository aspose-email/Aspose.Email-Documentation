---
title: "Tutorial de Email"
url: /es/net/email-tutorial/
weight: 5
type: docs
---

## **Formatos de Archivo de Email Más Populares**

### MSG

**Microsoft Outlook Message (MSG)** es un formato de email propietario utilizado por Microsoft Outlook para almacenar mensajes de email individuales. Estos archivos contienen el contenido del email y metadatos como el remitente, destinatarios, asunto y sellos de tiempo. Soportan formato enriquecido, archivos adjuntos y características específicas de Outlook como banderas, importancia y sensibilidad.

#### Características clave

- El archivo MSG representa un solo mensaje de email.
- Los archivos MSG se asocian con Microsoft Outlook y pueden ser abiertos por él.
- Los archivos MSG se utilizan comúnmente para archivar, crear copias de seguridad e intercambiar elementos de Outlook entre diferentes instancias de Outlook u otros clientes de email compatibles.

MSG está estrechamente relacionado en el contexto de Microsoft Outlook y **Messaging Application Programming Interface (MAPI)**. MAPI es una interfaz de programación que permite a las aplicaciones interactuar con los servicios de mensajería, principalmente Microsoft Exchange Server y Microsoft Outlook. Proporciona un conjunto de funciones y protocolos para enviar, recibir y gestionar mensajes de email, así como acceder a otras características relacionadas con la mensajería, como calendarios, contactos y tareas. MAPI es utilizado por Microsoft Outlook para crear, manipular y gestionar mensajes de email. Cuando un usuario compone o recibe un email en Outlook, MAPI maneja la comunicación subyacente con el servidor de correo y proporciona las funciones necesarias para gestionar el contenido del mensaje.

#### Base técnica para el formato MSG

Los archivos MSG almacenan datos de mensajes utilizando **propiedades MAPI**, que son atributos que definen varios aspectos del mensaje. Estas propiedades incluyen atributos estándar como remitente, destinatario, asunto y sellos de tiempo, así como propiedades personalizadas y atributos extendidos. Las propiedades organizan el mensaje en una estructura jerárquica, con propiedades de nivel superior que definen los atributos generales del mensaje y propiedades anidadas que representan componentes específicos como destinatarios, archivos adjuntos y objetos incrustados. Los archivos MSG pueden contener múltiples flujos de propiedades, cada uno conteniendo un conjunto de propiedades MAPI relacionadas. Estos flujos están estructurados de acuerdo con el **Compound File Binary Format (CFBF)** y almacenan tanto propiedades estándar como personalizadas.

### OFT

**Outlook File Template (OFT)** son formatos de email utilizados por Microsoft Outlook para crear mensajes estandarizados. A diferencia de los archivos MSG, los archivos OFT no contienen el contenido real del mensaje, sino que sirven como plantillas con formato, diseño y marcadores de posición predefinidos para contenido dinámico.

#### Características clave

- Los archivos OFT optimizan la creación de emails repetitivos al proporcionar plantillas pre-diseñadas para escenarios comunes como boletines, anuncios o respuestas.
- Al usar plantillas OFT, las organizaciones aseguran consistencia en la marca, formato y comunicación a través de todas las comunicaciones salientes.
- Los usuarios pueden personalizar las plantillas OFT al agregar o modificar contenido antes de enviarlo, permitiendo mensajes personalizados mientras se mantiene un formato estandarizado.

### EML

**EML** es uno de los formatos de archivo de email más reconocidos y utilizados, diseñado principalmente para adherirse al estándar **MIME (Multipurpose Internet Mail Extensions)**. Este formato es ampliamente soportado en varios clientes de correo y sistemas debido a su enfoque abierto y generalizado para el almacenamiento y transmisión de emails.

#### Características clave

- Cada archivo EML encapsula un solo mensaje de email junto con su metadatos asociados como el remitente, destinatarios, asunto y sellos de tiempo.
- Los archivos EML soportan formato enriquecido, archivos adjuntos y elementos incrustados, cumpliendo con el estándar MIME que permite una representación versátil del contenido del email.
- A diferencia de formatos propietarios como MSG (Microsoft Outlook Message), que están estrechamente ligados a software específico (Outlook y MAPI), los archivos EML ofrecen un enfoque más universal compatible con varios programas de email a través de diferentes plataformas. Los archivos EML son compatibles con una multitud de clientes de email, incluyendo pero no limitado a Microsoft Outlook, Mozilla Thunderbird, Apple Mail y muchos servicios de email basados en la web.

#### Base técnica para el formato EML

El formato de archivo EML está inherentemente ligado al estándar MIME, que es una especificación para el formato de los cuerpos de mensaje de Internet. MIME extiende el formato básico de email para soportar texto en conjuntos de caracteres distintos de ASCII, así como archivos adjuntos de contenido multimedia.

**Estructura MIME:**

- Un archivo EML comienza con la sección de encabezado, que contiene información como De, Para, Asunto, Fecha y otros encabezados. Encabezados adicionales pueden incluir Content-Type, Content-Transfer-Encoding, y más.
- Después de los encabezados, se presenta el cuerpo de un archivo EML. Esta sección puede contener texto plano, HTML o contenido multipart, permitiendo la combinación de diferentes tipos de contenido dentro de un solo mensaje.
- Un archivo EML puede incluir archivos adjuntos codificados en base64, permitiendo que datos binarios sean transferidos por email. Estos archivos adjuntos están definidos dentro de sus propias partes MIME con encabezados apropiados que indican el tipo de archivo y codificación.

**Tipos MIME:**

El contenido de un archivo EML se descompone en varios tipos MIME para diferenciar texto, HTML y otros tipos de medios. Los tipos MIME comunes encontrados dentro de un archivo EML incluyen:

- `text/plain` para mensajes de texto plano.
- `text/html` para mensajes con formato HTML.
- `multipart/mixed` para correos electrónicos que incluyen tanto el contenido del mensaje como archivos adjuntos.
- `application/octet-stream` para archivos adjuntos de formato binario.

### TNEF

**Transport Neutral Encapsulation Format (TNEF)** es un formato de email propietario utilizado por Microsoft Outlook y Microsoft Exchange Server para encapsular propiedades de email y contenido de texto enriquecido que puede no ser soportado por protocolos de email estándar. Se utiliza principalmente por clientes de email de Microsoft para codificar y transmitir formato de texto enriquecido, objetos incrustados y otras características de email propietarias, asegurando que contenido de email complejo, como formato, archivos incrustados y eventos de calendario, se conserve cuando se envían emails entre diferentes clientes de email de Microsoft.

#### Características clave

- TNEF puede encapsular una amplia gama de propiedades MAPI, un formato de texto enriquecido específico de Microsoft y propiedades especiales que no pueden ser transmitidas a través de email estándar MIME o de texto plano.
- Elementos de Outlook, como Calendario, Contactos, Tareas, Notas pueden ser encapsulados dentro del formato TNEF.
- Los clientes de email que no son de Microsoft pueden no entender o procesar correctamente los archivos adjuntos TNEF, a menudo resultando en el molesto archivo `winmail.dat`. Esto generalmente sucede porque no pueden decodificar el formato propietario codificado en TNEF.

#### Base técnica para el formato TNEF

- TNEF encapsula el contenido del email en un archivo adjunto binario especial. Este archivo adjunto típicamente lleva una extensión de archivo `.dat`, comúnmente nombrada `winmail.dat`.
- Los datos TNEF suelen estar asociados con el tipo MIME `application/ms-tnef`.
- El formato TNEF representa una jerarquía de propiedades de mensaje como una estructura plana, que puede verse como un flujo de datos secuencial. El formato típico de una propiedad específica en el flujo incluye un identificador con información de tipo de datos, tamaño (si no está definido por el tipo), y datos.

## **Formatos Comunes de Almacenamiento de Email**

### MBOX

**MBOX (corto para Mailbox)** es un formato de almacenamiento de email ampliamente utilizado que ha estado en uso durante varias décadas. Se utiliza para almacenar una colección de mensajes de email en un solo archivo, con cada mensaje concatenado y demarcado por una línea separadora.

MBOX fue desarrollado por primera vez en la década de 1970 y ha visto varias versiones e implementaciones a lo largo de los años. Ha sido implementado en numerosos clientes de email como Unix mail, Mozilla Thunderbird, Eudora, y más.

#### Características clave

- MBOX es soportado en una amplia gama de plataformas, incluyendo Unix, Linux y macOS.
- Clientes como Mozilla Thunderbird, Apple Mail y muchos otros pueden leer y escribir archivos MBOX.
- La naturaleza de texto plano del formato lo hace simple de analizar y procesar utilizando herramientas de manipulación de texto.
- Debido a su estructura simple, MBOX es utilizado comúnmente para propósitos de archivo y copia de seguridad.
- Dado que todos los emails se almacenan en un solo archivo, el archivo puede volverse bastante grande con el tiempo, llevando a ineficiencias.

#### Variantes de MBOX

MBOX viene en varias variantes, cada una con ligeras diferencias en cómo manejan los mensajes:

- **MBOXO:** El formato original donde las líneas "From " en el cuerpo del email son citadas con un carácter >.
- **MBOXRD:** Una variante de MBOXO que extiende aún más el método de citación de las líneas "From ".
- **MBOXCL:** Introducido por la variante "Clásica" MBOX donde cada línea "From " es citada con una cadena ffrom.
- **MBOXCL2:** Una variación de MBOXCL donde las líneas "From " son duplicadas para diferenciarlas.

#### Base técnica para el formato MBOX

**Estructura de Archivo:**
- Un archivo MBOX es un archivo de texto plano que contiene una serie de mensajes EML.
- Cada mensaje comienza con una línea "From " (un espacio después de la palabra "From") que normalmente incluye la dirección de email del remitente y el sello de tiempo cuando se recibió el mensaje.
- Cada mensaje es seguido por una línea en blanco para separarlo del siguiente mensaje.

    **Ejemplo:**
    
    ```
    From user@example.com Fri Jan 01 00:00:00 2021
    (Encabezados)
    
    (Cuerpo)
    
    From user2@example.com Fri Jan 01 00:01:00 2021
    (Encabezados)
    
    (Cuerpo)
    ```

### PST/OST

**Personal Storage Table (PST)** y **Offline Storage Table (OST)** son formatos de archivo utilizados por Microsoft Outlook para almacenar copias de emails, eventos de calendario y otros elementos.

#### Características clave

- Los archivos PST se utilizan para almacenar información personal y se utilizan típicamente para archivar emails y datos más antiguos. Usado principalmente por usuarios domésticos y pequeñas organizaciones para almacenamiento local de mensajes de email, contactos y eventos de calendario.
- Los archivos OST se utilizan para almacenamiento offline y sincronización de emails y otros datos con el servidor Exchange. Usado principalmente por usuarios que acceden a Microsoft Exchange Server o Office 365.
- Almacenados localmente en la computadora de un usuario. Pueden ser accedidos incluso cuando el usuario no está conectado al servidor de email.
- Los archivos PST pueden ser fácilmente respaldados y transferidos a otras computadoras. Los usuarios pueden transferir archivos PST entre diferentes sistemas o versiones de Outlook.
- Los archivos OST no están destinados a ser respaldados o transferidos manualmente ya que son copias sincronizadas de los datos del servidor. Los archivos OST están ligados a perfiles específicos y no pueden ser movidos fácilmente a otros sistemas.

### OLM

**Outlook for Mac Archive File (OLM)** es un formato de archivo utilizado por Microsoft Outlook para Mac para almacenar mensajes de email, eventos de calendario, contactos, tareas y otros elementos.

#### Características clave

- Los archivos OLM son utilizados principalmente para archivar y respaldar emails y otros elementos de Outlook en sistemas Mac.
- Los archivos OLM se almacenan localmente en el Mac del usuario.
- Los archivos OLM pueden ser abiertos y accesados a través de Microsoft Outlook para Mac. No son directamente compatibles con Outlook para Windows sin conversión.
- No hay un límite de tamaño fijo para los archivos OLM impuesto por Microsoft, pero pueden ocurrir problemas de rendimiento si el archivo se vuelve muy grande. Los usuarios típicamente gestionan el tamaño creando múltiples archivos de archivo más pequeños en lugar de un solo archivo OLM grande.
- Copia de seguridad: Dado que los archivos OLM se almacenan localmente, pueden ser respaldados o copiados a dispositivos de almacenamiento externos.

### TGZ

**TGZ** (usado por Zimbra para archivo de respaldo de buzones) es un formato de archivo utilizado para archivar y comprimir datos, comúnmente asociado con sistemas Unix y Linux. El término "TGZ" se refiere a una combinación de dos utilidades: "tar" (Tape Archive) y "gzip." El formato de archivo .tar agrupa múltiples archivos y directorios en un solo archivo de archivo. Preserva la información del sistema de archivos como estructuras de directorios, permisos de archivos y sellos de tiempo. El formato de archivo .gz comprime datos, haciendo que el archivo tar sea más pequeño y más fácil de gestionar o transferir. La naturaleza comprimida de TGZ lo hace adecuado para transferir archivos de archivo de email por internet o moverlos entre sistemas.

### NSF

**Notes Storage Facility (NSF)** es un formato de archivo propietario utilizado principalmente por IBM Lotus Notes (ahora HCL Notes) para almacenar varios tipos de datos, incluyendo email, eventos de calendario, tareas y otros datos de aplicación. Los archivos NSF utilizan un modelo de base de datos NoSQL basado en documentos. Cada base de datos se almacena como un único archivo NSF con extensión .nsf. La extensión representa un formato de base de datos utilizado por IBM Notes y Domino Server. Cada email, entrada de calendario o tarea se almacena como un documento que puede contener varios tipos de datos como texto, archivos adjuntos, enlaces, formato de texto enriquecido e incluso metadatos.

## **Protocolos de Email**

### SMTP

**SMTP (Simple Mail Transfer Protocol)** es un protocolo utilizado para enviar y recibir mensajes de email a través de Internet. Es una parte crucial del proceso de comunicación de email y es principalmente responsable de transferir emails desde el servidor de correo del remitente al servidor de correo del destinatario, así como de enviar emails desde un cliente a un servidor. El puerto predeterminado para SMTP es 25 para la comunicación entre servidores de correo. El puerto 587 y el puerto 465 también se utilizan para SMTP, siendo 587 comúnmente utilizado para la presentación de correo y 465 para SMTP sobre SSL (SMTPS). SMTP está definido por [RFC 5321 version](https://datatracker.ietf.org/doc/html/rfc5321).

#### Características clave

- Soporta mecanismos de autenticación (por ejemplo, SMTP AUTH) para asegurar que solo usuarios autorizados puedan enviar emails a través del servidor.
- SMTP puede utilizar SSL/TLS para encriptar la conexión entre el cliente y el servidor, asegurando que los datos del email sean transmitidos de manera segura.
- Proporciona mensajes de error detallados y códigos de estado para indicar el éxito o fallo de la transmisión de email.
- SMTP puede manejar mensajes multipart, permitiendo la inclusión de archivos adjuntos y varios tipos de contenido dentro de un email.
- SMTP es un protocolo ampliamente aceptado y estandarizado, asegurando compatibilidad entre diferentes sistemas y clientes de email (por ejemplo, Microsoft Outlook, Mozilla Thunderbird utilizan SMTP para enviar emails salientes). Sistemas y aplicaciones automatizadas utilizan SMTP para enviar notificaciones, alertas y otros emails automáticos.

### IMAP

**Internet Message Access Protocol (IMAP)** es un protocolo estándar utilizado por clientes de email para acceder, recuperar y gestionar mensajes de email desde un servidor de correo. Entre los clientes soportados se encuentran Microsoft Outlook, Mozilla Thunderbird, Apple Mail y muchos servicios de webmail como Gmail, Yahoo Mail y Outlook.com. La versión más utilizada es IMAP4, definida por [RFC 3501](https://datatracker.ietf.org/doc/html/rfc3501). A diferencia de **POP (Post Office Protocol)**, que descarga emails a un dispositivo local, IMAP almacena emails en el servidor. La capacidad de ver y gestionar mensajes de email directamente en el servidor proporciona flexibilidad para acceder a ellos desde múltiples dispositivos y ubicaciones, reduciendo el riesgo de pérdida de datos si un dispositivo se pierde o se daña. IMAP sincroniza el cliente de email con el servidor, asegurando que los cambios realizados en un cliente (como leer o eliminar un email) se reflejen en todos los demás clientes. IMAP utiliza típicamente el puerto 143 para comunicaciones no encriptadas y el puerto 993 para comunicaciones encriptadas (SSL/TLS).

#### Características clave

- Gestión de carpetas. IMAP permite a los usuarios crear, eliminar y renombrar carpetas en el servidor de correo. Soporta estructuras de carpetas jerárquicas para organizar emails.
- IMAP rastrea el estado de cada email (por ejemplo, leído, no leído, señalado, respondido). Estas banderas de estado se almacenan en el servidor, por lo que son consistentes en todos los dispositivos.
- IMAP puede recuperar partes específicas de un email, como encabezados o partes del cuerpo, que pueden ser útiles para previsualizar emails o manejar archivos adjuntos grandes.
- IMAP soporta búsqueda y filtrado del lado del servidor de emails basados en varios criterios, permitiendo a los clientes recuperar mensajes específicos sin descargar todos los emails.
- Múltiples clientes pueden acceder a la misma bandeja de entrada simultáneamente. IMAP maneja el acceso concurrente y actualiza el estado de los emails en tiempo real.
- Dependencia del servidor. Dado que los emails se almacenan en el servidor, una conexión a internet confiable es necesaria para acceder y gestionar emails. El tiempo de inactividad del servidor puede afectar la disponibilidad del email.
- IMAP puede utilizar SSL/TLS para encriptar la conexión entre el cliente y el servidor, asegurando que los datos del email sean transmitidos de manera segura.
- IMAP soporta varios métodos de autenticación, incluyendo OAuth, para verificar la identidad de los usuarios de manera segura.

#### Extensiones de protocolo

- **IMAP IDLE:** Una extensión que permite que el servidor notifique al cliente sobre nuevos mensajes o cambios en tiempo real, reduciendo la necesidad de sondeos frecuentes.
- **IMAP QUOTA:** Una extensión que proporciona mecanismos para gestionar y reportar cuotas de almacenamiento, ayudando a los usuarios a gestionar el tamaño de su bandeja de entrada.
- **IMAP MOVE:** Una extensión que optimiza el proceso de mover mensajes entre carpetas en el servidor, mejorando el rendimiento.

### POP3

**Post Office Protocol version 3 (POP3)** es un protocolo utilizado por clientes de email como Microsoft Outlook, Mozilla Thunderbird y Apple Mail para recuperar email de un servidor de correo. Es uno de los protocolos más antiguos y simples para la recuperación de email, diseñado para descargar emails a un dispositivo local y opcionalmente eliminarlos del servidor.

#### Características clave

- Dado que los emails son descargados al dispositivo local, los usuarios pueden acceder a sus emails sin conexión a internet.
- POP3 es simple de configurar y usar, haciendo que sea accesible para usuarios que necesitan recuperación básica de emails sin características avanzadas.
- POP3 no sincroniza emails en múltiples dispositivos. Una vez que un email es descargado a un dispositivo, ya no está disponible en el servidor por defecto.
- POP3 proporciona capacidades limitadas de gestión del lado del servidor. Características avanzadas como gestión de carpetas, búsqueda del lado del servidor y banderas de estado de mensajes no son soportadas.
- Dado que los emails se almacenan localmente, los usuarios deben asegurarse de respaldar sus datos de email para prevenir pérdidas en caso de fallas del dispositivo.
- Los usuarios pueden configurar las configuraciones de POP3 para eliminar emails del servidor inmediatamente después de la descarga, después de un período específico, o cuando se eliminen del cliente local.
- POP3 puede utilizar SSL/TLS para encriptar la conexión entre el cliente y el servidor, asegurando que los datos del email sean transmitidos de manera segura.

#### Versiones y extensiones de protocolo

- **POP3 sobre SSL (POP3S)** es una versión de POP3 que opera sobre una conexión SSL/TLS, proporcionando comunicación encriptada entre el cliente y el servidor.
- **APOP (Authenticated Post Office Protocol)** es una extensión que proporciona un método de autenticación más seguro al utilizar contraseñas hasheadas.

## **API para Acceder a Servicios de Email**

### Exchange Web DAV (ha sido oficialmente deprecado)

**Exchange WebDAV (Web Distributed Authoring and Versioning)** era una extensión de protocolo utilizada por Microsoft Exchange Server para permitir que los clientes accedieran y manipularan correos, eventos de calendario y elementos de contacto almacenados en el servidor a través de HTTP. Aunque ha sido oficialmente deprecado, jugó un papel significativo en el desarrollo de accesos remotos y basados en la web a datos de Exchange.

### EWS

**Exchange Web Services (EWS)** es una API proporcionada por Microsoft para interactuar con Microsoft Exchange Server. Permite a los desarrolladores acceder y manipular datos de Exchange como emails, eventos de calendario, contactos y tareas programáticamente. EWS fue introducida para reemplazar protocolos más antiguos como WebDAV y proporciona una forma más robusta y eficiente de trabajar con datos de Exchange.

Utiliza SOAP (Simple Object Access Protocol) sobre HTTP y HTTPS para enviar y recibir mensajes entre el cliente y el servidor de Exchange. La naturaleza basada en SOAP de EWS puede ser compleja de implementar y depurar en comparación con las APIs RESTful. Microsoft está cambiando gradualmente hacia Microsoft Graph API, que proporciona un enfoque más moderno y RESTful para acceder a los datos de Microsoft 365, incluyendo Exchange Online.

### Microsoft Graph

**Microsoft Graph** es una poderosa API que proporciona un punto de acceso unificado para acceder a una amplia gama de datos y servicios en el ecosistema de Microsoft 365. Permite a los desarrolladores interactuar con varios servicios de Microsoft, incluidos Office 365, Azure Active Directory, SharePoint, OneDrive, Outlook, Microsoft Teams, y más. Sirve como una puerta de enlace a datos e información dentro de Microsoft 365.

#### Características clave

- La URL base para la API es https://graph.microsoft.com.
- Utiliza OAuth 2.0 para autenticación y autorización.
- Aprovecha las capacidades de IA y aprendizaje automático de Microsoft para obtener información mejorada de los datos.

### Gmail API

**Gmail API** es una API RESTful proporcionada por Google que permite a los desarrolladores interactuar programáticamente con los buzones de Gmail y realizar varias operaciones en los datos de email (leer, enviar, eliminar y organizar mensajes de email). Ofrece una alternativa más flexible y potente a los protocolos tradicionales IMAP y SMTP, permitiendo a los desarrolladores acceder y gestionar mensajes, hilos, etiquetas, borradores de Gmail, y más. Está disponible a través de Google Cloud Platform. 

#### Características clave

- Realiza múltiples solicitudes de API en una sola llamada HTTP para mejorar la eficiencia y reducir la cantidad de solicitudes de red.
- Utiliza OAuth 2.0 para una autenticación y autorización seguras, asegurando que las aplicaciones solo accedan a los datos que los usuarios han otorgado explícitamente permiso para.
- Proporciona varios alcances de permisos, permitiendo a las aplicaciones solicitar solo el nivel de acceso que necesitan (por ejemplo, acceso solo de lectura, acceso completo).
- Todas las interacciones con la API ocurren a través de HTTPS para garantizar una comunicación segura entre la aplicación y los servidores de Google.

## **Tecnologías Avanzadas**

### S/MIME

**Secure/Multipurpose Internet Mail Extensions (S/MIME)** es un estándar ampliamente utilizado para asegurar la comunicación por email. Proporciona un método para enviar y recibir mensajes de email firmados y encriptados, asegurando la integridad, autenticidad y confidencialidad del mensaje.

#### Características clave

- S/MIME asegura que solo el destinatario previsto pueda leer el contenido del email. Utiliza una combinación de algoritmos de encriptación simétrica (por rapidez) y asimétrica (para intercambio de claves). Algoritmos comúnmente utilizados incluyen RSA (usado para encriptación asimétrica), AES o Estándar de Encriptación Avanzado (uno de los algoritmos simétricos), y Triple DES.
- Confirma la identidad del remitente.
- Verifica que el contenido del email no haya sido alterado durante la transmisión. Previene que el remitente niegue la autoría del email.
- Utiliza la clave privada del remitente para crear una firma y el cliente del destinatario utiliza la clave pública del remitente para verificarla.
- S/MIME se basa en una Infraestructura de Clave Pública (PKI) para la gestión y intercambio de claves. Certificados digitales, emitidos por Autoridades Certificadoras (CAs), ligan claves públicas a identidades individuales. Los certificados generalmente siguen el estándar X.509.

### DKIM

**DomainKeys Identified Mail (DKIM)** es un mecanismo de autenticación de email diseñado para detectar direcciones de remitente falsificadas, una técnica común utilizada en phishing y suplantación de correo electrónico. Permite a una organización asumir la responsabilidad de un email durante su tránsito al asociar un nombre de dominio con el mensaje, asegurando su autenticidad e integridad. DKIM verifica que un email que supuestamente proviene de un dominio específico fue efectivamente autorizado por el propietario del dominio, enfocándose principalmente en la autenticidad de la dirección de email "Desde". Esto se logra permitiendo que el remitente firme electrónicamente su email con una clave privada, mientras que el destinatario verifica esta firma utilizando una clave pública publicada en los registros DNS del remitente.

#### Características clave

- DKIM añade un encabezado "DKIM-Signature" al email que contiene la firma digital y varios parámetros clave. El cuerpo del email y encabezados selectos son hashados utilizando un algoritmo de hash como SHA-256. Este hash es luego encriptado utilizando la clave privada del remitente para generar la firma digital.
- El remitente publica la clave pública en sus registros DNS. El servidor de correo del destinatario busca la clave pública del remitente en DNS para verificar la firma digital.

### AMP Email

**Accelerated Mobile Pages (AMP)** para Email es un marco de trabajo de código abierto diseñado para crear experiencias de email dinámicas, interactivas y atractivas. Está diseñado para hacer que los emails sean más dinámicos y funcionales, transformando un medio que tradicionalmente ha sido estático y pasivo.

#### Características clave

- Permite a los usuarios realizar acciones directamente dentro del email, como responder a eventos, rellenar formularios o interactuar con carruseles de productos.
- Los emails pueden servir contenido dinámico que se actualiza en el momento de abrirse. Esto asegura que los usuarios vean la información más actual, ya sea el precio más reciente, el estado del stock o actualizaciones de noticias.
- Los emails AMP son soportados por varios clientes de email importantes, incluyendo Gmail, Yahoo Mail y Outlook.com. Cada cliente de email que soporta emails AMP mantiene su propio conjunto de requisitos y reglas de renderizado.
- Los emails AMP deben ser enviados en un formato MIME multiparte que contenga una versión de texto plano para accesibilidad básica, una versión HTML para contenido rico y visualmente atractivo, y una versión AMP para elementos dinámicos e interactivos, asegurando compatibilidad y una experiencia de usuario mejorada a través de varios clientes de email.
- Solo los remitentes verificados pueden enviar emails AMP, asegurando que los emails sean seguros y de confianza.

### AntiSpam

AntiSpam se refiere a una gama de técnicas, tecnologías y estrategias diseñadas para detectar, prevenir y mitigar mensajes de email no solicitados y a menudo dañinos, comúnmente conocidos como spam.

#### Técnicas AntiSpam

1. **Métodos de filtrado**
   - Filtrado basado en contenido: Analiza el contenido del email en busca de indicadores comunes de spam.
   - Listas negras: Listas de direcciones IP o dominios conocidos por spam que son bloqueados automáticamente.
   - Listas blancas: Listas de remitentes aprobados que siempre son permitidos.
   - Filtrado heurístico: Utiliza reglas y algoritmos para detectar spam basado en patrones.
   - Filtrado Bayesiano: Utiliza métodos estadísticos para identificar spam basado en datos históricos.
   - Greylisting: Rechaza temporalmente emails de remitentes desconocidos y los acepta si se envían nuevamente después de un retraso.
   - Aprendizaje automático: Utiliza modelos complejos entrenados en grandes conjuntos de datos para identificar spam.

2. **Métodos de autenticación**
   - SPF (Sender Policy Framework): Verifica que la dirección IP del remitente esté autorizada para enviar emails para el dominio.
   - DKIM (DomainKeys Identified Mail): Utiliza firmas digitales para verificar que el email no ha sido alterado durante el tránsito y que efectivamente proviene del dominio que indica ser.
   - DMARC (Domain-based Message Authentication, Reporting & Conformance): Se basa en SPF y DKIM para proporcionar un método estandarizado para que los remitentes de email indiquen que sus mensajes están protegidos y cómo los servidores receptores deben manejar los fallos de autenticación.

### Rebotes de Email

#### Tipos de Rebotes de Email

1. **Rebotes duros.** Fallos permanentes de entrega que indican que el email no puede ser entregado a la dirección del destinatario prevista.
   - Causas comunes:
     - Direcciones de email inválidas o no existentes.
     - El dominio del destinatario no existe.
     - Problemas permanentes en el servidor del destinatario.
     - Errores tipográficos o de formato en la dirección de email.

2. **Rebotes suaves.** Fallos de entrega temporales que indican que el email no pudo ser entregado en el momento, pero puede ser exitoso si se intenta de nuevo más tarde.
   - Causas comunes:
     - La bandeja de entrada del destinatario está llena.
     - Problemas temporales en el servidor del destinatario.
     - El servidor de email del destinatario está caído o fuera de línea.
     - Emails demasiado grandes para el sistema de email del destinatario.

Los servidores de email suelen devolver códigos de rebote que pueden ayudar a diagnosticar la razón de un rebote.

### Hilo de Emails

El hilo de emails es un método utilizado por clientes de email y aplicaciones para agrupar emails relacionados basados en su asunto o conversación, facilitando a los usuarios seguir y gestionar intercambios de email.

#### Características clave

- **Enlaces In-Reply-To y References.** Encabezados de email que apuntan a mensajes anteriores en el hilo, ayudando al cliente de email a vincular respuestas y reenvíos al email original.
- Líneas de asunto. A menudo se utilizan para agrupar emails en hilos. Los emails con la misma línea de asunto, típicamente prefijados con "Re:" (respuesta) o "Fwd:" (reenviar), se agrupan juntos.
- Los usuarios pueden expandir o colapsar hilos, enfocándose solo en las partes relevantes de una conversación.