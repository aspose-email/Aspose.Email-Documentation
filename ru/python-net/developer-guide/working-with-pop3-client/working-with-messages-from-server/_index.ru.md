---
title: "Работа с сообщениями от сервера"
url: /ru/python-net/working-with-messages-from-server/
weight: 40
type: docs
---

## **Получение информации о почтовом ящике**
Мы можем получить информацию о почтовом ящике, такую как количество сообщений и размер ящика, используя методы GetMailBoxSize() и GetMailBoxInfo().

- Метод `GetMailBoxSize()` возвращает размер почтового ящика в байтах.
- Метод `GetMailBoxInfo()` возвращает объект типа Pop3MailBoxInfo.

Также можно узнать количество сообщений с помощью свойства MessageCount и размер с помощью свойства OccupiedSize. Следующий образец кода показывает, как получить информацию о почтовом ящике. Он показывает, как:

1. Создать [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client).
1. Подключиться к POP3 серверу.
1. Узнать размер почтового ящика.
1. Получить информацию о почтовом ящике.
1. Узнать количество сообщений в почтовом ящике.
1. Получить занимаемый размер.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GettingMailboxInfo-GettingMailboxInfo.py" >}}
## **Получение количества email сообщений в почтовом ящике**
Следующий фрагмент кода показывает, как подсчитать email сообщения в почтовом ящике.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-GetEmailCountInMailbox-GetEmailCountInMailbox.py" >}}



Aspose.Email позволяет разработчикам работать с email сообщениями многими способами. Например, они могут извлекать информацию заголовка перед тем, как решить, загружать email или нет. Или они могут извлекать emails с сервера и сохранять их без их парсинга (быстрее) или после парсинга (медленнее). Эта статья показывает, как извлекать и конвертировать emails.
## **Извлечение информации заголовков email**
Заголовки email могут дать нам информацию о сообщении, которую мы можем использовать для решения, извлекать полное сообщение или нет. Обычно информация заголовка содержит отправителя, тему, дату получения и т. д. (Заголовки email подробно описаны в разделе Кастомизация заголовков email. Эта тема специфична для отправки email через SMTP, но информация о содержании заголовков email остается актуальной для POP3 email). Следующие примеры показывают, как извлечь заголовки email с POP3 сервера по номеру последовательности сообщения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailHeaders-RetrievingEmailHeaders.py" >}}
## **Извлечение email сообщений**
Компонент Aspose.Email.Pop3 предоставляет возможность извлекать email сообщения с POP3 сервера и парсить их в экземпляр MailMessage с помощью компонентов MailMessage. Класс MailMessage содержит несколько свойств и методов для манипуляции содержимым email. Используя функцию FetchMessage класса Pop3Client, вы можете получить экземпляр MailMessage напрямую с POP3 сервера. Следующий фрагмент кода показывает, как извлечь полное email сообщение с POP3 сервера.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrievingEmailMessages-RetrievingEmailMessages.py" >}}
## **Извлечение сводной информации о сообщении с помощью уникального ID**
POP3 клиент API может извлекать сводную информацию о сообщении с сервера, используя уникальный ID сообщения. Это позволяет быстро получить краткую информацию о сообщении без извлечения полного сообщения с сервера. Следующий фрагмент кода показывает, как извлечь сводную информацию о сообщении.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-RetrieveMessageSummaryInformationUsingUniqueId-RetrieveMessageSummaryInformationUsingUniqueId.py" >}}
## **Список сообщений с MultiConnection**

Для операций с высокой нагрузкой Aspose.Email предлагает свойство 'use_multi_connection' класса [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) для использования нескольких подключений при извлечении email. Однако, использование этого режима не обязательно должно приводить к увеличению производительности. Следующий фрагмент кода показывает, как установить соединение с POP3 сервером, настроить клиент для разрешения до 5 одновременных соединений и включить режим много подключений для извлечения информации о сообщениях на сервере:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
message_info_coll = client.list_messages()
```

## **Получение сообщений с сервера и сохранение на диск**
### **Сохранение сообщения на диск без парсинга**
Если вы хотите скачать email сообщения с POP3 сервера без их парсинга, используйте функцию SaveMessage класса Pop3Client. Функция SaveMessage не парсит email сообщение, поэтому она быстрее, чем функция FetchMessage. Следующий фрагмент кода показывает, как сохранить сообщение по его номеру последовательности, в этом случае номер 1. Метод SaveMessage сохраняет сообщение в исходном формате EML без парсинга.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SaveToDiscWithoutParsing-SaveToDiscWithoutParsing.py" >}}

### **Парсинг сообщения перед сохранением**

Используйте метод 'fetch_message' объекта клиента, созданного с помощью класса [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class), чтобы извлечь сообщение с конкретным номером последовательности. Пример кода ниже демонстрирует, как извлечь конкретное сообщение и сохранить его, используя его тему как имя файла, вызывая метод 'save' на объекте msg:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)

# Извлечение сообщения по его номеру последовательности и сохраняем сообщение, используя его тему как имя файла
msg = client.fetch_message(1)
msg.save("first-message_out.eml", ae.SaveOptions.default_eml)
```
### **Фильтрация сообщений по отправителю, получателю или дате**
Класс Pop3Client, описанный в разделе Подключение к POP3 серверу, предоставляет метод list_messages(), который получает все сообщения из почтового ящика. Чтобы получить только сообщения, которые соответствуют некоторому условию, используйте перегруженный метод ListMessages(), который принимает MailQuery в качестве аргумента. Класс MailQuery предоставляет различные свойства для указания условий запроса, например, дата, тема, отправитель, получатель и так далее. Класс MailQueryBuilder используется для построения выражения поиска. Сначала задаются все условия и ограничения, затем MailQuery заполняется запросом, разработанным MailQueryBuilder. Объект класса MailQuery используется Pop3Client для извлечения отфильтрованной информации с сервера. Эта статья показывает, как фильтровать email сообщения из почтового ящика. В первом примере иллюстрируется, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и как строить более сложные запросы. Также показывает применение фильтра даты и времени для извлечения определенных emails из почтового ящика. Кроме того, также показывает, как применять фильтрацию с учетом регистра.
### **Фильтрация сообщений из почтового ящика**
Чтобы отфильтровать сообщения из почтового ящика:

