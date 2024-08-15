---
title: "Прочитайте файл Outlook для Mac OLM и получите информацию о папках и подпапках"
url: /ru/java/read-outlook-for-mac-olm-file-and-get-folders-and-subfolders-information/
weight: 130
type: docs
---

{{% alert color="primary" %}}

Aspose.Email для Java позволяет читать файлы Outlook для Mac OLM. Вы можете загрузить файл OLM с диска в экземпляр [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) класс и получите информацию о его содержимом, например о папках, подпапках и сообщениях.

{{% /alert %}}

## **Откройте файлы формата OLM**

Файлы формата OLM можно открыть двумя способами:

- с помощью конструктора
- используя статический метод fromFile

Между этими методами существуют различия в поведении. См. раздел ниже.

### **Открывайте файлы с помощью конструктора**

Чтобы открыть файл, вызовите конструктор [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) класс и передайте ему полное имя файла или поток в качестве аргумента:

```java
OlmStorage olm = new OlmStorage("fileName");
```

### **Открывайте файлы статическим методом FromFile**

Чтобы открыть файл, используйте статический метод [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) и передайте ему полное имя файла в качестве аргумента:

```java
OlmStorage olm = OlmStorage.fromFile("fileName");
```
### **Открывайте файлы статическим методом FromStream**

Чтобы открыть файл статическим методом [fromStream](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromStream-java.io.InputStream-), передайте ему имя потока в качестве аргумента:


## **Прочтите файл OLM**

В следующем фрагменте кода показано, как загрузить файл OLM и получить его содержимое.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-LoadAndReadOLMFile.java" >}}

## **Получите папки**

Чтобы извлечь папки из файла OLM (Outlook для Mac), загрузите его вместе с [OlmStorage](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/) сначала займитесь классом, а затем используйте один из следующих методов в зависимости от ваших потребностей:

- [GetFolder (строковое имя, логическое значение IgnoreCase)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolder-java.lang.String-boolean-) - Получает папку по имени.
- [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) - Получает иерархию папок/коллекцию папок.
- [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) - Получает иерархию папок.

В приведенном ниже примере кода показано, как получить папку из файла OLM:

```java
// Get the folder by name
OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

} finally {

    olm.dispose();

}
```
При использовании [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) метод открытия файла OLM, [getFolderHierarchy()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolderHierarchy--) вернет нуль. В этом случае позвоните [getFolders()](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#getFolders--) метод явного получения списка каталогов в файле OLM.


### **Получить путь к папке**

Вы также можете получить путь к папкам в файле OML. Aspose.Email предоставляет [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) свойство, возвращающее путь к папке. Следующий фрагмент кода демонстрирует использование [OlmFolder.Path](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getPath--) свойство для получения путей к папкам в файле OML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-GetFolderPathInOLM-1.java" >}}

### **Подсчитайте количество элементов в папке**

Можно также подсчитать количество элементов в папке. Aspose.Email предоставляет [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) свойство, возвращающее количество элементов в папке. Следующий фрагмент кода демонстрирует использование [OlmFolder.MessageCount](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/#getMessageCount--) свойство для получения количества элементов в папках файла OML.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-olm-CountItemsInOLMFolder-1.java" >}}

## **Перечислить сообщения из заданной папки**

Aspose.Email предоставляет API для работы с хранилищами OLM и извлечения сообщений из заданной папки. [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) and [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) классы представляют собой краткую информацию о папке и сообщении в хранилище соответственно. [OlmFolder](https://reference.aspose.com/email/java/com.aspose.email/olmfolder/) класс предоставляет следующие методы:

- **OlmFolder.getSubFolder**(строка subfolderName, логическое значение ignoreCase) — получает подпапку по имени.

- **OlmFolder.enumerateMapiMessages()** - Открывает перечислитель, поддерживающий итерацию MapiMessages в текущей папке.

- **OlmFolder.enumerateMessages()** - Открывает перечислитель, поддерживающий итерацию OlmMessageInfo в текущей папке.

- **OlmFolder.enumerateMessages**(int startIndex, int count) — предоставляет перечислитель, поддерживающий итерацию OlmMessageInfo в заданном диапазоне.

- **OlmFolder.enumerateMessages**(запрос MailQuery) — предоставляет перечислитель, поддерживающий итерацию OlmMessageInfo по критериям поиска.

Приведенные ниже примеры кода продемонстрируют использование этих методов:

```java
 // Enumerates all messages in a given folder

OlmStorage olm = OlmStorage.fromFile("fileName");

try {

    OlmFolder inbox = olm.getFolder("inbox", true);

   for (OlmMessageInfo messageInfo : inbox.enumerateMessages()) {

        System.out.println(messageInfo.getSubject());

   }

} finally {

    olm.dispose();

}

// Enumerates a range of messages in a given folder

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

// Enumerates messages by search criteria

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

// Enumerates all messages and the extraction of some of them

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

Иногда требуется извлечь выбранные сообщения по идентификаторам. Например, ваше приложение хранит идентификаторы в базе данных и извлекает сообщение по запросу. Это эффективный способ избежать необходимости каждый раз просматривать все хранилище в поисках нужного сообщения для извлечения. Чтобы реализовать эту функцию для файлов OLM, Aspose.Email предоставляет следующие методы и классы:

- [EntryId](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getEntryId--) собственность [OlmMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/) class - Получает идентификатор записи сообщения.
- overloaded [Извлечь сообщение MAPI (идентификатор строки)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#extractMapiMessage-java.lang.String-) метод [OlmStorage]() class - получает сообщение от OLM.

В приведенном ниже примере кода показано, как извлекать сообщения из OLM по идентификаторам:

```java
for (OlmMessageInfo msgInfo : olmFolder.enumerateMessages()) {
    MapiMessage msg = storage.extractMapiMessage(msgInfo.getEntryId());
}
```
**Note:** Идентификатор сообщения уникален в файле хранилища. Идентификаторы создаются Aspose.Email и не могут использоваться в других сторонних библиотеках или приложениях для обработки OLM.


## **Извлеките элементы OLM из поврежденных файлов**

Aspose.Email предоставляет API обхода, который позволяет извлекать все элементы OLM, насколько это возможно, без исключения исключений, даже если некоторые данные исходного файла повреждены.

Используйте [Хранилище OLM (обратный вызов по обходу исключений)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#OlmStorage-com.aspose.email.TraversalExceptionsCallback-) конструктор и [load (строковое имя файла)](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#load-java.lang.String-) метод вместо [fromFile](https://reference.aspose.com/email/java/com.aspose.email/olmstorage/#fromFile-java.lang.String-) method.

Конструктор позволяет определить метод обратного вызова.

```java
OlmStorage olm = new OlmStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
});
```
Исключения для загрузки и обхода будут доступны с помощью метода обратного вызова.

Метод load возвращает значение true, если файл был успешно загружен и возможен дальнейший обход. Если файл поврежден и обход невозможен, возвращается значение false.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
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
## **Получить дату изменения сообщения**

The [OlmMessageInfo.getModifiedDate](https://reference.aspose.com/email/java/com.aspose.email/olmmessageinfo/#getModifiedDate--) свойство позволяет получить дату изменения сообщения.

```java
for (OlmMessageInfo messageInfo : inboxFolder.enumerateMessages()) {
    Date modifiedDate = messageInfo.getModifiedDate();
}
```