---
title: "Работа с контактами в файле PST"
url: /ru/python-net/working-with-contacts-in-pst-file/
weight: 60
type: docs
---


## **Добавление контакта в PST**
В статье «Создание нового файла PST и добавление подпапок» показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiContact в подпапку «Контакты» созданного или загруженного вами PST-файла. Ниже приведены шаги по добавлению MapiContact в PST:

1. Создайте объект MapiContact.
1. Задайте свойства MapiContact, используя различные конструкторы и методы.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предопределенную папку (Контакты) в корне файла PST, открыв корневую папку и вызвав метод add_mapi_message_item ().

В следующем фрагменте кода показано, как создать MapiContact, а затем добавить его в папку контактов вновь созданного файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiContactsAndAddToContactsSubFolder-CreateNewMapiContactsAndAddToContactsSubFolder.py" >}}
## **Сохраните информацию о контактах из файла PST в формате MSG**
В этой статье описывается, как получить доступ к контактной информации из файла Outlook PST и сохранить контакт на диск в формате MSG. Классы PersonalStorage и MapiContact для получения и отображения контактной информации. Чтобы получить контактную информацию, выполните следующие действия:

1. Загрузите файл PST в класс PersonalStorage.
1. Перейдите в папку «Контакты».
1. Получите содержимое папки «Контакты», чтобы получить коллекцию сообщений.
1. Просмотрите коллекцию сообщений.
1. Вызовите метод PersonalStorage.extract_Message (), чтобы получить контактную информацию в классе MapiMessage.
1. Вызовите метод MapiMessage.save (), чтобы сохранить контакт на диск в формате MSG.

В следующем фрагменте кода показано, как извлечь всю контактную информацию из файла PST и сохранить ее на диск в формате MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AccessContactInformation-AccessContactInformation.py" >}}
## **Сохранить информацию о контактах из файла PST в формате VCF**
В этой статье показано, как получить доступ к контактной информации из файла Microsoft Outlook PST и сохранить контакт на диск в формате vCard (VCF). Используйте классы PersonalStorage и MapiContact для получения контактной информации из файла PST. Чтобы получить контактную информацию, выполните следующие действия:

1. Загрузите файл PST в класс PersonalStorage.
1. Перейдите в папку «Контакты».
1. Получите содержимое папки «Контакты», чтобы получить коллекцию сообщений.
1. Просмотрите коллекцию сообщений.
1. Вызовите метод PersonalStorage.extract_Message (), чтобы получить контактную информацию в классе MapiContact.
1. Используйте различные свойства класса MapiContact для доступа к контактной информации.

Приведенная ниже программа загружает файл PST с диска и сохраняет все контакты в формате vCard (VCF). Затем файлы VCF можно использовать в любой другой программе, которая может загрузить стандартный файл контактов vCard. Если вы откроете какой-либо файл VCF в Microsoft Outlook, он будет выглядеть так, как показано на скриншоте ниже.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
|: - |
В следующем фрагменте кода показано, как экспортировать контакты из Outlook PST в формат vCard (VCF).



```py
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import ContactSaveFormat

# Load the Outlook PST file
pst = PersonalStorage.from_file("my.pst")

# Get the Contacts folder
folder_info = pst.root_folder.get_sub_folder("Contacts")

# Loop through all the contacts in this folder
message_info_collection = folder_info.get_contents()
for message_info in message_info_collection:
    # Get the contact information
    contact = pst.extract_message(message_info).to_mapi_message_item()

    # Display some contents on screen
    print("Name: " + contact.name_info.display_name + " - " + message_info.entry_id_string)

    # Save to disk in vCard VCF format
    contact.save("D:\\" + contact.name_info.display_name + ".vcf", ContactSaveFormat.V_CARD)
```
## **Работа со списками рассылки**
С помощью Aspose.Email API можно создать список рассылки, который представляет собой набор из нескольких контактов. Список рассылки можно сохранить на диск в формате Outlook MSG и просматривать и изменять его, открывая его в MS Outlook.
### **Создание и сохранение списка рассылки**
В следующем фрагменте кода показано, как создать и сохранить список рассылки.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}
### **Чтение списка рассылки из PST**
В следующем фрагменте кода показано, как читать список рассылки из PST.

```py
from aspose.email.mapi import MapiMessage

# Load the MAPI message from file
message = MapiMessage.load("dl.msg")

# Convert the message to MAPI distribution list
dlist = message.to_mapi_message_item()
```
