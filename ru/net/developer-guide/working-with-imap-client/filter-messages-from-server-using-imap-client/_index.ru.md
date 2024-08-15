---
title: "Фильтрация сообщений с сервера с помощью клиента IMAP"
url: /ru/net/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---


The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс предоставляет [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) метод, который принимает [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в качестве аргумента. [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) класс предоставляет различные свойства для указания условий, например дату, тему, отправитель, получатель и т. д. В первом примере показано, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и создавать более сложные запросы. API также предоставляет возможность применять критерии поиска, учитывающие регистр символов, для точного соответствия критериям фильтрации. API также позволяет указать кодировку поисковой строки для фильтрации сообщений из почтового ящика.

## **Фильтрация сообщений из почтового ящика**

1. [Подключитесь к серверу IMAP и войдите на него](https://docs.aspose.com/email/ru/net/connecting-to-imap-server/#connecting-with-imap-server)
2. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) и задайте свойства
3. Позвоните [`ImapClient.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_14) метод и передайте [`MailQuery`](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) с параметрами для получения только отфильтрованных сообщений.

В следующем фрагменте кода показано, как подключиться к почтовому ящику IMAP и получать сообщения, пришедшие сегодня и содержащие слово «информационный бюллетень» в теме.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FilteringMessagesFromIMAPMailbox-FilteringMessagesFromIMAPMailbox.cs" >}}

## **Получайте сообщения, соответствующие определенным критериям**

[Приведенные выше примеры кода](#filtering-messages-from-mailbox) фильтрует сообщения по теме и дате письма. Мы также можем использовать другие свойства для установки других поддерживаемых условий. Ниже приведены несколько примеров настройки условий с помощью [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Приведенные ниже фрагменты кода показывают, как фильтровать электронные письма по следующим адресам:

1. Сегодняшняя дата.
1. Диапазон дат.
1. От конкретного отправителя.
1. Из определенного домена.
1. От конкретного получателя.

### **Сегодняшняя дата**

В следующем фрагменте кода показано, как фильтровать электронные письма в Сегодняшняя дата.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

### **Диапазон дат**

В следующем фрагменте кода показано, как фильтровать электронные письма по диапазону дат.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetEmailsOverDateRange.cs" >}}

### **Конкретный отправитель**

В следующем фрагменте кода показано, как фильтровать электронные письма определенного отправителя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificSenderEmails.cs" >}}

### **Конкретный домен**

В следующем фрагменте кода показано, как фильтровать электронные письма в определенном домене.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificDomainEmails.cs" >}}

### **Конкретный получатель**

В следующем фрагменте кода показано, как фильтровать электронные письма по определенному получателю.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

## **Создание сложных запросов**

Если отличается [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) свойства задаются в отдельных выражениях, тогда все условия будут выполнены. Например, если мы хотим получать сообщения за определенный диапазон дат и от определенного хоста, нам нужно написать три выражения.

### **Объединение запросов с AND**

В следующем фрагменте кода показано, как комбинировать запросы с AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombineQueriesWithAND.cs" >}}

### **Объединение запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) обеспечивает [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) метод, который требует двух [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В следующем фрагменте кода показано, как фильтровать сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-BuildingComplexQueries-CombiningQueriesWithOR.cs" >}}

## **Фильтрация по внутренней дате**

Сообщения могут быть извлечены с сервера на основе InternalDate, однако иногда сервер не возвращает все сообщения, видимые в папке «Входящие». Это может быть связано с часовым поясом сервера, поскольку на всех серверах, таких как UTC, может быть не так. [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose отправляет команды типа 008 SEARCH 4 мая 2014 года в соответствии с [протокол IMAP](https://www.rfc-editor.org/rfc/rfc1730) однако результат может отличаться из-за настроек часового пояса сервера. Новый участник добавлен в [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) as [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) что дополнительно помогает фильтровать сообщения. Следующий фрагмент кода показывает использование [InternalDate](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/internaldate/) для фильтрации сообщений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-InternalDateFilter-InternalDateFilter.cs" >}}

### **Фильтрация писем с учетом регистра**

В следующем фрагменте кода показано, как использовать фильтрацию писем с учетом регистра букв.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CaseSensitiveEmailsFiltering-CaseSensitiveEmailsFiltering.cs" >}}

### **Укажите кодировку для конструктора запросов**

API [ImapQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapquerybuilder/) Конструктор можно использовать для указания кодировки строки поиска. Это также можно установить с помощью [DefaultEncoding](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/defaultencoding/) свойство конструктора MailQueryBuilder. В следующем фрагменте кода показано, как указать кодировку для конструктора запросов.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SpecifyEncodingForQueryBuilder-SpecifyEncodingForQueryBuilder.cs" >}}

### **Фильтрация сообщений с поддержкой пейджинга**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет возможность искать сообщения из почтового ящика и составлять их список с поддержкой пейджинга. В следующем фрагменте кода показано, как фильтровать сообщения с поддержкой пейджинга.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SearchWithPagingSupport-SearchWithPagingSupport.cs" >}}

## **Фильтрация сообщений с помощью настраиваемого флага**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GetMessagesWithSpecificCriteria-GetMessagesWithCustomFlags.cs" >}}

## **Фильтрация сообщений с помощью настраиваемого поиска**

Например, стандарт RFC 3501 не разрешает поиск сообщений на основе наличия вложений в сообщениях. Но **Gmail** provides [Расширения IMAP](https://developers.google.com/gmail/imap/imap-extensions?hl=ru) которые позволяют выполнить такой поиск. В следующем фрагменте кода показано, как сделать соответствующий запрос.

```csharp
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();
queryBuilder.CustomSearch("X-GM-RAW \"has:attachment\"");

MailQuery mailQuery = queryBuilder.GetQuery();
ImapMessageInfoCollection messageInfoCollection = imapClient.ListMessages(mailQuery);
```
