---
title: Фильтрация сообщений из почтового ящика Exchange с использованием WebDav
type: docs
weight: 40
url: /java/filter-messages-from-exchange-mailbox-using-webdav/
---

{{% alert color="primary" %}} 

Класс [ExchangeClient](http://www.aspose.com/api/java/email/com.aspose.email/classes/ExchangeClient) предоставляет метод listMessages(), который получает все сообщения из почтового ящика. Чтобы получить только те сообщения, которые соответствуют определенному условию, используйте перегруженный метод listMessages(), который принимает класс [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) в качестве аргумента. Класс [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) предоставляет различные свойства для указания условий, таких как дата, тема, отправитель и получатель. В дополнение к этому, API также позволяет применять фильтры с учетом регистра для извлечения электронных писем из почтового ящика.

{{% /alert %}} 
## **Фильтрация сообщений с использованием Web Dav**
Чтобы получить отфильтрованные сообщения из почтового ящика:

1. Подключитесь к серверу Exchange.
1. Создайте экземпляр MailQuery и установите необходимые свойства.
1. Вызовите метод ExchangeClient.listMessages(MailQuery query) и передайте MailQuery в качестве параметра, чтобы получить только отфильтрованные сообщения.

Приведенные ниже примеры кода показывают, как подключиться к почтовому ящику Exchange и получить сообщения, в которых в теме имеется строка "Newsletter" и которые были отправлены сегодня.


~~~Java
ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username", "username", "password", "domain");
SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

// Формирование запроса с помощью класса ExchangeQueryBuilder
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
// Тема содержит "Newsletter"
builder.getSubject().contains("Newsletter");

// Электронные письма, которые пришли сегодня
try {
	builder.getInternalDate().on(sdf.parse("10/05/2016 10:00:00"));
} catch (ParseException e) {
	e.printStackTrace();
}

// Построение запроса
MailQuery query = builder.getQuery();

// Получить список сообщений
ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
System.out.println("Imap: " + messages.size() + " message(s) found.");
~~~
## **Получение сообщений, которые соответствуют определенным критериям**
Примеры кода выше фильтруют сообщения на основе темы письма и даты. Мы можем фильтровать и по другим свойствам. Ниже приведены некоторые примеры установления условий с использованием [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery).
#### **Фильтр критериев по сегодняшней дате**
Следующий фрагмент кода показывает, как фильтровать все электронные письма на основе сегодняшней даты.


~~~Java
// Электронные письма, которые пришли сегодня
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Фильтр критериев по диапазону дат**
Следующий фрагмент кода показывает, как фильтровать все электронные письма на основе диапазона дат.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().beforeOrEqual(new Date());
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(1)));
~~~
#### **Фильтр критериев по конкретному отправителю**
Следующий фрагмент кода показывает, как фильтровать все электронные письма на основе конкретного отправителя.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Получить электронные письма от конкретного отправителя
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Фильтр критериев по конкретному домену**
Следующий фрагмент кода показывает, как фильтровать все электронные письма на основе конкретного домена.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Получить электронные письма из конкретного домена
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Фильтр критериев по конкретному получателю**
Следующий фрагмент кода показывает, как фильтровать все электронные письма на основе конкретного получателя.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Получить электронные письма, отправленные конкретному получателю
builder.getTo().contains("recipient");
~~~
#### **Фильтр критериев по MessageID**
Следующий фрагмент кода показывает, как фильтровать все электронные письма на основе MessageID.


~~~Java
// Получить электронное письмо с конкретным MessageId
ExchangeQueryBuilder builder1 = new ExchangeQueryBuilder();
builder1.getMessageId().equals("MessageID");
~~~
#### **Фильтр критериев для всех уведомлений о доставке почты**
Следующий фрагмент кода показывает, как фильтровать все электронные письма на основе всех уведомлений о доставке почты.


~~~Java
// Получить уведомления о доставке почты
builder1 = new ExchangeQueryBuilder();
builder1.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
## **Построение сложных запросов**
Если разные свойства QueryBuilder установлены в отдельных выражениях, все условия должны совпадать. Например, чтобы получить сообщение в определенном диапазоне дат и от конкретного хоста, напишите три выражения:
#### **Комбинирование запросов с AND**


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();

// Электронные письма от конкретного хоста
builder.getFrom().contains("SpecificHost.com");
// И все электронные письма, которые пришли до сегодняшнего дня
builder.getInternalDate().before(new Date());
// И все электронные письма, которые пришли за последние 7 дней
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(-7)));
~~~
#### **Комбинирование запросов с OR**

`QueryBuilder` предоставляет метод `or()`, который принимает два экземпляра `MailQuery` в качестве параметров. Это получит сообщения, которые соответствуют любому из двух указанных условий. Пример ниже фильтрует сообщения, которые либо имеют слово "test" в теме, либо "noreply@host.com" в качестве отправителя.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
		
// Укажите условие OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
#### **Фильтрация электронной почты с учетом регистра**
Электронные письма могут быть отфильтрованы с учетом регистра, задав флаг IgnoreCase в критериях фильтрации, как показано в следующем примере.


~~~Java
//IgnoreCase равно True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
~~~