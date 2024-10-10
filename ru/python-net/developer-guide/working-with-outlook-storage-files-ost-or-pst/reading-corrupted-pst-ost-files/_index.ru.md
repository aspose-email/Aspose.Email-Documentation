---
title: "Чтение поврежденных PST/OST файлов"
url: /ru/python-net/reading-corrupted-pst-ost-files/
weight: 90
type: docs
---


## **Чтение поврежденных PST/OST файлов**

Иногда может возникнуть невозможность открыть PST файл из-за некоторых проблем. Одной из таких проблем является повреждение файла. Если PST файл поврежден или испорчен, его может быть невозможно открыть с помощью клиента электронной почты Outlook. Aspose.Email предоставляет API, предназначенное для сканирования поврежденного PST файла и чтения неповрежденных сообщений в файле по их идентификаторам.

Следующие методы класса [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) являются важными для решения этих задач:

Чтобы получить список идентификаторов:

- **find_messages(parent_entry_id)** - извлекает список идентификаторов сообщений в указанной папке.

- **find_subfolders(parent_entry_id)** - получает список идентификаторов подпапок в корневой папке.

Чтобы использовать эти идентификаторы для получения содержимого файла:

- **extract_message(entry_id)** - пытается извлечь сообщение.

- **get_folder_by_id(entry_id)** - получает доступ к каждой папке.

Следующий пример кода демонстрирует, как исследовать и получать доступ к содержимому потенциально поврежденного PST файла:

```py
import aspose.email as ae

def explore_corrupted_pst(pst, root_folder_id):
    message_id_list = pst.find_messages(root_folder_id)

    for message_id in message_id_list:
        try:
            msg = pst.extract_message(message_id)
            print("- " + msg.subject)
        except Exception as e:
            print("Ошибка чтения сообщения. Идентификатор записи: " + message_id)

    folder_id_list = pst.find_subfolders(root_folder_id)

    for sub_folder_id in folder_id_list:
        if sub_folder_id != root_folder_id:
            try:
                subfolder = pst.get_folder_by_id(sub_folder_id)
                print(subfolder.display_name)
            except Exception as e:
                print("Ошибка чтения сообщения. Идентификатор записи: " + sub_folder_id)

            explore_corrupted_pst(pst, sub_folder_id)


pst = ae.storage.pst.PersonalStorage.from_file("target.pst")

explore_corrupted_pst(pst, pst.root_folder.entry_id_string)
```