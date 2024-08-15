---
title: "Novedades de Aspose.Email para.NET"
url: /es/net/whats-new/
weight: 5
type: docs
---


## [Aspose.Email para.NET 24.3](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-3-release-notes/)

- **Soporte para contactos y calendario en MS Graph** - Los métodos de la interfaz de iGraphClient le permiten acceder, administrar e interactuar con los contactos y eventos del calendario de los usuarios:
  - Recupera una colección de contactos de MAPI.
  - Recupera un contacto específico.
  - Crea un contacto nuevo.
  - Actualiza un contacto existente.
  - Recupera una colección de información del calendario.
  - Recupera una colección de elementos del calendario.
  - Recupera un elemento de calendario específico.
  - Crea un nuevo elemento de calendario.
  - Actualiza un elemento de calendario existente.

## [Aspose.Email para.NET 24.2](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-2-release-notes/)

- **Manipular las categorías de elementos de Outlook** - Aspose.Email permite recuperar y utilizar los colores de categoría asociados a las categorías de elementos de Outlook almacenadas en archivos OLM.

- **Coincidencia de clases de contenedores** - un nuevo [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) la propiedad se agregó al [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) clase que, al añadir una carpeta a un archivo PST, le permite asegurarse de que la clase de la carpeta coincide con el tipo o la categoría de carpetas esperados dentro del archivo PST.

## [Aspose.Email para.NET 23.12](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-12-release-notes/)

