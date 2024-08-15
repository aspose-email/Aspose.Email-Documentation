---
title: "Создайте новый PST, добавьте подпапки и сообщения"
url: /ru/java/create-new-pst-add-sub-folders-and-messages/
weight: 10
type: docs
---


Помимо анализа существующего файла PST, Aspose.Email предоставляет средства для создания файла PST с нуля. В этой статье показано, как создать файл Outlook PST и добавить в него подпапку.

1. [Создание нового файла PST](#creating-a-new-pst-file-and-add-subfolders).
1. [Изменение класса Container папки](#changing-a-folders-container-class).
1. [Добавляйте массовые сообщения с улучшенной производительностью](#add-bulk-messages-with-improved-performance)

Используйте [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) класс для создания файла PST в каком-то месте на локальном диске. Чтобы создать файл PST с нуля, выполните следующие действия:

1. Создайте PST, используя [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
1. Добавьте подпапку в корень файла PST, открыв корневую папку и вызвав [addSubFolder()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addSubFolder-java.lang.String-) method.

В следующем фрагменте кода показано, как создать файл PST и добавить подпапку под названием «Входящие».

```java
// Create new PST
try (PersonalStorage pst = PersonalStorage.create(path, FileFormatVersion.Unicode)) {
    // Add new folder "Test"
    pst.getRootFolder().addSubFolder("Inbox");
}
```
## **Создайте PST размером более 2 ГБ с помощью OutputStream**

Пользователи Aspose.Email могут оптимизировать внутренний кэш PST с помощью конструктора PersonalStorage:

- **blockSize** - Оптимальный размер блока для расширения буфера кэша (в байтах).

```java
PersonalStorage create(OutputStream stream, int blockSize, /*FileFormatVersion*/int version)
```
## **Уменьшите размер сообщения и размер созданного файла PST**

Aspose.Email предлагает возможность сжатия основного содержимого, что может помочь уменьшить размер сообщения. Это может быть особенно полезно при отправке больших сообщений или при работе с ограниченной полосой пропускания или ограничениями хранилища. Для этого в библиотеке предусмотрен параметр сжатия, включенный в следующие методы:

- [mapiMessageItembase.setBodyContent (содержимое строки,/*BodyContentType*/int (тип содержимого, логическое сжатие)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyContent-java.lang.String-int-boolean-) - Устанавливает содержимое тела.
- [MapiMessageItembase.setBodyrtf (строковое содержимое, логическое сжатие)](https://reference.aspose.com/email/java/com.aspose.email/mapimessageitembase/#setBodyRtf-java.lang.String-boolean-) - Получает или задает текст сообщения в формате RTF.

В приведенном ниже фрагменте кода показано, как использовать сжатие RTF при настройке тела сообщения MAPI:

```java
MapiMessage msg = new MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
// set the html body and keep it compressed
// this will reduce the message size
msg.setBodyContent(htmlBody, BodyContentType.Html, true);
```
## **Создайте персональное хранилище на основе SeekableByteChannel Stream**

Aspose.Email для Java позволяет работать с файлами персонального хранилища (PST) с помощью java.nio.channels. Это позволяет создать экземпляр PersonalStorage с помощью потока SeekableByteChannel. В следующем фрагменте кода показано, как создать экземпляр PersonalStorage на основе потока FileChannel, добавить подпапку с именем «MessageFolder» в корневую папку и импортировать сообщения из файлов в каталоге «MessageFolder»:


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


## **Изменение класса контейнера папок**

Иногда необходимо изменить класс папки. Типичный пример: сообщения разных типов (встречи, сообщения и т. д.) добавляются в одну и ту же папку. В таких случаях класс папки необходимо изменить, чтобы все элементы в папке отображались корректно. В следующем фрагменте кода показано, как изменить класс контейнера папки в PST для этой цели.

```java
try (PersonalStorage pst = PersonalStorage.fromFile("PersonalStorage1.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("Inbox");

    folder.changeContainerClass("IPF.Note");
}
```

## **Добавляйте массовые сообщения с улучшенной производительностью**

Добавление отдельных сообщений в PST подразумевает большее количество операций ввода-вывода на диск и может снизить производительность. Для повышения производительности сообщения можно добавлять в PST в массовом режиме, чтобы минимизировать операции ввода-вывода. [addMessages(Iterable<MapiMessage> messages)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMessages-java.lang.Iterable-com.aspose.email.MapiMessage--) Метод позволяет массово добавлять сообщения и может использоваться в следующих сценариях. Кроме того, [MessageAdded](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#MessageAdded) событие происходит при добавлении сообщения в папку.

### **Добавить сообщения из другого PST**

Чтобы добавить сообщения из другого PST, используйте [FolderInfo.enumerateMapiMessages()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMapiMessages--) метод, который возвращает `Iterable<MapiMessage>`:

```java
try (PersonalStorage srcPst = PersonalStorage.fromFile("source.pst", false)) {
    try (PersonalStorage destPst = PersonalStorage.fromFile("destination.pst")) {

        // Get the folder by name
        FolderInfo srcFolder = srcPst.getRootFolder().getSubFolder("SomeFolder");
        FolderInfo destFolder = destPst.getRootFolder().getSubFolder("SomeFolder");

        destFolder.MessageAdded.add(new MessageAddedEventHandler() {
            // Handles the MessageAdded event.
            public void invoke(Object sender, MessageAddedEventArgs e) {
                System.out.println("Added: " + e.getEntryId());
            }
        });
        destFolder.addMessages(srcFolder.enumerateMapiMessages());
    }
}
```

### **Добавить сообщения из каталога**

Чтобы добавить сообщения из каталога, создайте `getMessages(String pathToDir)` метод, который возвращает `Iterable<MapiMessage>`:

```java
// Read messages from directory.
static Iterable<MapiMessage> getMessages (String pathToDir)
{
    return Arrays.stream(listDirectory(pathToDir, "*.msg"))
            .map(MapiMessage::load).collect(Collectors.toList());
}

try ( PersonalStorage pst = PersonalStorage.fromFile("storage.pst")) {
    FolderInfo folder = pst.getRootFolder().getSubFolder("SomeFolder");
    folder.MessageAdded.add(new MessageAddedEventHandler() {
        // Handles the MessageAdded event.
        public void invoke(Object sender, MessageAddedEventArgs e) {
            System.out.println("Added: " + e.getEntryId());
        }
    });
    folder.addMessages(getMessages("MessageDirectory"));
}
```

