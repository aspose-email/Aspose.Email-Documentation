---
title: "Работа с журналом MAPIjournal в формате PST"
url: /ru/net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Добавление журнала MAPIjournal в PST**

The [Создайте новый файл PST и добавьте подпапки](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) В статье показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) в подпапку Journal созданного или загруженного файла PST. Ниже приведены шаги по добавлению [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) в PST:

1. Создайте [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) object
2. Установите [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) свойства с использованием конструктора и методов.
3. Создайте PST, используя [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Создайте предварительно определенную папку (Журналы) в корне файла PST, открыв корневую папку и вызвав [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

В следующем фрагменте кода показано, как создать [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) а затем добавьте его в папку журнала вновь созданного файла PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cs" >}}

## **Добавление вложений в MapiJournal**

В следующем фрагменте кода показано, как добавлять вложения в [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cs" >}}
