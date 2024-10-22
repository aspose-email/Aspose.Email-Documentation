---
title: "Trabalhando com MapiTask em PST"
url: /pt/net/trabalhando-com-mapitask-em-pst/
weight: 60
type: docs
---


## **Adicionando MapiTask ao PST**

O artigo [Criar um Novo Arquivo PST e Adicionar Subpastas](https://docs.aspose.com/email/pt/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) mostra como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) à subpasta Tarefas de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiTask a um PST:

1. Crie um objeto [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).
2. Defina as propriedades do [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) usando o construtor e diferentes métodos.
3. Crie um PST usando o método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crie uma pasta pré-definida (Tarefas) na raiz do arquivo PST acessando a pasta Raiz e, em seguida, chamando o método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

O seguinte trecho de código mostra como criar um [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) e, em seguida, adicioná-lo à pasta de tarefas de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cs" >}}