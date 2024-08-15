---
title: "Работа с MapiTask в PST"
url: /ru/python-net/working-with-mapitask-in-pst/
weight: 90
type: docs
---


## **Добавление MapiTask в PST**
В статье «Создание нового файла PST и добавление подпапок» показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiTask в подпапку Tasks созданного или загруженного вами PST-файла. Ниже приведены шаги по добавлению MapiTask в PST:

1. Создайте объект MapiTask.
1. Задайте свойства MapiTask с помощью конструктора и различных методов.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предварительно определенную папку (Tasks) в корне файла PST, открыв корневую папку и вызвав метод addMapiMessageItem ().

В следующем фрагменте кода показано, как создать MapiTask, а затем добавить его в папку задач вновь созданного файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiTaskToPST-AddMapiTaskToPST.py" >}}
