---
title: Работа с MapiNote в PST
type: docs
weight: 80
url: /java/working-with-mapinote-in-pst/
---

## **Добавление MapiNote в PST**

[Создание нового PST, добавление подкаталогов и сообщений](/email/java/create-new-pst-add-sub-folders-and-messages/) показало, как создать файл PST и добавить к нему подкаталог. С помощью Aspose.Email вы можете добавить MapiNote в подкаталог Заметки файла PST, который вы создали или загрузили.

Ниже приведены шаги для добавления MapiNote в PST:

1. Создайте шаблон MapiNote с помощью Microsoft Outlook и сохраните его как файл MSG.
1. Загрузите сохранённую заметку MSG в объект [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
1. Создайте объект [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) и загрузите в него шаблон заметки MSG.
1. Установите свойства [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) с помощью различных методов.
2. Создайте PST с помощью метода [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
3. Создайте предопределённую папку (Заметки) в корне файла PST, получив доступ к корневой папке и затем вызвав метод [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

Ниже приведён фрагмент кода, который показывает, как создать [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) и затем добавить его в папку Заметки нового файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiNoteToPST-.java" >}}