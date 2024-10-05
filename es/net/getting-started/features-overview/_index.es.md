---
title: "features-overview"
url: /es/net/features-overview/
weight: 25
type: docs
---

En Aspose.Email para.NET, hay un conjunto diverso de clases y métodos 
clasificados en espacios de nombres, cada uno con fines distintos relacionados con el procesamiento del correo electrónico. Desde la gestión de protocolos de correo electrónico como SMTP, POP3 e IMAP hasta la gestión de tareas como la integración de calendarios y la programación de tareas, cada espacio de nombres se crea para abordar casos de uso específicos. Este enfoque estructurado no solo simplifica la codificación, sino que también garantiza que los desarrolladores puedan implementar soluciones de correo electrónico con facilidad.

A continuación, profundizaremos en los distintos espacios de nombres proporcionados por Aspose.Email para .NET, explorando sus funciones principales y haciendo referencia a las clases más importantes.

## Aspose.Email: contiene clases comunes para gestionar varios aspectos de los mensajes de correo electrónico

El componente central de este espacio de nombres es [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, una entidad versátil y poderosa que facilita la creación, manipulación y procesamiento de mensajes de correo electrónico. La clase MailMessage admite una amplia gama de funciones, como redactar correos electrónicos con formato de texto enriquecido, incrustar imágenes, adjuntar archivos y especificar varios destinatarios con diferentes funciones (to, cc, bcc). También proporciona funcionalidades sólidas para analizar y leer los mensajes de correo electrónico entrantes, lo que permite a los desarrolladores extraer detalles como el asunto, el remitente, los destinatarios y el contenido del cuerpo sin problemas. Además, MailMessage se integra sin problemas con varios protocolos de correo electrónico como SMTP, IMAP y POP3, lo que garantiza que el envío y la recepción de correos electrónicos sean sencillos y fiables.

## Aspose.Email.Amp: proporciona clases para gestionar mensajes con el cuerpo HTML de AMP

[Aspose.Email.Amp](https://reference.aspose.com/email/net/aspose.email.amp/) ofrece un conjunto sólido de clases dedicadas a gestionar mensajes que incluyen cuerpos HTML de AMP, lo que la convierte en una herramienta para los desarrolladores que buscan incorporar contenido de correo electrónico dinámico e interactivo. En el centro de esta capacidad se encuentra la [AmpMessage](https://reference.aspose.com/email/net/aspose.email.amp/ampmessage/#ampmessage-class) class, que sirve como componente principal para crear, manipular y representar mensajes de correo electrónico con AMP. Esta clase permite a los desarrolladores integrar sin problemas elementos multimedia enriquecidos e interactivos directamente en el cuerpo de un correo electrónico, aprovechando la velocidad y las atractivas funciones del HTML de AMP.

Con ampMessage, puede agregar elementos como carruseles de imágenes, obtención de datos en tiempo real y formularios interactivos, todos diseñados para funcionar de manera eficiente en un cliente de correo electrónico. 

## Aspose.Email.Antispam: ofrece clases para implementar filtros de autoaprendizaje para detectar correos electrónicos no deseados

[Aspose.Email.AntiSpam](https://reference.aspose.com/email/net/aspose.email.antispam/) ofrece una solución para el filtrado de correo electrónico con su clase principal [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) diseñado para detectar correos electrónicos no deseados mediante un filtro bayesiano de autoaprendizaje. Esta clase permite a las aplicaciones analizar y clasificar los correos electrónicos entrantes como spam o no, basándose en estadísticas bayesianas. El SpamAnalyzer puede aprender de las entradas de los usuarios, lo que le permite mejorar su precisión con el tiempo ajustando su modelo interno en función de los correos electrónicos previamente clasificados.

## Aspose.Email.Bounce: proporciona clases para gestionar los mensajes de rebote

[Aspose.Email.Bounce](https://reference.aspose.com/email/net/aspose.email.bounce/) ofrece una solución integral para que las aplicaciones de correo electrónico administren de manera eficiente los mensajes de rebote. La clase [BounceResult] (https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/#bounceresult-class) representa el resultado del examen del mensaje como un mensaje de rebote.

## Aspose.Email.Calendar: contiene clases para trabajar con calendarios

[Aspose.Email.Calendar](https://reference.aspose.com/email/net/aspose.email.calendar/) es un espacio de nombres diseñado para dotar a los desarrolladores de herramientas para administrar y manipular los datos del calendario. El [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) La clase encapsula la funcionalidad para gestionar eventos y citas del calendario. Con la clase Appointment, los desarrolladores pueden crear, modificar y gestionar fácilmente los eventos del calendario, lo que incluye establecer las horas de inicio y finalización, los patrones recurrentes, los recordatorios y la invitación a los asistentes. La clase admite el formato iCalendar (ICS), lo que garantiza la compatibilidad y la integración con diferentes sistemas de calendario. Además, la clase Appointment permite exportar archivos de calendario al formato MSG, lo que facilita el intercambio y la sincronización de datos sin problemas en diversas plataformas.

## Aspose.Email.Clients.DeliveryService.Mailgun: Implementa el cliente para el servicio de entrega de correo electrónico Mailgun

The [Aspose.Email.Clients.DeliveryService.Mailgun](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.mailgun/) namespace proporciona una implementación de cliente personalizada para el servicio de entrega de correo electrónico de Mailgun, lo que facilita una integración perfecta para los desarrolladores que buscan capacidades de envío de correo electrónico confiables y eficientes. En el centro de este espacio de nombres se encuentra la clase fundamental, [MailgunClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.mailgun/mailgunclient/#mailgunclient-class), que sirve como componente principal para interactuar con la API de Mailgun.

## Aspose.Email.Clients.DeliveryService.SendGrid: implementa el cliente para el servicio de entrega de correo electrónico SendGrid

Dentro del [Aspose.Email.Clients.DeliveryService.SendGrid](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/) namespace es una implementación diseñada específicamente para el servicio de entrega de correo electrónico SendGrid, que ofrece a los desarrolladores una integración perfecta para un envío de correo electrónico eficiente. En el centro de este espacio de nombres se encuentra la clase fundamental, [SendGridClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/#sendgridclient-class), que sirve como componente principal para interactuar con la API de SendGrid.

## Aspose.Email.Clients.Exchange.Dav: proporciona clases para acceder a Exchange Server mediante el protocolo WebDAV Exchange Store

[Aspose.Email.Clients.Exchange.Dav](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/) namespace tiene herramientas para interactuar con Exchange Server a través del protocolo WebDAV Exchange Store. El [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/) servicio de clases para acceder a los recursos de Exchange Server.

## Aspose.Email.Clients.Exchange.WebService: proporciona acceso a MS Exchange Server mediante Exchange Web Services (EWS)

[Aspose.Email.Clients.Exchange.WebService](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/) está diseñado para proporcionar acceso a Microsoft Exchange Server mediante Exchange Web Services (EWS). Su clase principal, [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), facilita las interacciones con el servidor Exchange. EWSClient permite a los desarrolladores conectarse al servidor de manera eficiente y realizar diversas operaciones, incluida la administración de correos electrónicos, calendarios, contactos, tareas y carpetas públicas. Esta clase admite funcionalidades como el envío y la recepción de correos electrónicos, la organización de las carpetas de buzones, la programación de citas y la gestión de las convocatorias de reunión.

## Aspose.Email.Clients.Google: proporciona clases para acceder a las cuentas de Google

[Aspose.Email.Clients.Google](https://reference.aspose.com/email/net/aspose.email.clients.google/) es un espacio de nombres que ofrece clases para acceder a las cuentas de Google y administrarlas con facilidad. La clase de componente central de este espacio de nombres es la [GmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/gmailclient/). Esta clase permite a los desarrolladores integrar e interactuar con los servicios de Google Mail, aprovechando la autenticación OAuth 2.0.

## Aspose.Email.Clients.Graph: proporciona clases para acceder a los servicios de Microsoft 365 mediante la API REST

The [Aspose.Email.Clients.Graph](https://reference.aspose.com/email/net/aspose.email.clients.graph/) está diseñado para acceder y administrar los servicios de Microsoft 365 a través de la API REST, y ofrece un enfoque para integrar las funcionalidades del correo electrónico en las aplicaciones.NET. En el centro de este espacio de nombres se encuentra [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/) clase, que permite a los desarrolladores interactuar sin problemas con los servicios de Microsoft 365. El GraphClient permite una amplia gama de operaciones, que incluyen el envío y la recepción de correos electrónicos, la gestión de los eventos del calendario y la gestión de los contactos. Al ser compatible con la autenticación OAuth 2.0, garantiza un acceso seguro a los datos de los usuarios, manteniendo el cumplimiento de los estándares de seguridad modernos. Además, el GraphClient facilita la manipulación de carpetas, la sincronización de los buzones y la recuperación de los metadatos del correo electrónico.

## Aspose.Email.Clients.Imap: proporciona clases para acceder y manipular mensajes mediante IMAP

The [Aspose.Email.Clients.Imap](https://reference.aspose.com/email/net/aspose.email.clients.imap/) El espacio de nombres está diseñado para interactuar con los servidores de correo electrónico que utilizan el Protocolo de acceso a mensajes de Internet (IMAP). Un elemento central de este espacio de nombres es la [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class, que sirve como interfaz principal para realizar una amplia gama de operaciones de correo electrónico. Una vez conectados, los desarrolladores pueden usar el ImapClient para listar, buscar, eliminar y buscar correos electrónicos en varias carpetas de correo. Además, ofrece capacidades para administrar y manipular estas carpetas, incluida la creación, el cambio de nombre y la eliminación de las mismas.

## Aspose.Email.Clients.Pop3: proporciona clases para acceder y manipular mensajes mediante POP3

The [Aspose.Email.Clients.Pop3](https://reference.aspose.com/email/net/aspose.email.clients.pop3/) namespace está diseñado para agilizar la interacción con los servidores de correo electrónico que utilizan el Protocolo de Oficina Postal versión 3 (POP3), que ofrece un conjunto de clases para acceder a los mensajes de correo electrónico y manipularlos. En el centro de este espacio de nombres se encuentra [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) clase. La clase Pop3Client facilita el establecimiento de conexiones seguras con los servidores POP3 y admite una variedad de mecanismos de autenticación para garantizar un acceso seguro y fiable. Una vez conectado, el Pop3Client permite a los desarrolladores realizar operaciones de correo electrónico esenciales, como recuperar los mensajes del servidor, enumerar los correos electrónicos, marcar mensajes específicos para eliminarlos y obtener todos los detalles de los mensajes, incluidos los encabezados y los archivos adjuntos. Además, proporciona soporte integrado para los protocolos SSL y TLS.

## Aspose.Email.Clients.Smtp: proporciona clases para enviar mensajes mediante SMTP

The [Aspose.Email.Clients.Smtp](https://reference.aspose.com/email/net/aspose.email.clients.smtp/) namespace está diseñado para desarrolladores que buscan integrar la funcionalidad SMTP (Protocolo simple de transferencia de correo) en sus aplicaciones.NET para enviar mensajes de correo electrónico. En el centro de este espacio de nombres se encuentra el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) clase. La clase SmtpClient ofrece un conjunto de capacidades que permiten a los desarrolladores establecer conexiones seguras a los servidores SMTP y enviar correos electrónicos. Admite varios métodos de autenticación, lo que garantiza la compatibilidad con una amplia gama de servidores SMTP y ofrece opciones para especificar la prioridad de los mensajes, las notificaciones de entrega y los encabezados personalizados. Gracias a la compatibilidad integrada con los protocolos de cifrado SSL y TLS, la clase SMTPClient garantiza una comunicación segura.

## Aspose.email.dkim: contiene clases para trabajar con firmas DKIM

The [Aspose.Email.DKIM](https://reference.aspose.com/email/net/aspose.email.dkim/) namespace ofrece clases para gestionar las firmas de DomainKeys Identified Mail (DKIM), a fin de garantizar la integridad y la autenticidad del correo electrónico. El [DKIMSignatureInfo](https://reference.aspose.com/email/net/aspose.email.dkim/dkimsignatureinfo/) La clase sirve como el componente principal para proporcionar información relacionada con DKIM.

## Aspose.Email.Mapi: contiene clases que representan mensajes, contactos y citas de Outlook y funcionan con el formato de archivo PST/OST de Microsoft Outlook

The [Aspose.Email.Mapi](https://reference.aspose.com/email/net/aspose.email.mapi/) el espacio de nombres está diseñado para trabajar con datos de Microsoft Outlook. La clase de componentes principal de este espacio de nombres es [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), que sirve para gestionar los mensajes de Outlook. MapiMessage proporciona funciones para crear, leer, modificar y guardar mensajes de Outlook en formato MSG. Los desarrolladores pueden usar esta clase para acceder y manipular el contenido de los elementos de Outlook, incluidos el asunto, el cuerpo, los archivos adjuntos, los destinatarios y las propiedades.

Además de administrar correos electrónicos individuales, el espacio de nombres Aspose.Email.Mapi también incluye:

- clases para el manejo de contactos ([MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/)),
- citas ([MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/)),
- y otros elementos de Outlook, lo que permite interactuar mediante programación con varios elementos que normalmente se encuentran en archivos PST (tabla de almacenamiento personal) y OST (tabla de almacenamiento sin conexión). Este conjunto de clases permite la integración con los formatos de almacenamiento de datos de Outlook, lo que facilita tareas como la migración, la copia de seguridad y la sincronización del correo electrónico.

## Aspose.Email.PersonalInfo.vCard: contiene clases para trabajar con el formato de archivo vCard

The [Aspose.Email.PersonalInfo.VCard](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/) el espacio de nombres es esencial para los desarrolladores que buscan manipular los formatos de archivo vCard en sus aplicaciones. La clase principal de este espacio de nombres es [VCardContact](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/). Esta clase es fundamental para crear, analizar y administrar archivos vCard, que se utilizan ampliamente para intercambiar información de contacto. Con vCardContact, los desarrolladores pueden leer los archivos vCard para extraer la información de contacto o generar archivos vCard a partir de los datos existentes. Esta clase admite varias versiones de vCard para garantizar la compatibilidad y la flexibilidad a la hora de gestionar diferentes formatos de vCard. Además, incluye capacidades para codificar y decodificar la información de contacto, lo que permite la integración con otros sistemas y plataformas que utilizan los estándares vCard.

## Aspose.Email.Printing: contiene clases que representan la funcionalidad de impresión de mensajes

The [Aspose.Email.Printing](https://reference.aspose.com/email/net/aspose.email.printing/) el espacio de nombres está diseñado para proporcionar las herramientas necesarias para imprimir mensajes de correo electrónico directamente desde las aplicaciones. Una impresora para mensajes de correo está representada por la [MailPrinter](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/) clase. Esta clase ofrece un conjunto de funcionalidades para facilitar la impresión de varios formatos de mensajes, incluidos MSG, EML y MHTML. La MailPrinter permite personalizar el diseño de impresión y adaptar la configuración de la página para garantizar que los correos electrónicos renderizados cumplan con los requisitos específicos.

## Aspose.Email.Storage.Mbox: proporciona clases para trabajar con el formato MBOX

The [Aspose.Email.Storage.Mbox](https://reference.aspose.com/email/net/aspose.email.storage.mbox/) namespace ofrece un conjunto de clases diseñadas para administrar y manipular los formatos de archivo MBOX, que se utilizan ampliamente para almacenar colecciones de mensajes de correo electrónico. Las clases centrales de este espacio de nombres son [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/) clase y [MboxStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragewriter/), que sirven como componentes principales para interactuar con los archivos MBOX.
La clase mboxRDStorageReader proporciona la capacidad de leer y recorrer archivos MBOX. Permite a los desarrolladores extraer mensajes de correo electrónico individuales, lo que les permite procesar o analizar el contenido del correo electrónico mediante programación. Además, esta clase permite la conversión perfecta de los mensajes extraídos a otros formatos de correo electrónico populares, como EML o MSG, lo que amplía su utilidad en diversos escenarios de aplicación.
La clase mboxRDStorageWriter está diseñada para crear y escribir archivos MBOX.

## Aspose.Email.Storage.Olm: proporciona clases para trabajar con el formato de archivo OLM de Microsoft Outlook

The [Aspose.Email.Storage.Olm](https://reference.aspose.com/email/net/aspose.email.storage.olm/) el espacio de nombres es un conjunto de clases diseñadas para administrar y manipular Microsoft Outlook. Formatos de archivo OLM, que se utilizan principalmente para almacenar datos de correo electrónico en macOS. Aquí el [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) La clase es el componente principal responsable de interactuar con los archivos OLM. La clase OLMStorage permite a los desarrolladores cargar archivos OLM y, a continuación, extraer, leer y manipular su contenido, incluidos los correos electrónicos, los contactos, los elementos del calendario y las notas. En particular, permite navegar por las jerarquías de carpetas, filtrar tipos de mensajes específicos y extraer datos de manera eficiente.

## Aspose.Email.Storage.Pst: proporciona clases para trabajar con el formato de archivo PST/OST de Microsoft Outlook

The [Aspose.Email.Storage.Pst](https://reference.aspose.com/email/net/aspose.email.storage.pst/) namespace ofrece clases diseñadas para manejar los formatos de archivo PST y OST de Microsoft Outlook, que son esenciales para administrar los datos de correo electrónico en Windows. Un elemento central de este espacio de nombres es la [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class, el componente principal responsable de interactuar con los archivos PST y OST. La clase PersonalStorage proporciona funciones para cargar, crear y manipular estos tipos de archivos. Permite a los desarrolladores realizar una amplia gama de operaciones, incluida la extracción y administración de correos electrónicos, contactos, entradas de calendario, tareas y notas. La clase también admite la navegación jerárquica por carpetas, lo que permite una organización y recuperación de datos eficientes. Además, la clase PersonalStorage facilita la conversión de contenido PST y OST a varios otros formatos, como EML, MSG o MBOX, lo que amplía su utilidad.

## Aspose.Email.Storage.Zimbra: proporciona clases para trabajar con el almacenamiento de Zimbra

[Aspose.Email.Storage.Zimbra](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/) es un espacio de nombres dentro de la biblioteca Aspose.Email con el [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) clase que sirve para acceder y administrar archivos Zimbra TGZ (Tar GZip). La clase TGZReader ofrece capacidades para trabajar con archivos de correo electrónico, incluida la capacidad de analizar y extraer correos electrónicos, contactos y elementos del calendario de los archivos TGZ, en particular, la lectura de archivos TGZ, la iteración de su contenido y el acceso mediante programación a elementos individuales para su procesamiento personalizado.

## Aspose.Email.Tools.Logging: proporciona clases para la funcionalidad de registro

The [Aspose.Email.Tools.Logging](https://reference.aspose.com/email/net/aspose.email.tools.logging/) es un espacio de nombres para incorporar la funcionalidad de registro en las aplicaciones basadas en correo electrónico. La clase de componentes principal de este espacio de nombres es la [LoggerManager](https://reference.aspose.com/email/net/aspose.email.tools.logging/loggermanager/#loggermanager-class) clase, que está diseñada para ofrecer capacidades de registro, lo que permite a las aplicaciones rastrear y registrar varios eventos operativos.

## Aspose.Email.Tools.Merging: contiene clases para crear mensajes de correo electrónico mediante plantillas

The [Aspose.Email.Tools.Merging](https://reference.aspose.com/email/net/aspose.email.tools.merging/) es un espacio de nombres para automatizar la creación de mensajes de correo electrónico personalizados mediante plantillas. En el corazón de este espacio de nombres se encuentra el [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) class, que es la clase principal responsable de crear mensajes de correo electrónico mediante plantillas. La clase TemplateEngine permite combinar datos en plantillas predefinidas, lo que permite sustituir los marcadores de posición por información real. Esto es particularmente útil para generar correos electrónicos personalizados de forma masiva, garantizando que cada destinatario reciba un mensaje único adaptado a su contexto específico.

## Aspose.Email.Tools.Search: contiene clases base para la búsqueda de mensajes por criterios

The [Aspose.Email.Tools.Search](https://reference.aspose.com/email/net/aspose.email.tools.search/) el espacio de nombres está diseñado para agilizar el proceso de localización de los mensajes de correo electrónico en función de una amplia gama de criterios. La piedra angular de este espacio de nombres es la [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class, que sirve como el componente principal responsable de definir los parámetros de búsqueda y ejecutar consultas en los almacenes de correo electrónico. Con MailQuery, puedes especificar varias condiciones de búsqueda, como el remitente, el destinatario, las palabras clave del asunto, los intervalos de fechas e incluso los términos específicos del contenido. Esta capacidad permite filtrar y recuperar los mensajes de correo electrónico relevantes de archivos extensos o buzones de correo actuales. MailQuery admite la construcción de consultas complejas mediante operadores lógicos.

## Aspose.Email.Tools.Verifications: proporciona clases para la funcionalidad de validación de mensajes

The [Aspose.Email.Tools.Verifications](https://reference.aspose.com/email/net/aspose.email.tools.verifications/) namespace ofrece clases que son esenciales para garantizar la integridad y la validez de los mensajes de correo electrónico. En el centro de este espacio de nombres se encuentra el [EmailValidator](https://reference.aspose.com/email/net/aspose.email.tools.verifications/emailvalidator/#emailvalidator-class) class, que sirve como componente principal para implementar varias comprobaciones de validación en los correos electrónicos.

## Aspose.Email.Windows.Forms: contiene clases para gestionar archivos arrastrados desde Outlook en aplicaciones de Windows Forms

[Aspose.Email.Windows.Forms](https://reference.aspose.com/email/net/aspose.email.windows.forms/) es un espacio de nombres especializado diseñado para facilitar la integración de las funcionalidades relacionadas con el correo electrónico en las aplicaciones de Windows Forms, centrándose especialmente en la gestión de archivos arrastrados desde Microsoft Outlook. La clase de componentes principal de este espacio de nombres, [FileDropTargetManager](FileDropTargetManager), proporciona a los desarrolladores la capacidad de administrar y procesar las operaciones de arrastrar y soltar relacionadas con los elementos de Outlook. FileDropTargetManager permite a las aplicaciones capturar, gestionar y procesar mensajes de correo electrónico, archivos adjuntos y otros elementos de Outlook cuando se arrastran a una aplicación de Windows Forms. Con esta clase, puede implementar funciones como extraer y mostrar el contenido de los elementos arrastrados, guardar los archivos adjuntos en ubicaciones específicas o activar acciones personalizadas en función del tipo de elemento eliminado.

## Aspose.Email.Windows.WPF: contiene clases para gestionar archivos arrastrados desde Outlook en aplicaciones de Windows Presentation Foundation (WPF)

The [Aspose.Email.Windows.WPF](https://reference.aspose.com/email/net/aspose.email.windows.wpf/) El espacio de nombres está diseñado para permitir la integración de funcionalidades relacionadas con el correo electrónico en las aplicaciones de WPF, centrándose especialmente en la gestión de archivos arrastrados desde Microsoft Outlook. La piedra angular de este espacio de nombres es [FileDropPanel](https://reference.aspose.com/email/net/aspose.email.windows.wpf/filedroppanel/) clase, que permite a los desarrolladores implementar operaciones de arrastrar y soltar. El FileDropPanel actúa como un panel especializado que captura los elementos arrastrados desde Outlook, incluidos los correos electrónicos, los archivos adjuntos y otros elementos relacionados. Detecta automáticamente cuándo se colocan elementos en el panel y proporciona eventos y métodos para procesar estos elementos en consecuencia. Al utilizar FileDropPanel, los desarrolladores pueden extraer el contenido del correo electrónico, guardar los archivos adjuntos en ubicaciones específicas o ejecutar una lógica empresarial personalizada en función del tipo de elemento recibido.