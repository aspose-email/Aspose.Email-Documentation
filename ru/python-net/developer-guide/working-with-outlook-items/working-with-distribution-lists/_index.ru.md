---
title: "Работа с Распределительными Списками"
url: /ru/python-net/working-with-distribution-lists/
weight: 40
type: docs
---


Можно создать распределительный список с помощью Aspose.Email API, который представляет собой коллекцию нескольких контактов. Распределительный список можно сохранить на диск в формате Outlook MSG и просматривать/манипулировать им, открыв в MS Outlook.
## **Создание и Сохранение Распределительного Списка**
Следующий фрагмент кода показывает, как создать и сохранить распределительный список.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}

## **Чтение Распределительного Списка из PST**

Следующий фрагмент кода показывает, как прочитать распределительный список из файла PST.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file( "your_pst_file.pst")
folder = pst.root_folder.get_sub_folder("Contacts")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    dlist = msg.to_mapi_message_item()
    if isinstance(dlist, ae.mapi.MapiDistributionList):
        for member in dlist.members:
            print("Имя пользователя:", member.display_name)
            print("Электронный адрес пользователя:", member.email_address)
```