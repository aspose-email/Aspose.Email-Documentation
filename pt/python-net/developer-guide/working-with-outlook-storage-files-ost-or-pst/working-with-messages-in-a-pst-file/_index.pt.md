---
title: "Trabalhando com Mensagens em um Arquivo PST"
url: /pt/python-net/trabalhando-com-mensagens-em-um-arquivo-pst/
weight: 100
type: docs
---


## **Adicionando Mensagens a Arquivos PST**
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar mensagens a subpastas de um arquivo PST que você criou ou carregou. Este artigo adiciona duas mensagens do disco à subpasta Caixa de Entrada de um PST. Use as classes PersonalStorage e FolderInfo para adicionar mensagens a arquivos PST. Para adicionar mensagens à pasta Caixa de Entrada de um arquivo PST:

1. Crie uma instância da classe FolderInfo e carregue-a com o conteúdo da pasta Caixa de Entrada.
1. Adicione mensagens do disco à pasta Caixa de Entrada chamando o método FolderInfo.add_message(). A classe FolderInfo expõe o método add_messages que permite adicionar um grande número de mensagens à pasta, reduzindo operações de I/O no disco e melhorando o desempenho. Um exemplo completo pode ser encontrado abaixo, na seção Adicionando Mensagens em Lote.

Os trechos de código abaixo mostram como adicionar mensagens a uma subpasta PST chamada Caixa de Entrada.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesToPSTFiles-AddMessagesToPSTFiles.py" >}}
### **Adicionando Mensagens em Lote**
Adicionar mensagens individuais a um PST implica mais operações de I/O no disco e, portanto, pode diminuir o desempenho. Para melhorar o desempenho, as mensagens podem ser adicionadas ao PST em modo de lote para minimizar as operações de I/O. O método add_messages permite que você defina um intervalo de mensagens a ser adicionado ao PST para melhorar o desempenho e pode ser usado nas seguintes situações.
### **Carregando Mensagens do Disco**
O seguinte trecho de código mostra como carregar mensagens do disco.

```py
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion


def add_messages_in_bulk_mode(file_name, msg_folder_name):
    with PersonalStorage.from_file(file_name) as personal_storage:
        folder = personal_storage.root_folder.get_sub_folder("myInbox")
        folder.add_messages(message_collection(msg_folder_name))

# Uso
add_messages_in_bulk_mode("file.pst", "folder_with_messages")
```
### **Implementação de MapiMessageCollection**
O seguinte trecho de código mostra como implementar MapiMessageCollection.

```py
import os
from aspose.email.mapi import MapiMessage


class MapiMessageEnumerator:
    def __init__(self, path):
        self.files = os.listdir(path)
        self.position = -1

    def __next__(self):
        self.position += 1
        if self.position < len(self.files):
            return MapiMessage.from_file(os.path.join(self.path, self.files[self.position]))
        else:
            raise StopIteration

    def __iter__(self):
        return self


class MapiMessageCollection:
    def __init__(self, path):
        self.path = path

    def __iter__(self):
        return MapiMessageEnumerator(self.path)


# Uso
msg_folder_name = "\\Files\\msg"

message_collection = MapiMessageCollection(msg_folder_name)
for message in message_collection:
    # Faça algo com cada MapiMessage
    pass
```
### **Adicionando Mensagens de Outro PST**
Para adicionar mensagens de outro PST, use o método FolderInfo.enumerate_mapi_messages(). O seguinte trecho de código mostra como adicionar mensagens de outros PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMessagesFromOtherPST-AddMessagesFromOtherPST.py" >}}
## **Obter Informações de Mensagens de um Arquivo PST do Outlook**
No artigo Leia um Arquivo PST do Outlook e Obtenha Informações sobre Pastas e Subpastas, discutimos o carregamento de um arquivo PST do Outlook e a navegação em suas pastas para obter os nomes das pastas e o número de mensagens nelas. Este artigo explica como ler todas as pastas e subpastas no arquivo PST e exibir informações sobre mensagens, por exemplo, assunto, remetente e destinatários. O arquivo PST do Outlook pode conter pastas aninhadas. Para obter informações sobre mensagens destas, bem como das pastas de nível superior, use um método recursivo para ler todas as pastas. O seguinte trecho de código mostra como ler um arquivo PST do Outlook e exibir o conteúdo das pastas e mensagens recursivamente.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-GetMessagesInformation-GetMessagesInformation.py" >}}
## **Extraindo Mensagens de Arquivos PST**

