---
title: Splitting and Merging PST files
ArticleTitle: Splitting and Merging PST files
type: docs
weight: 40
url: /python-net/splitting-and-merging-pst-files/
---


Aspose.Email API provides the capability to split a single PST file into multiple PST files of desired file size. It can also merge multiple PST files into a single PST file. Both the splitting and merging of PSTs operations can be tracked by adding events to these operations.

{{% alert %}}
**Try it out!**

Merge and combine multiple email files online into a single one with the free [**Aspose.Email Merger App**](https://products.aspose.app/email/merger).
{{% /alert %}}

## **Splitting into multiple PSTs**
The following code snippet shows you how to split multiple PSTs.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
dst_split = os.path.join(data_dir, "Chunks")

# Delete the files if already present
for file in os.listdir(dst_split):
    file_path = os.path.join(dst_split, file)
    if os.path.isfile(file_path):
        os.remove(file_path)

pst_file = os.path.join(data_dir, "pst.pst")

try:
    with PersonalStorage.from_file(pst_file) as personal_storage:
        # Splits into PST chunks with a size of 5MB
        personal_storage.split_into(5000000, dst_split)

except Exception as ex:
    print(str(ex))
    print("This example will only work if you apply a valid Aspose.Email License. "
          "You can purchase a full license or get a 30-day"
          " temporary license from http://www.aspose.com/purchase/default.aspx.")
```
## **Splitting PST based on Specified Criterion**
The following code snippet shows you how to split PST based on specified criterion.

```py
import os
from datetime import datetime
from aspose.email.tools.search import MailQueryBuilder
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
path_to_pst = os.path.join(data_dir, "pathToPst")
pst_file = os.path.join(data_dir, "PersonalStorage_New.pst")

# Define search criteria
builder = MailQueryBuilder()
builder.sent_date.since(datetime(2005, 4, 1))
builder.sent_date.before(datetime(2005, 4, 7))
query = builder.get_query()

# Delete existing PST files if any
if os.path.exists(path_to_pst):
    for file in os.listdir(path_to_pst):
        file_path = os.path.join(path_to_pst, file)
        if os.path.isfile(file_path) and file.endswith(".pst"):
            os.remove(file_path)

# Split Personal Storage into multiple PST files based on criteria
with PersonalStorage.from_file(pst_file) as personal_storage:
    personal_storage.split_into(query, path_to_pst)
```
## **Merging into a single PST**
The following code snippet shows you how to merge into a single PST.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
sub_pst = os.path.join(data_dir, "Sub.pst")
merge_folder = os.path.join(data_dir, "MergePST")
total_added = 0

try:
    with PersonalStorage.from_file(sub_pst) as personal_storage:
        # Merge with the PST files located in the separate folder.
        personal_storage.merge_with(os.path.join(merge_folder, "*"))
        print("Total messages added:", total_added)

    print("\nPST merged successfully at", sub_pst)
except Exception as ex:
    print(ex)
    print("This example will only work if you apply a valid Aspose Email License. "
          "You can purchase a full license or get a 30-day temporary license "
          "from http://www.aspose.com/purchase/default.aspx.")
```
## **Merging Folders from another PST**
The following code snippet shows you how to merging folders from another PST.

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

        # Merge with the folder from another PST.
        destination_folder.merge_with(source_folder)
        print("Total messages added:", total_added)

except Exception as ex:
    print(ex)
    print("This example will only work if you apply a valid Aspose Email License. "
          "You can purchase a full license or get a 30-day temporary license "
          "from http://www.aspose.com/purchase/default.aspx.")
```
