---
title: "Работа с сообщениями от сервера"
url: /ru/net/working-with-messages-from-server/
weight: 50
type: docs
---


## **Получение информации о почтовом ящике**

Мы можем получить информацию о почтовом ящике, такую как количество сообщений и размер почтового ящика, используя методы [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/v) и [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

- Метод [GetMailBoxSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxsize/#getmailboxsize/) возвращает размер почтового ящика в байтах.
- Метод [GetMailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/getmailboxinfo/#getmailboxinfo/) возвращает объект типа [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/).

Также можно получить количество сообщений с использованием свойства [MessageCount](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/messagecount/) и размер с помощью свойства [OccupiedSize](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/occupiedsize/) класса [Pop3MailBoxInfo](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo/). Следующий пример кода показывает, как получить информацию о почтовом ящике. Он демонстрирует, как:

1. Создать [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
1. Подключиться к POP3-серверу.
1. Получить размер почтового ящика.
1. Получить информацию о почтовом ящике.
1. Получить количество сообщений в почтовом ящике.
1. Получить занимаемый размер.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GettingMailboxInfo-GettingMailboxInfo.cs" >}}

## **Получение количества электронных писем в почтовом ящике**

Следующий фрагмент кода показывает, как подсчитать электронные сообщения в почтовом ящике.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetEmailCountIntheMailbox-GetEmailCountIntheMailbox.cs" >}}

Aspose.Email позволяет разработчикам работать с электронными письмами многими разными способами. Например, они могут получить информацию заголовка перед тем, как решить, загружать ли электронное письмо. Или они могут извлекать электронные письма с сервера и сохранять их без их разбора (быстрее) или после разбора (медленнее). Эта статья показывает, как извлекать и конвертировать электронные письма.

## **Извлечение информации заголовков электронных писем**

Заголовки электронных писем могут дать нам информацию о сообщении, которую мы можем использовать, чтобы решить, извлекать полное сообщение или нет. Обычно информация заголовка включает отправителя, тему, дату получения и т.д. (Заголовки электронных писем описаны подробно в [Настройка заголовков электронных писем](https://docs.aspose.com/email/ru/net/creating-and-setting-contents-of-emails/#set-email-headers). Эта тема относится непосредственно к отправке электронной почты с использованием SMTP, но информация о содержании заголовков электронной почты остается действительной для POP3-писем). Следующие примеры показывают, как извлекать заголовки электронных писем с POP3-сервера по номеру последовательности сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.cs" >}}

## **Извлечение электронных сообщений**

Компонент класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) предоставляет возможность извлекать электронные сообщения с POP3-сервера и анализировать их в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) с помощью компонентов [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) содержит несколько свойств и методов для манипуляции содержимым электронной почты. Используя метод [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/), вы можете получить экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) непосредственно с POP3-сервера. Следующий фрагмент кода показывает, как извлечь полное сообщение электронной почты с POP3-сервера.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrievingEmailMessages-RetrievingEmailMessages.cs" >}}

## **Извлечение информации о сводке сообщения с использованием уникального идентификатора**

Клиент POP3 API может извлекать информацию о сводке сообщений с сервера, используя уникальный идентификатор сообщения. Это обеспечивает быстрый доступ к краткой информации о сообщении без предварительного извлечения полного сообщения с сервера. Следующий фрагмент кода показывает, как извлечь информацию о сводке сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.cs" >}}

## **Список сообщений с многосоединением**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) предоставляет свойство [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/), которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете установить количество соединений, которые будут использоваться в режиме многосоединения, с помощью [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). Следующий фрагмент кода демонстрирует использование режима многосоединения для перечисления сообщений и сравнивает его производительность с режимом единого соединения.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3ListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Обратите внимание, что использование режима многосоединения не гарантирует увеличение производительности.

{{% /alert %}} 

## **Получение сообщений с сервера и сохранение на диске**

### **Сохранить сообщение на диск без разбора**

Если вы хотите загрузить электронные сообщения с POP3-сервера без их разбора, используйте функцию класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/). Функция [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) не разбирает сообщение электронной почты, поэтому она быстрее, чем функция [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/). Следующий фрагмент кода показывает, как сохранить сообщение по его номеру последовательности. В этом случае метод [SaveMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/savemessage/#savemessage/) сохраняет сообщение в исходном формате EML без разбора.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SaveToDiskWithoutParsing-SaveToDiskWithoutParsing.cs" >}}

### **Разбор сообщения перед сохранением**

Следующий фрагмент кода использует метод [FetchMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/fetchmessage/#fetchmessage/) класса [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/), чтобы извлечь сообщение с POP3-сервера по его номеру последовательности, затем сохранить сообщение на диск, используя тему в качестве имени файла.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ParseMessageAndSave-ParseMessageAndSave.cs" >}}

## **Групповое получение сообщений**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) предоставляет метод [FetchMessages](https://docs.aspose.com/email/ru/net/working-with-messages-from-server/), который принимает итератор номеров последовательности или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Следующий фрагмент кода демонстрирует использование метода [FetchMessages](https://docs.aspose.com/email/ru/net/working-with-messages-from-server/) для извлечения сообщений по номерам последовательности и уникальным идентификаторам.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-POP3-Pop3FetchGroupMessages-1.cs" >}}

## **Фильтрация сообщений по отправителю, получателю или дате**

Класс [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/), описанный в [Подключение к POP3-серверу](https://docs.aspose.com/email/ru/net/connect-to-pop3-server/), предоставляет метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/), который получает все сообщения из почтового ящика. Чтобы получить только сообщения, соответствующие какому-либо условию, используйте перегруженный метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages/), который принимает в качестве аргумента [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/). Класс [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) предоставляет различные свойства для указания условий запроса, например, дата, тема, отправитель, получатель и так далее. Класс [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) используется для построения выражения поиска. Сначала устанавливаются все условия и ограничения, а затем [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) заполняется запросом, разработанным с помощью [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/). Объект класса [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) используется классом [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) для извлечения отфильтрованной информации с сервера. Эта статья показывает, как фильтровать сообщения электронной почты из почтового ящика. Первый пример иллюстрирует, как фильтровать сообщения на основе даты и темы. Мы также показываем, как фильтровать по другим критериям и как строить более сложные запросы. Также демонстрируется применение фильтрации по дате и времени для извлечения конкретных писем из почтового ящика. Кроме того, также показано, как применять чувствительную к регистру фильтрацию.

### **Фильтрация сообщений из почтового ящика**

Чтобы отфильтровать сообщения из почтового ящика:

1. [Подключитесь и войдите в POP3-сервер](https://docs.aspose.com/email/ru/net/connect-to-pop3-server/#connecting-to-pop3-server).
2. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) и установите нужные свойства.
3. Вызовите метод [`Pop3Client.ListMessages(MailQuery query)`](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/listmessages/#listmessages_8) и передайте [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в параметры, чтобы получить только отфильтрованные сообщения.

Следующий фрагмент кода показывает, как подключиться к POP3 почтовому ящику и получить сообщения, которые прибыли сегодня и имеют слово "newsletter" в теме.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-FilterMessagesFromPOP3Mailbox-FilterMessagesFromPOP3Mailbox.cs" >}}

### **Получение сообщений, соответствующих определенным критериям**

[Примеры кода выше](https://docs.aspose.com/email/ru/net/working-with-messages-from-server/#filtering-messages-from-mailbox) показывают, как можно фильтровать сообщения на основе темы электронного письма и даты. Мы можем использовать другие свойства, чтобы установить и другие поддерживаемые условия. Ниже приведены некоторые примеры установки условий с помощью [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/).

Следующие фрагменты кода показывают, как фильтровать электронные письма по другим критериям:

- Найти электронные письма, доставленные сегодня.
- Найти электронные письма, полученные в диапазоне.
- Найти электронные письма от конкретного отправителя.
- Найти электронные письма, отправленные с конкретного домена.
- Найти электронные письма, отправленные конкретному получателю.
  
#### **Сегодняшняя дата**

Следующий фрагмент кода показывает, как найти электронные письма, доставленные сегодня.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsWithTodayDate.cs" >}}

#### **Диапазон дат**

Следующий фрагмент кода показывает, как найти электронные письма, полученные в диапазоне.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetEmailsOverDateRange.cs" >}}

#### **Конкретный отправитель**

Следующий фрагмент кода показывает, как найти электронные письма от конкретного отправителя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificSenderEmails.cs" >}}

#### **Конкретный домен**

Следующий фрагмент кода показывает, как найти электронные письма, отправленные с конкретного домена.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificDomainEmails.cs" >}}

#### **Конкретный получатель**

Следующий фрагмент кода показывает, как найти электронные письма, отправленные конкретному получателю.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetMessagesUsingSpecificCriteria-GetSpecificRecipientEmails.cs" >}}

### **Строительство сложных запросов**

Если различные свойства [MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) установлены в отдельных операторов, то все условия будут совпадать. Например, если мы хотим получить сообщения между диапазоном дат и из конкретного хоста, нам нужно написать три оператора.

#### **Объединение запросов с помощью AND**

Следующий фрагмент кода показывает, как объединить запросы с помощью AND.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombineQueriesWithAND.cs" >}}

#### **Объединение запросов с помощью OR**

[MailQueryBuilder](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/) предоставляет метод [Or()](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquerybuilder/or/#or), который принимает два экземпляра [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) в качестве параметров. Он получает сообщения, которые соответствуют любому из двух заданных условий. Следующий фрагмент кода показывает, как фильтровать сообщения, которые либо имеют "test" в теме, либо "noreply@host.com" в качестве отправителя. Следующий фрагмент кода показывает, как объединить запросы с помощью OR.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-BuildComplexQueries-CombiningQueriesWithOR.cs" >}}

#### **Применение чувствительных к регистру фильтров**

API также предоставляет возможность фильтровать электронные письма из почтового ящика на основе критерия, чувствительного к регистру. Следующие методы обеспечивают возможность поиска электронных писем, указывая флаг чувствительности к регистру.

- Метод `Aspose.Email.StringComparisonField.Contains(string value, bool ignoreCase)`
- Метод `Aspose.Email.StringComparisonField.Equals(string value, bool ignoreCase)`
- Метод `Aspose.Email.StringComparisonField.NotContains(string value, bool ignoreCase)`
- Метод `Aspose.Email.StringComparisonField.NotEquals(string value, bool ignoreCase)`

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ApplyCaseSensitiveFilters-ApplyCaseSensitiveFilters.cs" >}}