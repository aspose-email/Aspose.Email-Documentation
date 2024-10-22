---
title: "Filtrar Mensagens da Caixa de Correio do Exchange"
url: /pt/cpp/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Aspose.Email fornece a capacidade de filtrar mensagens da Caixa de Correio do Exchange usando o [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) e ExchangeQueryBuilder. As mensagens podem ser filtradas através de diferentes critérios, como por data, domínio, messageId e por Notificações de Entrega de Email. Este artigo mostra como filtrar mensagens do Exchange Server usando diferentes critérios.

{{% /alert %}} 
A classe [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) fornece o método [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#aad8420247acd17cb1d73303ed1982d1e) que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que correspondam a alguma condição, use o método sobrecarregado [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) que recebe a classe *MailQuery* como argumento. A classe *MailQuery* fornece várias propriedades para especificar condições, por exemplo, data, assunto, remetente e destinatário.
##  **Filtrando Mensagens**
Para obter mensagens filtradas de uma caixa de correio:

1. Conecte-se ao servidor Exchange.
1. Crie uma instância de *MailQuery* e defina as propriedades desejadas.
1. Chame o método [IEWSClient->ListMessages](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) e passe o *MailQuery* nos parâmetros para obter apenas as mensagens filtradas.

O seguinte trecho de código mostra como obter mensagens que têm a string "Newsletter" no assunto e foram enviadas hoje.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cpp" >}}
##  **Filtrar Mensagens com Base em Critérios**
Os exemplos de código acima filtram mensagens com base no assunto do email e data. Também podemos filtrar por outras propriedades. Abaixo estão alguns exemplos de como definir as condições usando *MailQuery*.
###  **Critério de Filtragem Data de Hoje**
O seguinte trecho de código mostra como filtrar emails com base na data de hoje.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cpp" >}}
###  **Critério de Filtragem Intervalo de Datas**
O seguinte trecho de código mostra como filtrar emails com base em um intervalo de datas.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cpp" >}}
###  **Critério de Filtragem Remetente Específico**
O seguinte trecho de código mostra como filtrar emails com base em um remetente específico.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cpp" >}}
###  **Critério de Filtragem Domínio Específico**
O seguinte trecho de código mostra como filtrar emails com base em um domínio específico.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cpp" >}}
###  **Critério de Filtragem Destinatário Específico**
O seguinte trecho de código mostra como filtrar emails com base em um destinatário específico.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cpp" >}}
###  **Critério de Filtragem por MessageID**
O seguinte trecho de código mostra como filtrar emails com base em MessageID.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cpp" >}}
###  **Critério de Filtragem Todas as Notificações de Entrega de Email**
O seguinte trecho de código mostra como filtrar emails com base em todas as notificações de entrega de email.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cpp" >}}
###  **Filtrar por Tamanho da Mensagem**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cpp" >}}
##  **Construindo Consultas Complexas**
Se diferentes propriedades do [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) forem definidas em uma instrução separada, todas as condições são correspondidas. Por exemplo, para obter uma mensagem em um intervalo de datas particular e de um host específico, escreva três instruções:
###  **Combinando Consultas com E**
O seguinte trecho de código mostra como combinar consultas com E.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cpp" >}}
###  **Combinando Consultas com OU**

O [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) fornece o método [Or()](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/#afc735b8cd80758418502678ac69eecd4) que aceita duas instâncias de *MailQuery* como parâmetros. Ele obtém mensagens que correspondem a qualquer uma das duas condições especificadas. O exemplo abaixo filtra mensagens que têm a palavra “test” no assunto ou “noreply@host.com” como remetente. O seguinte trecho de código mostra como combinar consultas com OU.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cpp" >}}
##  **Filtragem de Emails Sensível a Maiúsculas e Minúsculas**
Os emails podem ser filtrados com base na sensibilidade a maiúsculas e minúsculas especificando a flag IgnoreCase nos critérios de filtragem, como mostrado no seguinte trecho de código.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cpp" >}}
#  **Filtrando Mensagens com Suporte de Paginação**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cpp" >}}