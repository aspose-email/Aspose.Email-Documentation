---
title: "Filtrar Mensagens da Caixa de Correio Exchange"
url: /pt/net/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---


{{% alert color="primary" %}}

Aspose.Email para .NET fornece a capacidade de filtrar mensagens da Caixa de Correio Exchange usando o EWSClient e o ExchangeQueryBuilder. As mensagens podem ser filtradas via diferentes critérios, como por data, domínio, id da mensagem e por Notificações de Entrega de Correio. Este artigo mostra como filtrar mensagens do Exchange Server usando diferentes critérios.

{{% /alert %}} 

## **Filtrando Mensagens usando EWS**

A interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) fornece o método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que correspondem a alguma condição, use o método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) sobrecarga que recebe a classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. A classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) fornece várias propriedades para especificar condições, por exemplo, data, assunto, remetente e destinatário. Além disso, a API também permite aplicar filtros de sensibilidade a maiúsculas e minúsculas para recuperar e-mails da caixa de correio.

### **Filtrar Mensagens com Base em Critérios**

Para obter mensagens filtradas de uma caixa de correio:

1. Conecte-se ao servidor Exchange.
1. Crie uma instância de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) e defina as propriedades desejadas.
1. Chame o método [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/#listmessages) e passe o [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) nos parâmetros para obter apenas as mensagens filtradas.

O seguinte trecho de código mostra como se conectar a uma caixa de correio IMAP e obter mensagens que contêm a string "Newsletter" no assunto e que foram enviadas hoje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cs" >}}

#### **Filtrar Mensagens pela Data de Hoje**

O seguinte trecho de código mostra como filtrar todos os e-mails com base na data de hoje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cs" >}}

#### **Filtrar Mensagens por Intervalo de Datas**

O seguinte trecho de código mostra como filtrar todos os e-mails com base no intervalo de datas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cs" >}}

#### **Filtrar Mensagens por Remetente Específico**

O seguinte trecho de código mostra como filtrar todos os e-mails com base em um remetente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cs" >}}

#### **Filtrar Mensagens por Domínio Específico**

O seguinte trecho de código mostra como filtrar todos os e-mails com base em um domínio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cs" >}}

#### **Filtrar Mensagens por Destinatário Específico**

O seguinte trecho de código mostra como filtrar todos os e-mails com base em um destinatário específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cs" >}}

#### **Filtrar Mensagens pelo MessageID**

O seguinte trecho de código mostra como filtrar todos os e-mails com base no MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cs" >}}

#### **Filtrar Mensagens por Todas as Notificações de Entrega de Correio**

O seguinte trecho de código mostra como filtrar todos os e-mails com base em todas as notificações de entrega de correio.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cs" >}}

#### **Filtrar Mensagens por Tamanho da Mensagem**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cs" >}}


### **Construindo Consultas Complexas**

Se diferentes propriedades do [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) forem definidas em uma declaração separada, todas as condições serão correspondidas. Por exemplo, para obter uma mensagem em um intervalo de datas específico e de um host específico, escreva três declarações:

#### **Combinando Consultas com AND**

O seguinte trecho de código mostra como combinar consultas com AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cs" >}}

#### **Combinando Consultas com OR**

O [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) fornece o método [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) que recebe duas instâncias de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parâmetros. Ele obtém mensagens que correspondem a qualquer uma das duas condições especificadas. O exemplo abaixo filtra mensagens que têm a palavra "teste" no assunto ou "noreply@host.com" como remetente. O seguinte trecho de código mostra como combinar consultas com OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cs" >}}

### **Filtragem de E-mails Sensíveis a Maiúsculas e Minúsculas**

Os e-mails podem ser filtrados com base na sensibilidade a maiúsculas e minúsculas, especificando a flag IgnoreCase nos critérios de filtragem, conforme mostrado no seguinte trecho de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cs" >}}

## **Filtrando Mensagens com Suporte a Paginação**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cs" >}}

## **Ordenando mensagens filtradas em ordem crescente/decrescente**

A filtragem de e-mails pode ser suportada com a ordenação de mensagens em ordem crescente/decrescente. Neste caso, o método [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/) é usado para especificar a ordem em que os resultados de uma pesquisa de e-mail são ordenados usando a classe MailQueryBuilder. Este método permite que você defina critérios de ordenação para uma consulta de pesquisa, especificando se os resultados devem ser ordenados em ordem crescente ou decrescente com base em uma propriedade específica.

O método aceita o parâmetro ascending, que especifica a ordem de classificação para a propriedade especificada. Se o parâmetro ascending for verdadeiro, isso significa que os resultados da pesquisa devem ser ordenados em ordem crescente. Por outro lado, se o parâmetro ascending for falso, isso significa que os resultados da pesquisa devem ser ordenados em ordem decrescente.

```cs
MailQueryBuilder builder = new MailQueryBuilder();
builder.Subject.Contains("Report");
builder.InternalDate.Since(new DateTime(2020, 1, 1));
builder.Subject.OrderBy(true); // ordena o assunto em ordem crescente
builder.InternalDate.OrderBy(false); // ordena a data em ordem decrescente

MailQuery query = builder.GetQuery();

// Obtenha a lista de mensagens
ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query, false);
```

No trecho de código acima, o método OrderBy é aplicado duas vezes, uma para o assunto e outra para a data dos e-mails. Como resultado da execução do método ListMessages com a solicitação enviada, obteremos uma lista de mensagens com o assunto contendo a palavra "Report" que foram recebidas na data especificada ou depois dessa data. Ao mesmo tempo, os resultados serão ordenados por assunto em ordem crescente. Isso significa que as mensagens serão organizadas alfabeticamente de A a Z, dependendo do seu assunto. Além disso, os resultados serão ordenados por data em ordem decrescente. Isso significa que as postagens serão organizadas do mais novo para o mais antigo.