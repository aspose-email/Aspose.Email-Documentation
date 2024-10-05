---
title: "Фильтрация сообщений с сервера с использованием IMAP-клиента"
url: /ru/python-net/filter-messages-from-server-using-imap-client/
weight: 30
type: docs
---

Класс ImapClient предоставляет метод ListMessages(), который получает все сообщения из почтового ящика. Чтобы получить только сообщения, соответствующие некоторому условию, используйте перегруженный метод ListMessages(), который принимает MailQuery в качестве аргумента. Класс MailQuery предоставляет различные свойства для указания условий, например, дата, тема, отправитель, получатель и так далее. В первом примере показано, как фильтровать сообщения по дате и теме. Мы также показываем, как фильтровать по другим критериям и как строить более сложные запросы. API также предоставляет возможность применения критериев поиска, чувствительных к регистру, для точного соответствия критериям фильтрации. API также позволяет указывать кодировку строки поиска для фильтрации сообщений из почтового ящика.
## **Фильтрация сообщений из почтового ящика**
1. Подключитесь и войдите на IMAP-сервер
1. Создайте экземпляр MailQuery и установите свойства
1. Вызовите `ImapClient.ListMessages(MailQuery query)` метод и передайте MailQuery с параметрами, чтобы получить только отфильтрованные сообщения.

Следующий код показывает, как подключиться к IMAP-почтовому ящику и получить сообщения, которые пришли сегодня и содержат слово "newsletter" в теме.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FilteringMessagesFromIMAPMailbox-FetchEmailMessageFromServer.py" >}}

## **Получение сообщений, соответствующих определенным критериям**

Aspose.Email также позволяет формировать сложные критерии поиска для запросов и фильтрации электронных писем. Для этой цели используйте класс [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) и его свойства. Критерии для извлечения следующие:

- Извлечение сообщений по дате доставки.
- Извлечение сообщений в диапазоне.
- Извлечение сообщений от конкретного отправителя.
- Извлечение сообщений из конкретного домена.
- Извлечение сообщений для конкретного получателя.

### **Сегодняшняя дата**

Чтобы извлечь сообщения по дате доставки, используйте свойство 'internal_date', как показано в приведенном ниже коде:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
### **Диапазон дат**

Чтобы извлечь сообщения в пределах диапазона дат, используйте то же свойство 'internal_date', указывая диапазон дат, как показано в следующем коде:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Электронные письма, которые пришли за последние 7 дней
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
### **Конкретный отправитель**

Чтобы извлечь сообщения от конкретного отправителя, используйте свойство 'from_address', как показано в следующем коде:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
### **Конкретный домен**

Чтобы извлечь сообщения из конкретного домена, используйте свойство 'from_address', как показано в следующем коде:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
### **Конкретный получатель**

Чтобы извлечь сообщения для конкретного получателя, используйте свойство 'to', как показано в следующем коде:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```

## **Создание сложных запросов**

Иногда необходимо удовлетворить более одного запроса. Aspose.Email позволяет это, комбинируя запросы в несколько операторов. Создайте объект [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) и используйте его свойства для создания конкретных запросов.

### **Комбинирование запросов с AND**

Следующий код показывает, как комбинировать запросы с AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
### **Комбинирование запросов с OR**

Следующий код показывает, как комбинировать запросы с OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```
## **Фильтрация по InternalDate**

API предоставляет возможность извлекать список сообщений с сервера, которые соответствуют заданным условиям. Пример кода ниже показывает, как построить запрос по условиям "внутренняя дата" и "тема содержит". "Внутренняя дата" относится к дате и времени, когда электронное сообщение было получено или добавлено на почтовый сервер и может быть установлена с помощью свойства 'internal_date' класса [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class).

```py
import aspose.email as ae
from datetime import datetime

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.select_folder("Inbox")

# Установите условия, Тема содержит "Newsletter", Электронные письма, пришедшие сегодня
builder = ae.clients.imap.ImapQueryBuilder()
builder.subject.contains("Newsletter")
builder.internal_date.on(datetime.now())

# Построить запрос и получить список сообщений
query = builder.get_query()
messages = client.list_messages(query)
for info in messages:
    print(f"Internal Date: {info.internal_date}")
```
Код выводит внутреннюю дату каждого сообщения, которое соответствует заданным условиям.

## **Фильтрация сообщений по пользовательским ключевым флагам**

Библиотека Aspose.Email позволяет создавать запрос для поиска в IMAP-почтовом ящике писем, которые содержат пользовательские ключевые флаги. В следующем примере используются пользовательские ключевые слова "custom1" и "custom2". Используйте класс [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), который является инструментом, позволяющим строить поисковые запросы, которые могут использоваться для фильтрации электронных писем при их получении с IMAP-сервера. Создайте конструктор запросов. Используя метод 'has_flags' конструктора, добавьте условия к запросу, чтобы включить только электронные письма, которые имеют ключевые слова IMAP флагов. Пользовательские ключевые слова в IMAP также известны как пользовательские флаги, которые могут использоваться для маркировки или отмечания электронных писем в почтовом ящике для различных целей, включая категоризацию, статус и многое другое. Следующий код демонстрирует, как создать запрос для получения конкретных электронных писем по пользовательским ключевым флагам:  

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom1"))
builder.has_flags(ae.clients.imap.ImapMessageFlags.keyword("custom2"))
```
## **Фильтрация сообщений с использованием пользовательского поиска**

Библиотека Python может быть использована для создания поискового запроса для IMAP-почтового ящика, который фильтрует электронные письма на основе пользовательского критерия поиска Gmail, в частности, писем, которые имеют вложения. Создайте экземпляр [ImapQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapquerybuilder/#imapquerybuilder-class), который позволяет вам строить сложные поисковые запросы IMAP, которые могут использоваться для фильтрации электронных писем с IMAP-сервера. Вызывая метод 'custom_search', добавьте пользовательскую строку поиска в конструктор запросов. Строка X-GM-RAW "has:attachment" является специальным поисковым термином Gmail, который использует атрибут X-GM-RAW. Gmail позволяет использовать их синтаксис поиска веб-почты в IMAP-поисках через этот атрибут. Термин "has:attachment" является оператором поиска Gmail, который находит все электронные письма, содержащие вложение. Следующий код демонстрирует, как фильтровать электронные письма в соответствии с заданными критериям(в данном случае, все электронные письма с вложением):

```py
import aspose.email as ae

builder = ae.clients.imap.ImapQueryBuilder()
builder.custom_search("X-GM-RAW \"has:attachment\"")

mailQuery = builder.get_query()
```

### **Применение фильтров, чувствительных к регистру**

API также предоставляет возможность фильтровать электронные письма из почтового ящика на основе критерия, чувствительного к регистру. Следующие методы класса [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) предоставляют возможность искать электронные письма, указывая флаги чувствительности к регистру.  

- Метод `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Метод `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Метод `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Метод `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

Следующий код показывает, как реализовать эту возможность в вашем проекте:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```