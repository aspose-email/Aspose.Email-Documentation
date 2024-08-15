---
title: "Работа с MapiNote в PST"
url: /ru/python-net/working-with-mapinote-in-pst/
weight: 80
type: docs
---


## **Добавление MapiNote в PST**
В статье «Создание нового файла PST и добавление подпапок» показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiNote в подпапку Notes созданного или загруженного вами PST-файла. Чтобы добавить MapiNote в PST, выполните следующие действия:

1. Создайте шаблон MapiNote с помощью Microsoft Outlook и сохраните его как файл MSG.
1. Загрузите сохраненную заметку MSG в объект MapiMessage.
1. Создайте объект MapiNote и загрузите шаблон заметки MSG.
1. Задайте свойства MapiNote.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предварительно определенную папку (Notes) в корне файла PST, открыв корневую папку и вызвав метод addMapiMessageItem ().

В следующем фрагменте кода показано, как создать файл MapiNote, а затем добавить его в папку заметок вновь созданного файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiNoteToPST-AddMapiNoteToPST.py" >}}
