---
title: "Filtrar Mensagens Com AQS De Caixa De Correio Exchange"
url: /pt/net/filter-messages-with-aqs-from-exchange-mailbox/
weight: 35
type: docs
---

[A Synax de Consulta Avançada (AQS)](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange) é a sintaxe de consulta utilizada pelo Exchange como uma alternativa aos filtros de pesquisa para expressar critérios de busca. AQS é uma maneira mais flexível de realizar pesquisas e entregar resultados de busca para todos os campos comumente usados nos itens. AQS também é amigável ao usuário, fácil de entender e rápido de dominar. Usar AQS é apropriado para encontrar mensagens por anexos e destinatários.

## Criando uma consulta de pesquisa com AQS

Você pode criar uma consulta de pesquisa com AQS por meio de:

- [`ExchangeAdvancedSyntaxQueryBuilder`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), que representa o construtor de expressão de pesquisa baseado na Sintaxe de Consulta Avançada (AQS). Ou
- [`ExchangeAdvancedSyntaxMailQuery`](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/), que cria uma string AQS diretamente com base nas palavras-chave suportadas.

## Criar uma consulta de pesquisa usando o construtor de consultas

Para criar uma consulta de pesquisa com [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) você precisa:

- criar uma instância de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) usando o método [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclient/)

- criar uma instância de [ExchangeAdvancedSyntaxQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/exchangeadvancedsyntaxquerybuilder/) e definir as propriedades necessárias para construir uma consulta.

- chamar o método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) ou [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/listitems/) e passar a instância de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) retornada pelo método [GetQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/getquery/), como um de seus parâmetros.

O exemplo de código abaixo mostra como as etapas acima podem ser realizadas:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    var advancedBuilder = new ExchangeAdvancedSyntaxQueryBuilder();
    advancedBuilder.From.Equals("Jim Martin");
    advancedBuilder.Subject.Contains("relatório");
    advancedBuilder.HasAttachment.Equals(true);

    var messages = client.ListMessages(client.MailboxInfo.InboxUri, advancedBuilder.GetQuery());
}
```

## Criar uma consulta de pesquisa diretamente usando AQS:

Para criar uma consulta de pesquisa com [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) você precisa:

- criar uma instância de [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/) usando o método [GetEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/ewsclient/getewsclient/)

- criar uma instância de [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxmailquery/#constructors) e passar uma string AQS. Veja a [descrição da sintaxe](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-perform-an-aqs-search-by-using-ews-in-exchange).

- chamar o método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/listmessages/) ou [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange/webservice/iewsclient/listitems/) e passar a instância de [ExchangeAdvancedSyntaxMailQuery](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeadvancedsyntaxquerybuilder/) como um de seus parâmetros.

O exemplo de código abaixo mostra como as etapas acima podem ser realizadas:

```csharp
using (var client = EWSClient.GetEWSClient(...))
{
    ExchangeAdvancedSyntaxMailQuery query = new ExchangeAdvancedSyntaxMailQuery("subject:(produto E relatório)");
    ExchangeMessageInfoCollection messages = client.ListMessages(client.MailboxInfo.InboxUri, query);
}
```