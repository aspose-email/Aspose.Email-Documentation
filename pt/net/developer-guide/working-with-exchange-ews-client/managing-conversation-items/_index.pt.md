---
title: "Gerenciando Itens de Conversa"
url: /pt/net/managing-conversation-items/
weight: 40
type: docs
---


Aspose.Email para .NET pode ser usado para gerenciar os itens de conversa no Exchange Server com a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Esta classe utiliza os Serviços Web do Exchange, que estão disponíveis apenas no Exchange Server 2007 e em versões posteriores. Este artigo mostra como [encontrar](#finding-conversations), [copiar](#copying-conversations), [mover](#moving-conversations) e [excluir](#deleting-conversations) itens de conversa no Exchange Server 2010. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos incluídos nesta seção.

## **Encontrando Conversas**

Para obter as informações da conversa de uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.FindConversations()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/findconversations/#findconversations) para encontrar todos os itens de conversa de uma pasta.
1. Exiba as propriedades do item de conversa, como ID, tópico da conversa e status da bandeira.

O seguinte trecho de código mostra como encontrar conversas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FindConversationsOnExchangeServer-FindConversationsOnExchangeServer.cs" >}}

## **Copiando Conversas**

Para copiar conversas de uma pasta para outra:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.CopyConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyconversationitems/#copyconversationitems) para copiar o item de conversa da pasta de origem para a pasta de destino.

O seguinte trecho de código mostra como copiar conversas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CopyConversations-CopyConversations.cs" >}}

## **Movendo Conversas**

Para mover conversas de uma pasta para outra:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.MoveConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveconversationitems/#moveconversationitems) para mover uma conversa da pasta de origem para a pasta de destino.

O seguinte trecho de código mostra como mover conversas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-MoveConversations-MoveConversations.cs" >}}

## **Excluindo Conversas**

Para excluir conversas de uma pasta:

1. Conecte-se ao Exchange Server usando a interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Chame o método [IEWSClient.DeleteConversationItems()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteconversationitems/#deleteconversationitems) para excluir o item de conversa da pasta de origem.

O seguinte trecho de código mostra como excluir conversas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteConversations-DeleteConversations.cs" >}}