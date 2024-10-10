---
title: "Чтение поврежденных PST/OST файлов"
url: /ru/net/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

Иногда может быть невозможно прочитать PST/OST из-за некоторых проблем. Например, некоторые блоки данных могут быть повреждены. В таких случаях обычно возникают исключения при вызове методов [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/), [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/), [GetContents](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getcontents/), [GetSubfolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/), и др. Но отдельные сообщения или папки могут остаться неповрежденными в хранилище.

## **Методы нахождения идентификаторов элементов**

Следующие методы позволяют находить идентификаторы элементов иерархическим образом.

- [FindMessages(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findmessages/) - находит идентификаторы сообщений для папки.
- [FindSubfolders(string parentEntryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findsubfolders/) - находит идентификаторы подпапок для папки.

Идентификаторы, полученные с помощью этих методов, могут быть использованы для извлечения сообщений и папок.

> **_ПРИМЕЧАНИЕ:_** Следует отметить, что, несмотря на свои преимущества, существуют поврежденные хранилища, которые нельзя прочитать даже с использованием этих методов.

## **Перебор файла PST**

Следующий пример кода демонстрирует перебор файла PST и извлечение папок и сообщений. Для получения списка идентификаторов используйте методы FindMessages и FindSubfolders. Затем идентификатор передается в метод [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) или [GetFolderById](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getfolderbyid/) для извлечения элементов.

```csharp
using (var pst = PersonalStorage.FromFile(fileName))
{
    ExploreCorruptedPst(pst, pst.RootFolder.EntryIdString);
}

public static void ExploreCorruptedPst(PersonalStorage pst, string rootFolderId)
{
    var messageIdList = pst.FindMessages(rootFolderId);

    foreach (var messageId in messageIdList)
    {
        try
        {
            var msg = pst.ExtractMessage(messageId);
            Console.WriteLine( "- " + msg.Subject);
        }
        catch
        {
            Console.WriteLine("Ошибка чтения сообщения. Идентификатор: " + messageId);
        }
    }

    var folderIdList = pst.FindSubfolders(rootFolderId);

    foreach (var subFolderId in folderIdList)
    {
        if (subFolderId != rootFolderId)
        {
            try
            {
                FolderInfo subfolder = pst.GetFolderById(subFolderId);
                Console.WriteLine(subfolder.DisplayName);
            }
            catch
            {
                Console.WriteLine("Ошибка чтения сообщения. Идентификатор: " + subFolderId);
            }

            ExplodeCorruptedPst(pst, subFolderId);
        }
    }
}
```