---
title: "Работа с папками на Exchange Server"
url: /ru/java/working-with-folders-on-exchange-server/
weight: 80
type: docs
---

## **Список всех папок на сервере**
API Aspose.Email предоставляет возможность подключаться к Exchange Server и перечислять все папки и подпапки. Вы также можете рекурсивно извлечь все подпапки из каждой папки. Он также предоставляет возможность перечисления папок с постраничной навигацией из клиента Exchange с использованием Exchange Web Service (EWS). Эта статья показывает, как получить все подпапки с сервера Exchange и извлечь папки с постраничной навигацией.

Следующий фрагмент кода показывает, как перечислить папки с сервера Exchange.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    try {
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
        System.out.println("Загрузка всех сообщений из Входящих....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI почтового ящика: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Перечислить все папки с сервера Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Вызвать рекурсивный метод для чтения сообщений и получения подпапок
            listSubFolders(client, folderInfo);
        }

        System.out.println("Все сообщения загружены.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void listSubFolders(IEWSClient client, ExchangeFolderInfo folderInfo) {
    // Создать папку на диске (такое же имя, как на IMAP-сервере)
    System.out.println(folderInfo.getDisplayName());
    try {
        // Если эта папка имеет подпапки, вызвать этот метод рекурсивно для получения сообщений
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Получение информации о типе папки с использованием EWS**
Свойство [FolderType](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderInfo#getFolderType\(\)), предоставляемое классом [ExchangeFolderInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangefolderinfo), может быть использовано для получения информации о типе папки. Это показано в следующем примере кода.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeFolderInfoCollection folderInfoCol = client.listSubFolders(client.getMailboxInfo().getRootUri());
for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCol) {
    switch (folderInfo.getFolderType()) {
    case ExchangeFolderType.Appointment:
        // обрабатывать назначение
        break;
    case ExchangeFolderType.Contact:
        // обрабатывать контакт
        break;
    case ExchangeFolderType.Task:
        // обрабатывать задачу
        break;
    case ExchangeFolderType.Note:
        // обрабатывать сообщение электронной почты
        break;
    case ExchangeFolderType.StickyNote:
        // обрабатывать заметку
        break;
    case ExchangeFolderType.Journal:
        // обрабатывать журнал
        break;
    default:
        break;
    }
}
~~~
## **Перечисление папок с поддержкой постраничной навигации с использованием EWS**
Следующий фрагмент кода показывает, как использовать поддержку постраничной навигации с использованием EWS.

~~~Java
// Создать экземпляр класса ExchangeWebServiceClient, предоставив учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Вызвать метод ListMessages для перечисления информации о сообщениях из Входящих
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
## **Доступ к пользовательским папкам или подпапкам почтового ящика**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) позволяет разработчикам получать доступ к любой пользовательской папке или подпапке из почтового ящика. Функция [folderExists()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#folderExists\(java.lang.String,%20java.lang.String\)) класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) возвращает URI указанной пользовательской папки/подпапки, который затем можно использовать для доступа к целевой папке. В следующем примере пользовательская папка с именем "TestInbox", созданная в папке ВХОДЯЩИЕ, доступна, и все сообщения отображаются из этой пользовательской папки. Чтобы выполнить эту задачу, выполните следующие шаги:

1. Инициализируйте объект IEWSClient, предоставив действительные учетные данные.
1. Получите доступ к стандартному почтовому ящику.
1. Получите доступ к родительской папке, которая в этом примере является ВХОДЯЩИЕ. Эта родительская папка также может быть пользовательской папкой.
1. Используйте folderExists(), чтобы найти указанную пользовательскую подпапку, например "TestInbox". Это вернет URI "TestInbox".
1. Используйте этот URI для доступа ко всем сообщениям в этой пользовательской папке.

Следующий фрагмент кода показывает, как получить доступ к пользовательским папкам или подпапкам почтового ящика с помощью EWS.

~~~Java
// Создать экземпляр класса EWSClient, предоставив учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Создать экземпляры ExchangeMailboxInfo и ExchangeMessageInfoCollection
ExchangeMailboxInfo mailbox = client.getMailboxInfo();
ExchangeMessageInfoCollection messages = null;
ExchangeFolderInfo subfolderInfo = new ExchangeFolderInfo();

// Проверить, существует ли указанная пользовательская папка, и получить всю информацию о сообщениях из целевого URI
ExchangeFolderInfo[] referenceToSubfolderInfo = { subfolderInfo };
client.folderExists(mailbox.getInboxUri(), "TestInbox", /* out */ referenceToSubfolderInfo);
subfolderInfo = referenceToSubfolderInfo[0];

// если пользовательская папка существует
if (subfolderInfo != null) {
    messages = client.listMessages(subfolderInfo.getUri());

    // Обработать всю коллекцию информации о сообщениях
    for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) messages) {
        String strMessageURI = info.getUniqueUri();
        // теперь получить детали сообщения, используя FetchMessage()
        MailMessage msg = client.fetchMessage(strMessageURI);
        System.out.println("Тема: " + msg.getSubject());
    }
} else {
    System.out.println("Папка с таким именем не найдена.");
}
~~~
## **Список общих папок**
Microsoft Exchange Server позволяет пользователям создавать общие папки и размещать сообщения в них. Чтобы сделать это через ваше приложение, используйте класс EWSClient от Aspose.Email, чтобы подключиться к Exchange Server и читать и загружать сообщения и публикации из общих папок. Следующий фрагмент кода показывает, как прочитать все общие папки и подпапки, а также перечислить и загрузить любые сообщения, найденные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, так как только они поддерживают EWS.

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
        System.out.println("Имя: " + publicFolder.getDisplayName());
        System.out.println("Количество подпапок: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);
    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Имя папки: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Вызвать этот метод рекурсивно для любых подпапок
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Копирование сообщения в другую папку**
API Aspose.Email позволяет копировать сообщение из одной папки в другую с помощью метода [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)). Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.

~~~Java
try {
    // Создать экземпляр класса EWSClient, предоставив учетные данные
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Копировать сообщение и получить ссылку на новый элемент копии");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Синхронизация элементов папки**
API Aspose.Email for Java [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) предоставляет возможность синхронизации папки Exchange для ее содержания. Метод [syncFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#syncFolder\(java.lang.String\)), предоставляемый классом [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient), может использоваться для выполнения синхронизации информации о папке в указанной папке. Следующий фрагмент кода показывает, как синхронизировать информацию о папке Exchange.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Синхронизация элементов папки");
client.send(message1);

MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "EMAILNET-34738 - " + UUID.randomUUID().toString(), "EMAILNET-34738 Синхронизация элементов папки");
client.send(message2);

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
SyncFolderResult result = client.syncFolder(client.getMailboxInfo().getInboxUri(), null);
System.out.println(result.getNewItems().size());
System.out.println(result.getChangedItems().size());
System.out.println(result.getReadFlagChanged().size());
System.out.println(result.getDeletedItems().length);
~~~
## **Получение разрешений для папок Exchange**
Пользователям назначаются разрешения на общие папки на Exchange Server, что ограничивает/определяет уровень доступа, который у них есть к этим папкам. Класс [ExchangeFolderPermission](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission) предоставляет набор свойств разрешений для папок Exchange, таких как [PermissionLevel](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeFolderPermission#getPermissionLevel\(\)), возможность [canCreateItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#canCreateItems\(\)), [deleteItems](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeBasePermission#setDeleteItems\(int\)), и выполнение других задач, как указано в свойствах разрешений. Разрешения могут быть извлечены с помощью метода [getFolderPermissions()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getFolderPermissions\(java.lang.String\)) класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Эта статья показывает, как получить разрешения, примененные к общей папке для всех пользователей, имеющих доступ к общим папкам.

Для выполнения этой задачи:

1. Инициализируйте EWSClient.
1. Используйте listPublicFolders для получения списка всех общих папок.
1. Извлеките разрешения, связанные с папкой, с помощью метода getFolderPermissions().

Следующий фрагмент кода показывает, как использовать класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) для извлечения разрешений, примененных к папке.

~~~Java
String folderName = "DesiredFolderName";

// Создать экземпляр класса EWSClient, предоставив учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeFolderInfoCollection folders = client.listPublicFolders();
ExchangeFolderPermissionCollection permissions = new ExchangeFolderPermissionCollection();

ExchangeFolderInfo publicFolder = null;
try {
    for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folders)
        if (folderInfo.getDisplayName().equals(folderName))
            publicFolder = folderInfo;

    if (publicFolder == null)
        System.out.println("общая папка не была создана в корневой общей папке");

    ExchangePermissionCollection folderPermissionCol = client.getFolderPermissions(publicFolder.getUri());
    for (ExchangeBasePermission perm : (Iterable<ExchangeBasePermission>) folderPermissionCol) {
        if (perm instanceof ExchangeFolderPermission)
            System.out.println("Разрешение равно null.");
        else {
            ExchangeFolderPermission permission = (ExchangeFolderPermission) perm;

            System.out.println("Основной smtp-адрес пользователя: " + permission.getUserInfo().getPrimarySmtpAddress());
            System.out.println("Пользователь может создавать элементы: " + permission.canCreateItems());
            System.out.println("Пользователь может удалять элементы: " + permission.getDeleteItems());
            System.out.println("Является ли папка видимой: " + permission.isFolderVisible());
            System.out.println("Является ли пользователь владельцем этой папки: " + permission.isFolderOwner());
            System.out.println("Пользователь может читать элементы: " + permission.getReadItems());
        }
    }
    ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
    // Получить разрешения для папок Контактов и Календаря
    ExchangePermissionCollection contactsPermissionCol = client.getFolderPermissions(mailboxInfo.getContactsUri());
    ExchangePermissionCollection calendarPermissionCol = client.getFolderPermissions(mailboxInfo.getCalendarUri());
} finally {
    // Выполнить необходимые действия
}
~~~
## **Создание папок и подпапок**
API Aspose.Email предоставляет возможность создавать папки в почтовом ящике Exchange. Метод [CreateFolder](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createFolder\(java.lang.String\)) класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) может быть использован для этой цели. Чтобы создать папку в почтовом ящике сервера Exchange, можно выполнить следующие шаги.

