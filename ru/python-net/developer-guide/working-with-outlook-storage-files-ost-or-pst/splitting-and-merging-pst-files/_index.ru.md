---
title: "Разделение и объединение PST файлов"
url: /ru/python-net/splitting-and-merging-pst-files/
weight: 40
type: docs
---

API Aspose.Email предоставляет возможность разделять один PST файл на несколько PST файлов заданного размера. Он также может объединять несколько PST файлов в один PST файл. Операции разделения и объединения PST могут отслеживаться путем добавления событий к этим операциям.

{{% alert %}}
**Попробуйте!**

Объедините и комбинируйте несколько email файлов онлайн в один с помощью бесплатного [**Aspose.Email Merger App**](https://products.aspose.app/email/ru/merger).
{{% /alert %}}

## **Разделение на несколько PST**
Следующий кодовый фрагмент показывает, как разделить несколько PST.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
dst_split = os.path.join(data_dir, "Chunks")

# Удалите файлы, если они уже присутствуют
for file in os.listdir(dst_split):
    file_path = os.path.join(dst_split, file)
    if os.path.isfile(file_path):
        os.remove(file_path)

pst_file = os.path.join(data_dir, "pst.pst")

try:
    with PersonalStorage.from_file(pst_file) as personal_storage:
        # Разделяет на куски PST размером 5MB
        personal_storage.split_into(5000000, dst_split)

except Exception as ex:
    print(str(ex))
    print("Этот пример будет работать только если у вас есть действующая лицензия Aspose.Email. "
          "Вы можете приобрести полноценную лицензию или получить 30-дневную"
          " временную лицензию на http://www.aspose.com/purchase/default.aspx.")
```
## **Разделение PST на основе заданного критерия**
Следующий кодовый фрагмент показывает, как разделить PST на основе заданного критерия.

```py
import os
from datetime import datetime
from aspose.email.tools.search import MailQueryBuilder
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
path_to_pst = os.path.join(data_dir, "pathToPst")
pst_file = os.path.join(data_dir, "PersonalStorage_New.pst")

# Определите критерии поиска
builder = MailQueryBuilder()
builder.sent_date.since(datetime(2005, 4, 1))
builder.sent_date.before(datetime(2005, 4, 7))
query = builder.get_query()

# Удалите существующие PST файлы, если таковые имеются
if os.path.exists(path_to_pst):
    for file in os.listdir(path_to_pst):
        file_path = os.path.join(path_to_pst, file)
        if os.path.isfile(file_path) and file.endswith(".pst"):
            os.remove(file_path)

# Разделите Личное Хранилище на несколько PST файлов на основе критериев
with PersonalStorage.from_file(pst_file) as personal_storage:
    personal_storage.split_into(query, path_to_pst)
```
## **Объединение в один PST**
Следующий кодовый фрагмент показывает, как объединить в один PST.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
sub_pst = os.path.join(data_dir, "Sub.pst")
merge_folder = os.path.join(data_dir, "MergePST")
total_added = 0

try:
    with PersonalStorage.from_file(sub_pst) as personal_storage:
        # Объединение с PST файлами, расположенными в отдельной папке.
        personal_storage.merge_with(os.path.join(merge_folder, "*"))
        print("Всего добавлено сообщений:", total_added)

    print("\nPST успешно объединен в", sub_pst)
except Exception as ex:
    print(ex)
    print("Этот пример будет работать только если у вас есть действующая лицензия Aspose Email. "
          "Вы можете приобрести полноценную лицензию или получить 30-дневную временную лицензию "
          "на http://www.aspose.com/purchase/default.aspx.")
```
## **Объединение папок из другого PST**
Следующий кодовый фрагмент показывает, как объединить папки из другого PST.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder

data_dir = "DataDir_Outlook\\"
destination_pst = PersonalStorage.from_file(data_dir + "destination.pst")
source_pst = PersonalStorage.from_file(data_dir + "source.pst")
total_added = 0

try:
    with destination_pst, source_pst:
        destination_folder = destination_pst.root_folder.add_sub_folder("FolderFromAnotherPst")
        source_folder = source_pst.get_predefined_folder(StandardIpmFolder.DELETED_ITEMS)

        # Объединение с папкой из другого PST.
        destination_folder.merge_with(source_folder)
        print("Всего добавлено сообщений:", total_added)

except Exception as ex:
    print(ex)
    print("Этот пример будет работать только если у вас есть действующая лицензия Aspose Email. "
          "Вы можете приобрести полноценную лицензию или получить 30-дневную временную лицензию "
          "на http://www.aspose.com/purchase/default.aspx.")
```