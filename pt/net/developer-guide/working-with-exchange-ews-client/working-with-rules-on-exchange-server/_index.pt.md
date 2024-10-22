---
title: "Trabalhando com Regras no Exchange Server"
url: /pt/net/trabalhando-com-regras-no-exchange-server/
weight: 90
type: docs
---

## **Gerenciando Regras**

Aspose.Email para .NET pode ser usado para gerenciar as regras no Exchange Server usando a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Esta classe utiliza os Serviços Web do Exchange (EWS), que estão disponíveis no Exchange Server 2007 e versões posteriores. Este artigo explica como gerenciar as regras:

- Ler as regras já no servidor.
- Criar uma nova regra.
- Atualizar uma regra existente.

O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos descritos neste artigo.

### **Ler Regras**

Para obter todas as regras do Exchange Server:

1. Conecte-se a um Exchange Server usando a classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) para obter todas as regras.
1. Em um loop foreach, navegue por todas as regras e exiba as propriedades da regra, como condições, ações e nome.

O seguinte trecho de código mostra como ler regras.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cs" >}}

### **Criando uma Nova Regra**

Para criar uma nova regra no Exchange Server, execute os seguintes passos:

1. Conecte-se a um Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Crie uma nova instância da classe [InboxRule](https://reference.aspose.com/email/net/aspose.email.clients.exchange/inboxrule/) e defina as seguintes propriedades obrigatórias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Chame o método [IEWSClient.CreateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createinboxrule/#createinboxrule) para criar a regra.

O seguinte trecho de código mostra como criar uma nova regra.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CriarNovaRegraNoExchangeServer-CriarNovaRegraNoExchangeServer.cs" >}}

### **Atualizando uma Regra**

Para atualizar uma regra no Exchange Server:

1. Conecte-se a um Exchange Server usando a classe [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.GetInboxRules()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getinboxrules/#getinboxrules) para obter todas as regras.
1. Em um loop foreach, navegue por todas as regras e obtenha a regra que você deseja alterar correspondendo o DisplayName em uma condição.
1. Atualize as propriedades da regra.
1. Chame o método [IEWSClient.UpdateInboxRule()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateinboxrule/#updateinboxrule/) para atualizar a regra.

O seguinte trecho de código mostra como atualizar uma regra.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AtualizarRegraNoExchangeServer-AtualizarRegraNoExchangeServer.cs" >}}