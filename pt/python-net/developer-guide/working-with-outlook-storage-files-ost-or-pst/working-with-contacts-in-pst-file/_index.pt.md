---
title: "Trabalhando com Contatos em Arquivo PST"
url: /pt/python-net/trabalhando-com-contatos-em-arquivo-pst/
weight: 60
type: docs
---

## **Adicionando Contato ao PST**
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar um MapiContact à subpasta Contatos de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiContact a um PST:

1. Crie um objeto MapiContact.
1. Defina as propriedades do MapiContact usando diferentes construtores e métodos.
1. Crie um PST usando o método PersonalStorage.create().
1. Crie uma pasta pré-definida (Contatos) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método add_mapi_message_item().

O seguinte trecho de código mostra como criar um MapiContact e depois adicioná-lo à pasta de contatos de um arquivo PST recém-criado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiContactsAndAddToContactsSubFolder-CreateNewMapiContactsAndAddToContactsSubFolder.py" >}}
## **Salvar informações de contatos do arquivo PST em formato MSG**
Este artigo explica como acessar informações de contato de um arquivo PST do Outlook e salvar o contato no disco em formato MSG. As classes PersonalStorage e MapiContact são usadas para obter e exibir as informações de contato. Os passos para obter as informações de contato são:

1. Carregar o arquivo PST na classe PersonalStorage.
1. Navegar até a pasta Contatos.
1. Obter o conteúdo da pasta Contatos para obter a coleção de mensagens.
1. Percorrer a coleção de mensagens.
1. Chamar o método PersonalStorage.extract_message() para obter as informações de contato na classe MapiMessage.
1. Chamar o método MapiMessage.save() para salvar o contato no disco em formato MSG.

O seguinte trecho de código mostra como recuperar todas as informações de contato do arquivo PST e salvar no disco em formato MSG.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AccessContactInformation-AccessContactInformation.py" >}}
## **Salvar informações de Contatos do arquivo PST em formato VCF**
Este artigo mostra como acessar informações de contato de um arquivo PST do Microsoft Outlook e salvar o contato no disco em formato vCard (VCF). Use as classes PersonalStorage e MapiContact para obter informações de contato do arquivo PST. Para obter as informações de contato:

1. Carregar o arquivo PST na classe PersonalStorage.
1. Navegar até a pasta Contatos.
1. Obter o conteúdo da pasta Contatos para obter a coleção de mensagens.
1. Percorrer a coleção de mensagens.
1. Chamar o método PersonalStorage.extract_message() para obter as informações de contato na classe MapiContact.
1. Usar as diferentes propriedades da classe MapiContact para acessar as informações de contato.

O programa abaixo carrega um arquivo PST do disco e salva todos os contatos em formato vCard (VCF). Os arquivos VCF podem ser usados em qualquer outro programa que possa carregar o arquivo de contato vCard padrão. Se você abrir qualquer arquivo VCF no Microsoft Outlook, ele se parecerá com o da captura de tela abaixo.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
O seguinte trecho de código mostra como exportar contatos do Outlook PST para o formato vCard (VCF).

```py
from aspose.email.storage.pst import PersonalStorage
from aspose.email.mapi import ContactSaveFormat

# Carregar o arquivo PST do Outlook
pst = PersonalStorage.from_file("my.pst")

# Obter a pasta Contatos
folder_info = pst.root_folder.get_sub_folder("Contacts")

# Percorrer todos os contatos nesta pasta
message_info_collection = folder_info.get_contents()
for message_info in message_info_collection:
    # Obter as informações de contato
    contact = pst.extract_message(message_info).to_mapi_message_item()

    # Exibir algumas informações na tela
    print("Nome: " + contact.name_info.display_name + " - " + message_info.entry_id_string)

    # Salvar no disco em formato vCard VCF
    contact.save("D:\\" + contact.name_info.display_name + ".vcf", ContactSaveFormat.V_CARD)
```
## **Trabalhando com Listas de Distribuição**
É possível criar uma lista de distribuição usando a API Aspose.Email, que é uma coleção de vários contatos. Uma lista de distribuição pode ser salva no disco em formato MSG do Outlook e pode ser visualizada/manipulada abrindo-a no MS Outlook.
### **Criando e Salvando uma Lista de Distribuição**
O seguinte trecho de código mostra como criar e salvar uma lista de distribuição.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateDistributionListInPST-CreateDistributionListInPST.py" >}}
### **Lendo uma Lista de Distribuição de um PST**
O seguinte trecho de código mostra como ler uma lista de distribuição de um PST.

```py
from aspose.email.mapi import MapiMessage

# Carregar a mensagem MAPI do arquivo
message = MapiMessage.load("dl.msg")

# Converter a mensagem para uma lista de distribuição MAPI
dlist = message.to_mapi_message_item()
```