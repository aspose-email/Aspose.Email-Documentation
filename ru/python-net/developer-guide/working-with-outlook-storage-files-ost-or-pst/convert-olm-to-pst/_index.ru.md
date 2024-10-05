---
title: "Конвертировать OLM в PST"
url: /ru/python-net/convert-olm-to-pst/
weight: 90
type: docs
---


## **Конвертировать OLM в PST**

OLM (Outlook для Mac) — это формат файла, используемый Microsoft Outlook для Mac для хранения электронных писем, контактов, календарей, задач и других данных. Это родной формат файла для Outlook для Mac, поэтому невозможно открыть файл Outlook для Mac (OLM) в Outlook для Windows. Для работы с файлами OLM в Windows Aspose Email предоставляет инструменты, специально разработанные для обработки файлов OLM. Его подход заключается в конвертации файлов OLM в формат PST (файл данных Outlook), который широко поддерживается в средах Windows. После преобразования в формат PST вы можете импортировать данные в Outlook для Windows или любой другой совместимый почтовый клиент. Следующий пример кода покажет вам, как конвертировать OLM в PST.

**Миграция данных электронной почты из формата OLM в формат PST**

```py

import aspose.email as ae

# создайте экземпляр класса OlmStorage для открытия исходного OLM
olm = ae.storage.olm.OlmStorage("my.olm")
# создайте новый файл PST
pst = ae.storage.pst.PersonalStorage.create("my.pst", ae.storage.pst.FileFormatVersion.UNICODE)

# рекурсивно считывает каждую папку и ее сообщения
# и добавляет их в PST в том же порядке

for folder in olm.folder_hierarchy:
    add_to_pst(pst.root_folder, folder)
```
**Реализация 'get_container_class' для категоризации различных типов элементов Outlook**

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
**Реализация функции 'add_to_pst' для передачи данных из файла OLM в файл PST**

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