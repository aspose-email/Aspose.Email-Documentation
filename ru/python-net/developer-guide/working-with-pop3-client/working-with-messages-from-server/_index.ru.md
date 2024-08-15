---
title: "Работа с сообщениями с сервера"
url: /ru/python-net/working-with-messages-from-server/
weight: 40
type: docs
---

## **Получение данных почтового ящика**
Мы можем получить информацию о почтовом ящике, например количество сообщений и размер почтового ящика, используя методы getMailboxSize () и getMailboxInfo ().

- The `GetMailBoxSize()` метод возвращает размер почтового ящика в байтах.
- The `GetMailBoxInfo()` метод возвращает объект типа Pop3MailboxInfo.

Также можно получить количество сообщений с помощью свойства MessageCount и размер с помощью свойства OccupiedSize. В следующем примере кода показано, как получить информацию о почтовом ящике. В нем показано, как:

1. Создайте [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client).
1. Подключитесь к серверу POP3.
1. Узнайте размер почтового ящика.
1. Получите информацию о почтовом ящике.
1. Получите количество сообщений в почтовом ящике.
1. Найдите занятый размер.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GettingMailboxInfo-GettingMailboxInfo.py" >}}
## **Определение количества писем в почтовом ящике**
В следующем фрагменте кода показано, как подсчитать количество сообщений электронной почты в почтовом ящике.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GetEmailCountInMailbox-GetEmailCountInMailbox.py" >}}



Aspose.Email позволяет разработчикам работать с электронной почтой разными способами. Например, они могут получить информацию из заголовка, прежде чем принимать решение о загрузке электронного письма. Или они могут извлекать электронные письма с сервера и сохранять их без анализа (быстрее) или после анализа (медленнее). В этой статье показано, как извлекать и конвертировать электронные письма.
## **Получение информации о заголовках электронных писем**
Заголовки электронной почты могут предоставить нам информацию об электронном сообщении, которую мы можем использовать для принятия решения о том, следует ли получать все сообщение электронной почты. Как правило, информация в заголовке содержит отправителя, тему, дату получения и т. д. (заголовки электронных писем подробно описаны в разделе Настройка заголовков электронной почты). Этот раздел посвящен, в частности, отправке электронной почты по протоколу SMTP, но информация о содержимом заголовка письма остается актуальной для писем по протоколу POP3). В следующих примерах показано, как получать заголовки писем с сервера POP3 по порядковому номеру сообщения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.py" >}}
## **Получение сообщений электронной почты**
Компонент класса Aspose.Email.Pop3 предоставляет возможность извлекать сообщения электронной почты с сервера POP3 и преобразовывать их в экземпляр MailMessage с помощью компонентов MailMessage. Класс MailMessage содержит несколько свойств и методов управления содержимым электронной почты. Используя функцию FetchMessage класса Pop3Client, вы можете получить экземпляр MailMessage непосредственно с сервера POP3. В следующем фрагменте кода показано, как получить полное сообщение электронной почты с сервера POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailMessages-RetrievingEmailMessages.py" >}}
## **Получение сводной информации о сообщении с использованием уникального идентификатора**
Клиент API POP3 может получать сводную информацию о сообщении с сервера, используя уникальный идентификатор сообщения. Это обеспечивает быстрый доступ к краткой информации о сообщении без предварительного получения полного сообщения с сервера. В следующем фрагменте кода показано, как получить сводную информацию о сообщении.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.py" >}}
## **Список сообщений с помощью MultiConnection**

