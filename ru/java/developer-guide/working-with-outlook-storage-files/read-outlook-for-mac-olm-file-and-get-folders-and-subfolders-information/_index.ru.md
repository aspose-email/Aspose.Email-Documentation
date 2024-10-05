---
title: "Чтение файла OLM Outlook для Mac и получение информации о папках и подпапках"
url: /ru/java/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 130
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email для Java позволяет читать файлы OLM Outlook для Mac. Вы можете загрузить файл OLM с диска в экземпляр класса [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) и получить информацию о его содержимом, например, о папках, подпапках и сообщениях.

{{% /alert %}} 

## **Открытие файлов формата OLM**

Файлы формата OLM можно открывать двумя способами:

- с использованием конструктора
- с использованием статического метода FromFile

Существуют различия в поведении между этими методами. Смотрите раздел ниже.

### **Открытие файлов с помощью конструктора**

Чтобы открыть файл, вызовите конструктор класса [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) и передайте полное имя файла или поток в качестве аргумента:

```java
OlmStorage olm = new OlmStorage("fileName");
```

### **Открытие файлов с использованием статического метода FromFile**

Чтобы открыть файл, используйте статический метод [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) и передайте полное имя файла в качестве аргумента:

```java
OlmStorage olm = OlmStorage.fromFile("fileName");
```

### **Открытие файлов с использованием статического метода FromStream**

Чтобы открыть файл, используя статический метод [fromStream](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromStream-java.io.InputStream-), передайте имя потока в качестве аргумента:


## **Чтение файла OLM**

Следующий код показывает, как загрузить файл OLM и получить его содержимое.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-LoadAndReadOLMFile.java" >}}

## **Получение папок**

Чтобы извлечь папки из файла OLM (Outlook для Mac), сначала загрузите его с помощью класса [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/), а затем используйте один из следующих методов в зависимости от ваших потребностей:

- [getFolder(String name, boolean ignoreCase)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolder-java.lang.String-boolean-) - Получает папку по имени.
- [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) - Получает иерархию папок/коллекцию папок.
- [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) - Получает иерархию папок.

Пример кода ниже покажет, как получить папку из файла OLM:

```java
// Получаем папку по имени
OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

} finally {

    olm.dispose();

}
```
При использовании метода [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) для открытия файла OLM метод [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) вернет null. В этом случае вызовите метод [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) явно, чтобы получить список каталогов в файле OLM.


### **Получение пути к папке**

Вы также можете получить путь к папке в файле OLM. Aspose.Email предоставляет свойство [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) которое возвращает путь к папке. Следующий код демонстрирует использование свойства [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) для получения путей к папкам в файле OLM.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-GetFolderPathInOLM-1.java" >}}

### **Подсчет количества элементов в папке**

Вы также можете подсчитать количество элементов в папке. Aspose.Email предоставляет свойство [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) которое возвращает количество элементов в папке. Следующий код демонстрирует использование свойства [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) для получения количества элементов в папках файла OLM.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-CountItemsInOLMFolder-1.java" >}}

## **Перечисление сообщений из заданной папки**

Aspose.Email предоставляет API для работы с хранилищами OLM и извлечения сообщений из заданной папки. Классы [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) и [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) представляют собой краткую информацию о папке и сообщении в хранилище соответственно. Класс [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) предоставляет следующие методы:

- **OlmFolder.getSubFolder**(String subfolderName, boolean ignoreCase) - Получает подпапку по имени.

- **OlmFolder.enumerateMapiMessages()** - Предоставляет перечислитель, который поддерживает итерацию MapiMessages в текущей папке.

- **OlmFolder.enumerateMessages()** - Предоставляет перечислитель, который поддерживает итерацию OlmMessageInfo в текущей папке.

- **OlmFolder.enumerateMessages**(int startIndex, int count) - Предоставляет перечислитель, который поддерживает итерацию OlmMessageInfo в заданном диапазоне.

