---
title: "Работа с сообщениями с сервера"
url: /ru/net/working-with-messages-from-server/
weight: 50
type: docs
---


## **Получение данных почтового ящика**

Мы можем получить информацию о почтовом ящике, такую как количество сообщений и размер почтового ящика, используя [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/v) and [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) методы [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.

- The [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/) метод возвращает размер почтового ящика в байтах.
- The [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) метод возвращает объект типа [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/).

Также можно получить количество сообщений, используя [MessageCount](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/messagecount/) свойство и размер с использованием [OccupiedSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/occupiedsize/) собственность [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/) класс. В следующем примере кода показано, как получить информацию о почтовом ящике. В нем показано, как:

1. Создайте [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Подключитесь к серверу POP3.
1. Узнайте размер почтового ящика.
1. Получите информацию о почтовом ящике.
1. Получите количество сообщений в почтовом ящике.
1. Найдите занятый размер.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GettingMailboxInfo-GettingMailboxInfo.cs" >}}

## **Определение количества писем в почтовом ящике**

В следующем фрагменте кода показано, как подсчитать количество сообщений электронной почты в почтовом ящике.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetEmailCountIntheMailbox-GetEmailCountIntheMailbox.cs" >}}

Aspose.Email позволяет разработчикам работать с электронной почтой разными способами. Например, они могут получить информацию из заголовка, прежде чем принимать решение о загрузке электронного письма. Или они могут извлекать электронные письма с сервера и сохранять их без анализа (быстрее) или после анализа (медленнее). В этой статье показано, как извлекать и конвертировать электронные письма.

## **Получение информации о заголовках электронных писем**

Заголовки электронной почты могут предоставить нам информацию об электронном сообщении, которую мы можем использовать для принятия решения о том, следует ли получать все сообщение электронной почты. Как правило, информация в заголовке содержит отправителя, тему, дату получения и т. д. (заголовки электронных писем подробно описаны в [Настройка заголовков электронной почты](https://docs.aspose.com/email/ru/net/creating-and-setting-contents-of-emails/#set-email-headers). Этот раздел посвящен, в частности, отправке электронного письма по протоколу SMTP, но информация о содержимом заголовка письма остается актуальной для писем по протоколу POP3). В следующих примерах показано, как получать заголовки писем с сервера POP3 по порядковому номеру сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.cs" >}}

## **Получение сообщений электронной почты**

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) компонент класса предоставляет возможность извлекать сообщения электронной почты с сервера POP3 и преобразовывать их в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр с помощью [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) компоненты. [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс содержит несколько свойств и методов для управления содержимым электронной почты. Используя [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) метод [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) класс, вы можете получить [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр непосредственно с сервера POP3. В следующем фрагменте кода показано, как получить полное сообщение электронной почты с сервера POP3.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailMessages-RetrievingEmailMessages.cs" >}}

## **Получение сводной информации о сообщении с использованием уникального идентификатора**

Клиент API POP3 может получать сводную информацию о сообщении с сервера, используя уникальный идентификатор сообщения. Это обеспечивает быстрый доступ к краткой информации о сообщении без предварительного получения полного сообщения с сервера. В следующем фрагменте кода показано, как получить сводную информацию о сообщении.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.cs" >}}

## **Список сообщений с помощью MultiConnection**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) обеспечивает [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) свойство, которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете настроить количество подключений, которое будет использоваться в режиме нескольких подключений, используя [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). В следующем фрагменте кода показано использование режима нескольких подключений для перечисления сообщений и сравнивается его производительность с режимом одиночного подключения.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3ListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Загрузка сообщений с сервера и сохранение на диск**

### **Сохранить сообщение на диск без парсинга**

Если вы хотите загрузить сообщения электронной почты с сервера POP3 без их анализа, используйте [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) функция. [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) функция не анализирует сообщение электронной почты, поэтому оно работает быстрее, чем [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) функция. В следующем фрагменте кода показано, как сохранить сообщение по порядковому номеру. В этом случае [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) метод сохраняет сообщение в исходном формате EML без его анализа.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SaveToDiskWithoutParsing-SaveToDiskWithoutParsing.cs" >}}

### **Проанализируйте сообщение перед сохранением**

В следующем фрагменте кода используется [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) метод получения сообщения с сервера POP3 по порядковому номеру, а затем сохранения сообщения на диск, используя тему в качестве имени файла.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ParseMessageAndSave-ParseMessageAndSave.cs" >}}

## **Групповая выборка сообщений**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) обеспечивает [FetchMessages](https://docs.aspose.com/email/ru/net/working-with-messages-from-server/) метод, который принимает итерацию последовательных номеров или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Следующий фрагмент кода демонстрирует использование [FetchMessages](https://docs.aspose.com/email/ru/net/working-with-messages-from-server/) метод получения сообщений по порядковым номерам и уникальному идентификатору.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3FetchGroupMessages-1.cs" >}}

## **Фильтрация сообщений по отправителю, получателю или дате**

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) класс, описанный в [Подключение к серверу POP3](https://docs.aspose.com/email/ru/net/connect-to-pop3-server/), предоставляет [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/) метод, который принимает [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в качестве аргумента. [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) класс предоставляет различные свойства для указания условий запроса, например дату, тему, отправитель, получатель и т. д. [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) класс используется для построения поискового выражения. Сначала задаются все условия и ограничения, а затем [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) заполняется запросом, разработанным [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/). [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) объект класса используется [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) для извлечения отфильтрованной информации с сервера. В этой статье показано, как фильтровать сообщения электронной почты из почтового ящика. В первом примере показано, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и создавать более сложные запросы. Также показано применение фильтра даты и времени для извлечения определенных писем из почтового ящика. Кроме того, в нем также показано, как применять фильтрацию с учетом регистра символов.

### **Фильтрация сообщений из почтового ящика**

Чтобы отфильтровать сообщения из почтового ящика, выполните следующие действия

1. [Подключение к серверу POP3 и вход на него](https://docs.aspose.com/email/ru/net/connect-to-pop3-server/#connecting-to-pop3-server).
2. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) и задайте нужные свойства.
3. Позвоните [`Pop3Client.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages_8) метод и передайте [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в параметрах, чтобы получать только отфильтрованные сообщения.

В следующем фрагменте кода показано, как подключиться к почтовому ящику POP3 и получать сообщения, пришедшие сегодня и содержащие слово «информационный бюллетень» в теме.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-FilterMessagesFromPOP3Mailbox-FilterMessagesFromPOP3Mailbox.cs" >}}

### **Получение сообщений, соответствующих определенным критериям**

[Приведенные выше примеры кода](https://docs.aspose.com/email/ru/net/working-with-messages-from-server/#filtering-messages-from-mailbox) показывает, как фильтровать сообщения по теме и дате письма. Мы также можем использовать другие свойства для установки других поддерживаемых условий. Ниже приведены несколько примеров настройки условий с помощью [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/).

Приведенные ниже фрагменты кода показывают, как фильтровать электронные письма по другим критериям:

- Найдите электронные письма, доставленные сегодня.
- Найдите электронные письма, полученные в пределах диапазона.
- Найдите электронные письма от определенного отправителя.
- Найдите электронные письма, отправленные с определенного домена.
- Найдите электронные письма, отправленные определенному получателю.
 
#### **Сегодняшняя дата**

В следующем фрагменте кода показано, как найти электронные письма, доставленные сегодня.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

#### **Диапазон дат**

В следующем фрагменте кода показано, как найти электронные письма, полученные в пределах диапазона.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsOverDateRange.cs" >}}

#### **Конкретный отправитель**

В следующем фрагменте кода показано, как найти электронные письма от определенного отправителя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificSenderEmails.cs" >}}

#### **Конкретный домен**

В следующем фрагменте кода показано, как найти электронные письма, отправленные с определенного домена.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificDomainEmails.cs" >}}

#### **Конкретный получатель**

В следующем фрагменте кода показано, как найти электронные письма, отправленные определенному получателю.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

### **Создание сложных запросов**

Если отличается [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) свойства задаются в отдельных выражениях, тогда все условия будут выполнены. Например, если мы хотим получать сообщения за определенный диапазон дат и от определенного хоста, нам нужно написать три выражения.

#### **Объединение запросов с AND**

В следующем фрагменте кода показано, как комбинировать запросы с AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombineQueriesWithAND.cs" >}}

#### **Объединение запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) обеспечивает [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or) метод, который требует двух [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В следующем фрагменте кода показано, как фильтровать сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombiningQueriesWithOR.cs" >}}

#### **Применение фильтров, чувствительных к регистру**

API также предоставляет возможность фильтровать электронные письма из почтового ящика на основе критериев, учитывающих регистр символов. Следующие методы позволяют искать электронные письма, указывая флажок, учитывающий регистр букв.

- Method `Aspose.Email.StringComparisonField.Contains(string value, bool ignoreCase)`
- Method `Aspose.Email.StringComparisonField.Equals(string value, bool ignoreCase)`
- Method `Aspose.Email.StringComparisonField.NotContains(string value, bool ignoreCase)`
- Method `Aspose.Email.StringComparisonField.NotEquals(string value, bool ignoreCase)`

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ApplyCaseSensitiveFilters-ApplyCaseSensitiveFilters.cs" >}}