- **Establecer la ruta relativa a los recursos al guardar un mensaje de correo electrónico como HTML** - Aspose.Email introduce la posibilidad de guardar recursos de correo electrónico con rutas relativas al exportar mensajes a formato HTML, lo que ofrece una mayor flexibilidad para vincular recursos. Los usuarios pueden elegir entre rutas absolutas y relativas y definir rutas personalizadas mediante el [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/resourcehtmlrendering/#htmlsaveoptionsresourcehtmlrendering-event) evento, simplificando el intercambio y la visualización de correos electrónicos en diferentes sistemas.

## [Aspose.Email para.NET 23.11](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-11-release-notes/)

- **Validar mensajes de correo electrónico** - Se agregó un conjunto de componentes para permitir a los usuarios validar los archivos de mensajes, que admiten formatos como eml, emlx, mht, msg y oft. Al utilizar esta funcionalidad, los usuarios pueden validar los mensajes y obtener información sobre el proceso de validación, incluidos el tipo de formato y los errores encontrados.

- **Adjunte firmas digitales a los mensajes de correo electrónico** - El *AttachSignature* método en el [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) La clase fue diseñada para agregar fácilmente una firma digital a un correo electrónico.

Una vez que se adjunta la firma, los usuarios pueden verificar los resultados mediante propiedades como «isSigned», «MessageClass» y los detalles del archivo adjunto.

Para personalizar el proceso de adjuntar firmas, los usuarios pueden utilizar el [SignatureOptions](https://reference.aspose.com/email/net/aspose.email/signatureoptions/#signatureoptions-class) class.

## [Aspose.Email para.NET 23.10](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-10-release-notes/)

- **Divida el almacenamiento de Mbox en partes más pequeñas** - divida archivos grandes en partes manejables e implemente acciones personalizadas durante el proceso:

  - Especifique un prefijo personalizado para los nombres de los archivos de Mbox divididos.
  - Personalice las acciones antes y después de copiar un correo electrónico en un nuevo archivo Mbox.
  - Reacciona cuando se crea un nuevo archivo Mbox.
  - Responda cuando un nuevo archivo Mbox esté lleno de correos electrónicos.

- **Obtenga contenido alternativo Ver por tipo de medio** - recuperar el contenido como una cadena de un AlternateView específico dentro de un mensaje de correo electrónico. - El  [MailMessage.getAlternateViewContent (cadena MediaType)](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/#mailmessagegetalternateviewcontent-method) El método le permite acceder al contenido desde un AlternateView que coincida con el tipo de medio especificado.

## [Aspose.Email para.NET 23.8](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-8-release-notes/)

- **Enviar correos electrónicos a través de Graph Client** - se agregó el soporte para métodos sobrecargados a la clase GraphClient que aceptan un objeto MailMessage para enviar correos electrónicos:
  - [CreateMessage (string folderId, mailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage)

  - void [Enviar (mensaje de correo electrónico)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send)

- **Guarde la lista de distribución de Mapi en un único archivo VCF de múltiples contactos** - Guarde la lista de distribución de Mapi en un nombre de archivo específico mediante las opciones de almacenamiento proporcionadas. Puede proporcionar el nombre del archivo y una instancia de la clase MapiDistributionListSaveOptions como parámetros.
  - void [Guardar (cadena FileName, opciones MapiDistributionListSaveOptions)](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_5) se ha agregado un método para este propósito.

## [Aspose.Email para.NET 23.7](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-7-release-notes/)

- **Eliminar elementos de PST** - Hemos añadido un nuevo método, [deleteItem (identificador de entrada de cadena)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/deleteitem/), a la clase PersonalStorage. Este método permite eliminar elementos (carpetas o mensajes) de una tabla de almacenamiento personal (PST) mediante el identificador de entrada único asociado al elemento.
- **Gestión de eventos y división de PST** - Funcionalidad mejorada en [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class:
  - [StorageProcessingEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventhandler/) el evento se produce antes de que se procese el almacenamiento, específicamente antes de procesar el almacenamiento actual en los métodos MergeWith o SplitInto. Este evento brinda la oportunidad de ejecutar una lógica personalizada o gestionar determinadas operaciones antes de que se produzca el procesamiento del almacenamiento.

  - [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventargs/) la clase proporciona datos para el evento PersonalStorage.storageProcessing.

  - [SplitInto (tamaño de fragmento largo, prefijo de nombre de archivo de sección de cadena, ruta de cadena)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto_1) El método de sobrecarga permite dividir el almacenamiento PST en partes de menor tamaño.
- **Manejo de calendarios** - Se agregaron nuevas propiedades y un método a la clase CalendarReader:
  - [Count](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/count/) Esta propiedad le permite recuperar el número de componentes (eventos) de Vevent presentes en el calendario, lo que facilita el seguimiento del número total de eventos.
  - [IsMultiEvents](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/ismultievents/) La propiedad determina si el calendario contiene varios eventos.
  - [Method](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/method/) la propiedad obtiene el tipo de método iCalendar asociado al objeto de calendario. Devuelve el tipo de método, como «REQUEST», «PUBLISH» o «CANCEL», lo que proporciona información valiosa sobre el propósito del calendario.
  - [Version](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/version/) obtiene la versión de iCalendar.
  - [LoadAsMultiple()](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/loadasmultiple/) El método permite cargar una lista de eventos de un calendario que contiene varios eventos. Devuelve una lista de objetos de cita, lo que permite un fácil acceso y procesamiento de cada evento de forma individual.

## [Aspose.Email para.NET 23.6](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-6-release-notes/)

- **Conservar o eliminar la firma en la conversión de MBOX a PST** - configurar el [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/#mboxtopstconversionoptionsremovesignature-property) propiedad en «true» para eliminar la firma.
- **Eliminar la firma al cargar archivos EML** - configurar el [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/) propiedad en «true» para eliminar la firma.
- **Verificación de firma de correo electrónico**
  - Se ha añadido un nuevo [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/) clase para comprobar la firma de correos electrónicos seguros. Ahora puede comprobar la firma de los objetos MAPIMessage y MailMessage.
  - Se ha añadido un nuevo [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/) clase para almacenar los resultados de la comprobación de correos electrónicos seguros.

  Métodos introducidos del SecureEmailManager:

  - [CheckSignature (mensaje de MAPIMessage)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3)
  - [Verificar la firma (mensaje de MapiMessage, certificado X509 Certificate 2 para descifrar)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4)
  - [Check Signature (mensaje de MapiMessage, certificado X509 Certificate 2 para desencriptar, X509 Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)
  - [CheckSignature (mensaje de correo electrónico)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature)
  - [Verificar la firma (mensaje de mensaje de correo, certificado X509 2 para descifrar)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1)
  - [Check Signature (mensaje de mensaje de correo, certificado X509 Certificate 2 para descifrar, X509 Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)

## [Aspose.Email para.NET 23.5](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-5-release-notes/)

- **Determine la versión de los archivos ICS/VCS** - Usa el [Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/) propiedad del [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) clase para recuperar la versión de los archivos ICS/VCS.
- **Personalice las opciones de almacenamiento de los archivos vCard** - Hemos añadido el nuevo [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/) clase a nuestra API con las siguientes propiedades:
  - [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) permite a los usuarios especificar la versión de vCard deseada al guardar los elementos de contacto. De forma predeterminada, la clase está configurada para usar la versión 2.1 de vCard (vCardVersion.v21).
  - [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/) - permite a los usuarios controlar si se pueden usar campos extendidos al guardar archivos vCard. Si se establece en verdadero (valor predeterminado), se permiten las extensiones, lo que proporciona compatibilidad con campos personalizados e información de contacto adicional.
  - [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) - la codificación que se utilizará al guardar los elementos de contacto de la vCard.
- **Obtenga el número total de elementos de mensajes contenidos en el almacenamiento de Zimbra** con el [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/) método del [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/) class.
- **Recuperar una subcarpeta PST por ruta** - Recupere una subcarpeta con el nombre especificado de la carpeta PST actual mediante el [FolderInfo.getSubfolder (nombre de cadena, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) sobrecarga de métodos.

## [Aspose.Email para.NET 23.4](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-4-release-notes/)

- **Agregar un adjunto de referencia a un mensaje** - Hemos añadido un nuevo [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) método para el [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) clase con los siguientes parámetros:
  - `name` - el nombre del adjunto
  - `sharedLink` - un enlace compartido totalmente cualificado al archivo adjunto proporcionado por el servicio web que manipula el archivo adjunto
  - `url` - una ubicación de archivo
  - `providerName` - el nombre del proveedor de archivos adjuntos de referencia
- **Comprobación de varios contactos de vCard** - Compruebe si un archivo fuente contiene varios contactos con el nuevo [vCardContact.isMultiContacts (ruta de archivo de cadena)](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/ismulticontacts/#ismulticontacts_1) method.
- **Convierta el formato ICS de calendario a formatos de mensajes** - Convierte citas en objetos de mensajes como MapiMessage y MailMessage. 
- **Opciones adicionales para guardar mensajes en formatos HTML y MHTML**:
  - [MapiTask.Priority](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/priority/) - Obtiene o establece la prioridad actual del objeto de tarea.
  - [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Define si es necesario guardar todos los encabezados en la salida mhtml o no.
  - [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/) - Indica que los campos de tareas específicos deben escribirse en el HTML de salida.
- **Establecer el tiempo de espera para el proceso de conversión y carga de mensajes** - Limite el tiempo en milisegundos al convertir y cargar los mensajes, asegurándose de que el proceso no demore más de lo necesario. Para ello, se han introducido las siguientes funciones:
  - [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/) - Limita el tiempo en milisegundos durante la conversión de un mensaje.
  - [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Se aumenta si se acaba el tiempo durante la conversión a MailMessage.
  - [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limita el tiempo en milisegundos durante la conversión de un mensaje.
  - [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Se aumenta si se acaba el tiempo durante la conversión a MailMessage.

## [Aspose.Email para.NET 23.3](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-3-release-notes/)

- **Obtenga el número total de elementos de mensaje contenidos en el almacenamiento de OLM** con el [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) método para [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class.
- **Determine si MapiMessage es OFT o MSG** - Determine si el mapiMessage se cargó desde un archivo OFT o MSG con el nuevo [MapiMessage.IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) property.
- **Detectar un formato de archivo NSF**

## [Aspose.Email para.NET 23.1](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-1-release-notes/)

-**Recuperar las propiedades de los mensajes de mboxMessageInfo** - Obtenga acceso a la información sobre los mensajes individuales almacenados en un archivo mbox, como el tamaño de los mensajes, el índice de los mensajes, los encabezados de los mensajes, las marcas de los mensajes y otros metadatos relacionados con los mensajes. Hemos añadido las siguientes propiedades a [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class:

DateTime Date: obtiene la fecha del mensaje
Dirección de correo de origen: obtiene la dirección del remitente
string (asunto): obtiene el asunto del mensaje
MailAddressCollection To: obtiene la colección de direcciones que contiene los destinatarios del mensaje
MailAddressCollection CC: obtiene la colección de direcciones que contiene los destinatarios del CC
MailAddressCollection Bcc: obtiene la colección de direcciones que contiene los destinatarios BCC del mensaje

## [Aspose.Email para.NET 22.12](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-12-release-notes/)

- **Obtenga el número total de elementos de mensaje contenidos en el PST** - Hemos añadido el [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) método para [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/) property.
- **Obtenga una carpeta de fuentes RSS estándar en Personal Storage**, **Agregar una carpeta de fuentes RSS estándar en PST** - Se ha agregado un nuevo valor de RSSFeeds a la enumeración StandardIPMFolder. Ahora, la carpeta de fuentes RSS se puede recuperar o agregar fácilmente al almacenamiento.
- **Descifrar un mensaje de correo electrónico almacenado en formato MAPI** - Hemos añadido un método Decrypt a la clase MAPIMessage:
  - [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/) - Obtiene un valor que indica si el mensaje está cifrado.
  - [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Descifra este mensaje (el método busca en el usuario y la computadora actuales de My stores el certificado y la clave privada apropiados).
  - [MapiMessage.decrypt (certificado X509 Certificate2)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Descifra este mensaje con un certificado.
- **Configuración de un identificador de producto al guardar MapiCalendar en ICS** - Hemos añadido [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) propiedad a [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) class.
- **Extraer mensajes por identificadores de OLM y MBOX** - Esta es la forma eficiente de evitar recorrer todo el almacenamiento cada vez para encontrar un mensaje específico para extraerlo.
- **Determine si el archivo adjunto está en línea o es normal** con el [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) property.

## [Aspose.Email para.NET 22.11](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-11-release-notes/)

- **Obtenga un tipo de elemento MAPI** - Evite comprobar el valor de la propiedad MessageClass cada vez antes de la conversión del mensaje.
- **Eliminar la firma de MapiMessage** - Para una mejor compatibilidad, el [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) método y [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) se agregaron propiedades.
- **Identificación de carpetas predefinidas** - El nuevo [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) method, [GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/), se introdujo para determinar si una carpeta está dentro de una carpeta predefinida devolviendo el valor de enumeración StandardIPMFolder en función del valor del parámetro especificado.
- **Verificación del formato TNEF del adjunto** - El [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/) La propiedad indica si el adjunto del mensaje es un mensaje con formato TNEF.

## [Aspose.Email para.NET 22.10](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-10-release-notes/)

- **Cambiar el nombre de un archivo adjunto en MapiMessage** - Ahora es posible editar el [DisplayName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/displayname/) valor de propiedad en los archivos adjuntos de MapiMessage.

## [Aspose.Email para.NET 22.9](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-9-release-notes/)

- **Listar mensajes con Graph API** - El nuevo [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) El método le permite controlar el orden de los mensajes recuperados según los criterios que especifique.

## [Aspose.Email para.NET 22.8](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-8-release-notes/)

- **Lectura de mensajes de MBOX** - Hemos introducido nuevas funciones para configurar las opciones de carga:
  - [MailStorageConverter.MboxMessageOptions](https://reference.aspose.com/email/net/aspose.email.storage/mailstorageconverter/mboxmessageoptions/) propiedad: obtiene o establece las opciones de carga de correo electrónico al analizar un almacenamiento de Mbox.
  - [mboxRDStorageReader.readNextMessage (opciones de EmllOdOptions)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage_1) método. El parámetro EmllOdOptions especifica las opciones al leer un mensaje del almacenamiento de Mbox.

## [Aspose.Email para.NET 22.7](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-7-release-notes/)

- **Obtener información de identificación de mensajes** como el UID o el número de secuencia mediante las siguientes funciones:
  - [MailboxInfo](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/#mailboxinfo-class) class: representa la información de identificación de un mensaje en un buzón.
  - [SequenceNumber](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/sequencenumber/) propiedad: el número de secuencia de un mensaje.
  - [UniqueId](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/uniqueid/) propiedad: el identificador único de un mensaje.
  - [MailMessage.ItemId](https://reference.aspose.com/email/net/aspose.email/mailmessage/itemid/) propiedad: representa la información de identificación de un mensaje en un buzón.

## [Aspose.Email para.NET 22.6](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-6-release-notes/)

- **Preservación de la marca de tiempo original en los archivos ICS** - Extraiga los elementos del calendario de los archivos PST y guárdelos en formato ICS con la marca de tiempo original mediante las siguientes opciones:
  - [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Permite especificar opciones adicionales al guardar MapiCalendar en formato ICS.
  - [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Permite mantener el valor original de DateTimeStamp en el archivo de salida.

## [Aspose.Email para.NET 22.5](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-5-release-notes/)

- **Enumerar mensajes con soporte de paginación mediante Graph Client** - La API proporciona soporte de paginación y filtrado para los mensajes de listado. Esto resulta muy útil cuando el buzón contiene un gran número de mensajes y se necesita mucho tiempo para recuperar la información resumida sobre los mismos.
- **Modo asincrónico en la gestión de clientes de correo** - Un nuevo enfoque de la tarea incluye los siguientes miembros de la API:
  - [`IAsyncSmtpClient`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/) - Permite que las aplicaciones envíen mensajes mediante el Protocolo simple de transferencia de correo (SMTP).
  - [`SmtpClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/#smtpclientcreateasync-method) - Crea una nueva instancia del `Aspose.Email.Clients.Smtp.SmtpClient` class.
  - [`IAsyncSmtpClient.SendAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpSend`) conjunto de parámetros del método.
  - [`IAsyncSmtpClient.ForwardAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpForward`) argumentos.
  - [`IAsyncImapClient`](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Permite a las aplicaciones acceder a los mensajes y manipularlos mediante el Protocolo de acceso a mensajes de Internet (IMAP).
  - [`ImapClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Crea una nueva instancia del `Aspose.Email.Clients.Imap.ImapClient` class.

## [Aspose.Email para.NET 22.4](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-4-release-notes/)

- **Envía correos electrónicos con los servicios de entrega de MailGun y SendGrid** - Hemos creado una API unificada que puedes usar para inicializar las opciones según el servicio que se vaya a usar para enviar mensajes, llamar a la instancia de cliente requerida con el generador, preparar y enviar un mensaje de correo electrónico. También hay una versión asincrónica del método de envío.
- **Establecer el encabezado X-ALT-DESC en el archivo ICS** - Introdujimos un nuevo [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) propiedad para establecer el encabezado X-ALT-DESC.

## [Aspose.Email para.NET 22.3](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-3-release-notes/)

- **Listar los archivos adjuntos de los mensajes mediante el cliente IMAP** - Obtenga información sobre los archivos adjuntos, como el nombre y el tamaño, sin buscar los datos del archivo adjunto. Miembros de la API que participan en la operación:
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfo`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) - Representa la información de un adjunto.
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfocollection/) - Representa una colección de IMAPAttachmentInfo.
  - [`Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/) - Obtiene la información de cada adjunto del mensaje.
- **Obtenga artículos con archivos adjuntos a través del cliente EWS** - Hemos añadido el [`FetchItems(EwsFetchItems options)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method) método para [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#iewsclient-interface). Acepta una instancia de [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) clase como parámetro para controlar el comportamiento del método.

## [Aspose.Email para.NET 22.2](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-2-release-notes/)

- **Añadir adjuntos de referencia**
    Miembros de la API introducidos:
  - [`Aspose.Email.ReferenceAttachment`](https://reference.aspose.com/email/net/aspose.email/referenceattachment/#referenceattachment-class) - representa un adjunto de referencia.
  - [`Aspose.Email.AttachmentPermissionType`](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) - Los datos del tipo de permiso asociados a un adjunto de referencia web.
  - [`Aspose.Email.AttachmentProviderType`](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) - El tipo de servicio web que manipula el archivo adjunto.
- **Recuperar clase de mensaje** - Hemos añadido [MessageClass](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/messageclass/#exchangemessageinfomessageclass-propertyм) propiedad a [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/#exchangemessageinfo-class) clase para recuperar la clase de cada mensaje de la colección de una carpeta pública, después de establecer una conexión con un cliente de EWS.
