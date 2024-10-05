---
title: "Работа с MapiNote в PST"
url: /ru/cpp/working-with-mapinote-in-pst/
weight: 80
type: docs
---

## **Добавление MapiNote в PST**

С помощью Aspose.Email вы можете добавить MapiNote в подкаталог Заметки файла PST, который вы создали или загрузили. Чтобы добавить MapiNote в PST:

1. Создайте шаблон MapiNote с помощью Microsoft Outlook и сохраните его как файл MSG.
1. Загрузите сохранённую заметку MSG в объект MapiMessage.
1. Создайте объект MapiNote и загрузите шаблон заметки MSG.
1. Установите свойства MapiNote.
1. Создайте PST с использованием метода PersonalStorage.Create().
1. Создайте предопределённую папку (Заметки) в корне файла PST, получив доступ к корневой папке, а затем вызвав метод AddMapiMessageItem().

Следующий фрагмент кода показывает, как создать MapiNote и затем добавить его в папку заметок вновь созданного файла PST.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cpp" >}}

