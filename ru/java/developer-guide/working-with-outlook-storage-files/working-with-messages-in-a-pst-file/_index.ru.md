---
title: "Работа с сообщениями в файле PST"
url: /ru/java/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---


## **Добавление сообщений в файлы PST**

[Создание нового файла PST и добавление подпапок](/email/java/create-new-pst-add-sub-folders-and-messages) показало, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавлять сообщения в подпапки файла PST, который вы создали или загрузили. В этой статье добавляются два сообщения с диска в подпапку "Входящие" файла PST. Используйте классы [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) и [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) для добавления сообщений в файлы PST. Чтобы добавить сообщения в папку "Входящие" файла PST:

1. Создайте экземпляр класса **FolderInfo** и загрузите его содержимое из папки "Входящие".
2. Добавьте сообщения с диска в папку "Входящие", вызвав метод [FolderInfo.addMessage()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessage-com.aspose.email.MapiMessage-). Класс [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) предоставляет метод [addMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--), который позволяет добавлять большое количество сообщений в папку, сокращая операции ввода-вывода на диск и улучшая производительность. Полный пример можно найти ниже, в [Добавление массовых сообщений](#adding-bulk-messages).

Ниже приведен фрагмент кода, который показывает, как добавить сообщения в подпапку PST под названием "Входящие".

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create new PST
PersonalStorage personalStorage = PersonalStorage.create(dataDir, FileFormatVersion.Unicode);

// Add new folder "Inbox"
personalStorage.getRootFolder().addSubFolder("Inbox");

// Select the "Inbox" folder
FolderInfo inboxFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

// Add some messages to "Inbox" folder
inboxFolder.addMessage(MapiMessage.fromFile(dataDir + "MapiMsgWithPoll.msg"));
~~~

### **Добавление массовых сообщений**

Добавление отдельных сообщений в PST подразумевает больше операций ввода-вывода на диск и, следовательно, может замедлять производительность. Для повышения производительности сообщения могут быть добавлены в PST оптом, чтобы минимизировать операции ввода-вывода. Метод [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) позволяет вам определить диапазон сообщений, которые будут добавлены в PST для повышения производительности, и может использоваться в следующих сценариях. Кроме того, событие MessageAdded происходит, когда сообщение добавляется в папку.

### **Загрузка сообщений с диска**

Следующий фрагмент кода показывает, как загружать сообщения с диска.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
private static void addMessagesInBulkMode(String fileName, String msgFolderName) {
    try (PersonalStorage personalStorage = PersonalStorage.fromFile(fileName)) {
        FolderInfo folder = personalStorage.getRootFolder().getSubFolder("myInbox");
        folder.MessageAdded.add(new MessageAddedEventHandler() {
            public void invoke(Object sender, MessageAddedEventArgs e) {
                onMessageAdded(sender, e);
            }
        });
        folder.addMessages(new MapiMessageCollection(msgFolderName));
    }
}

static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~

### **Реализация Iterable**

Следующий фрагмент кода показывает, как создать реализацию Iterable.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public class MapiMessageCollection implements Iterable<MapiMessage> {

    private final File folder;

    public MapiMessageCollection(String folder) {
        this.folder = new File(folder);
    }

    public Iterator<MapiMessage> iterator() {
        return new MapiMessageIterator(folder.listFiles());
    }
}

public class MapiMessageIterator implements Iterator<MapiMessage> {

    private Queue<String> queue = new LinkedList<String>();

    public MapiMessageIterator(File[] listOfFiles) {
        for (File file : listOfFiles) {
            queue.offer(file.getAbsolutePath());
        }
    }

    public boolean hasNext() {
        return !queue.isEmpty();
    }

    public MapiMessage next() {
        return MapiMessage.fromFile(queue.poll());
    }
}
~~~

### **Добавление сообщений из другого PST**

Для добавления сообщений из другого PST используйте метод [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--), который возвращает Iterable<MapiMessage>. Следующий фрагмент кода показывает, как добавить сообщения из другого PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
private static void bulkAddFromAnotherPst(String source) {
    // The path to the File directory.
    String dataDir = "data/";

    try (PersonalStorage pst = PersonalStorage.fromFile(source, false)) {
        try (PersonalStorage pstDest = PersonalStorage.fromFile(dataDir + "PersonalStorageFile1.pst")) {
            // Get the folder by name
            FolderInfo folderInfo = pst.getRootFolder().getSubFolder("Contacts");
            MessageInfoCollection ms = folderInfo.getContents();

            // Get the folder by name
            FolderInfo f = pstDest.getRootFolder().getSubFolder("myInbox");
            f.MessageAdded.add(new MessageAddedEventHandler() {
                public void invoke(Object sender, MessageAddedEventArgs e) {
                    onMessageAdded(sender, e);
                }
            });
            f.addMessages(folderInfo.enumerateMapiMessages());
            FolderInfo fi = pstDest.getRootFolder().getSubFolder("myInbox");
            MessageInfoCollection msgs = fi.getContents();
        }
    }
}

// Handles the MessageAdded event.
static void onMessageAdded(Object sender, MessageAddedEventArgs e) {
    System.out.println(e.getEntryId());
    System.out.println(e.getMessage().getSubject());
}
~~~

## **Получение информации о сообщениях из файла PST Outlook**

В [Чтение файла PST Outlook и получение информации о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/) мы обсуждали загрузку файла PST Outlook и просмотр его папок, чтобы получить имена папок и количество сообщений в них. Эта статья объясняет, как прочитать все папки и подпапки в файле PST и отобразить информацию о сообщениях, например, тему, отправителя и получателей. Метод [FolderInfo.getContents()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--) используется для отображения [краткой информации о сообщении](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) такой как тема, отправитель, получатели. С точки зрения производительности, это наиболее подходящий вариант для получения основной информации о сообщениях. Чтобы [извлечь](#extracting-messages-form-pst-files) полные данные сообщения, предоставлен метод [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-).
Файл PST Outlook может содержать вложенные папки. Чтобы получить информацию о сообщениях из этих папок, а также из верхних папок, используйте рекурсивный метод для чтения всех папок. Следующий фрагмент кода показывает, как загрузить файл PST Outlook и рекурсивно отобразить содержимое папки и сообщения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/";

    // Load the Outlook file
    String path = dataDir + "PersonalStorage.pst";

    try {

        // Load the Outlook PST file
        PersonalStorage personalStorage = PersonalStorage.fromFile(path);

        // Get the Display Format of the PST file
        System.out.println("Display Format: " + personalStorage.getFormat());

        // Get the folders and messages information
        FolderInfo folderInfo = personalStorage.getRootFolder();

        // Call the recursive method to display the folder contents
        displayFolderContents(folderInfo, personalStorage);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// This is a recursive method to display contents of a folder
private static void displayFolderContents(FolderInfo folderInfo, PersonalStorage pst) {
    // Display the folder name
    System.out.println("Folder: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // Display information about messages inside this folder
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Subject: " + messageInfo.getSubject());
        System.out.println("Sender: " + messageInfo.getSenderRepresentativeName());
        System.out.println("Recipients: " + messageInfo.getDisplayTo());
        System.out.println("------------------------------");
    }

    // Call this method recursively for each subfolder
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            displayFolderContents(subfolderInfo, pst);
        }
    }
}
~~~

## **Извлечение сообщений из файлов PST**

Эта статья показывает, как читать файлы PST Microsoft Outlook и [извлекать сообщения](#extracting-messages-form-pst-files). Сообщения затем сохраняются на диск в формате MSG. В статье также показано, как [извлечь определенное количество сообщений](#extracting-n-number-of-messages-from-a-pst-file) из файла PST. Используйте рекурсивный метод для просмотра всех папок (включая любые вложенные папки) и вызова метода [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) для получения сообщений Outlook в экземпляре класса [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/). После этого вызовите метод [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) для сохранения сообщения либо на диск, либо в поток в формате MSG. Следующий фрагмент кода показывает, как извлечь сообщения из файла PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/";

    // Load the Outlook file
    String path = dataDir + "PersonalStorage.pst";

    try {
        // load the Outlook PST file
        PersonalStorage pst = PersonalStorage.fromFile(path);

        // get the Display Format of the PST file
        System.out.println("Display Format: " + pst.getFormat());

        // get the folders and messages information
        FolderInfo folderInfo = pst.getRootFolder();

        // Call the recursive method to extract msg files from each folder
        extractMsgFiles(folderInfo, pst);
    } catch (Exception ex) {
        System.out.println(ex.getMessage());
    }
}

// This is a recursive method to display contents of a folder
private static void extractMsgFiles(FolderInfo folderInfo, PersonalStorage pst) {
    // display the folder name
    System.out.println("Folder: " + folderInfo.getDisplayName());
    System.out.println("==================================");
    // loop through all the messages in this folder
    MessageInfoCollection messageInfoCollection = folderInfo.getContents();
    for (MessageInfo messageInfo : messageInfoCollection) {
        System.out.println("Saving message {0} ...." + messageInfo.getSubject());
        // get the message in MapiMessage instance
        MapiMessage message = pst.extractMessage(messageInfo);
        // save this message to disk in msg format
        message.save(message.getSubject().replace(":", " ") + ".msg");
        // save this message to stream in msg format
        ByteArrayOutputStream messageStream = new ByteArrayOutputStream();
        message.save(messageStream);
    }

    // Call this method recursively for each subfolder
    if (folderInfo.hasSubFolders() == true) {
        for (FolderInfo subfolderInfo : folderInfo.getSubFolders()) {
            extractMsgFiles(subfolderInfo, pst);
        }
    }
}
~~~

### **Сохранение сообщений непосредственно из PST в поток**

Чтобы сохранить сообщения из файла PST непосредственно в поток, без извлечения MsgInfo для сообщений, используйте метод [saveMessageToStream()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) метод. Следующий фрагмент кода показывает, как сохранить сообщения непосредственно из PST в поток.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

// Load the Outlook file
String path = dataDir + "PersonalStorage.pst";

// Save message to MemoryStream
try (PersonalStorage personalStorage = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (ByteArrayOutputStream memeorystream = new ByteArrayOutputStream()) {
            personalStorage.saveMessageToStream(messageInfo.getEntryIdString(), memeorystream);
        }
    }
}

