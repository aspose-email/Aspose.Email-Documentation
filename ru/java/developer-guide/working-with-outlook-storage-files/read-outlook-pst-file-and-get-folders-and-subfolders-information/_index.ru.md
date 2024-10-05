---
title: "Чтение файла Outlook PST и получение информации о папках и подпапках"
url: /ru/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email для Java позволяет вам читать файлы PST Microsoft Outlook. Вы можете загрузить файл PST с диска или потока в экземпляр класса [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) и получить информацию о его содержимом, например, папках, подпапках и сообщениях.

{{% /alert %}} 

## **Загрузка файла PST**

Файл PST Outlook можно загрузить в экземпляр класса [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/). Ниже приведён фрагмент кода для загрузки файла PST:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-LoadAPSTFile.java" >}}

## **Отображение информации о папках**

После загрузки файла PST в класс [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) вы можете получить информацию о отображаемом имени файла, корневой папке, количестве подпапок и сообщениях. Следующий фрагмент кода отображает имя файла PST, папки и количество сообщений в папках:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-DisplayFolderAndMessageInformationForPSTFile.java" >}}

## **Получить только пользовательские папки**

Файлы PST/OST могут содержать папки, созданные пользователем. Aspose.Email предоставляет возможность получать только пользовательские папки, используя свойство [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--). Вы можете установить свойство [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) в **true**, чтобы получить только пользовательские папки. Следующий фрагмент кода демонстрирует использование [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) для получения пользовательских папок.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-GetFoldersCreatedByUserOnly-1.java" >}}

## **Проверка, является ли папка предопределённым типом папки**

При открытии и проверке папок внутри файла PST (Личная таблица хранения) вы можете проверить, является ли каждая папка предопределённым типом папки или подпапкой предопределённого типа папки, и получить информацию о каждой папке.

Метод [FolderInfo.getPredefinedType(boolean getForTopLevelParent)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getPredefinedType-boolean-) используется для проверки, является ли папка из [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/). 

Если параметр 'getForTopLevelParent' равен true, метод возвращает значение перечисления StandardIpmFolder для родительской папки верхнего уровня. Это определяет, является ли текущая папка подпапкой предопределённой папки. Если параметр 'getForTopLevelParent' равен false, он возвращает значение перечисления StandardIpmFolder для текущей папки.

```java
String fileName = "my.pst";

try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    checkFolders(pst.getRootFolder().getSubFolders());
}

private void checkFolders(FolderInfoCollection folders) {
    for (FolderInfo folder : folders) {
        System.out.println("Отображаемое имя: " + folder.getDisplayName());

        // Определяет, является ли текущая папка предопределённым типом
        int folderType = folder.getPredefinedType(false);
        String answer = folderType == StandardIpmFolder.Unspecified ? "Нет" : "Да, " + folderType;
        System.out.println("Является ли StandardIpmFolder?: " + answer);

        // Определяет, является ли текущая папка подпапкой предопределённой папки
        if (folderType == StandardIpmFolder.Unspecified) {
            folderType = folder.getPredefinedType(true);
            answer = folderType == StandardIpmFolder.Unspecified ? "Нет" : "Да, " + folderType;
            System.out.println("Является ли подпапкой от StandardIpmFolder родителя?: " + answer);
        }

        System.out.println();

        checkFolders(folder.getSubFolders());
    }
}
```
## **Получить или добавить стандартную папку RSS-каналов в файл PST**

Aspose.Email позволяет получать ссылку на предопределённую папку, содержащую RSS-каналы. Это может быть полезно, если вы хотите программно получить доступ и манипулировать RSS-каналами, хранящимися в файле PST Outlook. Установите значение RssFeeds для перечисления [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/).

Следующий пример кода показывает, как получить папку RSS-каналов:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    FolderInfo rssFolder = pst.getPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```
А следующий пример кода демонстрирует, как добавить папку RSS-каналов:

```java
try (PersonalStorage pst = PersonalStorage.create("my.pst", FileFormatVersion.Unicode)) {
    FolderInfo rssFolder = pst.createPredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Парсить searchable папки**

Файлы PST/OST могут содержать searchable папки в дополнение к нормальным типам папок. Aspose.Email предоставляет перечислитель [FolderKind](https://reference.aspose.com/email/java/com.aspose.email/folderkind/) для указания сообщений из таких searchable папок с помощью методов [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--) и [GetSubFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-ParseSearchableFolders.java" >}}

## **Получить информацию о родительской папке из MessageInfo**

Следующий фрагмент кода показывает, как получить информацию о родительской папке из [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-RetrieParentFolderInformationFromMessageInfo.java" >}}

## **API обхода файла PST**

API обхода позволяет извлекать все элементы PST насколько это возможно, не вызывая исключений, даже если некоторые данные оригинального файла повреждены.
Следующие шаги показывают, как использовать этот API.

Используйте конструктор [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) и метод [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) вместо метода fromFile.

Конструктор позволяет определить метод обратного вызова.

```java
try (PersonalStorage currentPst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Код обработки исключений.
    }
})) {
    //
}
```

Исключения при загрузке и обходе будут доступны через метод обратного вызова.

Метод [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) возвращает 'true', если файл был успешно загружен и дальнейший обход возможен. Если файл повреждён и дальнейший обход невозможен, возвращается 'false'.

```java
if (currentPst.load(inputStream))
```

Это позволяет открывать и обходить даже повреждённые файлы PST, не вызывая исключений. Как исключения, так и повреждённые элементы будут обрабатываться методом обратного вызова.

```java
try (PersonalStorage pst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Код обработки исключений.
    }
})) {
    if (pst.load("test.pst")) {
        getAllMessages(pst, pst.getRootFolder());
    }
}

private static void getAllMessages(PersonalStorage pst, FolderInfo folder) {
    for (String messageEntryId : folder.enumerateMessagesEntryId()) {
        MapiMessage message = pst.extractMessage(messageEntryId);
    }
    for (FolderInfo subFolder : folder.getSubFolders()) {
        getAllMessages(pst, subFolder);
    }
}
```