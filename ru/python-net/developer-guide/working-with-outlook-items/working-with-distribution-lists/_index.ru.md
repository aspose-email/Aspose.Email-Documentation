---
title: "Работа со списками рассылки"
url: /ru/python-net/working-with-distribution-lists/
weight: 40
type: docs
---


С помощью Aspose.Email API можно создать список рассылки, который представляет собой набор из нескольких контактов. Список рассылки можно сохранить на диск в формате Outlook MSG и просматривать и изменять его, открывая его в MS Outlook.
## **Создание и сохранение списка рассылки**
В следующем фрагменте кода показано, как создать и сохранить список рассылки.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}

## **Чтение списка рассылки из PST**

В следующем фрагменте кода показано, как читать список рассылки из файла PST.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file( "your_pst_file.pst")
folder = pst.root_folder.get_sub_folder("Contacts")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    dlist = msg.to_mapi_message_item()
    if isinstance(dlist, ae.mapi.MapiDistributionList):
        for member in dlist.members:
            print("Member Display Name:", member.display_name)
            print("Member Email Address:", member.email_address)
```