1. Создайте экземпляр IEWSClient.
1. Установите свойство UseSlashAsFolderSeparator по мере необходимости. Если установить в **true**, приложение будет считать "Слеш" разделителем папок, и подпапка будет создана после слеша.
1. Используйте метод createFolder для создания папки.

Следующий фрагмент кода показывает, как создать папки и подпапки.

~~~Java
// Создать экземпляр класса EWSClient, предоставив учетные данные
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
Часто пользователи могут захотеть сделать резервную копию всех или некоторых папок почтового ящика. Aspose.Email предоставляет возможность создать резервную копию всех или определенных папок почтового ящика Exchange в PST. Эта статья описывает, как сделать резервную копию папок Exchange в PST с примером кода. Чтобы сделать резервную копию папок сервера Exchange, можно выполнить следующие шаги.

1. Инициализируйте IEWSClient с учетными данными пользователя.
1. Добавьте необходимую информацию о папке в ExchangeFolderInfoCollection.
1. Используйте метод резервного копирования клиента для экспорта содержимого папки в PST.

Следующий фрагмент кода показывает, как сделать резервное копирование папок Exchange в PST.

~~~Java
String dataDir = "data/";
// Создать экземпляр класса IEWSClient, предоставив учетные данные
final String mailboxUri = "https://ews.domain.com/ews/Exchange.asmx";
final String domain = "";
final String username = "username";
final String password = "password";
NetworkCredential credential = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

// Получить информацию о почтовом ящике Exchange другого почтового аккаунта
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
ExchangeFolderInfo info = client.getFolderInfo(mailboxInfo.getInboxUri());
ExchangeFolderInfoCollection fc = new ExchangeFolderInfoCollection();
fc.addItem(info);
client.backup(fc, dataDir + "Backup_out.pst", BackupOptions.None);
~~~