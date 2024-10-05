---
title: Работа с MapiTask в PST
type: docs
weight: 90
url: /cpp/working-with-mapitask-in-pst/
---

## **Добавление MapiTask в PST**
С помощью Aspose.Email вы можете добавить MapiTask в подпапку Задачи файла PST, который вы создали или загрузили. Ниже приведены шаги для добавления MapiTask в PST:

1. Создайте объект MapiTask.
1. Установите свойства MapiTask, используя конструктор и различные методы.
1. Создайте PST, используя метод PersonalStorage.Create().
1. Создайте предопределенную папку (Задачи) в корне файла PST, получив доступ к корневой папке, а затем вызвав метод AddMapiMessageItem().

Следующий фрагмент кода показывает, как создать MapiTask, а затем добавить его в папку задач нового файла PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cpp" >}}