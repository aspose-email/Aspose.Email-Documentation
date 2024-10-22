---
title: "Trabalhando com MapiNote em PST"
url: /pt/java/trabalhando-com-mapinote-em-pst/
weight: 80
type: docs
---

## **Adicionando MapiNote ao PST**

[Criar Novo PST, Adicionar Subpastas e Mensagens](/email/java/criar-novo-pst-adicionar-subpastas-e-mensagens/) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar um MapiNote à subpasta Notas de um arquivo PST que você criou ou carregou.

Abaixo estão os passos para adicionar MapiNote a um PST:

1. Crie um MapiNote de template usando o Microsoft Outlook e salve-o como um arquivo MSG.
1. Carregue a nota MSG salva no objeto [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
1. Crie um objeto [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) e carregue a nota MSG de template.
1. Defina as propriedades do [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) usando diferentes métodos.
2. Crie um PST usando o método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
3. Crie uma pasta pré-definida (Notas) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

O trecho de código abaixo mostra como criar um [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/mapinote/) e então adicioná-lo à pasta Notas de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiNoteToPST-.java" >}}