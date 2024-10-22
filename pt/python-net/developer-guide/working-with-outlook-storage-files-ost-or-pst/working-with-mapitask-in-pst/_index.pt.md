---
title: "Trabalhando com MapiTask em PST"
url: /pt/python-net/trabalhando-com-mapitask-em-pst/
weight: 90
type: docs
---


## **Adicionando MapiTask ao PST**
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar MapiTask à subpasta de Tarefas de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiTask a um PST:

1. Crie um objeto MapiTask.
1. Defina as propriedades do MapiTask usando o construtor e diferentes métodos.
1. Crie um PST usando o método PersonalStorage.Create().
1. Crie uma pasta pré-definida (Tarefas) na raiz do arquivo PST acessando a pasta Raiz e, em seguida, chamando o método AddMapiMessageItem().

O seguinte trecho de código mostra como criar um MapiTask e, em seguida, adicioná-lo à pasta de tarefas de um arquivo PST recém-criado.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiTaskToPST-AddMapiTaskToPST.py" >}}