// Save message to file
try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");
    for (MessageInfo messageInfo : inbox.enumerateMessages()) {
        try (FileOutputStream fs = new FileOutputStream(new File(dataDir + messageInfo.getSubject() + ".msg"))) {
            pst.saveMessageToStream(messageInfo.getEntryIdString(), fs);
        }
    }
}

try (PersonalStorage pst = PersonalStorage.fromFile(path)) {
    FolderInfo inbox = pst.getRootFolder().getSubFolder("Inbox");

    // To enumerate entryId of messages you may use FolderInfo.EnumerateMessagesEntryId() method:
    for (String entryId : inbox.enumerateMessagesEntryId()) {
        try (ByteArrayOutputStream ms = new ByteArrayOutputStream()) {
            pst.saveMessageToStream(entryId, ms);
        }
    }
}
~~~

### **Извлечение n количества сообщений из файла PST**

Следующий фрагмент кода показывает, как извлечь заданное количество сообщений из PST. Просто укажите индекс для первого сообщения и общее количество сообщений, которые нужно извлечь.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.getContents(10, 100);
~~~

### **Получение общего количества элементов из файла PST**

Aspose.Email предоставляет метод [GetTotalItemsCount()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#getTotalItemsCount--) свойства [PersonalStorage.Store](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#getStore--). Он возвращает общее количество элементов сообщений, содержащихся в PST.

Следующий образец кода показывает, как получить общее количество элементов (сообщений, назначений, контактов и т. д.), хранящихся в файле PST:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    int count = pst.getStore().getTotalItemsCount();
}
```

## **Удаление элементов из файлов PST**

[Добавление сообщений в файлы PST](#adding-messages-to-pst-files) показало, как добавлять сообщения в файлы PST. Конечно, также возможно удалять элементы (содержимое) из файла PST, и может быть желательным удалить сообщения оптом. Элементы из файла PST можно удалить, используя метод [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---). API также предоставляет метод [FolderInfo.deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) для массового удаления элементов из файла PST.

### **Удаление сообщений из файлов PST**

Эта статья показывает, как использовать класс [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) для доступа к определенным папкам в файле PST. Чтобы удалить сообщения из папки "Отправленные" ранее загруженного или созданного файла PST:

1. Создайте экземпляр класса [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) и загрузите его с содержимым из папки "Отправленные".
2. Удалите сообщения из папки "Отправленные", вызвав метод [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---) и передав в качестве параметра [MessageInfo.EntryId](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/#getEntryId--). Следующий фрагмент кода показывает, как удалить сообщения из подпапки "Отправленные" файла PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Get the Sent items folder
FolderInfo folderInfo = personalStorage.getPredefinedFolder(StandardIpmFolder.SentItems);

MessageInfoCollection msgInfoColl = folderInfo.getContents();
for (MessageInfo msgInfo : msgInfoColl) {
    System.out.println(msgInfo.getSubject() + ": " + msgInfo.getEntryIdString());
    if (msgInfo.getSubject().equals("some delete condition")) {
        // Delete this item
        folderInfo.deleteChildItem(msgInfo.getEntryId());
        System.out.println("Deleted this message");
    }
}
~~~

### **Удаление папок из файлов PST**

Вы можете удалить папку PST, переместив ее в папку "Удаленные элементы".

~~~Java
try (PersonalStorage pst = PersonalStorage.fromFile("test.pst")) {
    FolderInfo deletedItemsFolder = pst.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.getRootFolder().getSubFolder("Empty folder");
    FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
    pst.moveItem(emptyFolder, deletedItemsFolder);
    pst.moveItem(someFolder, deletedItemsFolder);
}
~~~
Преимущества этого метода заключаются в том, что удаленную папку можно легко восстановить.

~~~Java
FolderInfo someFolder = deletedItemsFolder.getSubFolder("Some folder");
pst.moveItem(someFolder, pst.getRootFolder());
~~~
Кроме того, по мере необходимости вы можете безвозвратно удалить папку из папки "Удаленные элементы".

~~~Java
deletedItemsFolder.deleteChildItem(emptyFolder.getEntryId());
~~~
Метод [deleteChildItem()](https://apireference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) может использоваться для любых папок, если вы хотите немедленно и навсегда удалить подпапку, минуя папку "Удаленные элементы".

~~~Java
FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
pst.getRootFolder().deleteChildItem(someFolder.getEntryId());
~~~

### **Массовое удаление элементов из файла PST**

API Aspose.Email может использоваться для массового удаления элементов из файла PST. Это достигается с помощью метода [deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--), который принимает список элементов Entry ID, относящихся к удаляемым элементам. Следующий фрагмент кода показывает, как удалить элементы массово из файла PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
    // Get Inbox SubFolder from Outlook file
    FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

    // Create instance of PersonalStorageQueryBuilder
    PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();

    queryBuilder.getFrom().contains("someuser@domain.com");
    MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());
    List<String> deleteList = new ArrayList<String>();
    for (MessageInfo messageInfo : messages) {
        deleteList.add(messageInfo.getEntryIdString());
    }

    // delete messages having From = "someuser@domain.com"
    inbox.deleteChildItems(deleteList);
}
~~~

## **Поиск сообщений и папок в PST по критериям**

Файлы личного хранения (PST) могут содержать огромные объемы данных, и поиск данных, удовлетворяющих конкретному критерию в таких больших файлах, требует включения нескольких контрольных точек в код для фильтрации информации. С помощью класса [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) Aspose.Email позволяет искать конкретные записи в PST на основе заданных критериев поиска. PST можно искать по сообщениям на основе параметров поиска, таких как отправитель, получатель, тема, важность сообщения, наличие вложений, размер сообщения и даже идентификатор сообщения. Класс [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) также может использоваться для поиска подпапок.

### **Поиск сообщений и папок в PST**

Следующий фрагмент кода показывает, как использовать класс [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) для поиска содержимого в PST на основе различных критериев поиска. Например, он показывает поиск в PST по:

- Важность сообщения.
- Класс сообщения.
- Наличие вложений.
- Размер сообщения.
- Дата сообщения.
- Непрочитанные сообщения.
- Непрочитанные сообщения с вложениями и
- папки с конкретным именем подпапки.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalStorage.getRootFolder().getSubFolder("Inbox");
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();

    // High importance messages
    builder.getImportance().equals((int) MapiImportance.High);
    MessageInfoCollection messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with High Imp:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    builder.getMessageClass().equals("IPM.Note");
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with IPM.Note:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages with attachments AND high importance
    builder.getImportance().equals((int) MapiImportance.High);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages with atts: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages with size > 15 KB
    builder.getMessageSize().greater(15000);
    messages = folder.getContents(builder.getQuery());
    System.out.println("messags size > 15Kb:" + messages.size());

    java.util.Calendar c = java.util.Calendar.getInstance();

    builder = new PersonalStorageQueryBuilder();
    // Messages by Current Date
    // (Note that queries by date are not supported for Calendar Items in the Appointments folder)
    builder.getSentDate().on(c.getTime(), DateComparisonType.ByDate);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages by Current Date: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Messages between Dates
    // (Note that queries by date are not supported for Calendar Items in the Appointments folder)
    c.set(2020,  0, 1, 0, 0, 0);
    builder.getSentDate().since(c.getTime());
    c.set(2021,  0, 1, 0, 0, 0);
    builder.getSentDate().before(c.getTime());
    messages = folder.getContents(builder.getQuery());
    System.out.println("Messages between Dates: " + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Unread messages
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Unread:" + messages.size());

    builder = new PersonalStorageQueryBuilder();
    // Unread messages with attachments
    builder.hasNoFlags(MapiMessageFlags.MSGFLAG_READ);
    builder.hasFlags(MapiMessageFlags.MSGFLAG_HASATTACH);
    messages = folder.getContents(builder.getQuery());
    System.out.println("Unread msgs with atts: " + messages.size());

    // Folder with name of 'SubInbox'
    builder = new PersonalStorageQueryBuilder();
    builder.getFolderName().equals("SubInbox");
    FolderInfoCollection folders = folder.getSubFolders(builder.getQuery());
    System.out.println("Folder having subfolder: " + folders.size());

    builder = new PersonalStorageQueryBuilder();
    // Folders with subfolders
    builder.hasSubfolders();
    folders = folder.getSubFolders(builder.getQuery());
    System.out.println(folders.size());
}
~~~

### **Поиск строки в PST с параметром игнорирования регистра**

Следующий фрагмент кода показывает, как искать строку в PST с параметром игнорирования регистра.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "CaseSensitivity.pst", FileFormatVersion.Unicode)) {
    FolderInfo folderinfo = personalStorage.createPredefinedFolder("Inbox", StandardIpmFolder.Inbox);
    folderinfo.addMessage(MapiMessage.fromMailMessage(MailMessage.load("Sample.eml")));
    PersonalStorageQueryBuilder builder = new PersonalStorageQueryBuilder();
    // IgnoreCase is True
    builder.getFrom().contains("automated", true);
    MailQuery query = builder.getQuery();
    MessageInfoCollection coll = folderinfo.getContents(query);
    System.out.println(coll.size());
}
~~~ 

### **Поиск тем сообщений по нескольким ключевым словам в файле PST**

Вы можете использовать метод [MailQueryBuilder.or](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) для поиска сообщений с темой, содержащей по крайней мере одно из указанных слов, как показано ниже:

~~~java
PersonalStorageQueryBuilder builder1 = new PersonalStorageQueryBuilder();
builder1.getSubject().contains("Review"); // 'Review' is key word for the search

PersonalStorageQueryBuilder builder2 = new PersonalStorageQueryBuilder();
builder2.getSubject().contains("Error"); // 'Error' is also key word for the search

PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.or(builder1.getQuery(), builder2.getQuery()); // message subjects must contain 'Review' or 'Error' words

try (PersonalStorage storage = PersonalStorage.fromFile("example.pst"))
{
    FolderInfo folderInfo = storage.getRootFolder().getSubFolder("Inbox");
    MessageInfoCollection messageInfos = folderInfo.getContents(queryBuilder.getQuery());

    for (MessageInfo messageInfo : messageInfos)
    {
        System.out.println(messageInfo.getSubject());
    }
}
~~~ 

## **Перемещение элементов в другие папки файла PST**

Aspose.Email позволяет перемещать элементы из одной папки в другую папку в одном и том же файле личного хранения (PST). Это включает:

- Перемещение указанной папки в новую родительскую папку.
- Перемещение указанного сообщения в новую папку.
- Перемещение содержимого в новую папку.
- Перемещение подпапок в новую родительскую папку.

Следующий фрагмент кода показывает, как перемещать элементы, такие как сообщения и папки, из одной папки в другую папку в том же файле PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
try (PersonalStorage personalStorage = PersonalStorage.fromFile("test.pst")) {
    FolderInfo inbox = personalStorage.getPredefinedFolder(StandardIpmFolder.Inbox);
    FolderInfo deleted = personalStorage.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo subfolder = inbox.getSubFolder("Subfolder");

    // Move folder and message to the Deleted Items
    personalStorage.moveItem(subfolder, deleted);
    MessageInfoCollection contents = subfolder.getContents();
    personalStorage.moveItem(contents.get(0), deleted);

    // Move all inbox subfolders and subfolder contents to the Deleted Items
    inbox.moveSubfolders(deleted);
    subfolder.moveContents(deleted);
}
~~~ 

## **Обновление свойств сообщений в файле PST**

Иногда требуется обновить определенные свойства сообщений, например, изменить тему, отметить важность сообщения и подобные вещи. Обновление сообщения в файле PST с такими изменениями в свойствах сообщения можно выполнить, используя метод [FolderInfo.changeMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#changeMessages-com.aspose.email.MapiPropertyCollection-). Эта статья показывает, как обновить сообщения оптом в файле PST для изменений в свойствах. Следующий фрагмент кода показывает, как обновить свойства сообщений в режиме массовой обработки для нескольких сообщений в файле PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/" + "Sub.pst";

// Load the Outlook PST file
PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir);

// Get Requierd Subfolder
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// find messages having From = "someuser@domain.com"
PersonalStorageQueryBuilder queryBuilder = new PersonalStorageQueryBuilder();
queryBuilder.getFrom().contains("someuser@domain.com");

// Get Contents from Query
MessageInfoCollection messages = inbox.getContents(queryBuilder.getQuery());

// Save (MessageInfo,EntryIdString) in List
List<String> changeList = new ArrayList<String>();
for (MessageInfo messageInfo : messages) {
    changeList.add(messageInfo.getEntryIdString());
}

// Compose the new properties
MapiPropertyCollection updatedProperties = new MapiPropertyCollection();
updatedProperties.add(MapiPropertyTag.PR_SUBJECT_W, new MapiProperty(MapiPropertyTag.PR_SUBJECT_W, "New Subject".getBytes(Charset.forName("utf-16le"))));
updatedProperties.add(MapiPropertyTag.PR_IMPORTANCE, new MapiProperty(MapiPropertyTag.PR_IMPORTANCE, BitConverter.getBytesInt64(2)));

// update messages having From = "someuser@domain.com" with new properties
inbox.changeMessages(changeList, updatedProperties);
~~~

## **Обновление пользовательских свойств в файле PST**

Иногда необходимо отметить элементы, которые были обработаны внутри файла PST. API Aspose.Email позволяет достичь этого с помощью MapiProperty и MapiNamedProperty. Следующие методы полезны для достижения этого.

- `constructor MapiNamedProperty(long propertyTag, String nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `constructor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `FolderInfo.changeMessages(MapiPropertyCollection updatedProperties)` - изменяет все сообщения в папке
- `PersonalStorage.changeMessage(String entryId, MapiPropertyCollection updatedProperties)` - изменение свойств сообщения

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dataDir = "data/" + "Sub.pst";

    try (PersonalStorage personalStorage = PersonalStorage.fromFile(dataDir)) {
        FolderInfo testFolder = personalStorage.getRootFolder().getSubFolder("Inbox");

        // Create the collection of message properties for adding or updating
        MapiPropertyCollection newProperties = new MapiPropertyCollection();

        // Normal, Custom and PidLidLogFlags named property
        MapiProperty property = new MapiProperty(MapiPropertyTag.PR_ORG_EMAIL_ADDR_W, "test_address@org.com".getBytes(Charset.forName("utf-16le")));
        MapiProperty namedProperty1 = new MapiNamedProperty(generateNamedPropertyTag(0L, MapiPropertyType.PT_LONG), "ITEM_ID", UUID.randomUUID(),
                BitConverter.getBytesInt64(123));
        MapiProperty namedProperty2 = new MapiNamedProperty(generateNamedPropertyTag(1L, MapiPropertyType.PT_LONG), 0x0000870C,
                UUID.fromString("0006200A-0000-0000-C000-000000000046"), BitConverter.getBytesInt64(0));
        newProperties.add(namedProperty1.getTag(), namedProperty1);
        newProperties.add(namedProperty2.getTag(), namedProperty2);
        newProperties.add(property.getTag(), property);
        testFolder.changeMessages(testFolder.enumerateMessagesEntryId(), newProperties);
    }
}

private static long generateNamedPropertyTag(long index, int dataType) {
    return (((0x8000 | index) << 16) | (long) dataType) & 0x00000000FFFFFFFFL;
}
~~~

## **Извлечение вложений без извлечения полного сообщения**

API Aspose.Email можно использовать для извлечения вложений из сообщений PST без предварительного извлечения полного сообщения. Метод [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) класса [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) может быть использован для этого. Следующий фрагмент кода показывает, как извлечь вложения без извлечения полного сообщения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalstorage = PersonalStorage.fromFile(dataDir + "Outlook.pst")) {
    FolderInfo folder = personalstorage.getRootFolder().getSubFolder("Inbox");

    for (String messageInfo : folder.enumerateMessagesEntryId()) {
        MapiAttachmentCollection attachments = personalstorage.extractAttachments(messageInfo);

        if (attachments.size() != 0) {
            for (MapiAttachment attachment : attachments) {
                if (attachment.getLongFileName() != null && !attachment.getLongFileName().isEmpty()) {
                    if (attachment.getLongFileName().contains(".msg")) {
                        continue;
                    } else {
                        attachment.save(dataDir + "Attachments/" + attachment.getLongFileName());
                    }
                }
            }
        }
    }
}
~~~ 

## **Добавление файлов в PST**

Ключевая функция Microsoft Outlook - это управление электронной почтой, календарями, задачами, контактами и записями в журнале. Кроме того, файлы также могут быть добавлены в папку PST, и получившийся PST сохраняет записи о добавленных документах. Aspose.Email предоставляет возможность добавлять файлы в папку таким же образом, как и добавление сообщений, контактов, задач и записей в журнал в PST. Следующий фрагмент кода показывает, как добавить документы в папку PST с помощью Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "data/";

try (PersonalStorage personalStorage = PersonalStorage.create(dataDir + "Ps1_out.pst", FileFormatVersion.Unicode)) {
    FolderInfo folder = personalStorage.getRootFolder().addSubFolder("Files");

    // Add Document.doc file with the "IPM.Document" message class by default.
    folder.addFile(dataDir + "attachment_1.doc", null);
}
~~~