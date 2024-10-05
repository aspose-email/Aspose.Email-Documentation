---
title: "Работа с MapiJournal в PST"
url: /ru/python-net/working-with-mapijournal-in-pst/
weight: 70
type: docs
---


## **Добавление MapiJournal в PST**
Создание нового PST файла и добавление подпапок показало, как создать PST файл и добавить подпапку к нему. С помощью Aspose.Email вы можете добавить MapiJournal в подпапку Journal PST файла, который вы создали или загрузили. Ниже приведены шаги для добавления MapiJournal в PST:

1. Создайте объект MapiJournal
1. Установите свойства MapiJournal, используя конструктор и методы.
1. Создайте PST, используя метод PersonalStorage.create().
1. Создайте предопределенную папку (Journals) в корне PST файла, получив доступ к корневой папке и затем вызвав метод add_mapi_message_item().

Следующий фрагмент кода показывает, как создать MapiJournal и затем добавить его в папку журналов вновь созданного PST файла.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiJournalAndAddToPST-CreateNewMapiJournalAndAddToPST.py" >}}
## **Добавление вложений в MapiJournal**
Следующий фрагмент кода показывает, как добавить вложения в MapiJournal.

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