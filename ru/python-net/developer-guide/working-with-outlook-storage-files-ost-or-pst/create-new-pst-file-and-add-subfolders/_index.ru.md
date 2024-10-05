---
title: "Создание нового PST файла и добавление подпапок"
url: /ru/python-net/create-new-pst-file-and-add-subfolders/
weight: 10
type: docs
---

В дополнение к парсингу существующего PST файла, Aspose.Email предоставляет средства для создания PST файла с нуля. Эта статья демонстрирует, как создать PST файл Outlook и добавить к нему подпапку.

1. Создание нового PST файла.
2. Изменение класса контейнера папки.

Используйте класс PersonalStorage для создания PST файла в определенном месте на локальном диске. Чтобы создать PST файл с нуля:

1. Создайте PST, используя метод PersonalStorage.Create().
2. Добавьте подпапку в корень PST файла, получив доступ к корневой папке и затем вызвав метод AddSubFolder.

Следующий фрагмент кода показывает, как создать PST файл и добавить подпапку с именем Inbox.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.py" >}}

## **Проверка соответствия класса контейнера при добавлении папки в PST**

Aspose.Email для Python предлагает решение, которое улучшает процесс валидации во время создания папок в PST файлах. С помощью свойства 'EnforceContainerClassMatching' класса [FolderCreationOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) вы можете обеспечить строгую проверку соответствия классов контейнеров при добавлении новой папки в PST хранилище. Эта функция помогает поддерживать организационную иерархию внутри PST файла, предотвращая несоответствия в классах контейнеров. Установив 'EnforceContainerClassMatching' в 'true', будет выброшено исключение, если классы контейнеров родительской и дочерней папок не совпадают, что предоставляет защиту от неправильных структур папок. Поведение по умолчанию для этого свойства 'false', позволяя гибкость в создании папок, при этом позволяя вам обеспечивать строгое соответствие классов контейнеров при необходимости.

Следующий пример кода демонстрирует использование свойства 'EnforceContainerClassMatching' для управления тем, должно ли быть выброшено исключение при добавлении папок с несовпадающими классами контейнеров:

```py
with PersonalStorage.create("storage.pst", FileFormatVersion.Unicode) as pst:
    contacts = pst.createpredefinedfolder("Contacts", StandardIpmFolder.Contacts)
    
    # Исключение не возникнет. EnforceContainerClassMatching по умолчанию False.
    contacts.addsubfolder("Subfolder1", "IPF.Note")
    
    # Исключение произойдёт, так как класс контейнера добавляемой подпапки (IPF.Note)
    # не соответствует классу контейнера родительской папки (IPF.Contact).
    contacts.addsubfolder("Subfolder3", FolderCreationOptions(enforcecontainerclassmatching=True, containerclass="IPF.Note"))
```

## **Изменение класса контейнера папки**
Иногда необходимо изменить класс контейнера папки. Общий пример - это когда сообщения разных типов (встречи, сообщения и т.д.) добавляются в одну и ту же папку. В таких случаях необходимо изменить класс папки, чтобы все элементы в папке отображались правильно. Следующий фрагмент кода показывает, как изменить класс контейнера папки в PST для этой цели.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ChangeFolderContainerClass-ChangeFolderContainerClass.py" >}}

## **Добавление массовых сообщений с улучшенной производительностью**

Добавление массовых сообщений в PST файл, в отличие от добавления их по отдельности, может предложить несколько преимуществ, особенно в отношении эффективности и производительности: меньше операций ввода-вывода, уменьшенное время выполнения задачи, более эффективное использование ресурсов системы и др. Метод *add_messages* класса [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) используется для передачи коллекции MAPI сообщений, полученных из исходной папки, в целевую папку.

### **Добавление сообщений из другого PST**

Чтобы перечислить и извлечь все MAPI сообщения из исходной папки PST файла, используйте метод *enumerate_mapi_messages()* класса [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Затем добавьте эти сообщения в целевую папку другого PST файла.

```python
import aspose.email as ae

src_pst = ae.storage.pst.PersonalStorage.from_file("source.pst", False)
dest_pst = ae.storage.pst.PersonalStorage.from_file("destination.pst")

# Получите папку по имени
src_folder = src_pst.root_folder.get_sub_folder("SomeFolder")
dest_folder = dest_pst.root_folder.get_sub_folder("SomeFolder")

dest_folder.add_messages(src_folder.enumerate_mapi_messages())
```

### **Добавление сообщений из директории**

Чтобы добавить сообщения из директории, после открытия файла и получения ссылки на конкретную папку внутри PST файла, получите список имен файлов из директории, указанной переменной "path", и создайте пустой список MSG для загрузки каждого файла как MapiMessage. Добавьте каждое загруженное сообщение в msg_list. Пример кода ниже демонстрирует процесс добавления сообщений из директории:

```python
import aspose.email as ae
import os

pst = ae.storage.pst.PersonalStorage.from_file("my.pst", False)

# Получите папку по имени
folder = pst.root_folder.get_sub_folder("SomeFolder")

dirs = os.listdir("path")
msg_list = []

for file in dirs:
    msg = ae.mapi.MapiMessage.load(file)
    msg_list.append(msg)

folder.add_messages(iter(msg_list))
```