---
title: "Trabalhando com Regras no Exchange Server"
url: /pt/cpp/trabalhando-com-regras-no-exchange-server/
weight: 90
type: docs
---
  
## **Gerenciando Regras**  
Aspose.Email pode ser usado para gerenciar as regras no Exchange Server usando a classe [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/). Esta classe usa os Serviços Web do Exchange (EWS), que estão disponíveis no Exchange Server 2007 e em versões posteriores. Para mostrar como gerenciar regras, este artigo explica como:  
  
- Ler as regras já no servidor.  
- Criar uma nova regra.  
- Atualizar uma regra existente.  
  
O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos descritos neste artigo.  
### **Ler Regras**  
Para obter todas as regras do Exchange Server:  
  
1. Conecte-se a um Exchange Server usando a classe [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).  
1. Chame o método [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) para obter todas as regras.  
1. Em um loop, navegue por todas as regras e exiba as propriedades da regra, como condições, ações e nomes.  
  
O seguinte trecho de código mostra como ler regras.  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExchangeServerReadRules-ExchangeServerReadRules.cpp" >}}  
### **Criando uma Nova Regra**  
Para criar uma nova regra no Exchange Server, siga os seguintes passos:  
  
1. Conecte-se a um Exchange Server usando a classe [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).  
1. Crie uma nova instância da classe *InboxRule* e defina as seguintes propriedades obrigatórias:  
   1. DisplayName  
   1. Conditions  
   1. Actions  
1. Chame o método [IEWSClient->CreateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7af390adad4a0248d17b11bbebe8e97f) para criar a regra.  
  
O seguinte trecho de código mostra como criar uma nova regra.  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CriarNovaRegraNoExchangeServer-CriarNovaRegraNoExchangeServer.cpp" >}}  
### **Atualizando uma Regra**  
Para atualizar uma regra no Exchange Server:  
  
1. Conecte-se a um Exchange Server usando a classe [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).  
1. Chame o método [IEWSClient->GetInboxRules()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ad8b80596b53806955cdc326b3cd23ebb) para obter todas as regras.  
1. Em um loop, navegue por todas as regras e obtenha a regra que você deseja alterar, correspondendo o *DisplayName* em uma condição.  
1. Atualize as propriedades da regra  
1. Chame o método [IEWSClient.UpdateInboxRule()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a077ef824948d486b7633ee9f3f61e863) para atualizar a regra.  
  
O seguinte trecho de código mostra como atualizar uma regra.  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AtualizarRegraNoExchangeServer-AtualizarRegraNoExchangeServer.cpp" >}}  