---
title: "Фильтрация сообщений из почтового ящика Exchange"
url: /ru/java/filter-messages-from-exchange-mailbox/
weight: 30
type: docs
---


{{% alert color="primary" %}}

Aspose.Email для Java предоставляет возможность фильтровать сообщения из почтового ящика Exchange с помощью [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) and [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Сообщения можно фильтровать по различным критериям, например по дате, домену, идентификатору сообщения и уведомлениям о доставке почты. В этой статье показано, как фильтровать сообщения с сервера Exchange по разным критериям.

{{% /alert %}}
## **Фильтрация сообщений с помощью EWS**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) класс предоставляет [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(\)) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20com.aspose.email.MailQuery\)) метод, который принимает [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) класс в качестве аргумента. [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) класс предоставляет различные свойства для указания условий, например даты, темы, отправителя и получателя. Кроме того, API также позволяет применять фильтры, учитывающие регистр символов, для получения писем из почтового ящика.
### **Фильтрация сообщений**
Чтобы получить отфильтрованные сообщения из почтового ящика, выполните следующие действия:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр MailQuery и задайте нужные свойства.
1. Вызовите метод IEWSclient.listMessages () и передайте MailQuery в параметры, чтобы получить только отфильтрованные сообщения.

В следующем фрагменте кода показано, как подключиться к почтовому ящику IMAP и получать сообщения со строкой «Newsletter» в теме и отправленные сегодня.

~~~Java
try {
    // Connect to EWS
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String username = "username";
    final String password = "password";
    final String domain = "domain";

    IEWSClient client = EWSClient.getEWSClient(mailboxUri, username, password, domain);

    // Query building by means of ExchangeQueryBuilder class
    ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

    // Set Subject and Emails that arrived today
    builder.getSubject().contains("Newsletter");
    builder.getInternalDate().on(new Date());

    MailQuery query = builder.getQuery();

    // Get list of messages
    ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
    System.out.println("EWS: " + messages.size() + " message(s) found.");

    // Disconnect from EWS
    client.dispose();
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
### **Фильтрация сообщений по критериям**
Приведенные выше примеры кода фильтруют сообщения по теме и дате письма. Мы также можем фильтровать другие свойства. Ниже приведены несколько примеров настройки условий с помощью [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery).
#### **Отфильтровать сообщения по сегодняшней дате**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе сегодняшней даты.

~~~Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Фильтрация сообщений по диапазону дат**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе диапазона дат.



~~~Java
// Emails that arrived in last 7 days
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Фильтрация сообщений по определенному отправителю**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного отправителя.

~~~Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Фильтрация сообщений по определенному домену**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе определенного домена.

~~~Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Фильтрация сообщений по определенному получателю**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе конкретного получателя.

~~~Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~
#### **Фильтровать сообщения по MessageID**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе MessageID.

~~~Java
// Get email with specific MessageId
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getMessageId().equals("MessageID");
~~~
#### **Фильтрация сообщений по всем уведомлениям о доставке почты**
В следующем фрагменте кода показано, как фильтровать все электронные письма на основе всех уведомлений о доставке почты.

~~~Java
// Get Mail Delivery Notifications
builder = new ExchangeQueryBuilder();
builder.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
#### **Фильтровать сообщения по размеру**
~~~Java
builder = new ExchangeQueryBuilder();
builder.getItemSize().greater(80000);
~~~
#### **Фильтрация сообщений по строковому значению**

В следующем фрагменте кода показано, как фильтровать все электронные письма на основе указанной строки в заголовках (subject, from, to, cc). [getText()](https://reference.aspose.com/email/java/com.aspose.email/exchangequerybuilder/#getText--) метод возвращает строковое значение вместе с телом сообщения.

```java
 ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

builder.getText().equals("SomeText");

MailQuery query = builder.getQuery();

ExchangeMessageInfoCollection messages = ewsClient.listMessages("InboxUri", query, false);
```
#### **Фильтрация сообщений в порядке возрастания/убывания**

Aspose.Email предоставляет [Поле сравнения. OrderBy (логическое значение по возрастанию)](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) метод, который задает значение, указывающее на то, что клиент использует сортировку по возрастанию или убыванию в поле поиска. Он позволяет сортировать сообщения электронной почты в порядке возрастания/убывания на основе критериев, указанных в [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/).

В приведенном ниже фрагменте кода показано, как фильтровать сообщения в порядке возрастания/убывания:

```java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Report");
builder.getInternalDate().since(sinceDate);
builder.getSubject().orderBy(true); // sort the subject ascending
builder.getInternalDate().orderBy(false); // sort the date descending  

ExchangeMessageInfoCollection miColl = client.listMessages(client.getMailboxInfo().getInboxUri(), builder.getQuery());
```
### **Создание сложных запросов**
Если отличается [MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) свойства задаются в отдельном выражении, все условия соблюдены. Например, чтобы получить сообщение в определенном диапазоне дат и от определенного хоста, напишите три выражения:
#### **Объединение запросов с AND**
В следующем фрагменте кода показано, как комбинировать запросы с AND.

~~~Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Объединение запросов с OR**

[MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) обеспечивает [or()](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) метод, который требует двух [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В приведенном ниже примере отфильтровываются сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.

~~~Java
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
### **Фильтрация электронной почты с учетом регистра**
Электронные письма можно отфильтровать на основе чувствительности к регистру, указав флаг IgnoreCase в критериях фильтрации, как показано в следующем фрагменте кода.

~~~Java
// Query building by means of ExchangeQueryBuilder class
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~
## **Фильтрация сообщений с поддержкой пейджинга**
~~~Java
int itemsPerPage = 5;
String sGuid = UUID.randomUUID().toString();
String str1 = sGuid + " - " + "Query 1";
String str2 = sGuid + " - " + "Query 2";

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
