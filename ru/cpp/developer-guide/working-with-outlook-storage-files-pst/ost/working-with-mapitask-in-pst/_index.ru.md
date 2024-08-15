---
title: "Работа с MapiTask в PST"
url: /ru/cpp/working-with-mapitask-in-pst/
weight: 90
type: docs
---

## **Добавление MapiTask в PST**
С помощью Aspose.Email вы можете добавить MapiTask в подпапку Tasks созданного или загруженного файла PST. Ниже приведены шаги по добавлению MapiTask в PST:

1. Создайте объект MapiTask.
1. Задайте свойства MapiTask с помощью конструктора и различных методов.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предварительно определенную папку (Tasks) в корне файла PST, открыв корневую папку и вызвав метод addMapiMessageItem ().

В следующем фрагменте кода показано, как создать MapiTask, а затем добавить его в папку задач вновь созданного файла PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cpp" >}}
