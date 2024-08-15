---
title: "Чтение поврежденных файлов PST/OST"
url: /ru/python-net/reading-corrupted-pst-ost-files/
weight: 90
type: docs
---


## **Чтение поврежденных файлов PST/OST**

Иногда из-за некоторых проблем может быть невозможно открыть файл PST. Одной из таких проблем является повреждение файла. Если файл PST поврежден или поврежден, возможно, его невозможно открыть с помощью почтового клиента Outlook. Aspose.Email предоставляет API, предназначенный для сканирования поврежденного файла PST и чтения неповрежденных сообщений в файле по их идентификаторам.

Следующие методы [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) классы необходимы для решения следующих задач:

Чтобы получить список идентификаторов, выполните следующие действия:

- **find_messages(parent_entry_id)** - извлекает список идентификаторов сообщений в указанной папке.

- **find_subfolders(parent_entry_id)** - получает список идентификаторов подпапок в корневой папке.

Чтобы использовать эти идентификаторы для получения содержимого файла, выполните следующие действия:

- **extract_message(entry_id)** - пытается получить сообщение.

- **get_folder_by_id(entry_id)** - получает доступ к каждой папке.

В следующем примере кода показано, как исследовать и получить доступ к содержимому потенциально поврежденного PST-файла:

```py
import aspose.email as ae

def explore_corrupted_pst(pst, root_folder_id):
    message_id_list = pst.find_messages(root_folder_id)

    for message_id in message_id_list:
        try:
            msg = pst.extract_message(message_id)
            print("- " + msg.subject)
        except Exception as e:
            print("Message reading error. Entry id: " + message_id)

    folder_id_list = pst.find_subfolders(root_folder_id)

    for sub_folder_id in folder_id_list:
        if sub_folder_id != root_folder_id:
            try:
                subfolder = pst.get_folder_by_id(sub_folder_id)
                print(subfolder.display_name)
            except Exception as e:
                print("Message reading error. Entry id: " + sub_folder_id)

            explore_corrupted_pst(pst, sub_folder_id)


pst = ae.storage.pst.PersonalStorage.from_file("target.pst")

explore_corrupted_pst(pst, pst.root_folder.entry_id_string)
```