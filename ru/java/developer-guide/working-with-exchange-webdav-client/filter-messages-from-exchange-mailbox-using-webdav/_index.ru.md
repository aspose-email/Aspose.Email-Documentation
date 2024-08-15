---
title: "Фильтрация сообщений из почтового ящика Exchange с помощью WebDAV"
url: /ru/java/filter-messages-from-exchange-mailbox-using-webdav/
weight: 40
type: docs
---

{{% alert color="primary" %}}

The [ExchangeClient](http://www.aspose.com/api/java/email/com.aspose.email/classes/ExchangeClient) класс предоставляет метод listMessages (), который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный метод listMessages (), который принимает [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) класс в качестве аргумента. [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) класс предоставляет различные свойства для указания условий, например даты, темы, отправителя и получателя. Кроме того, API также позволяет применять фильтры, учитывающие регистр символов, для получения писем из почтового ящика.

{{% /alert %}}
## **Фильтрация сообщений с помощью Web Dav**
Чтобы получить отфильтрованные сообщения из почтового ящика, выполните следующие действия:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр MailQuery и задайте нужные свойства.
1. Вызовите метод ExchangeClient.listMessages (запрос MailQuery) и передайте MailQuery в параметры, чтобы получить только отфильтрованные сообщения.

В приведенных ниже примерах кода показано, как подключиться к почтовому ящику Exchange и получать сообщения со строкой «Новостная рассылка», отправленные сегодня.


~~~Java
ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username", "username", "password", "domain");
SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

// Query building by means of ExchangeQueryBuilder class
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
// Subject contains "Newsletter"
builder.getSubject().contains("Newsletter");

// Emails that arrived today
try {
	builder.getInternalDate().on(sdf.parse("10/05/2016 10:00:00"));
} catch (ParseException e) {
	e.printStackTrace();
}

// Build the query
MailQuery query = builder.getQuery();

// Get list of messages
ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
System.out.println("Imap: " + messages.size() + " message(s) found.");
~~~
## **Получайте сообщения, соответствующие определенным критериям**
Приведенные выше примеры кода фильтруют сообщения по теме и дате письма. Мы также можем фильтровать другие свойства. Ниже приведены несколько примеров настройки условий с помощью [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery).
#### **Критерии фильтрации: сегодняшняя дата**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе сегодняшней даты.


~~~Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Диапазон дат критериев фильтрации**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе диапазона дат.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().beforeOrEqual(new Date());
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(1)));
~~~
#### **Критерии фильтрации: конкретный отправитель**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного отправителя.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Критерии фильтрации: конкретный домен**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе определенного домена.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Критерии фильтрации: конкретный получатель**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного получателя.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~
#### **Критерии фильтрации по MessageID**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе MessageID.


~~~Java
// Get email with specific MessageId
ExchangeQueryBuilder builder1 = new ExchangeQueryBuilder();
builder1.getMessageId().equals("MessageID");
~~~
#### **Критерии фильтрации Все уведомления о доставке почты**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе всех уведомлений о доставке почты.


~~~Java
// Get Mail Delivery Notifications
builder1 = new ExchangeQueryBuilder();
builder1.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
## **Создание сложных запросов**
Если разные свойства QueryBuilder заданы в отдельном выражении, все условия соблюдаются. Например, чтобы получить сообщение в определенном диапазоне дат и от определенного хоста, напишите три выражения:
#### **Объединение запросов с AND**


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();

// Emails from specific host
builder.getFrom().contains("SpecificHost.com");
// AND all emails that arrived before today
builder.getInternalDate().before(new Date());
// AND all emails that arrived since 7 days ago
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(-7)));
~~~
#### **Объединение запросов с OR**

`QueryBuilder` обеспечивает `or()` метод, который требует двух `MailQuery` экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В приведенном ниже примере отфильтровываются сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
		
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
#### **Фильтрация электронной почты с учетом регистра**
Электронные письма можно отфильтровать на основе чувствительности к регистру, указав флаг IgnoreCase в критериях фильтрации, как показано в следующем примере.


~~~Java
//IgnoreCase is True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
~~~
