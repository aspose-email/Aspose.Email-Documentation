---
title: "Trabajar con carpetas en Exchange Server"
url: /es/java/working-with-folders-on-exchange-server/
weight: 80
type: docs
---


## **Listar todas las carpetas del servidor**
La API Aspose.Email ofrece la capacidad de conectarse al servidor Exchange y enumerar todas las carpetas y subcarpetas. También puede recuperar todas las subcarpetas de cada carpeta de forma recursiva. También ofrece la capacidad de enumerar carpetas con paginación desde el cliente de Exchange mediante el servicio web de Exchange (EWS). En este artículo se muestra cómo recuperar todas las subcarpetas del servidor de Exchange y cómo recuperar las carpetas con paginación.

El siguiente fragmento de código muestra cómo enumerar carpetas de Exchange Server.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    try {
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
        System.out.println("Downloading all messages from Inbox....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Call the recursive method to read messages and get sub-folders
            listSubFolders(client, folderInfo);
        }

        System.out.println("All messages downloaded.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void listSubFolders(IEWSClient client, ExchangeFolderInfo folderInfo) {
    // Create the folder in disk (same name as on IMAP server)
    System.out.println(folderInfo.getDisplayName());
    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Obtenga información sobre el tipo de carpeta mediante EWS**
The [FolderType](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderInfo#getFolderType\(\)) propiedad proporcionada por [ExchangeFolderInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangefolderinfo) La clase se puede usar para obtener información sobre el tipo de carpeta. Esto es como se muestra en el ejemplo de código siguiente.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeFolderInfoCollection folderInfoCol = client.listSubFolders(client.getMailboxInfo().getRootUri());
for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCol) {
    switch (folderInfo.getFolderType()) {
    case ExchangeFolderType.Appointment:
        // handle Appointment
        break;
    case ExchangeFolderType.Contact:
        // handle Contact
        break;
    case ExchangeFolderType.Task:
        // handle Task
        break;
    case ExchangeFolderType.Note:
        // handle email message
        break;
    case ExchangeFolderType.StickyNote:
        // handle StickyNote
        break;
    case ExchangeFolderType.Journal:
        // handle Journal
        break;
    default:
        break;
    }
}
~~~
## **Enumeración de carpetas con soporte de paginación mediante EWS**
El siguiente fragmento de código muestra cómo utilizar el soporte de paginación mediante EWS.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
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
## **Acceso a las carpetas o subcarpetas personalizadas del buzón**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) permite a los desarrolladores acceder a cualquier carpeta o subcarpeta personalizada desde el buzón. El [folderExists()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#folderExists\(java.lang.String,%20java.lang.String\)) función de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) devuelve el URI de una carpeta/subcarpeta personalizada especificada, que se puede usar entonces para acceder a la carpeta de destino. En el ejemplo siguiente, se accede a una carpeta personalizada denominada «TestInbox», que se crea en INBOX, y se muestran todos los mensajes de esta carpeta personalizada. Para realizar esta tarea, siga los pasos siguientes:

1. Inicialice el objeto IewsClient proporcionando credenciales válidas.
1. Acceda al buzón predeterminado.
1. Acceda a la carpeta principal, que en este ejemplo es INBOX. Esta carpeta principal también puede ser una carpeta personalizada en sí misma.
1. Utilice FolderExists () para buscar en la subcarpeta personalizada especificada, por ejemplo, «TestInbox». Devolverá el URI de «TestInbox».
1. Usa este Uri para acceder a todos los mensajes de esa carpeta personalizada.

El siguiente fragmento de código muestra cómo acceder a las carpetas o subcarpetas personalizadas de los buzones de correo con EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create ExchangeMailboxInfo, ExchangeMessageInfoCollection instance
ExchangeMailboxInfo mailbox = client.getMailboxInfo();
ExchangeMessageInfoCollection messages = null;
ExchangeFolderInfo subfolderInfo = new ExchangeFolderInfo();

// Check if specified custom folder exisits and Get all the messages info from the target Uri
ExchangeFolderInfo[] referenceToSubfolderInfo = { subfolderInfo };
client.folderExists(mailbox.getInboxUri(), "TestInbox", /* out */ referenceToSubfolderInfo);
subfolderInfo = referenceToSubfolderInfo[0];

// if custom folder exists
if (subfolderInfo != null) {
    messages = client.listMessages(subfolderInfo.getUri());

    // Parse all the messages info collection
    for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) messages) {
        String strMessageURI = info.getUniqueUri();
        // now get the message details using FetchMessage()
        MailMessage msg = client.fetchMessage(strMessageURI);
        System.out.println("Subject: " + msg.getSubject());
    }
} else {
    System.out.println("No folder with this name found.");
}
~~~
## **Listado de carpetas públicas**
Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de su aplicación, utilice Aspose.Email [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase para conectarse al servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. En el siguiente fragmento de código, se muestra cómo leer todas las carpetas, subcarpetas y listas públicas y cómo descargar los mensajes que se encuentran en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.



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
        System.out.println("Name: " + publicFolder.getDisplayName());
        System.out.println("Subfolders count: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Folder Name: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Call this method recursively for any subfolders
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Copiar un mensaje a otra carpeta**
La API Aspose.Email permite copiar un mensaje de una carpeta a otra mediante el [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)) método. La versión sobrecargada de este método devuelve el URI único del mensaje copiado, como se muestra en este artículo.



~~~Java
try {
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Sincronización de elementos de carpeta**
Aspose.Email para API de Java [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) proporciona la función de sincronizar una carpeta de Exchange para su contenido. El [syncFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#syncFolder\(java.lang.String\)) método expuesto por el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) la clase se puede usar para sincronizar la información de carpetas en una carpeta específica. El siguiente fragmento de código muestra cómo sincronizar la información de la carpeta de Exchange.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sync Folder Items");
client.send(message1);

MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Sync Folder Items");
client.send(message2);

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
SyncFolderResult result = client.syncFolder(client.getMailboxInfo().getInboxUri(), null);
System.out.println(result.getNewItems().size());
System.out.println(result.getChangedItems().size());
System.out.println(result.getReadFlagChanged().size());
System.out.println(result.getDeletedItems().length);
~~~
## **Recuperación de permisos para carpetas de Exchange**
A los usuarios se les asignan permisos para las carpetas públicas de Exchange Server, lo que limita o determina el nivel de acceso que un usuario tiene a estas carpetas. El [ExchangeFolderPermission](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission) la clase proporciona un conjunto de propiedades de permisos para las carpetas de Exchange, como [PermissionLevel](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission#getPermissionLevel\(\)), si pueden [canCreateItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#canCreateItems\(\)), [deleteItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#setDeleteItems\(int\))y realizar otras tareas según lo especificado en las propiedades del permiso. Los permisos se pueden recuperar mediante el [getFolderPermissions()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getFolderPermissions\(java.lang.String\)) método de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). En este artículo se muestra cómo recuperar los permisos aplicados a una carpeta pública para todos los usuarios que tienen acceso a las carpetas compartidas.

Para realizar esta tarea:

1. Inicialice EWSClient.
1. Use ListPublicFolders para obtener una lista de todas las carpetas públicas.
1. Recuperar los permisos asociados a una carpeta mediante el método getFolderPermissions ()

El siguiente fragmento de código muestra cómo usar el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase para recuperar los permisos aplicados a una carpeta.



~~~Java
String folderName = "DesiredFolderName";

// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeFolderInfoCollection folders = client.listPublicFolders();
ExchangeFolderPermissionCollection permissions = new ExchangeFolderPermissionCollection();

ExchangeFolderInfo publicFolder = null;
try {
    for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folders)
        if (folderInfo.getDisplayName().equals(folderName))
            publicFolder = folderInfo;

    if (publicFolder == null)
        System.out.println("public folder was not created in the root public folder");

    ExchangePermissionCollection folderPermissionCol = client.getFolderPermissions(publicFolder.getUri());
    for (ExchangeBasePermission perm : (Iterable<ExchangeBasePermission>) folderPermissionCol) {
        if (perm instanceof ExchangeFolderPermission)
            System.out.println("Permission is null.");
        else {
            ExchangeFolderPermission permission = (ExchangeFolderPermission) perm;

            System.out.println("User's primary smtp address: " + permission.getUserInfo().getPrimarySmtpAddress());
            System.out.println("User can create Items: " + permission.canCreateItems());
            System.out.println("User can delete Items: " + permission.getDeleteItems());
            System.out.println("Is Folder Visible: " + permission.isFolderVisible());
            System.out.println("Is User owner of this folder: " + permission.isFolderOwner());
            System.out.println("User can read items: " + permission.getReadItems());
        }
    }
    ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
    // Get the Permissions for the Contacts and Calendar Folder
    ExchangePermissionCollection contactsPermissionCol = client.getFolderPermissions(mailboxInfo.getContactsUri());
    ExchangePermissionCollection calendarPermissionCol = client.getFolderPermissions(mailboxInfo.getCalendarUri());
} finally {
    // Do the needfull
}
~~~
## **Creación de carpetas y subcarpetas**
La API Aspose.Email ofrece la capacidad de crear carpetas en un buzón de Exchange. La [CreateFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createFolder\(java.lang.String\)) método de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) se puede utilizar para este propósito. Para crear una carpeta en el buzón del servidor Exchange, se pueden seguir los pasos siguientes.

1. Crea una instancia de iEWSClient.
1. Establezca la propiedad UseFlashAsFolderSeparator según sea necesario. Si se establece en **true**, la aplicación considerará la «barra» como separador de carpetas y la subcarpeta se creará después de la barra.
1. Utilice el método CreateFolder para crear la carpeta.

El siguiente fragmento de código muestra cómo crear carpetas y subcarpetas.



~~~Java
// Create instance of EWSClient class by giving credentials
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
## **Haga copias de seguridad de las carpetas de Exchange en PST**
Suele ocurrir que los usuarios deseen realizar una copia de seguridad de todas o algunas de las carpetas del buzón. Aspose.Email ofrece la posibilidad de realizar una copia de seguridad de todas las carpetas de buzones de correo de Exchange o de las especificadas en un archivo PST. En este artículo se describe cómo realizar copias de seguridad de las carpetas de Exchange en un PST con código de ejemplo. Para realizar la copia de seguridad de las carpetas del servidor Exchange, se pueden seguir los pasos siguientes.

1. Inicie iEWSClient con las credenciales de usuario
1. Agregue la información de la carpeta requerida a ExchangeFolderInfoCollection
1. Utilice el método de copia de seguridad del cliente para exportar el contenido de la carpeta a PST

El siguiente fragmento de código muestra cómo hacer copias de seguridad de las carpetas de intercambio en PST.



~~~Java
String dataDir = "data/";
// Create instance of IEWSClient class by providing credentials
final String mailboxUri = "https://ews.domain.com/ews/Exchange.asmx";
final String domain = "";
final String username = "username";
final String password = "password";
NetworkCredential credential = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
ExchangeFolderInfo info = client.getFolderInfo(mailboxInfo.getInboxUri());
ExchangeFolderInfoCollection fc = new ExchangeFolderInfoCollection();
fc.addItem(info);
client.backup(fc, dataDir + "Backup_out.pst", BackupOptions.None);
~~~