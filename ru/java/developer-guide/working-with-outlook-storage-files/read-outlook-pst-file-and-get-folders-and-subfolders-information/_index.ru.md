---
title: "Прочитайте файл Outlook PST и получите информацию о папках и подпапках"
url: /ru/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

{{% alert color="primary" %}}

Aspose.Email для Java позволяет читать файлы Microsoft Outlook PST. Вы можете загрузить файл PST с диска или в потоковом режиме в экземпляр [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) класс и получите информацию о его содержимом, например о папках, подпапках и сообщениях.

{{% /alert %}}

## **Загрузите файл PST**

Файл Outlook PST можно загрузить в экземпляр [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) класс. Ниже приведен фрагмент кода для загрузки файла PST:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-LoadAPSTFile.java" >}}

## **Отображение информации о папках**

После загрузки файла PST в [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) класс, вы можете получить информацию о отображаемом имени файла, корневой папке, подпапках и количестве сообщений. В следующем фрагменте кода отображается имя файла PST, папки и количество сообщений в папках:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-DisplayFolderAndMessageInformationForPSTFile.java" >}}

## **Получайте только определенные пользователем папки**

Файлы PST/OST могут содержать папки, созданные пользователем. Aspose.Email предоставляет возможность доступа только к определенным пользователем папкам с помощью [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) имущество. Вы можете установить [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) недвижимость для **true** чтобы получить только определенные пользователем папки. Следующий фрагмент кода демонстрирует использование [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/java/com.aspose.email/personalstoragequerybuilder/#getOnlyFoldersCreatedByUser--) для получения определенных пользователем папок.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-GetFoldersCreatedByUserOnly-1.java" >}}

## **Проверка того, находится ли папка в предопределенной папке**

При открытии и проверке папок в файле PST (Personal Storage Table) вы можете проверить, является ли каждая папка предопределенным типом папки или подпапкой предопределенного типа, и получить информацию о каждой папке.

The [FolderInfo.get Предопределенный тип (логическое значение getFortoLevelParent)](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getPredefinedType-boolean-) метод используется для проверки того, взята ли папка из [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/).

Если параметр getFortopLevelParent имеет значение true, метод возвращает значение перечисления StandardipMFolder для родительской папки верхнего уровня. Это определяет, является ли текущая папка подпапкой предопределенной папки. Если параметр getFortopLevelParent имеет значение false, он возвращает значение перечисления StandardipMFolder для текущей папки.

```java
String fileName = "my.pst";

try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    checkFolders(pst.getRootFolder().getSubFolders());
}

private void checkFolders(FolderInfoCollection folders) {
    for (FolderInfo folder : folders) {
        System.out.println("Display Name: " + folder.getDisplayName());

        // Determines whether the current folder is a predefined folder
        int folderType = folder.getPredefinedType(false);
        String answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Yes, " + folderType;
        System.out.println("Is StandardIpmFolder?: " + answer);

        // Determines whether the current folder is a subfolder of a predefined folder
        if (folderType == StandardIpmFolder.Unspecified) {
            folderType = folder.getPredefinedType(true);
            answer = folderType == StandardIpmFolder.Unspecified ? "No" : "Yes, " + folderType;
            System.out.println("Is subfolder from StandardIpmFolder parent?: " + answer);
        }

        System.out.println();

        checkFolders(folder.getSubFolders());
    }
}
```
## **Получите или добавьте стандартную папку RSS-каналов в файл PST**

Aspose.Email позволяет получить ссылку на предопределенную папку, в которой хранятся RSS-каналы. Это может быть полезно, если вы хотите программно получать доступ к RSS-каналам, хранящимся в файле Outlook PST, и управлять ими. Присвойте значение RSS-каналов [StandardIpmFolder](https://reference.aspose.com/email/java/com.aspose.email/standardipmfolder/) enum.

В следующем примере кода показано, как получить папку RSS Feeds:

```java
try (PersonalStorage pst = PersonalStorage.fromFile("my.pst", false)) {
    FolderInfo rssFolder = pst.getPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```
А в приведенном ниже примере кода показано, как добавить папку RSS Feeds:

```java
try (PersonalStorage pst = PersonalStorage.create("my.pst", FileFormatVersion.Unicode)) {
    FolderInfo rssFolder = pst.createPredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Разбор папок с возможностью поиска**

PST/OST может содержать папки с возможностью поиска в дополнение к папкам обычного типа. Aspose.Email предоставляет [FolderKind](https://reference.aspose.com/email/java/com.aspose.email/folderkind/) перечислитель для указания сообщений из таких папок поиска с помощью [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--) and [GetSubFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--) methods.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-ParseSearchableFolders.java" >}}

## **Извлечение информации о родительской папке из MessageInfo**

В следующем фрагменте кода показано, как получить информацию о родительской папке из [MessageInfo](https://reference.aspose.com/email/java/com.aspose.email/messageinfo/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ReadOutlookPSTFile-RetrieParentFolderInformationFromMessageInfo.java" >}}

## **API для обхода файлов PST**

API обхода позволяет извлекать все элементы PST, насколько это возможно, без исключений, даже если некоторые данные исходного файла повреждены.
Следующие шаги показывают, как использовать этот API.

Use [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) конструктор и [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) метод вместо метода FromFile.

Конструктор позволяет определить метод обратного вызова.

```java
try (PersonalStorage currentPst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Exception handling code.
    }
})) {
    //
}
```

Исключения для загрузки и обхода будут доступны с помощью метода обратного вызова.

The [load](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.io.InputStream-) метод возвращает значение true, если файл был успешно загружен и возможен дальнейший обход. Если файл поврежден и обход невозможен, возвращается значение false.

```java
if (currentPst.load(inputStream))
```

Это позволяет открывать и перемещать даже поврежденные файлы PST, не выбрасывая исключений. Как исключения, так и поврежденные элементы будут обрабатываться методом обратного вызова.

```java
try (PersonalStorage pst = new PersonalStorage(new TraversalExceptionsCallback() {
    public void invoke(TraversalAsposeException exception, String itemId) {
        // Exception handling code.
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
