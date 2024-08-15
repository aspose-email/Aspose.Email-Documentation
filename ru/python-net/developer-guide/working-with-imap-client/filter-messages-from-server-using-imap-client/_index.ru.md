---
title: "Фильтрация сообщений с сервера с помощью клиента IMAP"
url: /ru/python-net/filter-messages-from-server-using-imap-client/
weight: 30
type: docs
---


Класс IMapClient предоставляет метод listMessages (), который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный метод listMessages (), который принимает MailQuery в качестве аргумента. Класс MailQuery предоставляет различные свойства для указания условий, например дату, тему, отправитель, получатель и т. д. В первом примере показано, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и создавать более сложные запросы. API также предоставляет возможность применять критерии поиска, учитывающие регистр символов, для точного соответствия критериям фильтрации. API также позволяет указать кодировку поисковой строки для фильтрации сообщений из почтового ящика.
## **Фильтрация сообщений из почтового ящика**
1. Подключитесь к серверу IMAP и войдите на него
1. Создайте экземпляр MailQuery и задайте свойства
1. Позвоните `ImapClient.ListMessages(MailQuery query)` метод и передайте MailQuery с параметрами для получения только отфильтрованных сообщений.

В следующем фрагменте кода показано, как подключиться к почтовому ящику IMAP и получать сообщения, пришедшие за день, в теме которых указано слово «информационный бюллетень».



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FilteringMessagesFromIMAPMailbox-FetchEmailMessageFromServer.py" >}}

## **Получение сообщений, соответствующих определенным критериям**

Aspose.Email также позволяет создавать сложные критерии поиска для запроса и фильтрации сообщений электронной почты. Для этого используйте [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) класс и его свойства. Критерии выборки следующие:

- Получайте сообщения по дате доставки.
- Получайте сообщения в пределах диапазона.
- Получайте сообщения от определенного отправителя.
- Получайте сообщения из определенного домена.
- Получайте сообщения определенному получателю.

### **Сегодняшняя дата**

Чтобы получить сообщения по дате доставки, используйте свойство internal_date, как показано в примере кода ниже:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
### **Диапазон дат**

Чтобы получать сообщения в пределах диапазона дат, используйте то же свойство internal_date, указывающее диапазон дат, как показано в примере кода ниже:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
### **Конкретный отправитель**

Чтобы получить сообщения от определенного отправителя, используйте свойство from_address, как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
### **Конкретный домен**

Чтобы получать сообщения из определенного домена, используйте свойство from_address, как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
### **Конкретный получатель**

Чтобы отправить сообщения определенному получателю, используйте свойство «to», как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

## **Создание сложных запросов**

Иногда необходимо удовлетворить более одного запроса. Aspose.Email делает это возможным, объединяя запросы в несколько выражений. Создайте [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) объект и используйте его свойства для создания конкретных запросов.

### **Объединение запросов с AND**

В следующем фрагменте кода показано, как комбинировать запросы с AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
### **Объединение запросов с OR**

В следующем фрагменте кода показано, как комбинировать запросы с OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```
## **Фильтрация по внутренней дате**

API предоставляет возможность получать с сервера список сообщений, удовлетворяющих указанным условиям. В приведенном ниже примере кода показано, как построить запрос на основе условий «внутренняя дата» и «тема содержит». Под «внутренней датой» понимается дата и время получения или добавления сообщения электронной почты на почтовый сервер. Ее можно задать с помощью свойства 'internal_date' [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) class.


```py
import aspose.email as ae
from datetime import datetime

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.select_folder("Inbox")

# Set conditions, Subject contains "Newsletter", Emails that arrived today
builder = ae.clients.imap.ImapQueryBuilder()
builder.subject.contains("Newsletter")
builder.internal_date.on(datetime.now())

# Build the query and Get list of messages
query = builder.get_query()
messages = client.list_messages(query)
for info in messages:
    print(f"Internal Date: {info.internal_date}")
```
Код печатает внутреннюю дату каждого сообщения, удовлетворяющего указанным условиям.

## **Фильтрация сообщений по настраиваемым флагам ключевых слов**

Библиотека Aspose.Email позволяет создать запрос для поиска в почтовом ящике IMAP писем, содержащих собственные флаги ключевых слов. В приведенном ниже примере используются настраиваемые ключевые слова «custom1» и «custom2». Используйте [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class) класс, который представляет собой инструмент, позволяющий создавать поисковые запросы, которые можно использовать для фильтрации электронных писем при их получении с сервера IMAP. Создайте конструктор запросов. Используя метод конструктора 'has_flags', добавьте в запрос условия, чтобы включить только электронные письма, содержащие ключевые слова с флагами IMAP. Настраиваемые ключевые слова в IMAP также называются определяемыми пользователем флагами, которые можно использовать для пометки или маркировки писем в почтовом ящике для различных целей, включая классификацию, статус и многое другое. В следующем фрагменте кода показано, как создать запрос для получения определенных писем с помощью настраиваемых флагов ключевых слов: 

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom1"))
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom2"))
```
## **Фильтрация сообщений с помощью настраиваемого поиска**

Библиотеку Python можно использовать для создания поискового запроса для почтового ящика IMAP, который фильтрует электронные письма на основе настраиваемого критерия поиска Gmail, в частности письма с вложениями. Создайте экземпляр [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), который позволяет создавать сложные поисковые запросы IMAP, которые можно использовать для фильтрации писем с сервера IMAP. Вызвав метод custom_search, добавьте в конструктор запросов настраиваемую строку поиска. Строка X-GM-RAW «has:attachment» — это специфичный для Gmail поисковый запрос, в котором используется атрибут X-GM-RAW. Gmail позволяет использовать свой синтаксис поиска в веб-почте при поиске по протоколу IMAP с помощью этого атрибута. Термин «has:attachment» — это поисковый оператор Gmail, который находит все электронные письма, содержащие вложения. В следующем фрагменте кода показано, как фильтровать электронные письма в соответствии с заданными критериями (в данном случае все письма с вложением):

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.custom_search("X-GM-RAW \"has:attachment\"")

mailQuery = builder.get_query()
```

### **Применение фильтров, чувствительных к регистру**

API также предоставляет возможность фильтровать электронные письма из почтового ящика на основе критериев, учитывающих регистр символов. Следующие методы [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) класс предоставляет возможность поиска электронных писем с указанием флажков, чувствительных к регистру. 

- Method `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Method `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Method `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Method `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

В следующем фрагменте кода показано, как реализовать эту возможность в своем проекте:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```
