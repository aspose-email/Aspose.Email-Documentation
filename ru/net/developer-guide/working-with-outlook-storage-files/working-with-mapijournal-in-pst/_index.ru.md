---
title: "Работа с MapiJournal в PST"
url: /ru/net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Добавление MapiJournal в PST**

Статья [Создание нового PST-файла и добавление подпапок](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) демонстрирует, как создать PST-файл и добавить в него подпапку. С помощью Aspose.Email вы можете добавить [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) в подпапку Журнал PST-файла, который вы создали или загрузили. Ниже приведены шаги по добавлению [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) в PST:

1. Создайте объект [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/)
2. Установите свойства [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) с помощью конструктора и методов.
3. Создайте PST с помощью метода [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Создайте заранее определённую папку (Журналы) в корне PST-файла, получив доступ к корневой папке и затем вызвав метод [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

Следующий код показывает, как создать [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) и затем добавить его в папку журнала вновь созданного PST-файла.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cs" >}}

## **Добавление вложений в MapiJournal**

Следующий код показывает, как добавлять вложения в [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cs" >}}