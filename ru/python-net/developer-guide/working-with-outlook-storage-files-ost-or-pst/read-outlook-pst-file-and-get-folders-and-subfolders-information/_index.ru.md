---
title: "Прочитайте файл Outlook PST и получите информацию о папках и подпапках"
url: /ru/python-net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---


Aspose.Email для .NET предоставляет API для чтения файлов Microsoft Outlook PST. PST-файл можно загрузить с диска или в потоковом режиме в экземпляр класса PersonalStorage и получить информацию о его содержимом, например о папках, подпапках и сообщениях. API также предоставляет возможность включать папки поиска при поиске сообщений из папок PST.
## **Загрузка файла PST**
Файл Outlook PST можно загрузить в экземпляре класса PersonalStorage. В следующем фрагменте кода показано, как загрузить файл PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
## **Отображение информации PST**
После загрузки файла PST в класс PersonalStorage вы можете получить информацию о отображаемом имени файла, корневой папке, подпапках и количестве сообщений. В следующем фрагменте кода показано, как отобразить имя файла PST, папки и количество сообщений в папках.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.py" >}}

## **Получайте только созданные пользователем папки**

Файлы PST/OST могут содержать папки, созданные пользователем, т.е. исключая все стандартные папки IPM. Aspose.Email предоставляет возможность доступа только к созданным пользователем папкам с помощью *only_folders_created_by_user* собственность [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) класс. Вы можете установить *only_folders_created_by_user* свойство True для получения только созданных пользователем папок. В следующем фрагменте кода показано, как можно использовать *only_folders_created_by_user* недвижимость в вашем проекте:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

query_builder = ae.storage.pst.PersonalStorageQueryBuilder()
query_builder.only_folders_created_by_user.equals(True)

folders = pst.root_folder.get_sub_folders(query_builder.get_query())

for folder in folders:
    print(f"Folder: {folder.display_name}")
```

## **Проверка того, находится ли папка в предопределенной папке**

Метод «get_predefined_type» [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) класс позволяет узнать, является ли папка в файле PST стандартной папкой. Стандартные (или предопределенные) папки, в отличие от папок, созданных пользователем, — это папки, создаваемые Outlook при добавлении учетной записи электронной почты, например папки «Входящие», «Отправленные», «Черновики», «Удаленные элементы», «Календарь», «Задачи», «Заметки» и т. д.

В приведенном ниже примере кода показано, как использовать этот метод в проекте. Если задано значение True, оно возвращает предопределенный тип родительской папки верхнего уровня. Это определяет, является ли текущая папка подпапкой предопределенной папки. Если установлено значение False, возвращается предопределенный тип текущей папки.


```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders()

for folder in folders:
    print(f"Folder: {folder.display_name}")
    print(f"Is predefined: {folder.get_predefined_type(False) != ae.storage.pst.StandardIpmFolder.UNSPECIFIED}")
    print("-----------------------------------")
```
## **Получение и добавление стандартной папки RSS-каналов в PersonalStorage**

Aspose.Email предоставляет возможность получить ссылку на предопределенную папку RSS-каналов, что позволяет разработчикам программно получать доступ к RSS-каналам, хранящимся в файле Outlook PST, и управлять ими. Получив ссылку на «Папку RSS-каналов», разработчики могут работать с данными RSS-канала, включая подписку на новые каналы, обновление существующих каналов или извлечение информации из лент.

Значение RSSFeeds в перечислении StandardipMFolder обычно представляет собой предопределенный тип папки, специально предназначенный для хранения RSS-каналов в PST-файле Outlook. Используя это значение перечисления, разработчики могут программно ориентироваться на «папку RSS-каналов» и взаимодействовать с ней. Следующие примеры кода продемонстрируют, как реализовать эту функцию в вашем проекте:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```
Чтобы добавить папку RSS Feeds, используйте следующий фрагмент кода:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

rss_folder = pst.create_predefined_folder("RSS Feeds", ae.storage.pst.StandardIpmFolder.RSS_FEEDS)
```

## **Разбор папок с возможностью поиска**

Aspose.Email предоставляет [FolderKind](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderkind/#folderkind-enumeration) перечисление для работы с различными типами папок PST. Помимо обычных папок, он работает с папками SEARCH. Папка SEARCH — это виртуальная папка, в которой отображаются все элементы электронной почты, соответствующие определенным критериям поиска. Для анализа папок SEARCH используйте следующий фрагмент кода:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)

# Browse through each folder to display folder name and number of messages
for folder in folders:
    print(f"Folder: {folder.display_name}")
    sub_folders = folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)
    for sub_folder in sub_folders:
        print(f"Sub-folder: {folder.display_name}")
```

## **Получение информации о родительской папке из MessageInfo**
В следующем фрагменте кода показано, как получить информацию о родительской папке из MessageInfo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-RetrievingParentFolderInformationFromMessageInfo-RetrievingParentFolderInformationFromMessageInfo.py" >}}

## **Получение подпапки PST по пути**

Чтобы получить подпапку PST по пути, используйте *get_sub_folder* метод [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) класс. Он извлекает определенную подпапку в каталоге или файловой системе.

Метод принимает следующие параметры:

- **name** - представляет собой имя вложенной папки, которую необходимо извлечь. Он используется для указания имени или идентификатора подпапки, которую метод должен искать.

- **ignore_case** - это логическое значение, определяющее, следует ли методу игнорировать чувствительность к регистру при сравнении имени вложенной папки. Если задано значение True, метод рассмотрит совпадение имен без учета регистра (например, «папка» и «папка» будут рассматриваться как одно и то же). Если задано значение False, метод выполнит сравнение с учетом регистра символов.

- **handle_path_separator** - это логическое значение, указывающее, должен ли метод обрабатывать разделитель путей при поиске вложенной папки. Разделители путей — это символы, используемые для разделения папок в пути к каталогу (например, `\` в Windows или `/` в Unix). Если установлено значение True, метод автоматически обработает разделитель путей, обеспечивая правильное соответствие папок. Если задано значение False, разделитель путей будет рассматриваться как часть имени вложенной папки, что приведет к иному поведению при поиске.

В следующем примере кода показано, как получить подпапку PST по пути:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# In this sample, the method will return a ‘Jan’ named folder
# that is located at the Inbox\Reports\ path
# relative to the root folder.
folder = pst.root_folder.get_sub_folder("Inbox\Reports\Jan", True, True)
```