1. Подключитесь и войдите на POP3 сервер.
1. Создайте экземпляр MailQuery и задайте необходимые свойства.
1. Вызовите метод `Pop3Client.list_messages(MailQuery query)` и передайте MailQuery в параметры, чтобы получить только отфильтрованные сообщения.

Следующий фрагмент кода показывает, как подключиться к POP3 почтовому ящику и получить сообщения, которые прибыли сегодня и имеют слово "рассылка" в теме.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-FilterMessagesFromMailbox-FilterMessagesFromMailbox.py" >}}

### **Получение сообщений, соответствующих определенным критериям**

Aspose.Email также позволяет создавать сложные критерии поиска для запроса и фильтрации email сообщений. Для этой цели используйте класс [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) и его свойства. Критерии для извлечения следующие:

- Извлечение сообщений по дате доставки.
- Извлечение сообщений в определенном диапазоне.
- Извлечение сообщений от конкретного отправителя.
- Извлечение сообщений от конкретного домена.
- Извлечение сообщений к конкретному получателю.

#### **Сегодняшняя дата**

Чтобы извлечь сообщения по дате доставки, используйте свойство 'internal_date', как показано в примере кода ниже:

```py
import aspose.email as ae
from datetime import datetime

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.on(datetime.now())
```
#### **Диапазон дат**

Чтобы извлечь сообщения в определенном диапазоне дат, используйте то же свойство 'internal_date', указывая диапазон дат, как показано в примере кода ниже:

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
# Emails, которые поступили за последние 7 дней
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
```
#### **Конкретный отправитель**

Чтобы извлечь сообщения от конкретного отправителя, используйте свойство 'from_address', как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("saqib.razzaq@127.0.0.1")
```
#### **Конкретный домен**

Чтобы извлечь сообщения от конкретного домена, используйте свойство 'from_address', как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("SpecificHost.com")
```
#### **Конкретный получатель**

Чтобы извлечь сообщения к конкретному получателю, используйте свойство 'to', как показано в примере кода ниже:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.to.contains("recipient")
```
### **Построение сложных запросов**

Иногда необходимо удовлетворить более одного запроса. Aspose.Email позволяет это, комбинируя запросы в несколько операторов. Создайте объект [MailQueryBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools.search/mailquerybuilder/#mailquerybuilder-class) и используйте его свойства для формирования конкретных запросов.

#### **Комбинирование запросов с AND**

Следующий фрагмент кода показывает, как комбинировать запросы с AND.

```py
import aspose.email as ae
from datetime import datetime, timedelta

builder = ae.tools.search.MailQueryBuilder()
builder.internal_date.before(datetime.now())
builder.internal_date.since(datetime.today() - timedelta(days=7))
builder.from_address.contains("SpecificHost.com")
```
#### **Комбинирование запросов с OR**

Следующий фрагмент кода показывает, как комбинировать запросы с OR.

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.either(builder.subject.contains("test"), builder.from_address.contains("noreply@host.com"))
```

#### **Применение фильтров с учетом регистра**

API также предоставляет возможность фильтровать email сообщения из почтового ящика на основе критерия с учетом регистра. Следующие методы класса [StringComparisonField](https://reference.aspose.com/email/python-net/aspose.email.tools.search/stringcomparisonfield/#stringcomparisonfield-class) предоставляют возможность искать email, указывая флаги учета регистра.  

- Метод `Aspose.Email.StringComparisonField.contains(value, ignore_case)`
- Метод `Aspose.Email.StringComparisonField.equals(value, ignore_case)`
- Метод `Aspose.Email.StringComparisonField.not_contains(value, ignore_case)`
- Метод `Aspose.Email.StringComparisonField.not_equals(value, ignore_case)`

Следующий фрагмент кода показывает, как реализовать эту возможность в вашем проекте:

```py
import aspose.email as ae

builder = ae.tools.search.MailQueryBuilder()
builder.from_address.contains("noreply@host.com", True)
```