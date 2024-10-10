---
title: "Чтение файла Outlook PST и получение информации о папках и подпапках"
url: /ru/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---

Aspose.Email для .NET предоставляет API для чтения файлов PST Microsoft Outlook. Вы можете загрузить файл PST с диска или потока в экземпляр класса [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) и получить информацию о его содержимом, например, о папках, подпапках и сообщениях. API также предоставляет возможность включать папки поиска при обходе сообщений из папок PST.

## **Загрузка файла PST**

Файл PST Outlook может быть загружен в экземпляр класса [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/). Следующий фрагмент кода показывает, как загрузить файл PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cs" >}}

## **Отображение информации о папках**

После загрузки файла PST в класс [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) вы можете получить информацию о имени файла для отображения, корневой папке, количестве подпапок и сообщений. Следующий фрагмент кода показывает, как отобразить имя файла PST, папки и количество сообщений в папках.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cs" >}}

## **Получение только определённых пользователем папок**

Файлы PST/OST могут содержать папки, которые были созданы пользователем. Aspose.Email предоставляет возможность доступа только к папкам, определённым пользователем, с помощью свойства [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/). Вы можете установить свойство [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) в **true**, чтобы получить только папки, созданные пользователем. Следующий фрагмент кода демонстрирует использование [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) для получения папок, определённых пользователем.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-PST-GetFoldersCreatedByUserOnly-1.cs" >}}

## **Проверка, является ли папка предопределённым типом папки**

При открытии и проверке папок в файле PST (Личная таблица хранения) вы можете проверить, является ли каждая папка предопределённым типом папки или подпапкой предопределённого типа папки, и получить информацию о каждой папке.

Метод [FolderInfo.GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/#folderinfogetpredefinedtype-method)(bool getForTopLevelParent) позволяет определить, является ли папка папкой [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/). Если параметр *getForTopLevelParent* равен true, метод возвращает значение перечисления [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) для родительской папки верхнего уровня. Это определяет, является ли текущая папка подпапкой предопределённой папки. Если параметр *getForTopLevelParent* равен false, он возвращает значение перечисления [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) для текущей папки.

Следующий образец кода показывает, как реализовать эту функцию в вашем проекте:

```cs
PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders();

            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Folder: {folder.DisplayName}");
                Console.WriteLine($"Is predefined: {folder.GetPredefinedType(false) != StandardIpmFolder.Unspecified}");
                Console.WriteLine("-----------------------------------");
            }
        }
    }
```
## **Получение и добавление предопределённой папки для RSS-каналов в PersonalStorage**

Aspose.Email позволяет получить ссылку на предопределённую папку, в которой хранятся RSS-каналы. Это может быть полезно, если вы хотите программно получить доступ и управлять RSS-каналами, хранящимися в файле PST Outlook. Используйте значение RssFeeds для перечисления [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/#standardipmfolder-enumeration).

Следующий пример кода показывает, как получить папку для RSS-каналов.

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var rssFolder = pst.GetPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```

Чтобы добавить папку для RSS-каналов, используйте следующий фрагмент кода:

```cs
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    var rssFolder = pst.CreatePredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Парсинг папок для поиска**

Файл PST/OST может содержать папки для поиска в дополнение к обычным типам папок. Aspose.Email предоставляет перечислитель [FolderKind](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderkind/) для указания сообщений из таких папок поиска с помощью методов [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/#enumeratefolders/) и [GetSubFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/#getsubfolders/). Следующий фрагмент кода показывает, как парсить папки для поиска.

```cs
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders(FolderKind.Search | FolderKind.Normal);

            // Просматриваем каждую папку для отображения имени папки и количества сообщений
            foreach (FolderInfo folder in folders)
            {
                Console.WriteLine($"Folder: {folder.DisplayName}");

                FolderInfoCollection subFolders = folder.GetSubFolders(FolderKind.Search | FolderKind.Normal);
                foreach (FolderInfo subFolder in subFolders)
                {
                    Console.WriteLine($"Sub-folder: {subFolder.DisplayName}");
                }
            }
        }
```

## **Получение информации о родительской папке из MessageInfo**

Следующий фрагмент кода показывает, как получить информацию о родительской папке из [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-PST-RetreivingParentFolderInformationFromMessageInfo-RetreivingParentFolderInformationFromMessageInfo.cs" >}}

## **Получение подпапки PST по пути**

Перегрузка метода [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) позволит вам получить подпапку с указанным именем из текущей папки PST.

Метод принимает следующие параметры:

- **name** - указывает имя подпапки для получения.
- **ignoreCase** - определяет, должен ли поиск имени подпапки быть чувствительным к регистру или нечувствительным. Если установлено *true*, поиск будет нечувствительным к регистру, иначе - чувствительным.
- **handlePathSeparator** - определяет, должно ли указанное имя папки рассматриваться как путь, если оно содержит обратные слэши. Если установлено *true*, метод будет интерпретировать имя папки как путь, пытаясь перейти к подпапке, используя этот путь. Если установлено *false*, метод будет рассматривать имя папки как простое имя, и произведёт поиск подпапки с точным совпадением имени.
  
Следующий пример кода демонстрирует, как реализовать этот метод в вашем проекте:

```cs
var folder = pst.RootFolder.GetSubFolder(@"Inbox\Reports\Jan", true, true);
В этом примере метод вернёт папку с именем 'Jan', расположенную по пути Inbox\Reports\ относительно корневой папки.
```

## **API обхода файла PST**

API обхода позволяет извлекать все элементы PST по мере возможности, не выбрасывая исключения, даже если некоторые данные оригинального файла повреждены. Следующие шаги показывают, как использовать этот API.

Используйте конструктор [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) и метод [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) вместо метода FromFile.

Конструктор позволяет определить метод обратного вызова.

```csharp
using (var currentPst = new PersonalStorage((exception, itemId) => { /* Код обработки исключений. */ }))
```

Исключения при загрузке и обходе будут доступны через метод обратного вызова.

Метод [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) возвращает 'true', если файл был загружен успешно и дальнейший обход возможен. Если файл повреждён и дальнейший обход невозможен, возвращается 'false'.

```csharp
if (currentPst.Load(inputStream))
```

Это позволяет открывать и обходить даже повреждённые файлы PST без выбрасывания исключений. Исключения и повреждённые элементы будут обрабатываться методом обратного вызова.

```csharp
using (PersonalStorage pst = new PersonalStorage((exception, itemId) => { /* Код обработки исключений. */ }))
{
    if (pst.Load(@"test.pst"))
	{
		GetAllMessages(pst, pst.RootFolder);
	}
}

private static void GetAllMessages(PersonalStorage pst, FolderInfo folder)
{
    foreach (var messageEntryId in folder.EnumerateMessagesEntryId())
    {
        MapiMessage message = pst.ExtractMessage(messageEntryId);
    }
    foreach (var subFolder in folder.GetSubFolders())
    {
        GetAllMessages(pst, subFolder);
    }
}
```