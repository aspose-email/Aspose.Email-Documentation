---
title: "Filtrar Mensagens da Caixa de Correio do Exchange usando WebDav"
url: /pt/net/filter-messages-from-exchange-mailbox-using-webdav/
weight: 30
type: docs
---

## **Filtrando Mensagens usando WebDav**
A classe [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) fornece o método [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que correspondam a alguma condição, use o método sobrecarregado [ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) que aceita a classe [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) como argumento. A classe [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) fornece várias propriedades para especificar condições, por exemplo, data, assunto, remetente e destinatário. Além disso, a API também permite aplicar filtros de diferenciação entre maiúsculas e minúsculas para recuperar emails da caixa de correio.
### **Filtrando Mensagens**
Para obter mensagens filtradas de uma caixa de correio:

1. Conecte-se ao servidor Exchange.
1. Crie uma instância de [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) e defina as propriedades desejadas.
1. Chame o método [ExchangeClient.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav.exchangeclient/listmessages/methods/2) e passe o [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery) nos parâmetros para obter apenas as mensagens filtradas.

O seguinte trecho de código mostra como se conectar a uma caixa de correio IMAP e obter mensagens que contêm a string "Newsletter" no assunto e foram enviadas hoje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesFromExchangeMailbox-FilterMessagesFromExchangeMailbox.cs" >}}
### **Filtrar Mensagens com Critérios**
Os exemplos de código acima filtram mensagens com base no assunto e na data do email. Podemos filtrar outras propriedades também. Abaixo estão alguns exemplos de configuração das condições usando [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery).
#### **Critérios de Filtragem Data de Hoje**
O seguinte trecho de código mostra como filtrar todos os emails com base na data de hoje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsWithTodayDate.cs" >}}
#### **Critérios de Filtragem Faixa de Datas**
O seguinte trecho de código mostra como filtrar todos os emails com base na faixa de datas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetEmailsOverDateRange.cs" >}}
#### **Critérios de Filtragem Remetente Específico**
O seguinte trecho de código mostra como filtrar todos os emails com base em um remetente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificSenderEmails.cs" >}}
#### **Critérios de Filtragem Domínio Específico**
O seguinte trecho de código mostra como filtrar todos os emails com base em um domínio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificDomainEmails.cs" >}}
#### **Critérios de Filtragem Destinatário Específico**
O seguinte trecho de código mostra como filtrar todos os emails com base em um destinatário específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificRecipientEmails.cs" >}}
#### **Critérios de Filtragem por MessageID**
O seguinte trecho de código mostra como filtrar todos os emails com base no MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetSpecificMessageIdEmail.cs" >}}
#### **Critérios de Filtragem Todas as Notificações de Entrega de Email**
O seguinte trecho de código mostra como filtrar todos os emails com base em todas as notificações de entrega de email.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterMessagesOnCriteriaUsingExchangeClient-GetMailDeliveryNotifications.cs" >}}
### **Construindo Consultas Complexas**
Se diferentes propriedades do [ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) forem definidas em uma declaração separada, todas as condições são correspondidas. Por exemplo, para obter uma mensagem em uma faixa de datas específica e de um host específico, escreva três declarações:
#### **Combinando Consultas com AND**
O seguinte trecho de código mostra como combinar consultas com AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombineQueriesWithAND.cs" >}}

#### **Combinando Consultas com OR**
O [ExchangeQueryBuilder](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder) fornece o método [Or()](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/methods/or) que aceita duas instâncias de [MailQuery](https://apireference.aspose.com/email/net/aspose.email.tools.search/mailquery)como parâmetros. Ele obtém mensagens que correspondem a qualquer uma das duas condições especificadas. O exemplo abaixo filtra mensagens que têm a palavra “teste” no assunto ou “noreply@host.com” como remetente. O seguinte trecho de código mostra como combinar consultas com OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FilterWithComplexQueriesUsingExchangeClient-CombiningQueriesWithOR.cs" >}}
### **Filtragem de Emails com Diferenciação entre Maiúsculas e Minúsculas**
Os emails podem ser filtrados com base na diferenciação entre maiúsculas e minúsculas, especificando a flag IgnoreCase nos critérios de filtragem, conforme mostrado no seguinte trecho de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-CaseSensitiveEmailsFilteringUsingExchangeClient-CaseSensitiveEmailsFilteringUsingExchangeClient.cs" >}}