Для высоконагруженных операций Aspose.Email предлагает свойство use_multi_connection [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) класс для использования нескольких подключений при получении электронных писем. Однако использование этого режима не обязательно должно приводить к повышению производительности. В следующем фрагменте кода показано, как установить соединение с сервером POP3, настроить клиент на разрешение до 5 одновременных подключений и включить режим нескольких подключений для получения информации о сообщениях, присутствующих на сервере:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
message_info_coll = client.list_messages()
```

## **Загрузка сообщений с сервера и сохранение на диск**
### **Сохранить сообщение на диск без парсинга**
Если вы хотите загружать сообщения электронной почты с сервера POP3 без их анализа, используйте функцию SaveMessage класса Pop3Client. Функция SaveMessage не анализирует сообщение электронной почты, поэтому она работает быстрее, чем функция fetchMessage. В следующем фрагменте кода показано, как сохранить сообщение по порядковому номеру, в данном случае по номеру 1. Метод SaveMessageMethod сохраняет сообщение в исходном формате EML без его анализа.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}

### **Проанализируйте сообщение перед сохранением**

Используйте метод fetch_message клиентского объекта, созданного с помощью [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) класс для получения сообщения с определенным порядковым номером. В приведенном ниже примере кода показано, как извлечь конкретное сообщение и сохранить его, используя тему в качестве имени файла, вызвав метод save для объекта msg:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

# Fetch the message by its sequence number and Save the message using its subject as the file name
msg = client.fetch_message(1)
msg.save("first-message_out.eml", ae.SaveOptions.default_eml)
```
### **Фильтрация сообщений по отправителю, получателю или дате**
Класс Pop3Client, описанный в разделе Подключение к серверу POP3, предоставляет метод list_messages (), который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный метод listMessages (), который принимает MailQuery в качестве аргумента. Класс MailQuery предоставляет различные свойства для указания условий запроса, например дату, тему, отправитель, получатель и т. д. Класс MailQueryBuilder используется для создания поискового выражения. Сначала задаются все условия и ограничения, а затем MailQuery заполняется запросом, разработанным MailQueryBuilder. Объект класса MailQuery используется Pop3Client для извлечения отфильтрованной информации с сервера. В этой статье показано, как фильтровать сообщения электронной почты из почтового ящика. В первом примере показано, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и создавать более сложные запросы. Также показано применение фильтра даты и времени для извлечения определенных писем из почтового ящика. Кроме того, в нем также показано, как применять фильтрацию с учетом регистра символов.
### **Фильтрация сообщений из почтового ящика**
Чтобы отфильтровать сообщения из почтового ящика, выполните следующие действия

1. Подключитесь к серверу POP3 и войдите на него.
1. Создайте экземпляр MailQuery и задайте нужные свойства.
1. Позвоните `Pop3Client.list_messages(MailQuery query)` метод и передайте MailQuery в параметры, чтобы получать только отфильтрованные сообщения.

В следующем фрагменте кода показано, как подключиться к почтовому ящику POP3 и получать сообщения, пришедшие за день, в теме которых указано слово «информационный бюллетень».



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}

### **Получение сообщений, соответствующих определенным критериям**

Aspose.Email также позволяет создавать сложные критерии поиска для запроса и фильтрации сообщений электронной почты. Для этого используйте [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) класс и его свойства. Критерии выборки следующие:

- Получайте сообщения по дате доставки.
- Получайте сообщения в пределах диапазона.
- Получайте сообщения от определенного отправителя.
- Получайте сообщения из определенного домена.
- Получайте сообщения определенному получателю.

#### **Сегодняшняя дата**

Чтобы получить сообщения по дате доставки, используйте свойство internal_date, как показано в примере кода ниже:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
#### **Диапазон дат**

Чтобы получать сообщения в пределах диапазона дат, используйте то же свойство internal_date, указывающее диапазон дат, как показано в примере кода ниже:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails that arrived in last 7 days
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
#### **Конкретный отправитель**

Чтобы получить сообщения от определенного отправителя, используйте свойство from_address, как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
#### **Конкретный домен**

Чтобы получать сообщения из определенного домена, используйте свойство from_address, как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
#### **Конкретный получатель**

Чтобы отправить сообщения определенному получателю, используйте свойство «to», как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```
### **Создание сложных запросов**

Иногда необходимо удовлетворить более одного запроса. Aspose.Email делает это возможным, объединяя запросы в несколько выражений. Создайте [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) объект и используйте его свойства для создания конкретных запросов.

#### **Объединение запросов с AND**

В следующем фрагменте кода показано, как комбинировать запросы с AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
#### **Объединение запросов с OR**

В следующем фрагменте кода показано, как комбинировать запросы с OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Применение фильтров, чувствительных к регистру**

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

