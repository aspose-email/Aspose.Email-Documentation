---
title: "Criar Novo Arquivo PST e Adicionar Subpastas"
url: /pt/cpp/create-new-pst-file-and-add-subfolders/
weight: 10
type: docs
---

## **Criando um Novo Arquivo PST e Adicionando Subpastas**
Assim como a análise de um arquivo PST existente, o Aspose.Email fornece os meios para criar um arquivo PST do zero. Este artigo demonstra como criar um arquivo PST do Outlook e adicionar uma subpasta a ele.

1. Criando um novo arquivo PST.
1. Alterando a classe do contêiner de uma pasta.

Use a classe PersonalStorage para criar um arquivo PST em algum local em um disco local. Para criar um arquivo PST do zero:

1. Crie um PST usando o método PersonalStorage.Create().
1. Adicione uma subpasta na raiz do arquivo PST acessando a pasta Raiz e, em seguida, chamando o método AddSubFolder.

O seguinte trecho de código mostra como criar um arquivo PST e adicionar uma subpasta chamada Caixa de Entrada.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.cpp" >}}
## **Alterando a Classe do Contêiner de uma Pasta**
Às vezes, é necessário alterar a classe da pasta de uma pasta. Um exemplo comum é quando mensagens de diferentes tipos (compromissos, mensagens, etc.) são adicionadas à mesma pasta. Nesses casos, a classe da pasta precisa ser alterada para que todos os elementos na pasta sejam exibidos corretamente. O seguinte trecho de código mostra como alterar a classe do contêiner de uma pasta em PST para esse fim.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ChangeFolderContainerClass-ChangeFolderContainerClass.cpp" >}}