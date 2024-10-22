---
title: "Trabalhando com Opção de Votação Usando MapiMessage"
url: /pt/python-net/trabalhando-com-opcao-de-votacao-usando-mapimessage/
weight: 120
type: docs
---

## **Criando Opção de Votação Usando MapiMessage**
O Microsoft Outlook permite que os usuários criem uma enquete ao compor uma nova mensagem. Ele permite que incluam opções de votação como Sim, Não, Talvez, etc. Aspose.Email permite o mesmo ao criar uma nova mensagem do Outlook. A classe [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) fornece a propriedade VotingButtons que pode ser usada para definir ou obter o valor das opções de votação. Este artigo fornece um exemplo detalhado de criação de um MapiMessage com opções de votação para criar uma enquete.

### **Criando uma Enquete usando MapiMessage**

O seguinte exemplo de código mostra como usar a propriedade *voting_buttons* da classe [FollowUpOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupoptions/#followupoptions-class) para criar uma enquete:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Definir Botões FollowUpOptions
options = ae.mapi.FollowUpOptions()
options.voting_buttons = "Sim;Não;Talvez;Exatamente!"

msg.save("voting_btns.msg")
```

### **Lendo Opções de Votação de um MapiMessage**
O seguinte trecho de código mostra como ler opções de votação de um MapiMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingVotingOptions-ReadingVotingOptions.py" >}}

### **Lendo Apenas Botões de Votação**
O seguinte trecho de código mostra como ler apenas os botões de votação.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadingOnlyVotingButtons-ReadingOnlyVotingButtons.py" >}}
### **Adicionando botão de votação a uma Mensagem Existente**
O seguinte trecho de código mostra como adicionar um botão de votação a uma mensagem existente.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingVotingButtonToExistingMessage-AddingVotingButtonToExistingMessage.py" >}}
### **Excluindo Botão de Votação de uma Mensagem**
O seguinte trecho de código mostra como excluir um botão de votação de uma Mensagem.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DeleteVotingButtonFromMessage-DeleteVotingButtonFromMessage.py" >}}
### **Ler as Informações dos Resultados da Votação**
O seguinte trecho de código mostra como ler as informações dos resultados da votação.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ReadVoteResultsInformation-ReadVoteResultsInformation.py" >}}
### **Definir flag de mensagem não enviada**
O seguinte trecho de código mostra como amostrar métodos usados nos exemplos.

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage("from@test.com", "to@test.com", "Mensagem sinalizada", "Faça de forma agradável e curta, mas descritiva. A descrição pode aparecer nas páginas de resultados de pesquisa dos motores de busca...")
msg.set_message_flags(msg.flags ^ ae.mapi.MapiMessageFlags.UNSENT)
```