---
title: "Работа с MapiJournal в PST"
url: /ru/cpp/working-with-mapijournal-in-pst/
weight: 70
type: docs
---

## **Добавление MapiJournal в PST**
С помощью Aspose.Email вы можете добавить MapiJournal в подпапку Журнал файла PST, который вы создали или загрузили. Ниже приведены шаги для добавления MapiJournal в PST:

1. Создайте объект MapiJournal
1. Установите свойства MapiJournal с помощью конструктора и методов.
1. Создайте PST с помощью метода PersonalStorage.Create().
1. Создайте предопределенную папку (Журналы) в корне файла PST, получив доступ к корневой папке и затем вызвав метод AddMapiMessageItem().

Следующий фрагмент кода показывает, как создать MapiJournal и затем добавить его в папку журналов только что созданного файла PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cpp" >}}
## **Добавление вложений в MapiJournal**
Следующий фрагмент кода показывает, как добавить вложения в MapiJournal.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cpp" >}}