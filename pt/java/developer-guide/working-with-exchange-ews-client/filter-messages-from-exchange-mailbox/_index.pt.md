---
title: "Filtrar Mensagens da Caixa de Correio do Exchange"
url: /pt/java/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---


{{% alert color="primary" %}} 

Aspose.Email para Java fornece a capacidade de filtrar mensagens da Caixa de Correio do Exchange usando o [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) e [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). As mensagens podem ser filtradas através de diferentes critérios, como por data, domínio, id da mensagem e por Notificações de Entrega de Correio. Este artigo mostra como filtrar mensagens do Servidor Exchange usando diferentes critérios.

{{% /alert %}} 
## **Filtrando Mensagens usando EWS**
A classe [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) fornece o método [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(\)) que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que correspondem a alguma condição, use o método sobrecarregado [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20com.aspose.email.MailQuery\)) que aceita a classe [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) como argumento. A classe [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) fornece várias propriedades para especificar condições, por exemplo, data, assunto, remetente e destinatário. Além disso, a API também permite aplicar filtros de distinguir maiúsculas de minúsculas para recuperar e-mails da caixa de correio.
### **Filtrando Mensagens**
Para obter mensagens filtradas de uma caixa de correio:

1. Conecte-se ao servidor Exchange.
1. Crie uma instância de MailQuery e defina as propriedades desejadas.
1. Chame o método IEWSClient.listMessages() e passe o MailQuery nos parâmetros para obter apenas as mensagens filtradas.

O seguinte trecho de código mostra como conectar-se a uma caixa de correio IMAP e obter mensagens que contêm a string "Newsletter" no assunto e foram enviadas hoje.

