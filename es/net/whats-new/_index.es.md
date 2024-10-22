---
title: "Novedades en Aspose.Email para .NET"
url: /es/net/whats-new/
weight: 5
type: docs
---


## [Aspose.Email para .NET 24.3](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-3-release-notes/)

- **Soporte para Contactos y Calendario en MS Graph** - Los métodos de la interfaz IGraphClient permiten acceder, gestionar e interactuar con los contactos y eventos del calendario de los usuarios:
  - Recuperar una colección de contactos MAPI.
  - Recuperar un contacto específico.
  - Crear un nuevo contacto.
  - Actualizar un contacto existente.
  - Recuperar una colección de información del calendario.
  - Recuperar una colección de elementos del calendario.
  - Recuperar un elemento de calendario específico.
  - Crear un nuevo elemento de calendario.
  - Actualizar un elemento de calendario existente.

## [Aspose.Email para .NET 24.2](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-2-release-notes/)

- **Manipular Categorías de Elementos de Outlook** - Aspose.Email permite recuperar y utilizar colores de categoría asociados con categorías de elementos de Outlook almacenados en archivos OLM.

- **Coincidencia de Clase de Contenedor** - se agregó una nueva propiedad [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) a la clase [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class), que, al agregar una carpeta a un archivo PST, permite asegurar que la clase de la carpeta coincida con el tipo o categoría esperada de carpetas dentro del archivo PST.

## [Aspose.Email para .NET 23.12](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-12-release-notes/)