- **OlmFolder.enumerateMessages**(MailQuery query) - Предоставляет перечислитель, который поддерживает итерацию OlmMessageInfo по критериям поиска.

Примеры кода ниже демонстрируют использование этих методов:

```java
 // Перечисляет все сообщения в заданной папке

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Перечисляет диапазон сообщений в заданной папке

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   int startIndex = 10;

   int count = 100;

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(startIndex, count)) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Перечисляет сообщения по критериям поиска

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

    MailQueryBuilder mailQueryBuilder = new MailQueryBuilder();

    mailQueryBuilder.getSubject().contains("invitation");

    mailQueryBuilder.getFrom().contains("Mark");

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages(mailQueryBuilder.getQuery())) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Перечисляет все сообщения и извлечение некоторых из них

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

       if (messageInfo.hasAttachments()) {

            MapiMessage msg = olm.extractMapiMessage(messageInfo);

       }

   }

} finally {

    olm.dispose();

}
```
## **Извлечение сообщений из OLM по идентификаторам**

Иногда требуется извлекать выбранные сообщения по идентификаторам. Например, ваше приложение хранит идентификаторы в базе данных и извлекает сообщение по запросу. Это эффективный способ избежать обхода всего хранилища каждый раз для поиска конкретного сообщения для извлечения. Для реализации этой функции для файлов OLM Aspose.Email предоставляет следующие методы и классы:

- свойство [EntryId](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getEntryId--) класса [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) - Получает идентификатор записи сообщения.
- перегруженный метод [extractMapiMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#extractMapiMessage-java.lang.String-) класса [OlmStorage]() - Получает сообщение из OLM.

Пример кода ниже демонстрирует, как извлечь сообщения из OLM по идентификаторам:

```java
for (OlmMessageInfo msgInfo : olmFolder.enumerateMessages()) {
    MapiMessage msg = storage.extractMapiMessage(msgInfo.getEntryId());
}
```
**Примечание:** Идентификатор сообщения уникален в пределах файла хранилища. Идентификаторы создаются Aspose.Email и не могут быть использованы в других сторонних библиотеках или приложениях для обработки OLM.


## **Извлечение элементов OLM из поврежденных файлов**

Aspose.Email предоставляет API обхода, который позволяет извлекать все элементы OLM, насколько это возможно, не выбрасывая исключения, даже если некоторые данные оригинального файла повреждены.

Используйте конструктор [OlmStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#OlmStorage-com.aspose.email.TraversalExceptionsCallback-) и метод [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#load-java.lang.String-) вместо метода [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-).

Конструктор позволяет определить метод обратного вызова.

```java
OlmStorage olm = new OlmStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Код обработки исключений. */
    }
});
```
Исключения загрузки и обхода будут доступны через метод обратного вызова.

Метод загрузки возвращает 'true', если файл был успешно загружен и дальнейший обход возможен. Если файл поврежден и дальнейший обход невозможен, возвращается 'false'.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Код обработки исключений. */
    }
};
try (OlmStorage olm = new OlmStorage(exceptionsCallback)) {
    if (olm.load(fileName)) {
        List<OlmFolder> folderHierarchy = olm.getFolders();
        extractItems(olm, folderHierarchy);
    }
}

private static void extractItems(OlmStorage olm, List<OlmFolder> folders) {
    for (OlmFolder folder : folders) {
        if (folder.hasMessages()) {
            System.out.println(folder);

            for (MapiMessage msg : olm.enumerateMessages(folder)) {
                System.out.println(msg.getSubject());
            }
        }

        if (folder.getSubFolders().size() > 0) {
            extractItems(olm, folder.getSubFolders());
        }
    }
}
```
## **Получение даты изменения сообщения**

Свойство [OlmMessageInfo.getModifiedDate](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getModifiedDate--) позволяет получить дату изменения сообщения.

```java
for (OlmMessageInfo messageInfo : inboxFolder.enumerateMessages()) {
    Date modifiedDate = messageInfo.getModifiedDate();
}
```