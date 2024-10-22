---
title: "Dividir y fusionar archivos PST"
url: /es/python-net/splitting-and-merging-pst-files/
weight: 40
type: docs
---

La API Aspose.Email proporciona la capacidad de dividir un solo archivo PST en múltiples archivos PST de tamaño deseado. También puede fusionar múltiples archivos PST en un solo archivo PST. Ambas operaciones de dividir y fusionar archivos PST se pueden rastrear agregando eventos a estas operaciones.

{{% alert %}}
**¡Pruébalo!**

Fusiona y combina múltiples archivos de correo electrónico en línea en uno solo con la gratuita [**Aplicación de fusión de Aspose.Email**](https://products.aspose.app/email/es/merger).
{{% /alert %}}

## **Dividir en múltiples PSTs**
El siguiente fragmento de código muestra cómo dividir múltiples PSTs.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
dst_split = os.path.join(data_dir, "Chunks")

# Elimina los archivos si ya están presentes
for file in os.listdir(dst_split):
    file_path = os.path.join(dst_split, file)
    if os.path.isfile(file_path):
        os.remove(file_path)

pst_file = os.path.join(data_dir, "pst.pst")

try:
    with PersonalStorage.from_file(pst_file) as personal_storage:
        # Divide en fragmentos PST con un tamaño de 5MB
        personal_storage.split_into(5000000, dst_split)

except Exception as ex:
    print(str(ex))
    print("Este ejemplo solo funcionará si aplicas una licencia válida de Aspose.Email. "
          "Puedes comprar una licencia completa o obtener una licencia temporal de 30 días "
          "en http://www.aspose.com/purchase/default.aspx.")
```
## **Dividir PST según criterio especificado**
El siguiente fragmento de código muestra cómo dividir el PST basado en un criterio especificado.

```py
import os
from datetime import datetime
from aspose.email.tools.search import MailQueryBuilder
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
path_to_pst = os.path.join(data_dir, "pathToPst")
pst_file = os.path.join(data_dir, "PersonalStorage_New.pst")

# Definir criterios de búsqueda
builder = MailQueryBuilder()
builder.sent_date.since(datetime(2005, 4, 1))
builder.sent_date.before(datetime(2005, 4, 7))
query = builder.get_query()

# Eliminar archivos PST existentes si los hay
if os.path.exists(path_to_pst):
    for file in os.listdir(path_to_pst):
        file_path = os.path.join(path_to_pst, file)
        if os.path.isfile(file_path) and file.endswith(".pst"):
            os.remove(file_path)

# Dividir Almacenamiento Personal en múltiples archivos PST según criterios
with PersonalStorage.from_file(pst_file) as personal_storage:
    personal_storage.split_into(query, path_to_pst)
```
## **Fusionar en un solo PST**
El siguiente fragmento de código muestra cómo fusionar en un solo PST.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
sub_pst = os.path.join(data_dir, "Sub.pst")
merge_folder = os.path.join(data_dir, "MergePST")
total_added = 0

try:
    with PersonalStorage.from_file(sub_pst) as personal_storage:
        # Fusionar con los archivos PST ubicados en la carpeta separada.
        personal_storage.merge_with(os.path.join(merge_folder, "*"))
        print("Total de mensajes añadidos:", total_added)

    print("\nPST fusionado exitosamente en", sub_pst)
except Exception as ex:
    print(ex)
    print("Este ejemplo solo funcionará si aplicas una licencia válida de Aspose Email. "
          "Puedes comprar una licencia completa o obtener una licencia temporal de 30 días "
          "en http://www.aspose.com/purchase/default.aspx.")
```
## **Fusionar carpetas de otro PST**
El siguiente fragmento de código muestra cómo fusionar carpetas de otro PST.

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

        # Fusionar con la carpeta de otro PST.
        destination_folder.merge_with(source_folder)
        print("Total de mensajes añadidos:", total_added)

except Exception as ex:
    print(ex)
    print("Este ejemplo solo funcionará si aplicas una licencia válida de Aspose Email. "
          "Puedes comprar una licencia completa o obtener una licencia temporal de 30 días "
          "en http://www.aspose.com/purchase/default.aspx.")
```