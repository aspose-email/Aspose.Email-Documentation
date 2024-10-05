---
title: "Работа с контактами в PST файле"
url: /ru/python-net/working-with-contacts-in-pst-file/
weight: 60
type: docs
---


## **Добавление контакта в PST**
Создание нового файла PST и добавление подпапок показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiContact в подпапку Контакты файла PST, который вы создали или загрузили. Ниже приведены шаги для добавления MapiContact в PST:

1. Создайте объект MapiContact.
1. Установите свойства MapiContact, используя различные конструкторы и методы.
1. Создайте PST с помощью метода PersonalStorage.create().
1. Создайте предопределенную папку (Контакты) в корне файла PST, получив доступ к корневой папке и затем вызвав метод add_mapi_message_item().

Следующий фрагмент кода показывает, как создать MapiContact и затем добавить его в папку контактов только что созданного файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiContactsAndAddToContactsSubFolder-CreateNewMapiContactsAndAddToContactsSubFolder.py" >}}
## **Сохранение информации о контактах из PST файла в формате MSG**
В этой статье объясняется, как получить информацию о контактах из файла Outlook PST и сохранить контакт на диск в формате MSG. Классы PersonalStorage и MapiContact используются для получения и отображения информации о контактах. Шаги для получения информации о контактах:

1. Загрузите файл PST в класс PersonalStorage.
1. Просмотрите папку Контакты.
1. Получите содержимое папки Контакты, чтобы получить коллекцию сообщений.
1. Пройдите через коллекцию сообщений.
1. Вызовите метод PersonalStorage.extract_message(), чтобы получить информацию о контакте в классе MapiMessage.
1. Вызовите метод MapiMessage.save(), чтобы сохранить контакт на диск в формате MSG.

Следующий фрагмент кода показывает, как извлечь всю информацию о контакте из файла PST и сохранить на диск в формате MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AccessContactInformation-AccessContactInformation.py" >}}
## **Сохранение информации о контактах из PST файла в формате VCF**
Эта статья показывает, как получить информацию о контактах из файла PST Microsoft Outlook и сохранить контакт на диск в формате vCard (VCF). Используйте классы PersonalStorage и MapiContact для получения информации о контактах из файла PST. Чтобы получить информацию о контактах:

1. Загрузите файл PST в класс PersonalStorage.
1. Просмотрите папку Контакты.
1. Получите содержимое папки Контакты, чтобы получить коллекцию сообщений.
1. Пройдите через коллекцию сообщений.
1. Вызовите метод PersonalStorage.extract_message(), чтобы получить информацию о контакте в классе MapiContact.
1. Используйте различные свойства класса MapiContact для доступа к информации о контакте.

Программа ниже загружает файл PST с диска и сохраняет все контакты в формате vCard (VCF). Файлы VCF затем могут быть использованы в любой другой программе, которая может загрузить стандартный файл контактов vCard. Если вы откроете любой файл VCF в Microsoft Outlook, он будет выглядеть как на скриншоте ниже.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
Следующий фрагмент кода показывает, как экспортировать контакты из Outlook PST в формат vCard (VCF).



```py
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import ContactSaveFormat

# Загрузите файл PST Outlook
pst = PersonalStorage.from_file("my.pst")

# Получите папку Контакты
folder_info = pst.root_folder.get_sub_folder("Contacts")

# Пройдите через все контакты в этой папке
message_info_collection = folder_info.get_contents()
for message_info in message_info_collection:
    # Получите информацию о контакте
    contact = pst.extract_message(message_info).to_mapi_message_item()

    # Отобразите некоторые данные на экране
    print("Имя: " + contact.name_info.display_name + " - " + message_info.entry_id_string)

    # Сохраните на диск в формате vCard VCF
    contact.save("D:\\" + contact.name_info.display_name + ".vcf", ContactSaveFormat.V_CARD)
```
## **Работа с рассылками**
С помощью API Aspose.Email можно создать рассылку, которая представляет собой коллекцию нескольких контактов. Рассылку можно сохранить на диск в формате Outlook MSG и просматривать/изменять, открыв ее в MS Outlook.
### **Создание и сохранение рассылки**
Следующий фрагмент кода показывает, как создать и сохранить рассылку.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}
### **Чтение рассылки из PST**
Следующий фрагмент кода показывает, как прочитать рассылку из PST.

```py
from aspose.email.mapi import MapiMessage

# Загрузите MAPI сообщение из файла
message = MapiMessage.load("dl.msg")

# Преобразуйте сообщение в MAPI рассылку
dlist = message.to_mapi_message_item()
```