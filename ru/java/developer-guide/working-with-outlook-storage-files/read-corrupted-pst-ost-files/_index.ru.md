---
title: "Чтение поврежденных файлов PST/OST"
url: /ru/java/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

## **Чтение поврежденных файлов PST/OST**

Иногда из-за некоторых проблем чтение PST/OST может оказаться невозможным. Например, некоторые блоки данных могут быть повреждены. В таких случаях обычно возникают исключения при вызове [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--), [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessages--), [GetContents](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--), [GetSubfolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--)и т. д. методы. Но отдельные сообщения или папки могут остаться неповрежденными в хранилище.

Пользователи Aspose.Email могут найти идентификаторы товаров в иерархическом порядке. Кроме того, вы можете извлекать элементы по идентификаторам. Для этого библиотека предлагает следующие методы:

- [Персональное хранилище. Поиск сообщений (идентификатор родительской записи в строке)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findMessages-java.lang.String-) - находит идентификаторы сообщений для папки.
- [Персональное хранилище. Найдите подпапки (идентификатор родительской записи в строке)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findSubfolders-java.lang.String-) - находит идентификаторы подпапок для папки.

**Note**, что, несмотря на преимущества, существуют поврежденные хранилища, которые невозможно прочитать даже с помощью этих методов.

Следующий фрагмент кода демонстрирует использование этих методов для чтения поврежденных файлов PST/OST:

```java
try (PersonalStorage pst = PersonalStorage.fromFile(fileName)) {
    exploreCorruptedPst(pst, pst.getRootFolder().getEntryIdString());
}

public static void exploreCorruptedPst(PersonalStorage pst, String rootFolderId) {
    Iterable<String> messageIdList = pst.findMessages(rootFolderId);

    for (String messageId : messageIdList) {
        try {
            MapiMessage msg = pst.extractMessage(messageId);
            System.out.println("- " + msg.getSubject());
        } catch (Exception e) {
            System.out.println("Message reading error. Entry id: " + messageId);
        }
    }

    Iterable<String> folderIdList = pst.findSubfolders(rootFolderId);

    for (String subFolderId : folderIdList) {
        if (subFolderId != rootFolderId) {
            try {
                FolderInfo subfolder = pst.getFolderById(subFolderId);
                System.out.println(subfolder.getDisplayName());
            } catch (Exception e) {
                System.out.println("Message reading error. Entry id: " + subFolderId);
            }

            exploreCorruptedPst(pst, subFolderId);
        }
    }
}
```
## **Извлечение элементов PST из поврежденных файлов**

API обхода позволяет извлекать все элементы PST, насколько это возможно, без исключений, даже если некоторые данные исходного файла повреждены.

Используйте [Персональное хранилище (обратный звонок по обходу исключений)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#PersonalStorage-com.aspose.email.TraversalExceptionsCallback-) конструктор и [load (строковое имя файла)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.lang.String-) метод вместо [fromFile](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-) method.

Конструктор позволяет определить метод обратного вызова.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    @Override
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Exception handling  code. */
    }
};

try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) { }
```
Исключения для загрузки и обхода будут доступны с помощью метода обратного вызова.

Метод load возвращает значение true, если файл был успешно загружен и возможен дальнейший обход. Если файл поврежден и обход невозможен, возвращается значение false.

```java
if (currentPst.load(inputStream))
```
В следующем примере кода показано, как внедрить API обхода файлов PST в проект:

```java
public static void main(String[] args) {
    TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
        @Override
        public void invoke(TraversalAsposeException exception, String itemId) {
            /* Exception handling  code. */
        }
    };

    try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) {
        if (pst.load("test.pst")) {
            getAllMessages(pst, pst.getRootFolder());
        }
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