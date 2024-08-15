---
title: "Прочитайте файл Outlook PST и получите информацию о папках и подпапках"
url: /ru/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 110
type: docs
---


Aspose.Email для .NET предоставляет API для чтения файлов Microsoft Outlook PST. Вы можете загрузить файл PST с диска или в потоковом режиме в экземпляр [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) класс и получите информацию о его содержимом, например о папках, подпапках и сообщениях. API также предоставляет возможность включать папки поиска при поиске сообщений из папок PST.

## **Загрузка файла PST**

Файл Outlook PST можно загрузить в экземпляре [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) класс. В следующем фрагменте кода показано, как загрузить файл PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cs" >}}

## **Отображение информации о папках**

После загрузки файла PST в [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) класс, вы можете получить информацию о отображаемом имени файла, корневой папке, подпапках и количестве сообщений. В следующем фрагменте кода показано, как отображать имя файла PST, папки и количество сообщений в папках.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cs" >}}

## **Получайте только определенные пользователем папки**

Файлы PST/OST могут содержать папки, созданные пользователем. Aspose.Email предоставляет возможность доступа только к определенным пользователем папкам с помощью [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) имущество. Вы можете установить [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) недвижимость для **true** чтобы получить только определенные пользователем папки. Следующий фрагмент кода демонстрирует использование [PersonalStorageQueryBuilder.OnlyFoldersCreatedByUser](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstoragequerybuilder/onlyfolderscreatedbyuser/) для получения определенных пользователем папок.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-PST-GetFoldersCreatedByUserOnly-1.cs" >}}

## **Проверка того, находится ли папка в предопределенной папке**

При открытии и проверке папок в файле PST (Personal Storage Table) вы можете проверить, является ли каждая папка предопределенным типом папки или подпапкой предопределенного типа, и получить информацию о каждой папке.

The [FolderInfo.GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/#folderinfogetpredefinedtype-method)(bool getFortopLevelParent) метод позволяет проверить, откуда взята папка [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/). Если *getForTopLevelParent* параметр имеет значение true, метод возвращает [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) значение перечисления для родительской папки верхнего уровня. Это определяет, является ли текущая папка подпапкой предопределенной папки. Если *getForTopLevelParent* параметр равен false, он возвращает [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/) значение перечисления для текущей папки.

В следующем примере кода показано, как внедрить эту функцию в свой проект:

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
## **Получение и добавление стандартной папки RSS-каналов в PersonalStorage**

Aspose.Email позволяет получить ссылку на предопределенную папку, в которой хранятся RSS-каналы. Это может быть полезно, если вы хотите программно получать доступ к RSS-каналам, хранящимся в файле Outlook PST, и управлять ими.
Присвойте значение RSS-каналов [StandardIpmFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/standardipmfolder/#standardipmfolder-enumeration) enum.  

В следующем примере кода показано, как получить папку RSS Feeds.

```cs
using (var pst = PersonalStorage.FromFile("my.pst", false))
{
    var rssFolder = pst.GetPredefinedFolder(StandardIpmFolder.RssFeeds);
}
```

Чтобы добавить папку RSS Feeds, используйте следующий фрагмент кода:

```cs
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    var rssFolder = pst.CreatePredefinedFolder("RSS Feeds", StandardIpmFolder.RssFeeds);
}
```

## **Разбор папок с возможностью поиска**

PST/OST может содержать папки с возможностью поиска в дополнение к папкам обычного типа. Aspose.Email предоставляет [FolderKind](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderkind/) перечислитель для указания сообщений из таких папок поиска с помощью [EnumerateFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/enumeratefolders/#enumeratefolders/) and [GetSubFolders](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolders/#getsubfolders/) методы. В следующем фрагменте кода показано, как анализировать папки с возможностью поиска.

```cs
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
        {
            FolderInfoCollection folders = pst.RootFolder.GetSubFolders(FolderKind.Search | FolderKind.Normal);

            // Browse through each folder to display folder name and number of messages
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

В следующем фрагменте кода показано, как получить информацию о родительской папке из [MessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-PST-RetreivingParentFolderInformationFromMessageInfo-RetreivingParentFolderInformationFromMessageInfo.cs" >}}

## **Извлечь подпапку PST по пути**

The [FolderInfo.getSubfolder (строковое имя, логическое значение IgnoreCase, логическое значение HandlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) метод overload позволит вам получить подпапку с указанным именем из текущей папки PST.

Метод принимает следующие параметры:

- **name** - указывает имя извлекаемой вложенной папки.
- **ignoreCase** - определяет, следует ли искать имя вложенной папки с учетом регистра или без учета регистра. Если задано значение *true*, поиск будет вестись без учета регистра, в противном случае — с учетом регистра.
- **handlePathSeparator** - указывает, следует ли рассматривать указанное имя папки как путь, если оно содержит обратную косую черту. Если задано значение *true*, метод интерпретирует имя папки как путь и пытается перейти к подпапке, используя этот путь. Если задано значение *false*, метод будет рассматривать имя папки как простое имя и искать вложенную папку с точным совпадением имени.
 
В следующем примере кода показано, как реализовать этот метод в вашем проекте:

```cs
var folder = pst.RootFolder.GetSubFolder(@"Inbox\Reports\Jan", true, true);
In this sample, the method will return a ‘Jan’ named folder that is located at the Inbox\Reports\ path relative to the root folder.
```

## **API для обхода файлов PST**

API обхода позволяет извлекать все элементы PST, насколько это возможно, без исключений, даже если некоторые данные исходного файла повреждены.
Следующие шаги показывают, как использовать этот API.

Use [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) конструктор и [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) метод вместо метода FromFile.

Конструктор позволяет определить метод обратного вызова.

```csharp
using (var currentPst = new PersonalStorage((exception, itemId) => { /* Exception handling  code. */ }))
```

Исключения для загрузки и обхода будут доступны с помощью метода обратного вызова.

The [Load](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/load/) метод возвращает значение true, если файл был успешно загружен и возможен дальнейший обход. Если файл поврежден и обход невозможен, возвращается значение false.

```csharp
if (currentPst.Load(inputStream))
```

Это позволяет открывать и перемещать даже поврежденные файлы PST, не выбрасывая исключений. А исключения и поврежденные элементы будут обрабатываться методом обратного вызова.

```csharp
using (PersonalStorage pst = new PersonalStorage((exception, itemId) => { /* Exception handling  code. */ }))
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
