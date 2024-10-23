---
title: "Filtrar Mensagens da Caixa de Correio do Exchange usando WebDav"
url: /pt/java/filter-messages-from-exchange-mailbox-using-webdav/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

A classe [ExchangeClient](http://www.aspose.com/api/java/email/com.aspose.email/classes/ExchangeClient) fornece o método listMessages() que obtém todas as mensagens de uma caixa de correio. Para obter apenas mensagens que correspondem a alguma condição, utilize o método sobrecarregado listMessages() que recebe a classe [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) como argumento. A classe [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) fornece várias propriedades para especificar condições, como data, assunto, remetente e destinatário. Além disso, a API também permite aplicar filtros com sensibilidade a maiúsculas e minúsculas para recuperar e-mails da caixa de correio.

{{% /alert %}} 
## **Filtrar Mensagens usando Web Dav**
Para obter mensagens filtradas de uma caixa de correio:

1. Conecte-se ao servidor Exchange.
1. Crie uma instância de MailQuery e defina as propriedades desejadas.
1. Chame o método ExchangeClient.listMessages(MailQuery query) e passe o MailQuery nos parâmetros para obter apenas as mensagens filtradas.

Os exemplos de código abaixo mostram como se conectar a uma caixa de correio do Exchange e obter mensagens que contêm a string "Newsletter" no assunto e foram enviadas hoje.


~~~Java
ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username", "username", "password", "domain");
SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

// Construção da consulta por meio da classe ExchangeQueryBuilder
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
// Assunto contém "Newsletter"
builder.getSubject().contains("Newsletter");

// E-mails que chegaram hoje
try {
	builder.getInternalDate().on(sdf.parse("10/05/2016 10:00:00"));
} catch (ParseException e) {
	e.printStackTrace();
}

// Construa a consulta
MailQuery query = builder.getQuery();

// Obtenha a lista de mensagens
ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
System.out.println("Imap: " + messages.size() + " mensagem(ns) encontrada(s).");
~~~
## **Obter Mensagens que Atendam a Critérios Específicos**
Os exemplos de código acima filtram mensagens com base no assunto do e-mail e na data. Podemos filtrar outras propriedades também. Abaixo estão alguns exemplos de definição das condições usando [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery).
#### **Critérios de Filtragem Data de Hoje**
O seguinte trecho de código mostra como filtrar todos os e-mails com base na data de hoje.


~~~Java
// E-mails que chegaram hoje
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Critérios de Filtragem Intervalo de Datas**
O seguinte trecho de código mostra como filtrar todos os e-mails com base no intervalo de datas.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().beforeOrEqual(new Date());
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(1)));
~~~
#### **Critérios de Filtragem Remetente Específico**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em um remetente específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Obter e-mails de remetente específico
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Critérios de Filtragem Domínio Específico**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em um domínio específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Obter e-mails de domínio específico
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Critérios de Filtragem Destinatário Específico**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em um destinatário específico.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Obter e-mails enviados para destinatário específico
builder.getTo().contains("recipient");
~~~
#### **Critérios de Filtragem por MessageID**
O seguinte trecho de código mostra como filtrar todos os e-mails com base no MessageID.


~~~Java
// Obter e-mail com MessageId específico
ExchangeQueryBuilder builder1 = new ExchangeQueryBuilder();
builder1.getMessageId().equals("MessageID");
~~~
#### **Critérios de Filtragem Todas as Notificações de Entrega de E-mails**
O seguinte trecho de código mostra como filtrar todos os e-mails com base em todas as notificações de entrega de e-mails.


~~~Java
// Obter Notificações de Entrega de E-mails
builder1 = new ExchangeQueryBuilder();
builder1.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
## **Construindo Consultas Complexas**
Se diferentes propriedades de QueryBuilder forem definidas em declarações separadas, todas as condições são combinadas. Por exemplo, para obter uma mensagem em um intervalo de datas específico e de um host específico, escreva três declarações:
#### **Combinando Consultas com AND**


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();

// E-mails de host específico
builder.getFrom().contains("SpecificHost.com");
// E AND todos os e-mails que chegaram antes de hoje
builder.getInternalDate().before(new Date());
// E AND todos os e-mails que chegaram desde 7 dias atrás
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(-7)));
~~~
#### **Combinando Consultas com OR**

`QueryBuilder` fornece o método `or()` que recebe duas instâncias `MailQuery` como parâmetros. Ele obtém mensagens que correspondem a qualquer uma das duas condições especificadas. O exemplo abaixo filtra mensagens que têm a palavra "teste" no assunto ou "noreply@host.com" como remetente.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
		
// Especificar condição OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
#### **Filtragem de E-mails com Sensibilidade a Maiúsculas e Minúsculas**
Os e-mails podem ser filtrados com base na sensibilidade a maiúsculas e minúsculas especificando a flag IgnoreCase nos critérios de filtragem, como mostrado no exemplo a seguir.


~~~Java
//IgnoreCase é True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
~~~