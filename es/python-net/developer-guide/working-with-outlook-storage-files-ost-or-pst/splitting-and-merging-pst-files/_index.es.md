---
title: "Dividir y combinar archivos PST"
url: /es/python-net/splitting-and-merging-pst-files/
weight: 40
type: docs
---


La API Aspose.Email ofrece la capacidad de dividir un único archivo PST en varios archivos PST del tamaño de archivo deseado. También puede combinar varios archivos PST en un solo archivo PST. Se puede rastrear tanto la división como la fusión de las operaciones de PST añadiendo eventos a estas operaciones.

{{% alert %}}
**¡Pruébalo!**

Combine y combine varios archivos de correo electrónico en línea en uno solo con el servicio gratuito [**Aplicación Aspose.Email Merger**](https://products.aspose.app/email/es/merger).
{{% /alert %}}

## **Dividir en varios PST**
El siguiente fragmento de código muestra cómo dividir varios PST.

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
## **División de PST según un criterio especificado**
El siguiente fragmento de código muestra cómo dividir PST según un criterio específico.

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
## **Fusión en un único PST**
El siguiente fragmento de código muestra cómo combinar en un único PST.

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
## **Combinar carpetas de otro PST**
El siguiente fragmento de código muestra cómo combinar carpetas de otro PST.

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
