---
title: "Trabajando con Carpetas en el Servidor de Exchange"
url: /es/java/working-with-folders-on-exchange-server/
weight: 80
type: docs
---


## **Listando todas las Carpetas desde el Servidor**
La API de Aspose.Email proporciona la capacidad de conectarse al Servidor de Exchange y listar todas las carpetas y subcarpetas. También puedes recuperar todas las subcarpetas de cada carpeta de forma recursiva. Además, proporciona la capacidad de enumerar carpetas con paginación desde el cliente de Exchange utilizando el Servicio Web de Exchange (EWS). Este artículo muestra cómo recuperar todas las subcarpetas del servidor de Exchange y recuperar carpetas con paginación.

El siguiente fragmento de código muestra cómo listar carpetas desde el Servidor de Exchange.



~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    try {
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
        System.out.println("Descargando todos los mensajes de la Bandeja de entrada....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI de la Bandeja de entrada: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Listar todas las carpetas desde el servidor de Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Llamar al método recursivo para leer mensajes y obtener subcarpetas
            listSubFolders(client, folderInfo);
        }

        System.out.println("Todos los mensajes descargados.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void listSubFolders(IEWSClient client, ExchangeFolderInfo folderInfo) {
    // Crear la carpeta en el disco (mismo nombre que en el servidor IMAP)
    System.out.println(folderInfo.getDisplayName());
    try {
        // Si esta carpeta tiene subcarpetas, llamar a este método recursivamente para obtener mensajes
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Obtener Información del Tipo de Carpeta usando EWS**
La propiedad [FolderType](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderInfo#getFolderType\(\)) proporcionada por la clase [ExchangeFolderInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangefolderinfo) puede ser utilizada para obtener información sobre el tipo de la carpeta. Esto se muestra en el siguiente ejemplo de código.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeFolderInfoCollection folderInfoCol = client.listSubFolders(client.getMailboxInfo().getRootUri());
for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCol) {
    switch (folderInfo.getFolderType()) {
    case ExchangeFolderType.Appointment:
        // manejar Cita
        break;
    case ExchangeFolderType.Contact:
        // manejar Contacto
        break;
    case ExchangeFolderType.Task:
        // manejar Tarea
        break;
    case ExchangeFolderType.Note:
        // manejar mensaje de correo
        break;
    case ExchangeFolderType.StickyNote:
        // manejar Nota Adhesiva
        break;
    case ExchangeFolderType.Journal:
        // manejar Diario
        break;
    default:
        break;
    }
}
~~~
## **Enumerando Carpetas con Soporte de Paginación usando EWS**
El siguiente fragmento de código muestra cómo usar el soporte de paginación utilizando EWS.



~~~Java
// Crear instancia de la clase ExchangeWebServiceClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Llamar al método ListMessages para listar información de mensajes desde la Bandeja de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());
int itemsPerPage = 5;
List<PageInfo> pages = new ArrayList<PageInfo>();
PageInfo pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
pages.add(pagedMessageInfoCol);
while (!pagedMessageInfoCol.getLastPage()) {
    pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
    pages.add(pagedMessageInfoCol);
}
pagedMessageInfoCol = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
while (!pagedMessageInfoCol.getLastPage()) {
    client.listMessages(client.getMailboxInfo().getInboxUri());
}
~~~
## **Acceso a Carpetas Personalizadas o Subcarpetas del Buzón**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) permite a los desarrolladores acceder a cualquier carpeta personalizada o subcarpeta del buzón. La función [folderExists()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#folderExists\(java.lang.String,%20java.lang.String\)) de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) devuelve la URI de una carpeta personalizada/subcarpeta especificada, que puede ser utilizada para acceder a la carpeta de destino. En el siguiente ejemplo, se accede a una carpeta personalizada llamada "TestInbox", que se creó bajo INBOX y se muestran todos los mensajes de esta carpeta personalizada. Para realizar esta tarea, se siguen los siguientes pasos:

1. Inicializar el objeto IEWSClient proporcionando credenciales válidas.
1. Acceder al buzón predeterminado.
1. Acceder a la carpeta principal, que es INBOX en este ejemplo. Esta carpeta principal también puede ser una carpeta personalizada.
1. Usar folderExists() para buscar la subcarpeta personalizada especificada, por ejemplo "TestInbox". Devolverá la URI de "TestInbox".
1. Usar esta Uri para acceder a todos los mensajes en esa carpeta personalizada.

El siguiente fragmento de código muestra cómo acceder a carpetas personalizadas o subcarpetas del buzón con EWS.



~~~Java
// Crear instancia de la clase EWSClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Crear instancia de ExchangeMailboxInfo, ExchangeMessageInfoCollection
ExchangeMailboxInfo mailbox = client.getMailboxInfo();
ExchangeMessageInfoCollection messages = null;
ExchangeFolderInfo subfolderInfo = new ExchangeFolderInfo();

// Verificar si la carpeta personalizada especificada existe y Obtener toda la información de mensajes de la URI de destino
ExchangeFolderInfo[] referenceToSubfolderInfo = { subfolderInfo };
client.folderExists(mailbox.getInboxUri(), "TestInbox", /* out */ referenceToSubfolderInfo);
subfolderInfo = referenceToSubfolderInfo[0];

// si la carpeta personalizada existe
if (subfolderInfo != null) {
    messages = client.listMessages(subfolderInfo.getUri());

    // Analizar toda la colección de información de mensajes
    for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) messages) {
        String strMessageURI = info.getUniqueUri();
        // ahora obtener los detalles del mensaje usando FetchMessage()
        MailMessage msg = client.fetchMessage(strMessageURI);
        System.out.println("Asunto: " + msg.getSubject());
    }
} else {
    System.out.println("No se encontró ninguna carpeta con este nombre.");
}
~~~
## **Listando Carpetas Públicas**
El Servidor de Microsoft Exchange permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacer esto a través de tu aplicación, utiliza la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) de Aspose.Email para conectarte al Servidor de Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. El siguiente fragmento de código muestra cómo leer todas las carpetas públicas y subcarpetas, y listar y descargar cualquier mensaje encontrado en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.



