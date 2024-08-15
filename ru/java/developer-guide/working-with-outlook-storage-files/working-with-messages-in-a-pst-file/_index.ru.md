---
title: "Работа с сообщениями в файле PST"
url: /ru/java/working-with-messages-in-a-pst-file/
weight: 30
type: docs
---


## **Добавление сообщений в файлы PST**

[Создайте новый файл PST и добавьте подпапки](/email/java/create-new-pst-add-sub-folders-and-messages) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавлять сообщения в подпапки созданного или загруженного файла PST. В этой статье два сообщения с диска добавляются во вложенную папку «Входящие» PST. Используйте [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) and [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) классы для добавления сообщений в файлы PST. Чтобы добавить сообщения в папку «Входящие» PST-файла, выполните следующие действия:

1. Создайте экземпляр **FolderInfo** класс и загрузите его вместе с содержимым папки «Входящие».
1. Добавьте сообщения с диска в папку «Входящие», вызвав [FolderInfo.addMessage()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessage-com.aspose.email.MapiMessage-) метод. [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) класс раскрывает [addMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) метод, позволяющий добавлять большое количество сообщений в папку, сокращая количество операций ввода-вывода на диск и повышая производительность. Полный пример можно найти ниже, в [Добавление массовых сообщений](#adding-bulk-messages).

В приведенных ниже фрагментах кода показано, как добавлять сообщения в подпапку PST под названием «Входящие».

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

Добавление отдельных сообщений в PST подразумевает большее количество операций ввода-вывода на диск и, следовательно, может снизить производительность. Для повышения производительности сообщения можно добавлять в PST в массовом режиме, чтобы минимизировать операции ввода-вывода. [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) Метод позволяет определить диапазон сообщений, добавляемых в PST для повышения производительности, и может использоваться в следующих сценариях. Кроме того, событие MessageAdded возникает при добавлении сообщения в папку.

### **Загрузка сообщений с диска**

В следующем фрагменте кода показано, как загружать сообщения с диска.

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

### **Итерируемая реализация**

В следующем фрагменте кода показано, как создать итерабельную реализацию.

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

Для добавления сообщений из другого PST используйте [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) метод, возвращающий Iterable<MapiMessage>. В следующем фрагменте кода показано, как добавлять сообщения из других PST.

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

## **Получение информации о сообщениях из файла Outlook PST**

In [Прочитайте файл Outlook PST и получите информацию о папках и подпапках](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/), мы обсуждали загрузку файла Outlook PST и просмотр его папок, чтобы узнать имена папок и количество сообщений в них. В этой статье объясняется, как читать все папки и подпапки в файле PST и отображать информацию о сообщениях, например тему, отправителя и получателя. [FolderInfo.getContents()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--) метод используется для отображения [краткая информация о сообщении](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) например, тема, отправитель, получатели.
С точки зрения производительности это наиболее подходящий вариант для получения первичной информации о сообщениях. Чтобы [extract](#extracting-messages-form-pst-files) полные данные сообщения, [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) предоставлен метод.
Файл Outlook PST может содержать вложенные папки. Чтобы получить информацию о сообщениях из этих папок, а также из папок верхнего уровня, используйте рекурсивный метод чтения всех папок. В следующем фрагменте кода показано, как читать PST-файл Outlook и рекурсивно отображать содержимое папки и сообщения.

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

В этой статье показано, как читать файлы Microsoft Outlook PST и [извлекать сообщения](#extracting-messages-form-pst-files). Затем сообщения сохраняются на диск в формате MSG. В статье также показано, как [извлеките определенное количество сообщений](#extracting-n-number-of-messages-from-a-pst-file) из файла PST. Используйте рекурсивный метод для просмотра всех папок (включая все вложенные папки) и вызовите [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) метод получения сообщений Outlook в экземпляр [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс. После этого позвоните [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) метод сохранения сообщения на диске или в потоке в формате MSG. В следующем фрагменте кода показано, как извлечь сообщения из файла PST.

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

### **Сохранение сообщений непосредственно из PST в потоковую передачу**

Чтобы сохранить сообщения из файла PST непосредственно в потоковом режиме, не извлекая MsgInfo для сообщений, используйте [saveMessageToStream()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#saveMessageToStream-java.lang.String-java.io.OutputStream-) метод. В следующем фрагменте кода показано, как сохранять сообщения непосредственно из PST в потоковом режиме.

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

### **Извлечение n количества сообщений из PST-файла**

В следующем фрагменте кода показано, как извлечь заданное количество сообщений из PST. Просто укажите индекс первого сообщения и общее количество сообщений, которые нужно извлечь.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
FolderInfo inbox = personalStorage.getRootFolder().getSubFolder("Inbox");

// Extracts messages starting from 10th index top and extract total 100 messages
MessageInfoCollection messages = inbox.getContents(10, 100);
~~~

### **Получить общее количество элементов из файла PST**

Aspose.Email предоставляет [GetTotalItemsCount()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#getTotalItemsCount--) метод [PersonalStorage.Store](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#getStore--) имущество. Оно возвращает общее количество сообщений, содержащихся в PST.

В следующем примере кода показано, как получить общее количество элементов (сообщений, встреч, контактов и т. д.), хранящихся в файле PST:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    int count = pst.getStore().getTotalItemsCount();
}
```

## **Удалить элементы из файлов PST**

[Добавление сообщений в файлы PST](#adding-messages-to-pst-files) показал, как добавлять сообщения в файлы PST. Конечно, также можно удалять элементы (содержимое) из файла PST, и может быть желательно удалять сообщения массово. Элементы из файла PST можно удалить с помощью [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---) метод. API также предоставляет [FolderInfo.deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) метод массового удаления элементов из файла PST.

### **Удаление сообщений из PST-файлов**

В этой статье показано, как использовать [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) класс для доступа к определенным папкам в файле PST. Чтобы удалить сообщения из подпапки «Отправленные» ранее загруженного или созданного файла PST, выполните следующие действия:

1. Создайте экземпляр [FolderInfo](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/) класс и загрузите его вместе с содержимым отправленной подпапки.
1. Удалите сообщения из папки «Отправленные», вызвав [FolderInfo.deleteChildItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItem-byte---) метод и передача [MessageInfo.EntryId](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/#getEntryId--) в качестве параметра. В следующем фрагменте кода показано, как удалять сообщения из вложенной папки Sent PST-файла.

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

Папку PST можно удалить, переместив ее в папку «Удаленные».

~~~Java
try (PersonalStorage pst = PersonalStorage.fromFile("test.pst")) {
    FolderInfo deletedItemsFolder = pst.getPredefinedFolder(StandardIpmFolder.DeletedItems);
    FolderInfo emptyFolder = pst.getRootFolder().getSubFolder("Empty folder");
    FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
    pst.moveItem(emptyFolder, deletedItemsFolder);
    pst.moveItem(someFolder, deletedItemsFolder);
}
~~~
Преимущество этого метода в том, что удаленную папку можно легко восстановить.


~~~Java
FolderInfo someFolder = deletedItemsFolder.getSubFolder("Some folder");
pst.moveItem(someFolder, pst.getRootFolder());
~~~
При необходимости можно также навсегда удалить папку из папки «Удаленные».


~~~Java
deletedItemsFolder.deleteChildItem(emptyFolder.getEntryId());
~~~
The [deleteChildItem()](https://apireference.aspose.com/email/java/com.aspose.email/FolderInfo#deleteChildItem\(byte[]\)) метод можно использовать для любых папок, если вы хотите немедленно и навсегда удалить подпапку, минуя папку «Удаленные».


~~~Java
FolderInfo someFolder = pst.getRootFolder().getSubFolder("Some folder");
pst.getRootFolder().deleteChildItem(someFolder.getEntryId());
~~~

### **Массовое удаление элементов из файла PST**

Aspose.Email API можно использовать для массового удаления элементов из файла PST. Это достигается с помощью [deleteChildItems()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#deleteChildItems-java.lang.Iterable-java.lang.String--) метод, который принимает список элементов Entry ID, относящихся к удаляемым элементам. В следующем фрагменте кода показано, как массово удалять элементы из файла PST.


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

## **Поиск сообщений и папок в PST по критерию**

Файлы персонального хранилища (PST) могут содержать огромное количество данных, и для поиска данных, соответствующих определенным критериям, в таких больших файлах необходимо включить в код несколько контрольных точек для фильтрации информации. С помощью [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) class, Aspose.Email позволяет искать определенные записи в PST на основе заданных критериев поиска. В PST можно искать сообщения на основе таких параметров поиска, как отправитель, получатель, тема, важность сообщения, наличие вложений, размер сообщения и даже идентификатор сообщения. [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) также можно использовать для поиска подпапок.

### **Поиск сообщений и папок в PST**

В следующем фрагменте кода показано, как использовать [PersonalStorageQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/) класс для поиска содержимого в PST на основе различных критериев поиска. Например, он показывает поиск в PST на основе:

- Важность сообщения.
- Класс сообщений.
- Наличие вложений.
- Размер сообщения.
- Дата сообщения.
- Непрочитанные сообщения.
- Непрочитанные сообщения с вложениями и
- папки с определенным именем подпапки.


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

### **Поиск строки в PST с параметром Ignore Case**

В следующем фрагменте кода показано, как искать строку в PST с помощью параметра ignore case.

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

Вы можете использовать [MailQueryBuilder.or](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) метод поиска сообщений, тема которых содержит хотя бы одно из указанных слов, как показано ниже:

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

## **Переместить элементы в другие папки файла PST**

Aspose.Email позволяет перемещать элементы из исходной папки в другую папку в том же файле личного хранилища (PST). Сюда входят:

- Перемещение указанной папки в новую родительскую папку.
- Перемещение указанного сообщения в новую папку.
- Перемещение содержимого в новую папку.
- Перемещение подпапок в новую родительскую папку.

В следующем фрагменте кода показано, как перемещать такие элементы, как сообщения и папки, из исходной папки в другую папку того же файла PST.

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

## **Обновление свойств сообщения в файле PST**

Иногда требуется обновить некоторые свойства сообщений, такие как смена темы, маркировка важности сообщения и т. д. Обновление сообщения в PST-файле с такими изменениями в свойствах сообщения можно осуществить с помощью [FolderInfo.changeMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#changeMessages-com.aspose.email.MapiPropertyCollection-) метод. В этой статье показано, как массово обновлять сообщения в PST-файле для изменения свойств. В следующем фрагменте кода показано, как массово обновлять свойства сообщений для нескольких сообщений в PST-файле.

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

## **Обновление настраиваемых свойств в файле PST**

Иногда требуется пометить элементы, обрабатываемые в файле PST. API Aspose.Email позволяет сделать это с помощью свойств MapiProperty и MapInamedProperty. В этом помогают следующие методы.

- `constructor MapiNamedProperty(long propertyTag, String nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `constructor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, byte[] propertyValue)`
- `FolderInfo.changeMessages(MapiPropertyCollection updatedProperties)` - изменяет все сообщения в папке
- `PersonalStorage.changeMessage(String entryId, MapiPropertyCollection updatedProperties)` - изменить свойства сообщения

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

Aspose.Email API можно использовать для извлечения вложений из сообщений PST без предварительного извлечения всего сообщения. [ExtractAttachments](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractAttachments-com.aspose.email.MessageInfo-) метод [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) можно использовать для этого. В следующем фрагменте кода показано, как извлекать вложения без извлечения всего сообщения.

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

Ключевые функции Microsoft Outlook — управление электронной почтой, календарями, задачами, контактами и записями журнала. Кроме того, файлы также можно добавлять в папку PST, и полученный PST сохраняет добавленные документы. Aspose.Email предоставляет возможность добавлять файлы в папку таким же образом, а также добавлять сообщения, контакты, задачи и записи журнала в PST. В следующем фрагменте кода показано, как добавлять документы в папку PST с помощью Aspose.Email.

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
