---
title: "Trabalhando com MapiTask em PST"
url: /pt/cpp/trabalhando-com-mapitask-em-pst/
weight: 90
type: docs
---

## **Adicionando MapiTask ao PST**
Com o Aspose.Email você pode adicionar MapiTask à subpasta Tarefas de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiTask a um PST:

1. Crie um objeto MapiTask.
1. Defina as propriedades do MapiTask usando o construtor e diferentes métodos.
1. Crie um PST usando o método PersonalStorage.Create().
1. Crie uma pasta pré-definida (Tarefas) na raiz do arquivo PST acessando a pasta Raiz e, em seguida, chamando o método AddMapiMessageItem().

O seguinte código demonstra como criar um MapiTask e, em seguida, adicioná-lo à pasta de tarefas de um arquivo PST recém-criado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cpp" >}}