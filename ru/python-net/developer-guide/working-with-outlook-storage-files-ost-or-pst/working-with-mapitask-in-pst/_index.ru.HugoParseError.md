---
title: Работа с MapiTask в PST
type: docs
weight: 90
url: /python-net/working-with-mapitask-in-pst/
---


## **Добавление MapiTask в PST**
В статье "Создание нового PST-файла и добавление подпапок" показано, как создать PST-файл и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiTask в подпапку Задачи PST-файла, который вы создали или загрузили. Ниже приведены шаги для добавления MapiTask в PST:

1. Создайте объект MapiTask.
1. Установите свойства MapiTask с помощью конструктора и различных методов.
1. Создайте PST с помощью метода PersonalStorage.Create().
1. Создайте предопределенную папку (Задачи) в корне PST-файла, получив доступ к корневой папке и затем вызвав метод AddMapiMessageItem().

Следующий фрагмент кода показывает, как создать MapiTask и затем добавить его в папку задач новосозданного PST-файла.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiTaskToPST-AddMapiTaskToPST.py" >}}