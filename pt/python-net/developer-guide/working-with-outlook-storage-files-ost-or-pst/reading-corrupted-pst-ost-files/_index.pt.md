---
title: "Lendo arquivos PST/OST corrompidos"
url: /pt/python-net/lendo-arquivos-pst-ost-corrompidos/
weight: 90
type: docs
---


## **Lendo arquivos PST/OST corrompidos**

Às vezes, pode não ser possível abrir um arquivo PST devido a alguns problemas. Um desses problemas é a corrupção do arquivo. Se um arquivo PST estiver corrompido ou danificado, pode não ser possível abrir o arquivo usando o cliente de email Outlook. Aspose.Email fornece uma API projetada para escanear um arquivo PST danificado e ler as mensagens não danificadas dentro de um arquivo por seus IDs.

Os seguintes métodos da classe [PersonalStorage](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#personalstorage-class) são essenciais para lidar com essas tarefas:

Para obter a lista de IDs:

- **find_messages(parent_entry_id)** - recupera uma lista de IDs de mensagens dentro de uma pasta especificada.

- **find_subfolders(parent_entry_id)** - obtém uma lista de IDs de subpastas dentro da pasta raiz.

Para usar esses IDs para obter o conteúdo do arquivo:

- **extract_message(entry_id)** - tenta recuperar uma mensagem.

- **get_folder_by_id(entry_id)** - acessa cada pasta.

O seguinte exemplo de código demonstra como explorar e acessar o conteúdo de um arquivo PST potencialmente corrompido:

```py
import aspose.email as ae

def explore_corrupted_pst(pst, root_folder_id):
    message_id_list = pst.find_messages(root_folder_id)

    for message_id in message_id_list:
        try:
            msg = pst.extract_message(message_id)
            print("- " + msg.subject)
        except Exception as e:
            print("Erro ao ler a mensagem. ID de entrada: " + message_id)

    folder_id_list = pst.find_subfolders(root_folder_id)

    for sub_folder_id in folder_id_list:
        if sub_folder_id != root_folder_id:
            try:
                subfolder = pst.get_folder_by_id(sub_folder_id)
                print(subfolder.display_name)
            except Exception as e:
                print("Erro ao ler a mensagem. ID de entrada: " + sub_folder_id)

            explore_corrupted_pst(pst, sub_folder_id)


pst = ae.storage.pst.PersonalStorage.from_file("target.pst")

explore_corrupted_pst(pst, pst.root_folder.entry_id_string)
```