~~~Java
public static void run() {
    try {
        readPublicFolders();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void readPublicFolders() {
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.listPublicFolders();
    for (ExchangeFolderInfo publicFolder : (Iterable<ExchangeFolderInfo>) folders) {
        System.out.println("Nombre: " + publicFolder.getDisplayName());
        System.out.println("Cantidad de subcarpetas: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Nombre de la Carpeta: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Llamar a este método recursivamente para cualquier subcarpeta
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Copiar un Mensaje a otra Carpeta**
La API de Aspose.Email permite copiar un mensaje de una carpeta a otra utilizando el método [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)). La versión sobrecargada de este método devuelve la URI Única del mensaje copiado como se muestra en este artículo.



~~~Java
try {
    // Crear instancia de la clase EWSClient dando credenciales
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copiar un mensaje y obtener referencia al nuevo elemento Copiado");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~ 
## **Sincronizando Elementos de Carpeta**
La API Aspose.Email para Java [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) proporciona la característica de sincronizar una carpeta de Exchange por su contenido. El método [syncFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#syncFolder\(java.lang.String\)) expuesto por la clase [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) puede ser utilizado para realizar la sincronización de información de carpetas en una carpeta especificada. El siguiente fragmento de código muestra cómo sincronizar información de carpeta de Exchange.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sincronizar Elementos de Carpeta");
client.send(message1);

MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sincronizar Elementos de Carpeta");
client.send(message2);

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
SyncFolderResult result = client.syncFolder(client.getMailboxInfo().getInboxUri(), null);
System.out.println(result.getNewItems().size());
System.out.println(result.getChangedItems().size());
System.out.println(result.getReadFlagChanged().size());
System.out.println(result.getDeletedItems().length);
~~~
## **Recuperando Permisos para Carpetas de Exchange**
A los usuarios se les asignan permisos para carpetas públicas en el Servidor de Exchange, lo que limita/determina el nivel de acceso que tiene un usuario a estas carpetas. La clase [ExchangeFolderPermission](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission) proporciona un conjunto de propiedades de permisos para carpetas de Exchange, como el [PermissionLevel](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission#getPermissionLevel\(\)), si pueden [canCreateItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#canCreateItems\(\)), [deleteItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#setDeleteItems\(int\)), y realizar otras tareas según lo especificado por las propiedades de permiso. Los permisos se pueden recuperar utilizando el método [getFolderPermissions()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getFolderPermissions\(java.lang.String\)) de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Este artículo muestra cómo recuperar los permisos aplicados a una carpeta pública para todos los usuarios que tienen acceso a las carpetas compartidas.

Para realizar esta tarea:

1. Inicializar el EWSClient.
1. Usar listPublicFolders para obtener una lista de todas las carpetas públicas.
1. Recuperar los permisos asociados a una carpeta utilizando el método getFolderPermissions().

El siguiente fragmento de código muestra cómo utilizar la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para recuperar permisos aplicados a una carpeta.



~~~Java
String folderName = "DesiredFolderName";

// Crear instancia de la clase EWSClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeFolderInfoCollection folders = client.listPublicFolders();
ExchangeFolderPermissionCollection permissions = new ExchangeFolderPermissionCollection();

ExchangeFolderInfo publicFolder = null;
try {
    for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folders)
        if (folderInfo.getDisplayName().equals(folderName))
            publicFolder = folderInfo;

    if (publicFolder == null)
        System.out.println("la carpeta pública no fue creada en la carpeta pública raíz");

    ExchangePermissionCollection folderPermissionCol = client.getFolderPermissions(publicFolder.getUri());
    for (ExchangeBasePermission perm : (Iterable<ExchangeBasePermission>) folderPermissionCol) {
        if (perm instanceof ExchangeFolderPermission)
            System.out.println("El permiso es nulo.");
        else {
            ExchangeFolderPermission permission = (ExchangeFolderPermission) perm;

            System.out.println("Dirección smtp principal del usuario: " + permission.getUserInfo().getPrimarySmtpAddress());
            System.out.println("El usuario puede crear elementos: " + permission.canCreateItems());
            System.out.println("El usuario puede eliminar elementos: " + permission.getDeleteItems());
            System.out.println("¿Es visible la carpeta?: " + permission.isFolderVisible());
            System.out.println("¿Es el usuario propietario de esta carpeta?: " + permission.isFolderOwner());
            System.out.println("El usuario puede leer elementos: " + permission.getReadItems());
        }
    }
    ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
    // Obtener los permisos para la carpeta de Contactos y Calendario
    ExchangePermissionCollection contactsPermissionCol = client.getFolderPermissions(mailboxInfo.getContactsUri());
    ExchangePermissionCollection calendarPermissionCol = client.getFolderPermissions(mailboxInfo.getCalendarUri());
} finally {
    // Realizar lo necesario
}
~~~ 
## **Creando Carpetas y Sub-Carpetas**
La API de Aspose.Email proporciona la capacidad de crear carpetas en un buzón de Exchange. El método [CreateFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createFolder\(java.lang.String\)) de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) se puede utilizar para este propósito. Para crear una carpeta en el buzón del servidor de Exchange, se pueden seguir los siguientes pasos.

1. Crear una instancia de IEWSClient.
1. Establecer la propiedad UseSlashAsFolderSeparator según sea necesario. Si se establece en **true**, la aplicación considerará la "Barra" como separador de carpetas y la subcarpeta se creará después de la barra.
1. Usar el método createFolder para crear la carpeta.

El siguiente fragmento de código muestra cómo crear carpetas y subcarpetas.



~~~Java
// Crear instancia de la clase EWSClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

String inbox = client.getMailboxInfo().getInboxUri();
String folderName1 = "EMAILNET-35054";
String subFolderName0 = "2015";
String folderName2 = folderName1 + "/" + subFolderName0;
String folderName3 = folderName1 + " / 2015";
ExchangeFolderInfo rootFolderInfo = null;
ExchangeFolderInfo folderInfo = null;

try {
    client.setUseSlashAsFolderSeparator(true);
    client.createFolder(client.getMailboxInfo().getInboxUri(), folderName1);
    client.createFolder(client.getMailboxInfo().getInboxUri(), folderName2);
} finally {
    ExchangeFolderInfo[] referenceToRootFolderInfo = { rootFolderInfo };
    boolean outRefCondition0 = client.folderExists(inbox, folderName1, /* out */ referenceToRootFolderInfo);
    rootFolderInfo = referenceToRootFolderInfo[0];
    if (outRefCondition0) {
        ExchangeFolderInfo[] referenceToFolderInfo = { folderInfo };
        boolean outRefCondition1 = client.folderExists(inbox, folderName2, /* out */ referenceToFolderInfo);
        folderInfo = referenceToFolderInfo[0];
        if (outRefCondition1)
            client.deleteFolder(folderInfo.getUri(), true);
        client.deleteFolder(rootFolderInfo.getUri(), true);
    }
}
~~~ 
## **Respaldo de Carpetas de Exchange a PST**
A menudo sucede que los usuarios pueden querer hacer una copia de seguridad de todas o algunas de las carpetas de correo. Aspose.Email proporciona la capacidad de hacer una copia de seguridad de todas las carpetas de correo de Exchange o de carpetas especificadas a un PST. Este artículo describe cómo hacer una copia de seguridad de las carpetas de Exchange a un PST con un código de ejemplo. Para hacer una copia de seguridad de las carpetas del servidor de Exchange, se pueden seguir los siguientes pasos.

1. Iniciar el IEWSClient con las credenciales del usuario.
1. Agregar la información de las carpetas requeridas a ExchangeFolderInfoCollection.
1. Usar el método de respaldo del cliente para exportar el contenido de la carpeta a PST.

El siguiente fragmento de código muestra cómo hacer una copia de seguridad de carpetas de Exchange a PST.



~~~Java
String dataDir = "data/";
// Crear instancia de la clase IEWSClient proporcionando credenciales
final String mailboxUri = "https://ews.domain.com/ews/Exchange.asmx";
final String domain = "";
final String username = "username";
final String password = "password";
NetworkCredential credential = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

// Obtener información del buzón de Exchange de otra cuenta de correo
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
ExchangeFolderInfo info = client.getFolderInfo(mailboxInfo.getInboxUri());
ExchangeFolderInfoCollection fc = new ExchangeFolderInfoCollection();
fc.addItem(info);
client.backup(fc, dataDir + "Backup_out.pst", BackupOptions.None);
~~~