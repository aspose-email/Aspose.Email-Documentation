---
title: Фильтрация сообщений из почтового ящика Exchange
type: docs
weight: 30
url: /java/filter-messages-from-exchange-mailbox/
---


{{% alert color="primary" %}} 

Aspose.Email для Java предоставляет возможность фильтровать сообщения из почтового ящика Exchange с использованием [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) и [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Сообщения могут быть отфильтрованы по различным критериям, таким как дата, домен, идентификатор сообщения и уведомления о доставке почты. В этой статье описывается, как фильтровать сообщения из Exchange Server, используя различные критерии.

{{% /alert %}} 
## **Фильтрация сообщений с использованием EWS**
Класс [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) предоставляет метод [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(\)), который получает все сообщения из почтового ящика. Чтобы получить только сообщения, соответствующие какому-либо условию, используйте перегруженный метод [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20com.aspose.email.MailQuery\)), который принимает класс [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) в качестве аргумента. Класс [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) предоставляет различные свойства для задания условий, такие как дата, тема, отправитель и получатель. Кроме того, API также позволяет применять фильтры с учетом регистра для извлечения писем из почтового ящика.
### **Фильтрация сообщений**
Чтобы получить отфильтрованные сообщения из почтового ящика:

1. Подключитесь к серверу Exchange.
2. Создайте экземпляр MailQuery и установите желаемые свойства.
3. Вызовите метод IEWSClient.listMessages() и передайте MailQuery в параметры, чтобы получить только отфильтрованные сообщения.

Следующий фрагмент кода показывает, как подключиться к IMAP почтовому ящику и получить сообщения с текстом "Newsletter" в теме, отправленных сегодня.

~~~Java
try {
    // Подключение к EWS
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String username = "username";
    final String password = "password";
    final String domain = "domain";

    IEWSClient client = EWSClient.getEWSClient(mailboxUri, username, password, domain);

    // Создание запроса с помощью класса ExchangeQueryBuilder
    ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

    // Установить тему и письма, которые пришли сегодня
    builder.getSubject().contains("Newsletter");
    builder.getInternalDate().on(new Date());

    MailQuery query = builder.getQuery();

    // Получить список сообщений
    ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
    System.out.println("EWS: " + messages.size() + " сообщение(й) найдено.");

    // Отключиться от EWS
    client.dispose();
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
### **Фильтрация сообщений по критериям**
Примеры кода выше фильтруют сообщения на основе темы электронной почты и даты. Мы также можем фильтровать по другим свойствам. Ниже приведены некоторые примеры установки условий с использованием [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery).
#### **Фильтрация сообщений по сегодняшней дате**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании сегодняшней даты.

~~~Java
// Письма, которые пришли сегодня
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Фильтрация сообщений по диапазону дат**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании диапазона дат.

~~~Java
// Письма, которые пришли за последние 7 дней
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Фильтрация сообщений по конкретному отправителю**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании конкретного отправителя.

~~~Java
// Получить письма от конкретного отправителя
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Фильтрация сообщений по конкретному домену**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании конкретного домена.

~~~Java
// Получить письма от конкретного домена
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Фильтрация сообщений по конкретному получателю**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании конкретного получателя.

~~~Java
// Получить письма, отправленные конкретному получателю
builder.getTo().contains("recipient");
~~~
#### **Фильтрация сообщений по MessageID**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании MessageID.

~~~Java
// Получить письмо с конкретным MessageId
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getMessageId().equals("MessageID");
~~~
#### **Фильтрация сообщений по всем уведомлениям о доставке почты**
Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании всех уведомлений о доставке почты.

~~~Java
// Получить уведомления о доставке почты
builder = new ExchangeQueryBuilder();
builder.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
#### **Фильтрация сообщений по размеру**
~~~Java
builder = new ExchangeQueryBuilder();
builder.getItemSize().greater(80000);
~~~
#### **Фильтрация сообщений по строковому значению**

Следующий фрагмент кода показывает, как отфильтровать все электронные письма на основании указанной строки в заголовках (тема, от, к, копия). Метод [getText()](https://reference.aspose.com/email/java/com.aspose.email/exchangequerybuilder/#getText--) возвращает строковое значение вместе с телом сообщения.

```java
 ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

builder.getText().equals("SomeText");

MailQuery query = builder.getQuery();

ExchangeMessageInfoCollection messages = ewsClient.listMessages("InboxUri", query, false);
```
#### **Фильтрация сообщений в восходящем/нисходящем порядке**

Aspose.Email предоставляет метод [ComparisonField.orderBy(boolean ascending)](https://reference.aspose.com/email/java/com.aspose.email/comparisonfield/#orderBy-boolean-) который устанавливает значение, указывающее, что клиент использует восходящую или нисходящую сортировку по полю поиска. Это позволяет сортировать электронные сообщения в восходящем/нисходящем порядке на основе критериев, указанных в [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/).

Следующий фрагмент кода демонстрирует, как фильтровать сообщения в восходящем/нисходящем порядке:

```java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Report");
builder.getInternalDate().since(sinceDate);
builder.getSubject().orderBy(true); // сортировка по теме в восходящем порядке
builder.getInternalDate().orderBy(false); // сортировка по дате в нисходящем порядке  

ExchangeMessageInfoCollection miColl = client.listMessages(client.getMailboxInfo().getInboxUri(), builder.getQuery());
```
### **Создание сложных запросов**
Если различные свойства [MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) установлены в отдельном операторе, все условия будут соблюдены. Например, чтобы получить сообщение в определённом диапазоне дат и от конкретного хоста, напишите три оператора:
#### **Объединение запросов с AND**
Следующий фрагмент кода показывает, как объединить запросы с AND.

~~~Java
// Письма от конкретного хоста, получить все письма, которые пришли до сегодня, и все письма, которые пришли за последние 7 дней
builder.getFrom().contains("SpecificHost.com");
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Объединение запросов с OR**

[MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) предоставляет метод [or()](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)), который принимает два экземпляра [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) в качестве параметров. Он получает сообщения, которые соответствуют любому из двух заданных условий. Пример ниже фильтрует сообщения, которые либо имеют слово "test" в теме, либо "noreply@host.com" в качестве отправителя. Следующий фрагмент кода показывает, как объединить запросы с OR.

~~~Java
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
### **Фильтрация электронных писем с учетом регистра**
Электронные письма могут фильтроваться с учетом регистра, указывая флаг IgnoreCase в критериях фильтрации, как показано в следующем фрагменте кода.

~~~Java
// Создание запроса с использованием класса ExchangeQueryBuilder
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~
## **Фильтрация сообщений с поддержкой постраничного отображения**
~~~Java
int itemsPerPage = 5;
String sGuid = UUID.randomUUID().toString();
String str1 = sGuid + " - " + "Запрос 1";
String str2 = sGuid + " - " + "Запрос 2";

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