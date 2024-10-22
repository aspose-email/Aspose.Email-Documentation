---
title: "Trabalhando com MapiTask em PST"
url: /pt/java/trabalhando-com-mapitask-em-pst/
weight: 60
type: docs
---

## **Adicionando MapiTask ao PST**

[Criar Novo PST, Adicionar Subpastas e Mensagens](/email/java/criar-novo-pst-adicionar-subpastas-e-mensagens/) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar MapiTask à subpasta Tarefas de um arquivo PST que você criou ou carregou.

Abaixo estão os passos para adicionar MapiTask a um PST:

1. Crie um objeto [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Defina as propriedades do [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) usando o construtor e métodos diferentes.
1. Crie um PST usando o método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
1. Crie uma pasta predefinida (Tarefas) na raiz do arquivo PST acessando a pasta Raiz e, em seguida, chamando o método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

O trecho de código abaixo mostra como criar um [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) e, em seguida, adicioná-lo à pasta Tarefas de um arquivo PST recém-criado.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiTaskToPST-.java" >}}