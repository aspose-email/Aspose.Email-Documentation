---
title: "Criar Novo Arquivo PST e Adicionar Subpastas"
url: /pt/python-net/create-new-pst-file-and-add-subfolders/
weight: 10
type: docs
---


Além de analisar um arquivo PST existente, a Aspose.Email oferece meios para criar um arquivo PST do zero. Este artigo demonstra como criar um arquivo PST do Outlook e adicionar uma subpasta a ele.

1. Criando um novo arquivo PST.
1. Mudando a classe Container de uma pasta.

Use a classe PersonalStorage para criar um arquivo PST em algum local em um disco local. Para criar um arquivo PST do zero:

1. Crie um PST usando o método PersonalStorage.Create().
1. Adicione uma subpasta na raiz do arquivo PST acessando a pasta Root e, em seguida, chamando o método AddSubFolder.

O seguinte trecho de código mostra como criar um arquivo PST e adicionar uma subpasta chamada Inbox.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.py" >}}

## **Verificação de Correspondência da Classe Container ao Adicionar uma Pasta ao PST**

Aspose.Email para Python oferece uma solução que aprimora o processo de validação durante a criação de pastas em arquivos PST. Com a propriedade 'EnforceContainerClassMatching' da classe [FolderCreationOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class), você pode garantir a correspondência rigorosa das classes de containers ao adicionar uma nova pasta ao armazenamento PST. Este recurso ajuda a manter a hierarquia organizacional dentro do arquivo PST, prevenindo discrepâncias nas classes de containers. Ao definir 'EnforceContainerClassMatching' como 'true', uma exceção será lançada se as classes de containers das pastas pai e filha não corresponderem, proporcionando uma proteção contra estruturas de pastas incorretas. O comportamento padrão dessa propriedade é 'false', permitindo flexibilidade na criação de pastas enquanto possibilita a aplicação de correspondência rigorosa de classes de containers quando necessário.

O seguinte exemplo de código demonstra o uso da propriedade 'EnforceContainerClassMatching' para controlar se uma exceção deve ser lançada ao adicionar pastas com classes de containers em desacordo:

```py
with PersonalStorage.create("storage.pst", FileFormatVersion.Unicode) as pst:
    contacts = pst.createpredefinedfolder("Contacts", StandardIpmFolder.Contacts)
    
    # Uma exceção não ocorrerá. EnforceContainerClassMatching é False por padrão.
    contacts.addsubfolder("Subfolder1", "IPF.Note")
    
    # Uma exceção ocorrerá, pois a classe de container da subpasta sendo adicionada (IPF.Note)
    # não corresponde à classe de container da pasta pai (IPF.Contact).
    contacts.addsubfolder("Subfolder3", FolderCreationOptions(enforcecontainerclassmatching=True, containerclass="IPF.Note"))
```

## **Mudando a Classe Container de uma Pasta**
Às vezes, é necessário mudar a classe de uma pasta. Um exemplo comum é quando mensagens de diferentes tipos (compromissos, mensagens, etc.) são adicionadas à mesma pasta. Nesses casos, a classe da pasta precisa ser alterada para que todos os elementos na pasta sejam exibidos corretamente. O seguinte trecho de código mostra como mudar a classe de container de uma pasta em PST para esse propósito.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ChangeFolderContainerClass-ChangeFolderContainerClass.py" >}}

## **Adicionar Mensagens em Lote com Desempenho Aprimorado**

Adicionar mensagens em lote a um arquivo PST em vez de adicioná-las individualmente pode oferecer várias vantagens, particularmente em termos de eficiência e desempenho: menos operações de I/O, tempo reduzido para concluir a tarefa, recursos do sistema utilizados de forma mais eficiente, etc. O método *add_messages* da classe [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class) é usado para transferir a coleção de mensagens MAPI obtidas da pasta de origem para a pasta de destino.

### **Adicionar Mensagens de Outro PST**

Para enumerar e recuperar todas as mensagens MAPI da pasta de origem de um arquivo PST, use o método *enumerate_mapi_messages()* da classe [FolderInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#folderinfo-class). Em seguida, adicione essas mensagens à pasta de destino de outro arquivo PST.

```python
import aspose.email as ae

src_pst = ae.storage.pst.PersonalStorage.from_file("source.pst", False)
dest_pst = ae.storage.pst.PersonalStorage.from_file("destination.pst")

# Obtenha a pasta pelo nome
src_folder = src_pst.root_folder.get_sub_folder("SomeFolder")
dest_folder = dest_pst.root_folder.get_sub_folder("SomeFolder")

dest_folder.add_messages(src_folder.enumerate_mapi_messages())
```

### **Adicionar Mensagens de Diretório**

Para adicionar mensagens de um diretório, depois que o arquivo é aberto e a referência a uma pasta específica dentro do arquivo PST é obtida, recupere uma lista de nomes de arquivos de um diretório especificado pela variável "path" e crie uma lista vazia de MSG para carregar cada arquivo como um MapiMessage. Adicione cada mensagem carregada à msg_list. O exemplo de código abaixo demonstra o processo de adição de mensagens de um diretório:

```python
import aspose.email as ae
import os

pst = ae.storage.pst.PersonalStorage.from_file("my.pst", False)

# Obtenha a pasta pelo nome
folder = pst.root_folder.get_sub_folder("SomeFolder")

dirs = os.listdir("path")
msg_list = []

for file in dirs:
    msg = ae.mapi.MapiMessage.load(file)
    msg_list.append(msg)

folder.add_messages(iter(msg_list))
```