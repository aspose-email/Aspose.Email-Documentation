---
title: "Работа с журналом MAPIjournal в формате PST"
url: /ru/cpp/working-with-mapijournal-in-pst/
weight: 70
type: docs
---

## **Добавление журнала MAPIjournal в PST**
С помощью Aspose.Email вы можете добавить MapiJournal в подпапку Journal созданного или загруженного вами PST-файла. Ниже приведены шаги по добавлению MapiJournal в PST:

1. Создайте объект MapiJournal
1. Задайте свойства MapiJournal с помощью конструктора и методов.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предварительно определенную папку (Journals) в корне файла PST, открыв корневую папку и вызвав метод addMapiMessageItem ().

В следующем фрагменте кода показано, как создать MapiJournal, а затем добавить его в папку журнала вновь созданного файла PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cpp" >}}
## **Добавление вложений в MapiJournal**
В следующем фрагменте кода показано, как добавлять вложения в MapiJournal.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cpp" >}}
