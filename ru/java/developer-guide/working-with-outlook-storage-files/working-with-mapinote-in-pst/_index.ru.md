---
title: "Работа с MapiNote в PST"
url: /ru/java/working-with-mapinote-in-pst/
weight: 80
type: docs
---

## **Добавление MapiNote в PST**

[Создайте новый PST, добавьте подпапки и сообщения](/email/java/create-new-pst-add-sub-folders-and-messages/) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить MapiNote в подпапку Notes созданного или загруженного вами PST-файла.

Ниже приведены шаги по добавлению MapiNote в PST:

1. Создайте шаблон MapiNote с помощью Microsoft Outlook и сохраните его как файл MSG.
1. Загрузите сохраненную заметку MSG в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) object.
1. Создайте [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) создайте объект и загрузите шаблон MSG-заметки.
1. Установите [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) свойства с использованием разных методов.
2. Создайте PST, используя [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
3. Создайте предварительно определенную папку (Notes) в корне файла PST, открыв корневую папку и вызвав [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

В приведенном ниже фрагменте кода показано, как создать [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) а затем добавьте его в папку Notes вновь созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiNoteToPST-.java" >}}
