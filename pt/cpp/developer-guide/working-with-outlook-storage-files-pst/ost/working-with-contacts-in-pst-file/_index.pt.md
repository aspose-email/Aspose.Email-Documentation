---
title: "Trabalhando com Contatos em Arquivo PST"
url: /pt/cpp/trabalhando-com-contatos-em-arquivo-pst/
weight: 60
type: docs
---

## **Adicionando Contato ao PST**
Com Aspose.Email, você pode adicionar um MapiContact à subpasta Contatos de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar um MapiContact a um PST:

1. Crie um objeto MapiContact.
1. Defina as propriedades do MapiContact usando diferentes construtores e métodos.
1. Crie um PST usando o método PersonalStorage.Create().
1. Crie uma pasta pré-definida (Contatos) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método AddMapiMessageItem().

O seguinte trecho de código mostra como criar um MapiContact e depois adicioná-lo à pasta de contatos de um arquivo PST recém-criado.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiContactAndAddToContactsSubfolder-CreateNewMapiContactAndAddToContactsSubfolder.cpp" >}}
## **Salvar informações de contatos do arquivo PST no formato MSG**
Este artigo explica como acessar informações de contato de um arquivo PST do Outlook e salvar o contato no disco no formato MSG. As classes PersonalStorage e MapiContact são utilizadas para obter e exibir as informações do contato. Os passos para obter as informações de contato são:

1. Carregue o arquivo PST na classe PersonalStorage.
1. Navegue até a pasta Contatos.
1. Obtenha o conteúdo da pasta Contatos para obter a coleção de mensagens.
1. Faça um loop pela coleção de mensagens.
1. Chame o método PersonalStorage.ExtractContactInfo() para obter as informações do contato na classe MapiContact. Use as propriedades da classe MapiContact para acessar as informações do contato.
1. Chame o método PersonalStorage.ExtractMessage() para obter as informações do contato na classe MapiMessage.
1. Chame o método MapiMessage.Save() para salvar o contato no disco no formato MSG.

O seguinte trecho de código mostra como recuperar todas as informações de contato do arquivo PST e salvar no disco no formato MSG.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AccessContactInformation-AccessContactInformation.cpp" >}}
## **Salvar informações de Contatos do arquivo PST no formato VCF**
Este artigo mostra como acessar informações de contato de um arquivo PST do Microsoft Outlook e salvar o contato no disco no formato vCard (VCF). Utilize as classes PersonalStorage e MapiContact para obter informações de contato do arquivo PST. Para obter as informações de contato:

1. Carregue o arquivo PST na classe PersonalStorage.
1. Navegue até a pasta Contatos.
1. Obtenha o conteúdo da pasta Contatos para obter a coleção de mensagens.
1. Faça um loop pela coleção de mensagens.
1. Chame o método PersonalStorage.ExtractMessage() para obter as informações do contato na classe MapiContact.
1. Utilize as diferentes propriedades da classe MapiContact para acessar as informações do contato.

O programa abaixo carrega um arquivo PST do disco e salva todos os contatos no formato vCard (VCF). Os arquivos VCF podem ser utilizados em qualquer outro programa que possa carregar o arquivo de contato padrão vCard. Se você abrir qualquer arquivo VCF no Microsoft Outlook, ele se parecerá com o da captura de tela abaixo.

|![todo:image_alt_text](trabalhando-com-contatos-em-arquivo-pst_1.png)|
| :- |
O seguinte trecho de código mostra como exportar contatos do PST do Outlook para o formato vCard (VCF).

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveContactInformation-SaveContactInformation.cpp" >}}
## **Trabalhando com Listas de Distribuição**
É possível criar uma lista de distribuição usando a API Aspose.Email que é uma coleção de múltiplos contatos. Uma lista de distribuição pode ser salva no disco no formato MSG do Outlook e pode ser visualizada/manipulada ao abri-la no MS Outlook.
### **Criando e Salvando uma Lista de Distribuição**
O seguinte trecho de código mostra como criar e salvar uma lista de distribuição.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cpp" >}}
### **Lendo uma Lista de Distribuição de um PST**
O seguinte trecho de código mostra como ler uma lista de distribuição de um PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingDistributionListFromPST-ReadingDistributionListFromPST.cpp" >}}