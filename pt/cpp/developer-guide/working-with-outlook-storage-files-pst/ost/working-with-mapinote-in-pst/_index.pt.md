---
title: "Trabalhando com MapiNote no PST"
url: /pt/cpp/trabalhando-com-mapinote-no-pst/
weight: 80
type: docs
---

## **Adicionando MapiNote ao PST**
Com Aspose.Email, você pode adicionar um MapiNote à subpasta Notas de um arquivo PST que você criou ou carregou. Para adicionar um MapiNote a um PST:

1. Crie um MapiNote de modelo usando o Microsoft Outlook e salve-o como um arquivo MSG.
1. Carregue a nota MSG salva em um objeto MapiMessage.
1. Crie um objeto MapiNote e carregue a nota MSG de modelo.
1. Defina as propriedades do MapiNote.
1. Crie um PST usando o método PersonalStorage.Create().
1. Crie uma pasta pré-definida (Notas) na raiz do arquivo PST acessando a pasta raiz e chamando o método AddMapiMessageItem().

O seguinte trecho de código mostra como criar um MapiNote e depois adicioná-lo à pasta de notas de um arquivo PST recém-criado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cpp" >}}