Este artigo mostra como ler arquivos PST do Microsoft Outlook e extrair mensagens. Abaixo está um trecho de código mostrando como extrair mensagens de um arquivo PST.

```python
from aspose.email.storage.pst import *
from aspose.email.mapi import MapiMessage

pst = PersonalStorage.from_file("Outlook.pst")

folderInfo = pst.root_folder

messageInfoCollection = folderInfo.get_contents()

for messageInfo in messageInfoCollection:
   mapi = pst.extract_message(messageInfo)

   print("Assunto: " + mapi.subject)
   print("Nome do remetente: " + mapi.sender_name)
   print("Endereço de email do remetente: " + mapi.sender_email_address)
   print("Para: ", mapi.display_to)
   print("Cc: ", mapi.display_cc)
   print("Cco: ", mapi.display_bcc)
   print("Hora de entrega: ", str(mapi.delivery_time))
   print("Corpo: " + mapi.body)
```
### **Extraindo n Número de Mensagens de um Arquivo PST**

Para extrair um número específico de mensagens de um arquivo PST, use o método *get_contents(start_index, count)* da classe [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Ele aceita dois parâmetros:

- **start_index** - o número da mensagem inicial, por exemplo, a 10ª;
- **count** - número total de mensagens a serem recuperadas.

Recuperar apenas o subconjunto necessário de mensagens de cada vez pode ser útil para gerenciar grandes volumes de dados de e-mail. O seguinte exemplo de código demonstra a implementação deste recurso:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")

# Extrai mensagens começando do 10º índice e extrai um total de 100 mensagens
messages = folder.get_contents(10, 100)
```
### **Obtendo a Contagem Total de Itens de um Arquivo PST**

Para recuperar o número total de itens (como e-mails, compromissos, tarefas, contatos, etc.) presentes no repositório de mensagens, use o método *get_total_items_count()* da classe [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class). Isso fornece uma maneira conveniente de reunir informações rapidamente sobre o tamanho e o volume de dados dentro do repositório. O seguinte trecho de código mostra como obter o número total de itens de um arquivo PST:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

count = pst.store.get_total_items_count()
```

## **Excluir Mensagens de Arquivos PST**
Adicionar Mensagens a Arquivos PST mostrou como adicionar mensagens a arquivos PST. É, claro, também possível excluir itens (conteúdos) de um arquivo PST e também pode ser desejável excluir mensagens em lote. Itens de um arquivo PST podem ser excluídos usando o método FolderInfo.delete_child_item(). A API também fornece o método FolderInfo.delete_child_items() para excluir itens em lote do arquivo PST.
### **Excluindo Mensagens de Arquivos PST**
Este artigo mostra como usar a classe FolderInfo para acessar pastas específicas em um arquivo PST. Para excluir mensagens da subpasta Enviados de um arquivo PST carregado ou criado anteriormente:

1. Crie uma instância da classe FolderInfo e carregue-a com o conteúdo da subpasta Enviados.
1. Exclua mensagens da pasta Enviados chamando o método FolderInfo.delete_child_item() e passando o MessageInfo.entry_id como parâmetro. O seguinte trecho de código mostra como excluir mensagens da subpasta Enviados de um arquivo PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteMessagesFromPSTFile-DeleteMessagesFromPSTFile.py" >}}

### **Excluindo Pastas de Arquivos PST**

Você pode excluir uma pasta PST movendo-a para a pasta Itens Excluídos.

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

deleted_items_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.DELETED_ITEMS)
empty_folder = pst.root_folder.get_sub_folder("Empty folder")
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(empty_folder, deleted_items_folder)
pst.move_item(some_folder, deleted_items_folder)
```
A vantagem deste método é que a pasta excluída pode ser facilmente recuperada.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.move_item(some_folder, pst.root_folder)
```
Você também pode remover permanentemente uma pasta da pasta Itens Excluídos, se necessário.


