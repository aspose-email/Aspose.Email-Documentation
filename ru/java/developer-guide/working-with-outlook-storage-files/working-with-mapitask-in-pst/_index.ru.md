---
title: "Работа с MapiTask в PST"
url: /ru/java/working-with-mapitask-in-pst/
weight: 60
type: docs
---

## **Добавление MapiTask в PST**

[Создайте новый PST, добавьте подпапки и сообщения](/email/java/create-new-pst-add-sub-folders-and-messages/) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить MapiTask в подпапку Tasks созданного или загруженного файла PST.

Ниже приведены шаги по добавлению MapiTask в PST:

1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) object.
1. Установите [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) свойства с использованием конструктора и различных методов.
1. Создайте PST, используя [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
1. Создайте предварительно определенную папку (Задачи) в корне файла PST, открыв корневую папку и вызвав [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

В приведенном ниже фрагменте кода показано, как создать [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) а затем добавьте его в папку Tasks вновь созданного файла PST.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiTaskToPST-.java" >}}
