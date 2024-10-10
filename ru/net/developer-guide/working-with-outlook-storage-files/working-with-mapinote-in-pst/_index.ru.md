---
title: "Работа с MapiNote в PST"
url: /ru/net/working-with-mapinote-in-pst/
weight: 80
type: docs
---


## **Добавление MapiNote в PST**

Статья [Создание нового PST-файла и добавление подкаталогов](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) показывает, как создать PST-файл и добавить подкаталог к нему. С помощью Aspose.Email вы можете добавить [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) в подкаталог Заметки PST-файла, который вы создали или загрузили. Чтобы добавить [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) в PST:

1. Создайте шаблон [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) с помощью Microsoft Outlook и сохраните его как MSG-файл.
2. Загрузите сохраненную MSG-запись в объект [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
3. Создайте объект [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) и загрузите шаблон MSG-заметки.
4. Установите [свойства MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/).
5. Создайте PST с помощью метода [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
6. Создайте предопределенную папку (Заметки) в корне PST-файла, получив доступ к корневой папке и затем вызвав метод [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

Следующий фрагмент кода показывает, как создать [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) и затем добавить его в папку заметок только что созданного PST-файла.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cs" >}}