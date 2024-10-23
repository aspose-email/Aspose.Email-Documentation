---
title: "Converter OLM para PST"
url: /pt/python-net/convert-olm-to-pst/
weight: 90
type: docs
---


## **Converter OLM para PST**

OLM (Outlook para Mac) é um formato de arquivo usado pelo Microsoft Outlook para Mac para armazenar mensagens de e-mail, contatos, calendários, tarefas e outros dados. É o formato de arquivo nativo para o Outlook para Mac, portanto, não é possível abrir um arquivo Outlook para Mac (OLM) no Outlook para Windows. Para trabalhar com arquivos OLM no Windows, o Aspose Email fornece ferramentas projetadas especificamente para lidar com arquivos OLM. Sua abordagem é converter arquivos OLM para o formato PST (Arquivo de Dados do Outlook), que é amplamente suportado em ambientes Windows. Uma vez convertido para o formato PST, você pode importar os dados para o Outlook para Windows ou qualquer outro cliente de e-mail compatível. O seguinte exemplo de código mostrará como converter um OLM em um PST.

**Migração de dados de e-mail do formato OLM para PST**

```py

import aspose.email as ae

# crie uma instância da classe OlmStorage para abrir o OLM de origem
olm = ae.storage.olm.OlmStorage("my.olm")
# crie um novo arquivo PST
pst = ae.storage.pst.PersonalStorage.create("my.pst", ae.storage.pst.FileFormatVersion.UNICODE)

# lê recursivamente cada pasta e suas mensagens
# e as adiciona ao PST na mesma ordem

for folder in olm.folder_hierarchy:
    add_to_pst(pst.root_folder, folder)
```
**Implementação de 'get_container_class' para categorizar diferentes tipos de itens do Outlook**

```py
def get_container_class(message_class):
    if message_class.startswith("IPM.Contact") or message_class.startswith("IPM.DistList"):
        return "IPF.Contact"

    if message_class.startswith("IPM.StickyNote"):
        return "IPF.StickyNote"

    if message_class.startswith("IPM.Activity"):
        return "IPF.Journal"

    if message_class.startswith("IPM.Task"):
        return "IPF.Task"

    if message_class.startswith("IPM.Appointment") or message_class.startswith("IPM.Schedule.meeting"):
        return "IPF.Appointment"

    return "IPF.Note"
```
**Implementação da função 'add_to_pst' para transferir dados de um arquivo OLM para um arquivo PST**

```py

def add_to_pst(pst_folder, olm_folder):
    pst_sub_folder = pst_folder.get_sub_folder(olm_folder.name)

    for msg in olm_folder.enumerate_mapi_messages():
        if pst_sub_folder is None:
            pst_sub_folder = pst_folder.add_sub_folder(olm_folder.name, get_container_class(msg.message_class))

        pst_sub_folder.add_message(msg)

    if pst_sub_folder is None:
        pst_sub_folder = pst_folder.add_sub_folder(olm_folder.name)

    for olm_sub_folder in olm_folder.sub_folders:
        add_to_pst(pst_sub_folder, olm_sub_folder)
```