~~~Java
try {
    // Conectar a EWS
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String username = "username";
    final String password = "password";
    final String domain = "domain";

    IEWSClient client = EWSClient.getEWSClient(mailboxUri, username, password, domain);

    // Construção de consulta por meio da classe ExchangeQueryBuilder
    ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

    // Definir Assunto e Emails que chegaram hoje
    builder.getSubject().contains("Newsletter");
    builder.getInternalDate().on(new Date());

    MailQuery query = builder.getQuery();

    // Obter lista de mensagens
    ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
    System.out.println("EWS: " + messages.size() + " mensagem(ns) encontrada(s).");

    // Desconectar do EWS
    client.dispose();
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~ 
### **Filtrar Mensagens por Critérios**
Os exemplos de código acima filtram mensagens com base no assunto do e-mail e na data. Podemos filtrar por outras propriedades também. Abaixo estão alguns exemplos de como definir as condições usando [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery).
#### **Filtrar Mensagens pela Data de Hoje**
O seguinte trecho de código mostra como filtrar todos os e-mails com base na data de hoje.

~~~Java
// Emails que chegaram hoje
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~ 
#### **Filtrar Mensagens por Intervalo de Datas**
O seguinte trecho de código mostra como filtrar todos os e-mails com base no intervalo de datas.

~~~Java
// Emails que chegaram nos últimos 7 dias
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~ 
#### **Filtrar Mensagens por Remetente Específico**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em um remetente específico.

~~~Java
// Obter e-mails de remetente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~ 
#### **Filtrar Mensagens por Domínio Específico**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em um domínio específico.

~~~Java
// Obter e-mails de domínio específico
builder.getFrom().contains("SpecificHost.com");
~~~ 
#### **Filtrar Mensagens por Destinatário Específico**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em um destinatário específico.

~~~Java
// Obter e-mails enviados para destinatário específico
builder.getTo().contains("recipient");
~~~ 
#### **Filtrar Mensagens por MessageID**
O seguinte trecho de código mostra como filtrar todos os e-mails com base no MessageID.

~~~Java
// Obter e-mail com MessageId específico
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getMessageId().equals("MessageID");
~~~ 
#### **Filtrar Mensagens por Todas as Notificações de Entrega de Correio**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em todas as notificações de entrega de correio.

~~~Java
// Obter Notificações de Entrega de Correio
builder = new ExchangeQueryBuilder();
builder.getContentClass().equals(ContentClassType.getMDN().toString());
~~~ 
#### **Filtrar Mensagens por Tamanho**
~~~Java
builder = new ExchangeQueryBuilder();
builder.getItemSize().greater(80000);
~~~ 
#### **Filtrar Mensagens por Valor de String**

O seguinte trecho de código mostra como filtrar todos os e-mails com base na string especificada nos cabeçalhos (assunto, de, para, cc). O método [getText()](https://reference.aspose.com/email/java/com.aspose.email/exchangequerybuilder/#getText--) retorna o valor string juntamente com o corpo da mensagem.

```java
 ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

builder.getText().equals("SomeText");

MailQuery query = builder.getQuery();

ExchangeMessageInfoCollection messages = ewsClient.listMessages("InboxUri", query, false);
```
#### **Filtrar Mensagens em Ordem Ascendente/Descendente**

Aspose.Email fornece o método [ComparisonField.orderBy(boolean ascending)](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) que define o valor indicando que o cliente usa ordenação ascendente ou descendente no campo de pesquisa. Ele permite que você ordene as mensagens de e-mail em ordem ascendente/descendente com base nos critérios especificados pelo [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/).

O trecho de código abaixo demonstra como filtrar mensagens em ordem ascendente/descendente:

```java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Report");
builder.getInternalDate().since(sinceDate);
builder.getSubject().orderBy(true); // ordenar o assunto em ordem ascendente
builder.getInternalDate().orderBy(false); // ordenar a data em ordem descendente  

ExchangeMessageInfoCollection miColl = client.listMessages(client.getMailboxInfo().getInboxUri(), builder.getQuery());
```
### **Construindo Consultas Complexas**
Se diferentes propriedades do [MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) são definidas em uma declaração separada, todas as condições são combinadas. Por exemplo, para obter uma mensagem em um intervalo de datas específico e de um host específico, escreva três declarações:
#### **Combinando Consultas com AND**
O seguinte trecho de código mostra como combinar consultas com AND.

~~~Java
// Emails de host específico, obter todos os e-mails que chegaram antes de hoje e todos os e-mails que chegaram desde 7 dias atrás
builder.getFrom().contains("SpecificHost.com");
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~ 
#### **Combinando Consultas com OR**

[MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) fornece o método [or()](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) que aceita duas instâncias de [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) como parâmetros. Ele obtém mensagens que correspondem a qualquer uma das duas condições especificadas. O exemplo abaixo filtra mensagens que têm a palavra "teste" no assunto ou "noreply@host.com" como remetente. O seguinte trecho de código mostra como combinar consultas com OR.

~~~Java
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~ 
### **Filtragem de E-mails Sensível a Maiúsculas e Minúsculas**
Os e-mails podem ser filtrados com base na sensibilidade a maiúsculas e minúsculas especificando a flag IgnoreCase nos critérios de filtro, como mostrado no seguinte trecho de código.

~~~Java
// Construção de consulta por meio da classe ExchangeQueryBuilder
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~ 
## **Filtrando Mensagens com Suporte a Paginação**
~~~Java
int itemsPerPage = 5;
String sGuid = UUID.randomUUID().toString();
String str1 = sGuid + " - " + "Consulta 1";
String str2 = sGuid + " - " + "Consulta 2";

MailQueryBuilder queryBuilder1 = new MailQueryBuilder();
queryBuilder1.getSubject().contains(str1);
MailQuery query1 = queryBuilder1.getQuery();
List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), query1, itemsPerPage);
pages.add(pageInfo);
int str1Count = pageInfo.getItems().size();
while (!pageInfo.getLastPage()) {
    pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), query1, itemsPerPage, pageInfo.getPageOffset() + 1);
    pages.add(pageInfo);
    str1Count += pageInfo.getItems().size();
}
~~~