---
title: Работа с MapiTask в PST
type: docs
weight: 60
url: /java/working-with-mapitask-in-pst/
---

## **Добавление MapiTask в PST**

[Создание нового PST, добавление подпапок и сообщений](/email/java/create-new-pst-add-sub-folders-and-messages/) показало, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить MapiTask в подпапку Задачи файла PST, который вы создали или загрузили.

Ниже приведены шаги для добавления MapiTask в PST:

1. Создайте объект [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Установите свойства [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) с использованием конструктора и различных методов.
1. Создайте PST с помощью метода [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
1. Создайте предопределенную папку (Задачи) в корне файла PST, получив доступ к корневой папке и затем вызвав метод [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

Ниже приведен фрагмент кода, который показывает, как создать [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) и затем добавить его в папку Задачи только что созданного файла PST.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiTaskToPST-.java" >}}