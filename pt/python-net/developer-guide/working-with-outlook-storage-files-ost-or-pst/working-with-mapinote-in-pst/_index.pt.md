---
title: "Trabalhando com MapiNote em PST"
url: /pt/python-net/trabalhando-com-mapinote-em-pst/
weight: 80
type: docs
---


## **Adicionando MapiNote ao PST**
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar um MapiNote à subpasta Notas de um arquivo PST que você criou ou carregou. Para adicionar um MapiNote a um PST:

1. Crie um modelo de MapiNote usando o Microsoft Outlook e salve-o como um arquivo MSG.
1. Carregue a nota MSG salva em um objeto MapiMessage.
1. Crie um objeto MapiNote e carregue a nota MSG do modelo.
1. Defina as propriedades do MapiNote.
1. Crie um PST usando o método PersonalStorage.Create().
1. Crie uma pasta predefinida (Notas) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método AddMapiMessageItem().

O trecho de código a seguir mostra como criar um MapiNote e, em seguida, adicioná-lo à pasta de notas de um arquivo PST recém-criado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiNoteToPST-AddMapiNoteToPST.py" >}}