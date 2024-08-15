---
title: "Работа с папками на сервере Exchange"
url: /ru/java/working-with-folders-on-exchange-server/
weight: 80
type: docs
---


## **Список всех папок с сервера**
Aspose.Email API предоставляет возможность подключиться к серверу Exchange и вывести список всех папок и подпапок. Вы также можете рекурсивно извлекать все подпапки из каждой папки. Он также предоставляет возможность перечислять папки с разбиением на страницы из клиента Exchange с помощью веб-службы Exchange (EWS). В этой статье показано, как извлечь все подпапки с сервера Exchange и извлечь папки с разбиением на страницы.

В следующем фрагменте кода показано, как вывести список папок с сервера Exchange.



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
## **Получите информацию о типе папки с помощью EWS**
The [FolderType](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderInfo#getFolderType\(\)) имущество, предоставленное [ExchangeFolderInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangefolderinfo) класс можно использовать для получения информации о типе папки. Это показано в примере кода ниже.

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
## **Перечисление папок с поддержкой пейджинга с помощью EWS**
В следующем фрагменте кода показано, как использовать поддержку пейджинга в EWS.



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
## **Доступ к настраиваемым папкам или подпапкам почтового ящика**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) позволяет разработчикам получить доступ к любой настраиваемой папке или подпапке из почтового ящика. [folderExists()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#folderExists\(java.lang.String,%20java.lang.String\)) функция [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) возвращает URI указанной настраиваемой папки/подпапки, который затем можно использовать для доступа к целевой папке. В следующем примере открывается настраиваемая папка «TestInbox», созданная в папке INBOX, и отображаются все сообщения из этой настраиваемой папки. Для выполнения этой задачи выполните следующие шаги:

1. Инициализируйте объект IEWSClient, указав действительные учетные данные.
1. Получите доступ к почтовому ящику по умолчанию.
1. Откройте родительскую папку, которая в данном примере называется INBOX. Эта родительская папка также может быть пользовательской папкой.
1. Используйте folderExists () для поиска в указанной настраиваемой подпапке, например «TestInbox». Он вернет URI «TestInbox».
1. Используйте этот Uri для доступа ко всем сообщениям в этой настраиваемой папке.

В следующем фрагменте кода показано, как получить доступ к настраиваемым папкам или подпапкам почтового ящика с помощью EWS.



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
## **Список общедоступных папок**
Microsoft Exchange Server позволяет пользователям создавать общедоступные папки и публиковать в них сообщения. Чтобы сделать это через приложение, используйте Aspose.Email [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс для подключения к серверу Exchange и чтения и загрузки сообщений и сообщений из общедоступных папок. В следующем фрагменте кода показано, как читать все общедоступные папки и подпапки, а также перечислять и загружать все сообщения, обнаруженные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, поскольку только они поддерживают EWS.



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
## **Скопируйте сообщение в другую папку**
Aspose.Email API позволяет копировать сообщение из одной папки в другую с помощью [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)) метод. Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.



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
## **Синхронизация элементов папки**
Aspose.Электронная почта для API Java [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) предоставляет возможность синхронизации содержимого папки Exchange. [syncFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#syncFolder\(java.lang.String\)) метод, представленный [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) класс можно использовать для синхронизации информации о папках в указанной папке. В следующем фрагменте кода показано, как синхронизировать информацию о папках Exchange.



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
## **Получение разрешений для папок Exchange**
Пользователям назначаются разрешения на доступ к общедоступным папкам на сервере Exchange, что ограничивает или определяет уровень доступа пользователя к этим папкам. [ExchangeFolderPermission](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission) класс предоставляет набор свойств разрешений для папок Exchange, таких как [PermissionLevel](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission#getPermissionLevel\(\)), могут ли они [canCreateItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#canCreateItems\(\)), [deleteItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#setDeleteItems\(int\)), а также выполняйте другие задачи, указанные в свойствах разрешения. Разрешения можно получить с помощью [getFolderPermissions()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getFolderPermissions\(java.lang.String\)) метод [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). В этой статье показано, как получить разрешения, примененные к общей папке, для всех пользователей, имеющих доступ к общим папкам.

Для выполнения этой задачи выполните следующие действия:

1. Инициализируйте EWSClient.
1. Используйте ListPublicFolders, чтобы получить список всех общедоступных папок
1. Получите разрешения, связанные с папкой, с помощью метода getFolderPermissions ()

В следующем фрагменте кода показано, как использовать [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс для получения разрешений, примененных к папке.



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
## **Создание папок и подпапок**
Aspose.Email API предоставляет возможность создавать папки в почтовом ящике Exchange. [CreateFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createFolder\(java.lang.String\)) метод [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) можно использовать для этой цели. Чтобы создать папку в почтовом ящике сервера Exchange, можно выполнить следующие шаги.

1. Создайте экземпляр IEWSClient.
1. Задайте свойство UseSlashasFolderSeparator необходимым образом. Если установлено значение **true**, приложение будет считать «косую черту» разделителем папок, а вложенная папка будет создана после косой черты.
1. Используйте метод CreateFolder для создания папки.

В следующем фрагменте кода показано, как создавать папки и подпапки.



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
## **Резервное копирование папок Exchange в PST**
Часто бывает так, что пользователи могут захотеть сделать резервную копию всех или некоторых папок почтового ящика. Aspose.Email предоставляет возможность сделать резервную копию всех или указанных папок почтовых ящиков Exchange в PST. В этой статье описывается резервное копирование папок Exchange в PST с образцом кода. Чтобы создать резервную копию папок сервера Exchange, можно выполнить следующие шаги.

1. Запустите IEWSClient с учетными данными пользователя
1. Добавьте информацию о нужной папке в коллекцию ExchangeFolderInfoCollection
1. Для экспорта содержимого папки в PST используйте метод резервного копирования клиента

В следующем фрагменте кода показано, как создавать резервные копии папок Exchange в PST.



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