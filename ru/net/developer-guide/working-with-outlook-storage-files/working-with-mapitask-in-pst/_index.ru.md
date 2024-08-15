---
title: "Работа с MapiTask в PST"
url: /ru/net/working-with-mapitask-in-pst/
weight: 60
type: docs
---


## **Добавление MapiTask в PST**

The [Создайте новый файл PST и добавьте подпапки](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) В статье показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) в подпапку Tasks созданного или загруженного файла PST. Ниже приведены шаги по добавлению MapiTask в PST:

1. Создайте [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) object.
2. Установите [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) свойства с использованием конструктора и различных методов.
3. Создайте PST, используя [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Создайте предварительно определенную папку (Задачи) в корне файла PST, открыв корневую папку и вызвав [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

В следующем фрагменте кода показано, как создать [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) а затем добавьте его в папку задач вновь созданного файла PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cs" >}}
