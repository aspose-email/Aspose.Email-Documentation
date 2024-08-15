---
title: "Работа с MapiNote в PST"
url: /ru/net/working-with-mapinote-in-pst/
weight: 80
type: docs
---


## **Добавление MapiNote в PST**

The [Создайте новый файл PST и добавьте подпапки](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) В статье показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) в подпапку Notes созданного или загруженного файла PST. Чтобы добавить [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) в PST:

1. Создайте шаблон [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) используя Microsoft Outlook и сохраните его как файл MSG.
2. Загрузите сохраненную заметку MSG в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object.
3. Создайте [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) создайте объект и загрузите шаблон MSG-заметки.
4. Установите [Свойства MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/).
5. Создайте PST, используя [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
6. Создайте предварительно определенную папку (Notes) в корне файла PST, открыв корневую папку и вызвав [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

В следующем фрагменте кода показано, как создать [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) а затем добавьте его в папку заметок вновь созданного файла PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cs" >}}
