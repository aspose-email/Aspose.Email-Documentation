---
title: "Чтение поврежденных PST/OST файлов"
url: /ru/java/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

## **Чтение поврежденных PST/OST файлов**

Иногда чтение PST/OST может быть невозможно из-за некоторых проблем. Например, некоторые блоки данных могут быть повреждены. В таких случаях обычно возникают исключения при вызове методов [EnumerateFolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateFolders--), [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#enumerateMessages--), [GetContents](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getContents--), [GetSubfolders](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#getSubFolders--) и т.д. Однако отдельные сообщения или папки могут остаться неповрежденными в хранилище.

Пользователи Aspose.Email могут находить идентификаторы элементов иерархическим образом. Далее вы можете извлекать элементы по идентификаторам. Для этой цели библиотека предлагает следующие методы:

- [PersonalStorage.findMessages(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findMessages-java.lang.String-) - находит идентификаторы сообщений для папки.
- [PersonalStorage.findSubfolders(String parentEntryId)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#findSubfolders-java.lang.String-) - находит идентификаторы подпапок для папки.

**Примечание**, что несмотря на преимущества, существуют поврежденные хранилища, которые невозможно прочитать даже с использованием этих методов.

Следующий фрагмент кода демонстрирует использование этих методов для чтения поврежденных PST/OST файлов:

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
            System.out.println("Ошибка чтения сообщения. Идентификатор записи: " + messageId);
        }
    }

    Iterable<String> folderIdList = pst.findSubfolders(rootFolderId);

    for (String subFolderId : folderIdList) {
        if (subFolderId != rootFolderId) {
            try {
                FolderInfo subfolder = pst.getFolderById(subFolderId);
                System.out.println(subfolder.getDisplayName());
            } catch (Exception e) {
                System.out.println("Ошибка чтения сообщения. Идентификатор записи: " + subFolderId);
            }

            exploreCorruptedPst(pst, subFolderId);
        }
    }
}
```
## **Извлечение элементов PST из поврежденных файлов**

API обхода позволяет извлекать все элементы PST по возможности, без выброса исключений, даже если некоторые данные оригинального файла повреждены.

Используйте конструктор [PersonalStorage(TraversalExceptionsCallback callback)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#PersonalStorage-com.aspose.email.TraversalExceptionsCallback-) и метод [load(String fileName)](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#load-java.lang.String-) вместо метода [fromFile](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-).

Конструктор позволяет задавать метод обратного вызова.

```java
TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
    @Override
    public void invoke(TraversalAsposeException exception, String itemId) {
        /* Код обработки исключений. */
    }
};

try (PersonalStorage pst = new PersonalStorage(exceptionsCallback)) { }
```
Исключения при загрузке и обходе будут доступны через метод обратного вызова.

Метод load возвращает 'true', если файл был успешно загружен и дальнейший обход возможен. Если файл поврежден и обход невозможен, возвращается 'false'.

```java
if (currentPst.load(inputStream))
```
Следующий пример кода показывает, как интегрировать API обхода файла PST в проект:

```java
public static void main(String[] args) {
    TraversalExceptionsCallback exceptionsCallback = new TraversalExceptionsCallback() {
        @Override
        public void invoke(TraversalAsposeException exception, String itemId) {
            /* Код обработки исключений. */
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