```python
deleted_items_folder.delete_child_item(empty_folder.entry_id)
```
O método *delete_child_item* pode ser usado para qualquer pasta se você quiser excluir imediatamente e permanentemente uma subpasta, passando pela pasta Itens Excluídos.


```python
some_folder = pst.root_folder.get_sub_folder("Some folder")
pst.root_folder.delete_child_item(some_folder.entry_id)
```
### **Excluir Itens de PST**

Em muitos sistemas de mensagens ou clientes de e-mail, cada item (como um e-mail, compromissos ou tarefas) é atribuído a um identificador exclusivo chamado entry ID. O método *delete_item(entry_id)* da classe [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) aceita esse entry ID como parâmetro e remove o item correspondente do repositório de mensagens. Use o seguinte código para excluir um item do repositório de mensagens:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

# ...

pst.delete_item(entry_id)

# ...
```

### **Excluir Itens em Lote de um Arquivo PST**
A API Aspose.Email pode ser usada para excluir itens em lote de um arquivo PST. Isso é alcançado usando o método delete_child_items() que aceita uma lista de itens de Entry ID referindo-se aos itens a serem excluídos. O seguinte trecho de código mostra como excluir itens em lote de um arquivo PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-DeleteBulkItemsFromPst-DeleteBulkItemsFromPst.py" >}}
## **Pesquisar Mensagens e Pastas em um PST por Critério**
Arquivos de Armazenamento Pessoal (PST) podem conter uma enorme quantidade de dados e buscar dados que atendem a um critério específico em arquivos tão grandes precisa incluir múltiplos pontos de verificação no código para filtrar as informações. Com a classe PersonalStorageQueryBuilder, a Aspose.Email torna possível pesquisar registros específicos em um PST com base em um critério de busca especificado. Um PST pode ser pesquisado por mensagens com base em parâmetros de busca como remetente, destinatário, assunto, importância da mensagem, presença de anexos, tamanho da mensagem e até mesmo ID da mensagem. A PersonalStorageQueryBuilder também pode ser usada para pesquisar subpastas.
### **Pesquisando Mensagens e Pastas em PST**
O seguinte trecho de código mostra como usar a classe PersonalStorageQueryBuilder para pesquisar conteúdos em um PST com base em diferentes critérios de busca. Por exemplo, ele mostra a busca em um PST com base em:

- Importância da mensagem.
- Classe da mensagem.
- Presença de anexos.
- Tamanho da mensagem.
- Mensagens não lidas.
- Mensagens não lidas com anexos, e
- pastas com nome de subpasta específico.

```py
from aspose.email.mapi import MapiMessageFlags
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder, MapiImportance

