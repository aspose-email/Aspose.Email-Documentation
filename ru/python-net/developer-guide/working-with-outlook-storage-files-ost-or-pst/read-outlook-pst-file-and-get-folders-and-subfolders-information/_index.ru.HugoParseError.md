---
title: Прочитать файл PST Outlook и получить информацию о папках и подпапках
type: docs
weight: 30
url: /python-net/read-outlook-pst-file-and-get-folders-and-subfolders-information/
---


Aspose.Email для .NET предоставляет API для чтения файлов PST Microsoft Outlook. Вы можете загрузить файл PST с диска или потока в экземпляр класса PersonalStorage и получить информацию о его содержимом, например папки, подпапки и сообщения. API также предоставляет возможность включать папки поиска при обходе сообщений из папок PST.
## **Загрузка файла PST**
Файл PST Outlook может быть загружен в экземпляр класса PersonalStorage. Следующий фрагмент кода показывает, как загрузить файл PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
## **Отображение информации о PST**
После загрузки файла PST в класс PersonalStorage вы можете получить информацию о имени файла, корневой папке, числе подпапок и сообщениях. Следующий фрагмент кода показывает, как отобразить имя файла PST, папки и количество сообщений в папках.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.py" >}}

## **Получить только пользовательские папки**

Файлы PST/OST могут содержать папки, которые были созданы пользователем, т.е. исключая все стандартные папки IPM. Aspose.Email предоставляет возможность доступа только к пользовательским папкам с помощью свойства *only_folders_created_by_user* класса [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class). Вы можете установить свойство *only_folders_created_by_user* в True, чтобы получить только пользовательские папки. Следующий фрагмент кода демонстрирует, как вы можете использовать свойство *only_folders_created_by_user* в вашем проекте:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

query_builder = ae.storage.pst.PersonalStorageQueryBuilder()
query_builder.only_folders_created_by_user.equals(True)

folders = pst.root_folder.get_sub_folders(query_builder.get_query())

for folder in folders:
    print(f"Folder: {folder.display_name}")
```

## **Проверка нахождения папки в предопределенной папке**

Метод "get_predefined_type" класса [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) позволяет выяснить, является ли папка внутри файла PST стандартной папкой. Стандартные (или предопределенные) папки, в отличие от пользовательских, создаются Outlook, когда вы добавляете учетную запись электронной почты, такую как Входящие, Отправленные, Черновики, Удаленные элементы, Календарь, Задачи, Заметки и т.д. 

Пример кода ниже демонстрирует, как использовать этот метод в проекте. Если установлен в True, он возвращает предопределенный тип для родительской папки верхнего уровня. Это определяет, находится ли текущая папка в подпапке предопределенной папки. Если установлен в False, он возвращает предопределенный тип для текущей папки.


```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders()

for folder in folders:
    print(f"Folder: {folder.display_name}")
    print(f"Is predefined: {folder.get_predefined_type(False) != ae.storage.pst.StandardIpmFolder.UNSPECIFIED}")
    print("-----------------------------------")
```
## **Получение и добавление стандартной папки RSS Feeds в PersonalStorage**

Aspose.Email предоставляет функциональность для получения ссылки на предопределенную папку RSS Feeds, позволяя разработчикам программно получать доступ и манипулировать RSS-лентами, хранящимися в файле PST Outlook. Получив ссылку на папку "RSS Feeds", разработчики могут работать с данными RSS-ленты, которые могут включать подписку на новые ленты, обновление существующих лент или извлечение информации из лент.

Значение RssFeeds в перечислении StandardIpmFolder обычно представляет собой предопределенный тип папки, специально предназначенный для хранения RSS-лент в файле PST Outlook. Используя это значение перечисления, разработчики могут целенаправленно взаимодействовать с "папкой RSS Feeds" программно. Следующие примеры кода демонстрируют, как реализовать эту функцию в вашем проекте:

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

## **Парсинг поисковых папок**

Aspose.Email предоставляет перечисление [FolderKind](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderkind/#folderkind-enumeration) для работы с различными видами папок PST. Помимо Обычных папок, он работает с Поисковыми папками. Поисковая папка — это виртуальная папка, которая предоставляет представление всех элементов электронной почты, соответствующих определенным критериям поиска. Чтобы разобрать Поисковые папки, используйте следующий фрагмент кода:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folders = pst.root_folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)

# Просматриваем каждую папку, чтобы отобразить имя папки и количество сообщений
for folder in folders:
    print(f"Folder: {folder.display_name}")
    sub_folders = folder.get_sub_folders(ae.storage.pst.FolderKind.SEARCH | ae.storage.pst.FolderKind.NORMAL)
    for sub_folder in sub_folders:
        print(f"Sub-folder: {folder.display_name}")
```

## **Получение информации о родительской папке из MessageInfo**
Следующий фрагмент кода показывает, как получить информацию о родительской папке из MessageInfo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-RetrievingParentFolderInformationFromMessageInfo-RetrievingParentFolderInformationFromMessageInfo.py" >}}

## **Получение подпапки PST по пути**

Чтобы получить подпапку PST по пути, используйте метод *get_sub_folder* класса [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Он извлекает конкретную подпапку из каталога или файловой системы.

Метод принимает следующие параметры:

- **name** - представляет собой имя подпапки, которую необходимо извлечь. Он используется для указания имени или идентификатора подпапки, которую метод должен найти.

- **ignore_case** - это булево значение, которое определяет, должен ли метод игнорировать чувствительность к регистру при сравнении имени подпапки. Если установлено в True, метод будет учитывать совпадение имен, не принимая во внимание регистр (например, "folder" и "Folder" будут рассматриваться как одинаковые). Если установлено в False, метод будет выполнять сравнение с учетом регистра.

- **handle_path_separator** - это булево значение, которое указывает, должен ли метод обрабатывать разделитель пути при поиске подпапки. Разделители путей - это символы, используемые для разделения папок в пути каталога (например, `\` в Windows или `/` в Unix). Если установлено в True, метод автоматически обработает разделитель пути, обеспечивая правильное совпадение папок. Если установлено в False, он будет рассматривать разделитель пути как часть имени подпапки, что приведет к другому поведению поиска.

Следующий пример кода показывает, как получить подпапку PST по пути:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# В этом примере метод вернет папку с именем ‘Jan’
# которая находится по пути Inbox\Reports\ 
# относительно корневой папки.
folder = pst.root_folder.get_sub_folder("Inbox\Reports\Jan", True, True)
```