---
title: "Filtrar Mensagens do Servidor Usando Cliente IMAP"
url: /pt/net/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---

A classe [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) fornece o método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) que obtém todas as mensagens de uma caixa de entrada. Para obter apenas mensagens que correspondem a alguma condição, use o método sobrecarregado [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) que recebe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como argumento. A classe [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) fornece várias propriedades para especificar as condições, por exemplo, data, assunto, remetente, destinatário e assim por diante. O primeiro exemplo ilustra como filtrar mensagens com base na data e no assunto. Também mostramos como filtrar com base em outros critérios e como construir consultas mais complexas. A API também fornece a capacidade de aplicar critérios de pesquisa sensíveis a maiúsculas e minúsculas para corresponder a critérios de filtragem exatos. A API também permite especificar a codificação da string de pesquisa para filtrar mensagens da caixa de entrada.

## **Filtrando Mensagens da Caixa de Entrada**

1. [Conectar e fazer login em um servidor IMAP](https://docs.aspose.com/email/pt/net/connecting-to-imap-server/#connecting-with-imap-server)
2. Crie uma instância de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) e defina as propriedades
3. Chame o método [`ImapClient.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_14) e passe o [`MailQuery`](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) com os parâmetros para obter apenas mensagens filtradas.

O seguinte trecho de código mostra como se conectar a uma caixa de entrada IMAP e obter mensagens que chegaram hoje e têm a palavra "newsletter" no assunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FilteringMessagesFromIMAPMailbox-FilteringMessagesFromIMAPMailbox.cs" >}}

## **Obter Mensagens que Atendem a Critérios Específicos**

[Os exemplos de código acima](#filtering-messages-from-mailbox) filtram mensagens com base no assunto e na data do e-mail. Podemos usar outras propriedades para definir outras condições suportadas também. Abaixo estão alguns exemplos de como definir as condições usando [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Os trechos de código a seguir mostram como filtrar e-mails em:

1. Data de hoje.
1. Um intervalo de datas.
1. De um remetente específico.
1. De um domínio específico.
1. De um destinatário específico.

### **Data de Hoje**

O seguinte trecho de código mostra como filtrar e-mails na Data de Hoje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

### **Intervalo de Datas**

O seguinte trecho de código mostra como filtrar e-mails no intervalo de datas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsOverDateRange.cs" >}}

### **Remetente Específico**

O seguinte trecho de código mostra como filtrar e-mails de um remetente específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificSenderEmails.cs" >}}

### **Domínio Específico**

O seguinte trecho de código mostra como filtrar e-mails de um domínio específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificDomainEmails.cs" >}}

### **Destinatário Específico**

O seguinte trecho de código mostra como filtrar e-mails de um destinatário específico.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

## **Construindo Consultas Complexas**

Se diferentes propriedades de [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) forem definidas em declarações separadas, todas as condições serão correspondidas. Por exemplo, se quisermos obter mensagens entre um intervalo de datas e de um host específico, precisamos escrever três declarações.

### **Combinando Consultas com AND**

O seguinte trecho de código mostra como combinar consultas com AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombineQueriesWithAND.cs" >}}

### **Combinando Consultas com OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) fornece o método [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) que recebe duas instâncias de [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) como parâmetros. Ele obtém as mensagens que correspondem a qualquer uma das duas condições especificadas. O seguinte trecho de código mostra como filtrar mensagens que têm "teste" no assunto ou "noreply@host.com" como remetente. O seguinte trecho de código mostra como combinar consultas com OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombiningQueriesWithOR.cs" >}}

## **Filtragem com base em InternalDate**

As mensagens podem ser extraídas do servidor com base no InternalDate, no entanto, às vezes o servidor não retorna todas as mensagens visíveis na caixa de entrada. O motivo pode ser o fuso horário do servidor, já que pode não ser UTC para todos os servidores como o [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose envia comandos como 008 SEARCH ON 4-May-2014 de acordo com o [protocolo IMAP](https://www.rfc-editor.org/rfc/rfc1730), no entanto, o resultado pode diferir devido às configurações de fuso horário do servidor. Um novo membro é adicionado em [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) como [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/), o que ajuda ainda mais na filtragem das mensagens. O seguinte trecho de código mostra o uso de [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) para filtrar mensagens.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-InternalDateFilter-InternalDateFilter.cs" >}}

### **Filtragem de E-mails com Sensibilidade a Maiúsculas e Minúsculas**

O seguinte trecho de código mostra como usar filtragem de e-mails com sensibilidade a maiúsculas e minúsculas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CaseSensitiveEmailsFiltering-CaseSensitiveEmailsFiltering.cs" >}}

### **Especificar Codificação para o Construtor da Consulta**

O construtor [ImapQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapquerybuilder/) da API pode ser usado para especificar a codificação da string de pesquisa. Isso também pode ser definido usando a propriedade [DefaultEncoding](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/defaultencoding/) do MailQueryBuilder. O seguinte trecho de código mostra como especificar a codificação para o construtor da consulta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SpecifyEncodingForQueryBuilder-SpecifyEncodingForQueryBuilder.cs" >}}

### **Filtrar Mensagens com Suporte a Paginação**

O [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) fornece a capacidade de procurar mensagens na caixa de entrada e listá-las com suporte a paginação. O seguinte trecho de código mostra como filtrar mensagens com suporte a paginação.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SearchWithPagingSupport-SearchWithPagingSupport.cs" >}}

## **Filtrar Mensagens com Flag Personalizada**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetMessagesWithCustomFlags.cs" >}}

## **Filtrar Mensagens usando Pesquisa Personalizada**

Por exemplo, a norma RFC 3501 não permite a pesquisa de mensagens com base na existência de anexos nas mensagens. Mas o **Gmail** fornece [Extensões IMAP](https://developers.google.com/gmail/imap/imap-extensions?hl=ru) que permitem realizar essa pesquisa. O próximo trecho de código mostra como fazer uma consulta correspondente.

```csharp
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();
queryBuilder.CustomSearch("X-GM-RAW \"has:attachment\"");

MailQuery mailQuery = queryBuilder.GetQuery();
ImapMessageInfoCollection messageInfoCollection = imapClient.ListMessages(mailQuery);
```