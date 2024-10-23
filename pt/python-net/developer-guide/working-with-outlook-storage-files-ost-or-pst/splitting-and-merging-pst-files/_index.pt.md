---
title: "Dividindo e Mesclando arquivos PST"
url: /pt/python-net/dividindo-e-mesclando-arquivos-pst/
weight: 40
type: docs
---


A API Aspose.Email fornece a capacidade de dividir um único arquivo PST em vários arquivos PST do tamanho desejado. Também pode mesclar vários arquivos PST em um único arquivo PST. Tanto as operações de divisão quanto de mesclagem de PSTs podem ser acompanhadas adicionando eventos a essas operações.

{{% alert %}}
**Experimente!**

Mescle e combine vários arquivos de e-mail online em um único com o gratuito [**Aspose.Email Merger App**](https://products.aspose.app/email/pt/merger).
{{% /alert %}}

## **Dividindo em múltiplos PSTs**
O seguinte trecho de código mostra como dividir múltiplos PSTs.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
dst_split = os.path.join(data_dir, "Chunks")

# Exclua os arquivos se já estiverem presentes
for file in os.listdir(dst_split):
    file_path = os.path.join(dst_split, file)
    if os.path.isfile(file_path):
        os.remove(file_path)

pst_file = os.path.join(data_dir, "pst.pst")

try:
    with PersonalStorage.from_file(pst_file) as personal_storage:
        # Divide em pedaços de PST com um tamanho de 5MB
        personal_storage.split_into(5000000, dst_split)

except Exception as ex:
    print(str(ex))
    print("Este exemplo só funcionará se você aplicar uma licença válida da Aspose.Email. "
          "Você pode comprar uma licença completa ou obter uma licença temporária de 30 dias em http://www.aspose.com/purchase/default.aspx.")
```
## **Dividindo PST com base em Critério Especificado**
O seguinte trecho de código mostra como dividir PST com base em critérios especificados.

```py
import os
from datetime import datetime
from aspose.email.tools.search import MailQueryBuilder
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
path_to_pst = os.path.join(data_dir, "pathToPst")
pst_file = os.path.join(data_dir, "PersonalStorage_New.pst")

# Defina os critérios de pesquisa
builder = MailQueryBuilder()
builder.sent_date.since(datetime(2005, 4, 1))
builder.sent_date.before(datetime(2005, 4, 7))
query = builder.get_query()

# Exclua os arquivos PST existentes, se houver
if os.path.exists(path_to_pst):
    for file in os.listdir(path_to_pst):
        file_path = os.path.join(path_to_pst, file)
        if os.path.isfile(file_path) and file.endswith(".pst"):
            os.remove(file_path)

# Divida o Armazenamento Pessoal em vários arquivos PST com base em critérios
with PersonalStorage.from_file(pst_file) as personal_storage:
    personal_storage.split_into(query, path_to_pst)
```
## **Mesclando em um único PST**
O seguinte trecho de código mostra como mesclar em um único PST.

```py
import os
from aspose.email.storage.pst import PersonalStorage

data_dir = "DataDir_Outlook"
sub_pst = os.path.join(data_dir, "Sub.pst")
merge_folder = os.path.join(data_dir, "MergePST")
total_added = 0

try:
    with PersonalStorage.from_file(sub_pst) as personal_storage:
        # Mescle com os arquivos PST localizados na pasta separada.
        personal_storage.merge_with(os.path.join(merge_folder, "*"))
        print("Total de mensagens adicionadas:", total_added)

    print("\nPST mesclado com sucesso em", sub_pst)
except Exception as ex:
    print(ex)
    print("Este exemplo só funcionará se você aplicar uma licença válida da Aspose Email. "
          "Você pode comprar uma licença completa ou obter uma licença temporária de 30 dias "
          "em http://www.aspose.com/purchase/default.aspx.")
```
## **Mesclando Pastas de outro PST**
O seguinte trecho de código mostra como mesclar pastas de outro PST.

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

        # Mescle com a pasta de outro PST.
        destination_folder.merge_with(source_folder)
        print("Total de mensagens adicionadas:", total_added)

except Exception as ex:
    print(ex)
    print("Este exemplo só funcionará se você aplicar uma licença válida da Aspose Email. "
          "Você pode comprar uma licença completa ou obter uma licença temporária de 30 dias "
          "em http://www.aspose.com/purchase/default.aspx.")
```