with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")
    builder = PersonalStorageQueryBuilder()

    # Mensagens de alta importância
    builder.importance.equals(2)
    messages = folder.get_contents(builder.get_query())
    print("Mensagens com Alta Imp:", messages.count)

    builder = PersonalStorageQueryBuilder()
    builder.message_class.equals("IPM.Note")
    messages = folder.get_contents(builder.get_query())
    print("Mensagens com IPM.Note:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensagens com anexos E alta importância
    builder.importance.equals(2)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Mensagens com anexos:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensagens com tamanho > 15 KB
    builder.message_size.greater(15000)
    messages = folder.get_contents(builder.get_query())
    print("Mensagens tamanho > 15 KB:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensagens não lidas
    builder.has_no_flags(MapiMessageFlags.READ)
    messages = folder.get_contents(builder.get_query())
    print("Não lidas:", messages.count)

    builder = PersonalStorageQueryBuilder()
    # Mensagens não lidas com anexos
    builder.has_no_flags(MapiMessageFlags.READ)
    builder.has_flags(MapiMessageFlags.HASATTACH)
    messages = folder.get_contents(builder.get_query())
    print("Mensagens não lidas com anexos:", messages.count)

    # Pasta com nome 'SubInbox'
    builder = PersonalStorageQueryBuilder()
    builder.folder_name.equals("SubInbox")
    folders = folder.get_sub_folders(builder.get_query())
    print("Pasta contendo subpasta:", folders.count)

    builder = PersonalStorageQueryBuilder()
    # Pastas com subpastas
    builder.has_subfolders()
    folders = folder.get_sub_folders(builder.get_query())
    print("Pastas com subpastas:", folders.count)
```
### **Pesquisando por uma String em PST com o Parâmetro Ignorar Caixa**
O seguinte trecho de código mostra como pesquisar por uma string em PST com o parâmetro ignorar caixa.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SearchingStringInPSTWithIgnoreCaseParameter-SearchingStringInPSTWithIgnoreCaseParameter.py" >}}

### **Pesquisando por Assuntos de Mensagens com Múltiplas Palavras-chave em um Arquivo PST**

Recupere mensagens ou itens específicos de um arquivo de armazenamento pessoal (PST) ou repositório de mensagens implementando o método *either(query1, query2)* da classe [PersonalStorageQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstoragequerybuilder/#personalstoragequerybuilder-class) em seu projeto. Ele aceita dois parâmetros, permitindo que você combine duas consultas diferentes, query1 e query2, e encontre um assunto de mensagem que corresponda a uma das duas palavras especificadas. Veja o exemplo de código abaixo:

```python
import aspose.email as ae

builder1 = ae.storage.pst.PersonalStorageQueryBuilder()
builder1.subject.contains("Review") # 'Review' é palavra-chave para a busca

builder2 = ae.storage.pst.PersonalStorageQueryBuilder()
builder2.subject.contains("Error") # 'Error' também é palavra-chave para a busca

builder = ae.storage.pst.PersonalStorageQueryBuilder()
# os assuntos das mensagens devem conter as palavras 'Review' ou 'Error'
builder.either(builder1.get_query(), builder2.get_query())


pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

folder = pst.root_folder.get_sub_folder("Inbox")
messages = folder.get_contents(builder.get_query())

for message in messages:
    print(f"Mensagem: {message.subject}")
```

## **Mover Itens para Outras Pastas do Arquivo PST**
Aspose.Email permite mover itens de uma pasta de origem para outra pasta no mesmo arquivo de Armazenamento Pessoal (PST). Isso inclui:

- Mover uma pasta especificada para uma nova pasta mãe.
- Mover mensagens especificadas para uma nova pasta.
- Mover o conteúdo para uma nova pasta.
- Mover subpastas para uma nova pasta mãe.

O seguinte trecho de código mostra como mover itens, como mensagens e pastas, de uma pasta de origem para outra pasta no mesmo arquivo PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-MoveItemsToOtherFolders-MoveItemsToOtherFolders.py" >}}
## **Atualizando Propriedades de Mensagens em um Arquivo PST**
Às vezes, é necessário atualizar certas propriedades de mensagens, como mudar o assunto, marcar a importância da mensagem e outras semelhantes. Atualizar uma mensagem em um arquivo PST, com essas mudanças nas propriedades da mensagem, pode ser alcançado usando o método FolderInfo.change_messages. Este artigo mostra como atualizar mensagens em lote em um arquivo PST para mudanças nas propriedades. O seguinte trecho de código mostra como atualizar propriedades de mensagens em modo de lote para várias mensagens em um arquivo PST.

```py
from aspose.email.storage.pst import PersonalStorage, PersonalStorageQueryBuilder
from aspose.email.mapi import MapiPropertyTag, MapiProperty, MapiPropertyCollection

pst_file_path = data_dir + "ya4demia04vb.pst"

# Carregar o arquivo PST do Outlook
with PersonalStorage.from_file(pst_file_path) as personal_storage:
    # Obter a subpasta necessária
    inbox = personal_storage.root_folder.get_sub_folder("Inbox")

    # Encontrar mensagens com De = "someuser@domain.com"
    query_builder = PersonalStorageQueryBuilder()
    query_builder.from_address.contains("someuser@domain.com")

    # Obter conteúdos da consulta
    messages = inbox.get_contents(query_builder.get_query())

    # Salvar (MessageInfo, EntryIdString) em uma lista
    change_list = [message_info.entry_id_string for message_info in messages]

    # Compor as novas propriedades
    updated_properties = MapiPropertyCollection()
    updated_properties.add(
        MapiPropertyTag.SUBJECT_W,
        MapiProperty(MapiPropertyTag.SUBJECT_W, "Novo Assunto".encode("utf-16le"))
    )
    updated_properties.add(
        MapiPropertyTag.IMPORTANCE,
        MapiProperty(MapiPropertyTag.IMPORTANCE, bytearray([0x02, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]))
    )

    # Atualizar mensagens com De = "someuser@domain.com" com novas propriedades
    inbox.change_messages(change_list, updated_properties)
```
## **Atualizando Propriedades Personalizadas em um Arquivo PST**
Às vezes, é necessário marcar itens que foram processados no arquivo PST. A API Aspose.Email permite alcançar isso usando MapiProperty e MapiNamedProperty. Os seguintes métodos são úteis para alcançar este objetivo.

- ctor MapiNamedProperty(long propertyTag, string nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- ctor MapiNamedProperty(long propertyTag, long nameIdentifier, UUID propertyGuid, bytearray[] propertyValue)
- FolderInfo.change_messages(MapiPropertyCollection updatedProperties) - altera todas as mensagens na pasta
- PersonalStorage.change_messages(string entryId, MapiPropertyCollection updatedProperties) - altera as propriedades da mensagem

```py
from uuid import UUID
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import MapiNamedProperty, MapiPropertyCollection
from aspose.email.mapi import MapiPropertyType, MapiProperty, MapiPropertyTag

def generate_named_property_tag(index, data_type):
    return (((0x8000 | index) << 16) | data_type) & 0x00000000FFFFFFFF

def run():
    # Carregar o arquivo Outlook
    pst_file_path = data_dir + "my.pst"

    with PersonalStorage.from_file(pst_file_path) as personal_storage:
        test_folder = personal_storage.root_folder.get_sub_folder("Inbox")

        # Criar a coleção de propriedades de mensagens para adicionar ou atualizar
        new_properties = MapiPropertyCollection()

        # Propriedades nomeadas normais, personalizadas e PidLidLogFlags
        mapi_property = MapiProperty(
            MapiPropertyTag.ORG_EMAIL_ADDR_W,
            "test_address@org.com".encode("utf-16le")
        )
        named_property1 = MapiNamedProperty(
            generate_named_property_tag(0, MapiPropertyType.LONG),
            "ITEM_ID",
            UUID("00000000-0000-0000-0000-000000000000"),
            bytearray([0x7B, 0x00, 0x00, 0x00])
        )
        named_property2 = MapiNamedProperty(
            generate_named_property_tag(1, MapiPropertyType.LONG),
            0x0000870C,
            UUID("0006200A-0000-0000-C000-000000000046"),
            bytearray([0x00, 0x00, 0x00, 0x00])
        )
        new_properties.add(named_property1.tag, named_property1)
        new_properties.add(named_property2.tag, named_property2)
        new_properties.add(mapi_property.tag, mapi_property)
        test_folder.change_messages(test_folder.enumerate_messages_entry_id(), new_properties)

# Uso
run()
```
## **Extraindo Anexos sem Extrair a Mensagem Completa**
A API Aspose.Email pode ser usada para extrair anexos de mensagens PST sem extrair a mensagem completa primeiro. O método extract_attachments da classe IEWSClient pode ser usado para isso. O seguinte trecho de código mostra como extrair anexos sem extrair a mensagem completa.

```py
from aspose.email.storage.pst import PersonalStorage


with PersonalStorage.from_file(data_dir + "my.pst") as personal_storage:
    folder = personal_storage.root_folder.get_sub_folder("Inbox")

    for message_info in folder.enumerate_messages_entry_id():
        attachments = personal_storage.extract_attachments(message_info)

        if attachments.count != 0:
            for attachment in attachments:
                if attachment.long_file_name is not None and attachment.long_file_name.endswith(".msg"):
                    continue
                else:
                    attachment.save(data_dir + attachment.long_file_name)
```
## **Adicionando Arquivos a PST**
A funcionalidade chave do Microsoft Outlook é gerenciar e-mails, calendários, tarefas, contatos e entradas de diário. Além disso, arquivos também podem ser adicionados a uma pasta PST e o PST resultante mantém registro dos documentos adicionados. A Aspose.Email fornece a facilidade de adicionar arquivos a uma pasta da mesma forma que adicionar mensagens, contatos, tarefas e entradas de diário a PST. O seguinte trecho de código mostra como adicionar documentos a uma pasta PST usando Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddFilesToPST-AddFilesToPST.py" >}}