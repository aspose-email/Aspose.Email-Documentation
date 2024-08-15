---
title: "Работа с MapiNote в PST"
url: /ru/cpp/working-with-mapinote-in-pst/
weight: 80
type: docs
---

## **Добавление MapiNote в PST**
С помощью Aspose.Email вы можете добавить MapiNote в подпапку Notes созданного или загруженного файла PST. Чтобы добавить MapiNote в PST, выполните следующие действия:

1. Создайте шаблон MapiNote с помощью Microsoft Outlook и сохраните его как файл MSG.
1. Загрузите сохраненную заметку MSG в объект MapiMessage.
1. Создайте объект MapiNote и загрузите шаблон заметки MSG.
1. Задайте свойства MapiNote.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предварительно определенную папку (Notes) в корне файла PST, открыв корневую папку и вызвав метод addMapiMessageItem ().

В следующем фрагменте кода показано, как создать файл MapiNote, а затем добавить его в папку заметок вновь созданного файла PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cpp" >}}
