---
title: "Trabalhando com Opção de Votação Usando MapiMessage"
url: /pt/net/trabalhando-com-opcao-de-votacao-usando-mapimessage/
weight: 50
type: docs
---


## **Criando Opção de Votação Usando MapiMessage**

O Microsoft Outlook permite que os usuários criem uma enquete ao compor uma nova mensagem. Isso permite incluir opções de votação, como Sim, Não, Talvez, etc. Aspose.Email permite o mesmo ao criar uma nova mensagem do Outlook. A classe [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/) fornece a propriedade [VotingButtons](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/votingbuttons/) que pode ser usada para definir ou obter o valor das opções de votação. Este artigo fornece um exemplo detalhado de como criar uma [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) com opções de votação para criar uma enquete.

### **Criando uma Enquete usando MapiMessage**

O seguinte trecho de código mostra como criar uma enquete; a classe [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) pode ser usada como mostrado no seguinte trecho de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateAndSendingMessageWithVotingOptions.cs" >}}

### **Lendo Opções de Votação de uma MapiMessage**

O seguinte trecho de código mostra como ler opções de votação de uma [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVotingOptions-ReadingVotingOptions.cs" >}}

### **Lendo Apenas Botões de Votação**

O seguinte trecho de código mostra como ler apenas botões de votação.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.cs" >}}

### **Adicionando um botão de votação a uma Mensagem Existente**

O seguinte trecho de código mostra como adicionar um botão de votação a uma mensagem existente.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddVotingButtonToExistingMessage-AddVotingButtonToExistingMessage.cs" >}}

### **Deletando um botão de Votação de uma Mensagem**

O seguinte trecho de código mostra como deletar o botão de votação de uma Mensagem.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DeleteVotingButtonFromMessage-DeletVotingButtonFromMessage.cs" >}}

### **Ler as Informações dos Resultados da Votação**

O seguinte trecho de código mostra como ler as informações dos resultados da votação.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadVoteResultsInformation-ReadVoteResultsInformation.cs" >}}

### **Métodos de Exemplo Usados nos Exemplos**

O seguinte trecho de código mostra como criar a mensagem de exemplo usada nos exemplos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateAndSendingMessageWithVotingOptions-CreateTestMessage.cs" >}}