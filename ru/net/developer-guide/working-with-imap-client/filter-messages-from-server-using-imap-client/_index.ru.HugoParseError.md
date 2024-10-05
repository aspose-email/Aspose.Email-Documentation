---
title: Фильтрация сообщений с сервера с использованием IMAP-клиента
type: docs
weight: 40
url: /net/filter-messages-from-server-using-imap-client/
---


Класс [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages), который получает все сообщения из почтового ящика. Чтобы получить только сообщения, соответствующие некоторому условию, используйте перегруженный метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages), который принимает [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в качестве аргумента. Класс [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) предоставляет различные свойства для указания условий, например, дата, тема, отправитель, получатель и так далее. Первый пример иллюстрирует, как фильтровать сообщения по дате и теме. Мы также показываем, как отфильтровать по другим критериям и как строить более сложные запросы. API также предоставляет возможность применять критерии поиска с учетом регистра для точного соответствия условиям фильтрации. API также позволяет указывать кодировку строки поиска для фильтрации сообщений из почтового ящика.

## **Фильтрация сообщений из почтового ящика**

1. [Подключитесь и войдите на IMAP-сервер](https://docs.aspose.com/email/net/connecting-to-imap-server/#connecting-with-imap-server)
2. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) и настройте свойства
3. Вызовите метод [`ImapClient.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_14) и передайте [`MailQuery`](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) с параметрами для получения только отфильтрованных сообщений.

Следующий фрагмент кода показывает, как подключиться к IMAP-почтовому ящику и получить сообщения, которые пришли сегодня и содержат слово "newsletter" в теме.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FilteringMessagesFromIMAPMailbox-FilteringMessagesFromIMAPMailbox.cs" >}}

## **Получение сообщений, соответствующих определённым критериям**

[Примеры кода выше](#filtering-messages-from-mailbox) фильтруют сообщения по теме электронной почты и дате. Мы можем использовать другие свойства, чтобы установить и другие поддерживаемые условия. Ниже приведены некоторые примеры установки условий с помощью [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Следующие фрагменты кода показывают, как отфильтровать электронные письма по:

1. Дате сегодня.
1. Диапазону дат.
1. Из конкретного отправителя.
1. Из конкретного домена.
1. Из конкретного получателя.

### **Дата сегодня**

Следующий фрагмент кода показывает, как фильтровать электронные письма по дате сегодня.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

### **Диапазон дат**

Следующий фрагмент кода показывает, как фильтровать электронные письма по диапазону дат.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsOverDateRange.cs" >}}

### **Конкретный отправитель**

Следующий фрагмент кода показывает, как фильтровать электронные письма от конкретного отправителя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificSenderEmails.cs" >}}

### **Конкретный домен**

Следующий фрагмент кода показывает, как фильтровать электронные письма по конкретному домену.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificDomainEmails.cs" >}}

### **Конкретный получатель**

Следующий фрагмент кода показывает, как фильтровать электронные письма для конкретного получателя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

## **Построение сложных запросов**

Если различные свойства [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) устанавливаются в отдельных операторах, тогда все условия будут совпадать. Например, если мы хотим получить сообщения в диапазоне дат и от конкретного хоста, нам нужно написать три оператора.

### **Объединение запросов с AND**

Следующий фрагмент кода показывает, как объединять запросы с AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombineQueriesWithAND.cs" >}}

### **Объединение запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) предоставляет метод [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or), который принимает два экземпляра [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в качестве параметров. Он получает сообщения, которые соответствуют любому из двух указанных условий. Следующий фрагмент кода показывает, как фильтровать сообщения, которые либо содержат "test" в теме, либо "noreply@host.com" в качестве отправителя. Следующий фрагмент кода показывает, как объединять запросы с OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombiningQueriesWithOR.cs" >}}

## **Фильтрация по InternalDate**

Сообщения могут быть извлечены с сервера на основе InternalDate, однако иногда сервер не возвращает все сообщения, видимые во входящих. Причиной может быть часовой пояс сервера, поскольку он может не быть UTC для всех серверов, таких как [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose отправляет команды как 008 SEARCH ON 4-May-2014 согласно [IMAP-протоколу](https://www.rfc-editor.org/rfc/rfc1730), однако результат может отличаться из-за настроек часового пояса сервера. В [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) добавлен новый член [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/), который дополнительно помогает фильтровать сообщения. Следующий фрагмент кода показывает использование [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) для фильтрации сообщений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-InternalDateFilter-InternalDateFilter.cs" >}}

### **Фильтрация электронных писем с учётом регистра**

Следующий фрагмент кода показывает, как использовать фильтрацию электронных писем с учетом регистра.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CaseSensitiveEmailsFiltering-CaseSensitiveEmailsFiltering.cs" >}}

### **Указать кодировку для построителя запросов**

Конструктор API [ImapQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapquerybuilder/) может быть использован для указания кодировки для строки поиска. Это также может быть установлено с помощью свойства [DefaultEncoding](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/defaultencoding/) MailQueryBuilder. Следующий фрагмент кода показывает, как указать кодировку для построителя запросов.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SpecifyEncodingForQueryBuilder-SpecifyEncodingForQueryBuilder.cs" >}}

### **Фильтрация сообщений с поддержкой страниц**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет возможность искать сообщения из почтового ящика и перечислять их с поддержкой страниц. Следующий фрагмент кода показывает, как фильтровать сообщения с поддержкой страниц.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SearchWithPagingSupport-SearchWithPagingSupport.cs" >}}

## **Фильтрация сообщений с использованием пользовательского флага**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetMessagesWithCustomFlags.cs" >}}

## **Фильтрация сообщений с использованием пользовательского поиска**

Например, стандарт RFC 3501 не позволяет выполнять поиск сообщений на основе наличия вложений в сообщениях. Но **Gmail** предоставляет [IMAP-расширения](https://developers.google.com/gmail/imap/imap-extensions?hl=ru), которые позволяют выполнять такой поиск. Следующий фрагмент кода показывает, как сделать соответствующий запрос.

```csharp
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();
queryBuilder.CustomSearch("X-GM-RAW \"has:attachment\"");

MailQuery mailQuery = queryBuilder.GetQuery();
ImapMessageInfoCollection messageInfoCollection = imapClient.ListMessages(mailQuery);
```