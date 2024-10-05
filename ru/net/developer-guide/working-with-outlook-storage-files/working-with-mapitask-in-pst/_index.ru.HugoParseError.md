---
title: Работа с MapiTask в PST
type: docs
weight: 60
url: /net/working-with-mapitask-in-pst/
---


## **Добавление MapiTask в PST**

Статья [Создание нового PST-файла и добавление подкаталогов](https://docs.aspose.com/email/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) показывает, как создать PST-файл и добавить к нему подкаталог. С помощью Aspose.Email вы можете добавить [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) в подкаталог Задач PST-файла, который вы создали или загрузили. Ниже приведены шаги по добавлению MapiTask в PST:

1. Создайте объект [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).
2. Установите свойства [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) с помощью конструктора и различных методов.
3. Создайте PST с помощью метода [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Создайте предопределенную папку (Задачи) в корне PST-файла, получив доступ к корневой папке, а затем вызвав метод [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

Следующий фрагмент кода показывает, как создать [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) и затем добавить его в папку задач нового PST-файла.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cs" >}}