---
title: "Создание нового PST-файла, добавление подкаталогов и сообщений"
url: /ru/java/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---


Помимо парсинга существующего PST-файла, Aspose.Email предоставляет средства для создания PST-файла с нуля. В этой статье показано, как создать файл PST для Outlook и добавить к нему подкаталог.

1. [Создание нового PST-файла](#creating-a-new-pst-file-and-add-subfolders).
1. [Изменение класса контейнера папки](#changing-a-folders-container-class).
1. [Добавление пакетных сообщений с улучшенной производительностью](#add-bulk-messages-with-improved-performance) 

Используйте класс [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) для создания PST-файла в каком-либо месте на локальном диске. Чтобы создать PST-файл с нуля:

1. Создайте PST с использованием метода [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) .
1. Добавьте подкаталог в корень PST-файла, получив доступ к корневой папке и затем вызвав метод [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addSubFolder-java.lang.String-) .

Следующий фрагмент кода демонстрирует, как создать PST-файл и добавить подкаталог с названием Входящие.

```java
// Создайте новый PST
try (PersonalStorage pst = PersonalStorage.create(path, FileFormatVersion.Unicode)) {
    // Добавьте новую папку "Входящие"
    pst.getRootFolder().addSubFolder("Inbox");
}
```
## **Создание PST размером более 2 Гб с использованием OutputStream**

Пользователи Aspose.Email могут оптимизировать внутренний кеш PST с помощью конструктора PersonalStorage:

- **blockSize** - Оптимальный размер блока для расширения кеша (в байтах).

```java
PersonalStorage create(OutputStream stream, int blockSize, /*FileFormatVersion*/int version)
```
## **Сокращение размера сообщения и размера создаваемого PST-файла**

Aspose.Email предлагает возможность сжимать содержимое тела, что может помочь уменьшить размер сообщения. Это может быть особенно полезно при отправке больших сообщений или при ограниченной пропускной способности или ограничениях по хранилищу. В этой связи библиотека предоставляет параметр сжатия, включенный в следующие методы:

- [MapiMessageItemBase.setBodyContent(String content, /*BodyContentType*/int contentType, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyContent-java.lang.String-int-boolean-) - Устанавливает содержимое тела.
- [MapiMessageItemBase.setBodyRtf(String content, boolean compression)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyRtf-java.lang.String-boolean-) - Получает или устанавливает текст сообщения в формате RTF.

Ниже приведённый фрагмент кода демонстрирует, как использовать сжатие RTF при установке тела MAPI-сообщения:

```java
MapiMessage msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// установите html тело и сохраните его сжатым
// это уменьшит размер сообщения
msg.setBodyContent(htmlBody, BodyContentType.Html, true);
```
## **Создание PersonalStorage на основе потока SeekableByteChannel**

Aspose.Email для Java позволяет работать с файлами личного хранилища (PST) с использованием java.nio.channels. Это позволяет вам создать экземпляр PersonalStorage с помощью потока SeekableByteChannel. Следующий фрагмент кода демонстрирует, как создать экземпляр PersonalStorage на основе потока FileChannel, добавить подкаталог с именем "messageFolder" в корневую папку и импортировать сообщения из файлов в директории "messageFolder": 

```cs
try (RandomAccessFile raf = new RandomAccessFile("test.pst", "rw")) {
    FileChannel channel = raf.getChannel();
    try (PersonalStorage pst = PersonalStorage.create(channel, FileFormatVersion.Unicode)) {
        FolderInfo messageFolder = pst.getRootFolder().addSubFolder("messageFolder");

        for (File f : new File("messageFolder").listFiles()) {
            messageFolder.addMessage(MapiMessage.load(f.getAbsolutePath()));
        }
    }
}
```


## **Изменение класса контейнера папки**

Иногда необходимо изменить класс папки. Общий пример - это когда в одну и ту же папку добавляются сообщения разных типов (встречи, сообщения и т. д.). В таких случаях необходимо изменить класс папки, чтобы все элементы внутри нее отображались корректно. Следующий фрагмент кода показывает, как изменить класс контейнера папки в PST для этой цели.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("PersonalStorage1.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("Inbox");

    folder.changeContainerClass("IPF.Note");
}
```

## **Добавление пакетных сообщений с улучшенной производительностью**

Добавление отдельных сообщений в PST подразумевает больше операций ввода-вывода с диском и может замедлить производительность. Для улучшения производительности сообщения можно добавлять в PST в пакетном режиме для минимизации операций ввода-вывода. 
Метод [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) позволяет добавлять сообщения пакетами и может быть использован в следующих сценариях. Кроме того, событие [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#MessageAdded) происходит, когда сообщение добавляется в папку.

### **Добавление сообщений из другого PST**

Чтобы добавить сообщения из другого PST, используйте метод [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) , который возвращает `Iterable<MapiMessage>`:

```java
try (PersonalStorage srcPst = PersonalStorage.fromFile("source.pst", false)) {
    try (PersonalStorage destPst = PersonalStorage.fromFile("destination.pst")) {

        // Получите папку по имени
        FolderInfo srcFolder = srcPst.getRootFolder().getSubFolder("SomeFolder");
        FolderInfo destFolder = destPst.getRootFolder().getSubFolder("SomeFolder");

        destFolder.MessageAdded.add(new MessageAddedEventHandler() {
            // Обрабатывает событие MessageAdded.
            public void invoke(Object sender, MessageAddedEventArgs e) {
                System.out.println("Добавлено: " + e.getEntryId());
            }
        });
        destFolder.addMessages(srcFolder.enumerateMapiMessages());
    }
}
```

### **Добавление сообщений из директории**

Чтобы добавить сообщения из директории, создайте метод `getMessages(String pathToDir)`, который возвращает `Iterable<MapiMessage>`:

```java
// Чтение сообщений из директории.
static Iterable<MapiMessage> getMessages (String pathToDir)
{
    return Arrays.stream(listDirectory(pathToDir, "*.msg"))
            .map(MapiMessage::load).collect(Collectors.toList());
}

try ( PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("SomeFolder");
    folder.MessageAdded.add(new MessageAddedEventHandler() {
        // Обрабатывает событие MessageAdded.
        public void invoke(Object sender, MessageAddedEventArgs e) {
            System.out.println("Добавлено: " + e.getEntryId());
        }
    });
    folder.addMessages(getMessages("MessageDirectory"));
}
```