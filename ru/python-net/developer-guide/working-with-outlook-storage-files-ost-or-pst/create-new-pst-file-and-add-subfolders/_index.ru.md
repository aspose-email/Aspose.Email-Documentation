---
title: "Создайте новый файл PST и добавьте подпапки"
url: /ru/python-net/create-new-pst-file-and-add-subfolders/
weight: 10
type: docs
---


Помимо анализа существующего файла PST, Aspose.Email предоставляет средства для создания файла PST с нуля. В этой статье показано, как создать файл Outlook PST и добавить в него подпапку.

1. Создание нового файла PST.
1. Изменение класса контейнера папки.

Используйте класс PersonalStorage для создания файла PST в каком-либо месте на локальном диске. Чтобы создать файл PST с нуля, выполните следующие действия:

1. Создайте PST с помощью метода PersonalStorage.create ().
1. Добавьте подпапку в корень файла PST, открыв корневую папку и вызвав метод AddSubFolder.

В следующем фрагменте кода показано, как создать файл PST и добавить подпапку под названием «Входящие».



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.py" >}}

## **Проверка соответствия классов контейнеров при добавлении папки в PST**

Aspose.Email для Python предлагает решение, которое улучшает процесс проверки при создании папок в файлах PST. С помощью свойства «EnforceContainerClassMatching» в [FolderCreationOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) класс, вы можете обеспечить строгое соответствие классов контейнеров при добавлении новой папки в хранилище PST. Эта функция помогает поддерживать организационную иерархию в файле PST, предотвращая несовпадения в классах контейнеров. Если для параметра EnforceContainerClassMatching задано значение «true», в случае несовпадения классов контейнеров родительской и дочерней папок будет создано исключение, что обеспечит защиту от неправильной структуры папок. По умолчанию это свойство имеет значение «false», что позволяет гибко создавать папки и при необходимости применять строгое соответствие классов контейнеров.

В следующем примере кода показано использование свойства 'EnforceContainerClassMatching' для управления тем, следует ли создавать исключение при добавлении папок с несовпадающими классами контейнеров:

```py
with PersonalStorage.create("storage.pst", FileFormatVersion.Unicode) as pst:
    contacts = pst.createpredefinedfolder("Contacts", StandardIpmFolder.Contacts)
   
    # An exception will not arise. EnforceContainerClassMatching is False by default.
    contacts.addsubfolder("Subfolder1", "IPF.Note")
   
    # An exception will occur as the container class of the subfolder being added (IPF.Note)
    # does not match the container class of the parent folder (IPF.Contact).
    contacts.addsubfolder("Subfolder3", FolderCreationOptions(enforcecontainerclassmatching=True, containerclass="IPF.Note"))
```

## **Изменение класса контейнера папки**
Иногда необходимо изменить класс папки. Типичный пример: сообщения разных типов (встречи, сообщения и т. д.) добавляются в одну и ту же папку. В таких случаях класс папки необходимо изменить, чтобы все элементы в папке отображались корректно. В следующем фрагменте кода показано, как изменить класс контейнера папки в PST для этой цели.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ChangeFolderContainerClass-ChangeFolderContainerClass.py" >}}

## **Добавляйте массовые сообщения с улучшенной производительностью**

Добавление массовых сообщений в файл PST в отличие от добавления их по отдельности может дать ряд преимуществ, в частности с точки зрения эффективности и производительности: меньшее количество операций ввода-вывода, сокращение времени выполнения задачи, более эффективное использование системных ресурсов и т. д. *add_messages* метод [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) класс используется для переноса коллекции сообщений MAPI, полученных из исходной папки, в папку назначения.

### **Добавить сообщения из другого PST**

Чтобы перечислить и получить все сообщения MAPI из исходной папки файла PST, используйте *enumerate_mapi_messages()* метод [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) класс. Затем добавьте эти сообщения в папку назначения другого файла PST.

```python
import aspose.email as ae

src_pst = ae.storage.pst.PersonalStorage.from_file("source.pst", False)
dest_pst = ae.storage.pst.PersonalStorage.from_file("destination.pst")

# Get the folder by name
src_folder = src_pst.root_folder.get_sub_folder("SomeFolder")
dest_folder = dest_pst.root_folder.get_sub_folder("SomeFolder")

dest_folder.add_messages(src_folder.enumerate_mapi_messages())
```

### **Добавить сообщения из каталога**

Чтобы добавить сообщения из каталога, после открытия файла и получения ссылки на определенную папку в файле PST извлеките список имен файлов из каталога, указанного переменной «path», и создайте пустой список MSG для загрузки каждого файла в виде MapiMessage. Добавьте каждое загруженное сообщение в msg_list. В приведенном ниже примере кода показан процесс добавления сообщений из каталога:

```python
import aspose.email as ae
import os

pst = ae.storage.pst.PersonalStorage.from_file("my.pst", False)

# Get the folder by name
folder = pst.root_folder.get_sub_folder("SomeFolder")

dirs = os.listdir("path")
msg_list = []

for file in dirs:
    msg = ae.mapi.MapiMessage.load(file)
    msg_list.append(msg)

folder.add_messages(iter(msg_list))
```