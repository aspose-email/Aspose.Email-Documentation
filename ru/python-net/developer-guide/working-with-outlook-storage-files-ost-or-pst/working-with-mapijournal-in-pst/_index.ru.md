---
title: "Работа с журналом MAPIjournal в формате PST"
url: /ru/python-net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Добавление журнала MAPIjournal в PST**
В статье «Создание нового файла PST и добавление подпапок» показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiJournal в подпапку Journal созданного или загруженного вами PST-файла. Ниже приведены шаги по добавлению MapiJournal в PST:

1. Создайте объект MapiJournal
1. Задайте свойства MapiJournal с помощью конструктора и методов.
1. Создайте PST с помощью метода PersonalStorage.create ().
1. Создайте предварительно определенную папку (Journals) в корне файла PST, открыв корневую папку и вызвав метод add_mapi_message_item ().

В следующем фрагменте кода показано, как создать MapiJournal, а затем добавить его в папку журнала вновь созданного файла PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiJournalAndAddToPST-CreateNewMapiJournalAndAddToPST.py" >}}
## **Добавление вложений в MapiJournal**
В следующем фрагменте кода показано, как добавлять вложения в MapiJournal.

```py
import os
from datetime import datetime, timedelta
from aspose.email.mapi import MapiJournal

data_dir = "path_to_data_directory"
attach_file_names = [os.path.join(data_dir, "Desert.jpg"), os.path.join(data_dir, "download.png")]

journal = MapiJournal("testJournal", "This is a test journal", "Phone call", "Phone call")
journal.start_time = datetime.now()
journal.end_time = journal.start_time + timedelta(hours=1)
journal.companies = ["company 1", "company 2", "company 3"]

for attach in attach_file_names:
    journal.attachments.append(attach, open(attach, 'rb').read())

journal.save(os.path.join(data_dir, "AddAttachmentsToMapiJournal_out.msg"))
```