- **Establecer Ruta Relativa a Recursos al Guardar Mensajes de Correo como HTML** - Aspose.Email presenta la capacidad de guardar recursos de correo con rutas relativas al exportar mensajes al formato HTML, ofreciendo una mayor flexibilidad para el enlace de recursos. Los usuarios pueden elegir entre rutas absolutas y relativas, y definir rutas personalizadas utilizando el evento [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/resourcehtmlrendering/#htmlsaveoptionsresourcehtmlrendering-event), simplificando el intercambio y la visualización de correos electrónicos a través de diferentes sistemas.

## [Aspose.Email para .NET 23.11](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-11-release-notes/)

- **Validar Mensajes de Correo** - Se agregó un conjunto de componentes para permitir a los usuarios validar archivos de mensajes, soportando formatos como eml, emlx, mht, msg y oft. Al utilizar esta funcionalidad, los usuarios pueden validar mensajes y obtener información sobre el proceso de validación, incluyendo tipo de formato y errores encontrados.

- **Adjuntar Firmas Digitales a Mensajes de Correo** - El método *AttachSignature* en la clase [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) fue diseñado para agregar fácilmente una firma digital a un correo electrónico.

Una vez que se adjunta la firma, los usuarios pueden verificar los resultados a través de propiedades como 'IsSigned', 'MessageClass' y detalles del archivo adjunto.

Para personalizar el proceso de adjuntar la firma, los usuarios pueden utilizar la clase [SignatureOptions](https://reference.aspose.com/email/net/aspose.email/signatureoptions/#signatureoptions-class).

## [Aspose.Email para .NET 23.10](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-10-release-notes/)

- **Dividir Almacenamiento Mbox en Partes Más Pequeñas** - dividir archivos grandes en partes manejables e implementar acciones personalizadas durante el proceso:

  - Especificar un prefijo personalizado para los nombres de archivos Mbox divididos.
  - Personalizar acciones antes y después de copiar un correo electrónico a un nuevo archivo Mbox.
  - Reaccionar cuando se crea un nuevo archivo Mbox.
  - Responder cuando un nuevo archivo Mbox se llena de correos electrónicos.

- **Obtener Contenido AlternateView por MediaType** - recuperar el contenido como una cadena de un AlternateView específico dentro de un mensaje de correo. El método [MailMessage.GetAlternateViewContent(string mediaType)](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/#mailmessagegetalternateviewcontent-method) permite acceder al contenido de un AlternateView que coincide con el tipo de medio especificado.

## [Aspose.Email para .NET 23.8](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-8-release-notes/)

- **Enviar Correos Electrónicos a través del Cliente Graph** - se agregó soporte para métodos sobrecargados a la clase GraphClient que aceptan un objeto MailMessage para enviar correos electrónicos:
  - [CreateMessage(string folderId, MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage)

  - void [Send(MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send)

- **Guardar Lista de Distribución Mapi en un Solo Archivo VCF Multi Contacto** - Guardar la Lista de Distribución Mapi en un nombre de archivo especificado utilizando las opciones de guardado proporcionadas. Puede proporcionar el nombre del archivo y una instancia de la clase MapiDistributionListSaveOptions como parámetros.
  - void [Save(string fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_5) se ha añadido para este propósito.

## [Aspose.Email para .NET 23.7](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-7-release-notes/)

- **Eliminar Elementos de PST** - Se ha añadido un nuevo método, [DeleteItem(string entryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/deleteitem/), a la clase PersonalStorage. Este método proporciona una forma de eliminar elementos (carpetas o mensajes) de una Tabla de Almacenamiento Personal (PST) utilizando el unique entryId asociado con el elemento.
- **Manejo de Eventos y División de PST** - Funcionalidad Mejorada en la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class):
  - El evento [StorageProcessingEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventhandler/) ocurre antes de que se procese el almacenamiento, específicamente antes de procesar el almacenamiento actual en los métodos MergeWith o SplitInto. Este evento proporciona una oportunidad para ejecutar lógica personalizada o manejar ciertas operaciones antes de que ocurra el procesamiento del almacenamiento.

  - La clase [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventargs/) proporciona datos para el evento PersonalStorage.StorageProcessing. 

  - El método sobrecargado [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto_1) permite dividir el almacenamiento PST en partes de tamaño más pequeño. 
- **Manejo de Calendario** - Se agregaron nuevas propiedades y un método a la clase CalendarReader:
  - La propiedad [Count](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/count/) permite recuperar la cantidad de componentes Vevent (eventos) presentes en el calendario, facilitando el seguimiento del número total de eventos.
  - La propiedad [IsMultiEvents](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/ismultievents/) determina si el calendario contiene múltiples eventos.
  - La propiedad [Method](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/method/) obtiene el tipo de método iCalendar asociado con el objeto calendario. Devuelve el tipo de método, como "REQUEST", "PUBLISH", o "CANCEL", proporcionando información valiosa sobre el propósito del calendario.
  - [Version](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/version/) obtiene la versión de iCalendar.
  - El método [LoadAsMultiple()](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/loadasmultiple/) permite cargar una lista de eventos de un calendario que contiene múltiples eventos. Devuelve una lista de objetos Appointment, permitiendo un fácil acceso y procesamiento de cada evento individualmente.

## [Aspose.Email para .NET 23.6](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-6-release-notes/)

- **Preservar o Eliminar la Firma en la Conversión de MBOX a PST** - establecer la propiedad [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/#mboxtopstconversionoptionsremovesignature-property) en 'true' para eliminar la firma.
- **Eliminar Firma al Cargar Archivos EML** - establecer la propiedad [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/) en 'true' para eliminar la firma.
- **Verificación de Firma de Correo Electrónico**
  - Se añadió una nueva clase [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/) para verificar la firma de correos electrónicos seguros. Ahora puede verificar la firma de objetos MapiMessage y MailMessage.
  - Se añadió una nueva clase [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/) para almacenar los resultados de la verificación de correos electrónicos seguros.

  Se introdujeron métodos del SecureEmailManager:

  - [CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5) 
  - [CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)

## [Aspose.Email para .NET 23.5](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-5-release-notes/)

- **Determinar la Versión de Archivos ICS/VCS** - Utilice la propiedad [Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/) de la clase [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) para recuperar la versión de archivos ICS/VCS.
- **Personalizar Opciones de Guardado para Archivos VCard** - Se agregó la nueva clase [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/) a nuestra API con las siguientes propiedades:
  - [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) permite a los usuarios especificar la versión de vCard deseada al guardar elementos de contacto. Por defecto, la clase está configurada para utilizar la versión 2.1 de vCard (VCardVersion.V21).
  - [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/) - permite a los usuarios controlar si los campos extendidos pueden ser utilizados al guardar archivos vCard. Cuando se establece en verdadero (por defecto), se permiten extensiones, proporcionando compatibilidad con campos personalizados e información de contacto adicional.
  - [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) - la codificación que se debe utilizar al guardar elementos de contacto vCard.
- **Obtener el Número Total de Elementos de Mensaje Contenidos en el Almacenamiento Zimbra** con el método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/) de la clase [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/).
- **Recuperar una Subcarpeta PST por ruta** - Recuperar una subcarpeta con el nombre especificado de la carpeta PST actual usando el método sobrecargado [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2).

## [Aspose.Email para .NET 23.4](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-4-release-notes/)

- **Agregar un Archivo Adjunto de Referencia a un Mensaje** - Se ha añadido un nuevo método [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) a la clase [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) con los siguientes parámetros:
  - `name` - el nombre del archivo adjunto
  - `sharedLink` - un enlace compartido completamente calificado al archivo adjunto proporcionado por un servicio web que manipula el archivo adjunto
  - `url` - una ubicación de archivo
  - `providerName` - un nombre del proveedor de archivo adjunto de referencia
- **Verificación de Múltiples Contactos VCard** - Verifique si un archivo de origen contiene contactos múltiples con el nuevo método [VCardContact.IsMultiContacts(string filePath)](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/ismulticontacts/#ismulticontacts_1).
- **Convertir Formato ICS del Calendario a Formatos de Mensaje** - Convertir citas a objetos de mensaje como MapiMessage y MailMessage.  
- **Opciones Adicionales para Guardar Mensajes en Formatos HTML y MHTML**:
  - [MapiTask.Priority](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/priority/) - Obtiene o establece la Prioridad actual del objeto Tarea.
  - [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Define si es necesario guardar todos los encabezados en el output mhtml o no.
  - [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/) - Indica que los campos específicos de la tarea deben escribirse en html de salida.
- **Establecer Tiempo de Espera para el Proceso de Conversión y Carga de Mensajes** - Limitar el tiempo en milisegundos durante la conversión y carga de mensajes, asegurando que el proceso no tarde más de lo necesario. Para este propósito, se introdujeron las siguientes características:
  - [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/) - Limita el tiempo en milisegundos durante la conversión de un mensaje.
  - [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Se activa si se agota el tiempo durante la conversión a MailMessage.
  - [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limita el tiempo en milisegundos durante la conversión de un mensaje.
  - [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Se activa si se agota el tiempo durante la conversión a MailMessage.

## [Aspose.Email para .NET 23.3](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-3-release-notes/)

- **Obtener el Número Total de Elementos de Mensaje Contenidos en el Almacenamiento OLM** con el método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) para la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class).
- **Determinar si MapiMessage es OFT o MSG** - Determinar si el MapiMessage fue cargado desde un archivo OFT o MSG con la nueva propiedad [MapiMessage.IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/).
- **Detectar un Formato de Archivo NSF**

## [Aspose.Email para .NET 23.1](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-1-release-notes/)

-**Recuperar propiedades del mensaje de MboxMessageInfo** - Acceder a la información sobre mensajes individuales almacenados en un archivo mbox, como tamaño del mensaje, índice del mensaje, encabezados del mensaje, banderas del mensaje, y otros metadatos relacionados con el mensaje. Se han añadido las siguientes propiedades a la clase [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class):

DateTime Date - Obtiene la fecha del mensaje
MailAddress From - Obtiene la dirección del remitente
string Subject - Obtiene el asunto del mensaje
MailAddressCollection To - Obtiene la colección de direcciones que contiene los destinatarios del mensaje
MailAddressCollection CC - Obtiene la colección de direcciones que contiene los destinatarios CC
MailAddressCollection Bcc - Obtiene la colección de direcciones que contiene los destinatarios BCC del mensaje

## [Aspose.Email para .NET 22.12](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-12-release-notes/)

- **Obtener el número total de elementos de mensaje contenidos en el PST** - Se ha añadido el método [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) a la propiedad [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/).
- **Obtener una Carpeta de RSS Feeds Estándar en Almacenamiento Personal**, **Agregar una Carpeta de RSS Feeds Estándar en PST** - Se ha añadido un nuevo valor RssFeeds al enumerador StandardIpmFolder. Ahora la Carpeta de RSS Feeds se puede recuperar o agregar fácilmente al almacenamiento.
- **Desencriptar un Mensaje de Correo Almacenado en el Formato MAPI** - Se ha añadido un método Decrypt a la clase MapiMessage:
  - [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/) - Obtiene un valor que indica si el mensaje está encriptado.
  - [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Desencripta este mensaje (el método busca en las tiendas de certificados y claves privadas del usuario actual y computador).
  - [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Desencripta este mensaje con un certificado. 
- **Establecer un ID de Producto al Guardar MapiCalendar en ICS** - Se ha añadido la propiedad [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) a la clase [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) . 
- **Extraer Mensajes por Identificadores de OLM y MBOX** - Esta es la forma eficiente para evitar atravesar todo el almacenamiento cada vez que se busca un mensaje específico para extraer.
- **Determinar si el Archivo Adjunto es Inline o Regular** con la propiedad [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/).

## [Aspose.Email para .NET 22.11](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-11-release-notes/)

- **Obtener un Tipo de Elemento MAPI** - Evitar la verificación del valor de la propiedad MessageClass cada vez antes de la conversión del mensaje.
- **Eliminar la Firma de MapiMessage** - Para una mejor compatibilidad, se añadieron el método [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) y la propiedad [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/).
- **Identificar Carpetas Predefinidas** - Se introdujo el nuevo método [GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/) de la clase [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) para determinar si una carpeta está dentro de una carpeta predefinida, devolviendo el valor del enumerador StandardIpmFolder basado en el valor del parámetro especificado.
- **Verificar el Formato TNEF del Archivo Adjunto** - La propiedad [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/) indica si el archivo adjunto del mensaje está en formato TNEF.

## [Aspose.Email para .NET 22.10](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-10-release-notes/)

- **Renombrar un Archivo Adjunto en MapiMessage** - Ahora es posible editar el valor de la propiedad [DisplayName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/displayname/) en los archivos adjuntos de MapiMessage.

## [Aspose.Email para .NET 22.9](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-9-release-notes/)

- **Listar Mensajes con la API Graph** - El nuevo método [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) permite controlar el orden de los mensajes recuperados basado en los criterios que especifique.

## [Aspose.Email para .NET 22.8](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-8-release-notes/)

- **Leer Mensajes desde MBOX** - Hemos introducido nuevas características para configurar opciones de carga:
  - La propiedad [MailStorageConverter.MboxMessageOptions](https://reference.aspose.com/email/net/aspose.email.storage/mailstorageconverter/mboxmessageoptions/) - Obtiene o establece opciones de carga de correo al analizar un almacenamiento Mbox.
  - El método [MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage_1). El parámetro EmlLoadOptions especifica opciones al leer mensajes desde almacenamiento Mbox.

## [Aspose.Email para .NET 22.7](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-7-release-notes/)

- **Obtener Información de Identificación del Mensaje** como UID o número de secuencia utilizando las siguientes características:
  - La clase [MailboxInfo](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/#mailboxinfo-class) - Representa la información de identificación sobre un mensaje en un buzón.
  - La propiedad [SequenceNumber](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/sequencenumber/) - El número de secuencia de un mensaje.
  - La propiedad [UniqueId](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/uniqueid/) - El id único de un mensaje.
  - La propiedad [MailMessage.ItemId](https://reference.aspose.com/email/net/aspose.email/mailmessage/itemid/) - Representa la información de identificación sobre un mensaje en un buzón.

## [Aspose.Email para .NET 22.6](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-6-release-notes/)

- **Preservar la Marca de Tiempo Original en Archivos ICS** - Extraer elementos de calendario de archivos PST y guardarlos en formato ICS con la marca de tiempo original utilizando las siguientes opciones:
  - [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Permite especificar opciones adicionales al guardar MapiCalendar en formato ICS.
  - La propiedad [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Permite mantener el valor de DateTimeStamp original en el archivo de salida.

## [Aspose.Email para .NET 22.5](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-5-release-notes/)

- **Enumerar Mensajes con Soporte de Paginación a través del Cliente Graph** - La API proporciona soporte de paginación y filtrado para listar mensajes. Esto es muy útil cuando el buzón tiene un gran número de mensajes y requiere mucho tiempo para recuperar la información de resumen sobre estos.
- **Modo Asincrónico en el Manejo de Clientes de Correo** - Un nuevo enfoque para la tarea incluye los siguientes miembros API:
  - [`IAsyncSmtpClient`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/) - Permite que las aplicaciones envíen mensajes utilizando el Protocolo Simple de Transferencia de Correo (SMTP).
  - [`SmtpClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/#smtpclientcreateasync-method) - Crea una nueva instancia de la clase `Aspose.Email.Clients.Smtp.SmtpClient`.
  - [`IAsyncSmtpClient.SendAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpSend`) conjunto de parámetros.
  - [`IAsyncSmtpClient.ForwardAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpForward`) argumentos.
  - [`IAsyncImapClient`](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Permite que las aplicaciones accedan y manipulen mensajes utilizando el Protocolo de Acceso a Mensajes de Internet (IMAP).
  - [`ImapClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Crea una nueva instancia de la clase `Aspose.Email.Clients.Imap.ImapClient`.

## [Aspose.Email para .NET 22.4](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-4-release-notes/)

- **Enviar Correos Electrónicos con Servicios de Entrega MailGun y SendGrid** - Hemos creado una API unificada que puede utilizar para inicializar opciones dependiendo de qué servicio se utilizará para enviar mensajes, llamar a la instancia requerida del cliente utilizando el constructor, preparar y enviar un mensaje de correo electrónico. También hay una versión asincrónica del método Send.
- **Establecer el encabezado X-ALT-DESC en el archivo ICS** - Introdujimos una nueva propiedad [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) para establecer el encabezado X-ALT-DESC.

## [Aspose.Email para .NET 22.3](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-3-release-notes/)

- **Listar Archivos Adjuntos de Mensajes usando Cliente IMAP** - Obtener información sobre archivos adjuntos como nombre, tamaño sin recuperar los datos del archivo adjunto. Los miembros de la API involucrados en la operación: 
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfo`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) - Representa información sobre un archivo adjunto.
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfocollection/) - Representa una colección de ImapAttachmentInfo. 
  - [`Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/) - Obtiene información sobre cada archivo adjunto en el mensaje.
- **Recuperar Elementos con Archivos Adjuntos a través del Cliente EWS** - Agregamos el método [`FetchItems(EwsFetchItems options)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method) a [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#iewsclient-interface). Acepta una instancia de la clase [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) como parámetro para controlar el comportamiento del método.

## [Aspose.Email para .NET 22.2](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-2-release-notes/)

- **Agregar Archivos Adjuntos de Referencia**
    Se introdujeron miembros de API:
  - [`Aspose.Email.ReferenceAttachment`](https://reference.aspose.com/email/net/aspose.email/referenceattachment/#referenceattachment-class) - representa un archivo adjunto de referencia.
  - [`Aspose.Email.AttachmentPermissionType`](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) - El tipo de permiso de datos asociado con un archivo adjunto de referencia web.
  - [`Aspose.Email.AttachmentProviderType`](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) - El tipo de servicio web que manipula el archivo adjunto.
- **Recuperar clase de mensaje** - Se ha añadido la propiedad [MessageClass](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/messageclass/#exchangemessageinfomessageclass-propertyм) a la clase [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/#exchangemessageinfo-class) para recuperar la clase de cada mensaje en la colección de una carpeta pública, después de establecer una conexión con un cliente EWS.