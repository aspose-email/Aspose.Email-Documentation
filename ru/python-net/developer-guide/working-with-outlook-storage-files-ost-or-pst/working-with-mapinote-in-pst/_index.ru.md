---
title: "Работа с MapiNote в PST"
url: /ru/python-net/working-with-mapinote-in-pst/
weight: 80
type: docs
---


## **Добавление MapiNote в PST**
Создание нового PST-файла и добавление подпапок показали, как создать PST-файл и добавить подпапку в него. С помощью Aspose.Email вы можете добавить MapiNote в подпапку Заметки PST-файла, который вы создали или загрузили. Чтобы добавить MapiNote в PST:

1. Создайте шаблон MapiNote с помощью Microsoft Outlook и сохраните его в виде MSG-файла.
1. Загрузите сохранённую MSG-заметку в объект MapiMessage.
1. Создайте объект MapiNote и загрузите шаблон MSG-заметки.
1. Установите свойства MapiNote.
1. Создайте PST с помощью метода PersonalStorage.Create().
1. Создайте предопределённую папку (Заметки) в корне PST-файла, получив доступ к корневой папке и затем вызвав метод AddMapiMessageItem().

Следующий фрагмент кода показывает, как создать MapiNote, а затем добавить его в папку заметок вновь созданного PST-файла.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiNoteToPST-AddMapiNoteToPST.py" >}}