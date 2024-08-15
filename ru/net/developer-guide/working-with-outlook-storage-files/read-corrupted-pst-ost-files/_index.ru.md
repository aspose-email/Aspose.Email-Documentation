---
title: "Чтение поврежденных файлов PST/OST"
url: /ru/net/read-corrupted-pst-ost-files/
weight: 112
type: docs
---

Иногда из-за некоторых проблем чтение PST/OST может оказаться невозможным. Например, некоторые блоки данных могут быть повреждены. В таких случаях обычно возникают исключения при вызове [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/), [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratemessages/), [GetContents](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getcontents/), [GetSubfolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/)и т. д. методы. Но отдельные сообщения или папки могут остаться неповрежденными в хранилище.

## **Методы поиска идентификаторов товаров**

Следующие методы позволяют найти идентификаторы товаров в иерархическом порядке.

- [Поиск сообщений (идентификатор родительской записи в строке)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findmessages/) - находит идентификаторы сообщений для папки.
- [Поиск подпапок (идентификатор родительской записи в строке)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/findsubfolders/) - находит идентификаторы подпапок для папки.

Идентификаторы, полученные с помощью этих методов, можно использовать для извлечения сообщений и папок.

> **_NOTE:_** Следует отметить, что, несмотря на преимущества, существуют поврежденные хранилища, которые невозможно прочитать даже с помощью этих методов.

## **Обход файлов PST**

В следующем примере кода показано перемещение файлов PST и извлечение папок и сообщений. Чтобы получить список идентификаторов, используйте методы FindMessages и FindSubfolders. Затем идентификатор передается в [ExtractMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/) or [GetFolderById](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getfolderbyid/) метод извлечения элементов.

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
            Console.WriteLine("Message reading error. Entry id: " + messageId);
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
                Console.WriteLine("Message reading error. Entry id: " + subFolderId);
            }

            ExplodeCorruptedPst(pst, subFolderId);
        }
    }
}
```
