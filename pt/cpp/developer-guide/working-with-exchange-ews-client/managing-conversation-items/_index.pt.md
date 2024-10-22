---
title: "Gerenciando Itens de Conversa"
url: /pt/cpp/gerenciando-itens-de-conversa/
weight: 40
type: docs
---
  
Aspose.Email pode ser usado para gerenciar os itens de conversa no Exchange Server com a classe [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client). Esta classe utiliza os Serviços Web do Exchange, que estão disponíveis somente no Exchange Server 2007 e versões posteriores. Este artigo mostra como encontrar, copiar, mover e deletar itens de conversa no Exchange Server 2010. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos incluídos nesta seção.  
##  **Encontrando Conversas**  
Para obter as informações da conversa de uma pasta específica no Exchange Server:  
  
1. Conecte-se ao Exchange Server usando a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
1. Chame o método [FindConversations()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para encontrar todos os itens de conversa em uma pasta.  
1. Exiba as propriedades do item de conversa como ID, tópico da conversa e status da bandeira.  
  
O seguinte trecho de código mostra como encontrar conversas.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cpp" >}}  
##  **Copiando Conversas**  
Para copiar conversas de uma pasta para outra:  
  
1. Conecte-se ao Exchange Server usando a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
1. Chame o método [CopyConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para copiar o item de conversa da pasta de origem para a pasta de destino.  
  
O seguinte trecho de código mostra como copiar conversas.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CopyConversations-CopyConversations.cpp" >}}  
##  **Movendo Conversas**  
Para mover conversas de uma pasta para outra:  
  
1. Conecte-se ao Exchange Server usando a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
1. Chame o método [MoveConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para mover uma conversa da pasta de origem para a pasta de destino.  
  
O seguinte trecho de código mostra como mover conversas.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-MoveConversations-MoveConversations.cpp" >}}  
##  **Deletando Conversas**  
Para deletar conversas de uma pasta:  
  
1. Conecte-se ao Exchange Server usando a classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).  
1. Chame o método [DeleteConversationItems()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para deletar o item de conversa da pasta de origem.  
  
O seguinte trecho de código mostra como deletar conversas.  
  
  
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteConversations-DeleteConversations.cpp" >}}