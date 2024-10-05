---
title: Работа с задачами на Exchange Server
type: docs
weight: 100
url: /net/working-with-tasks-on-exchange-server/
---


## **Работа с задачами**

Aspose.Email поддерживает обработку задач на Exchange с использованием класса [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/). Различные свойства, предоставляемые [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/), такие как [Subject](https://reference.aspose.com/email/net/aspose.email.calendar/task/subject/), [Status](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/status/), [DueDate](https://reference.aspose.com/email/net/aspose.email.calendar/task/duedate/) и [Priority](https://reference.aspose.com/email/net/aspose.email.calendar/task/priority/), могут использоваться для настройки задачи на Exchange. Класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) предоставляет функции, такие как [CreateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createtask/#createtask/), [UpdateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatetask/#updatetask/) и [DeleteTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteitem/), которые используются для обработки задач на Exchange. В этой статье показано, как:

- Создать новую задачу.
- Установить временную зону задачи.
- Обновить задачу.
- Удалить задачу.
- Отправить запрос на задачу.
- Сохранить задачу на диск.
  
### **Создание новой задачи**

Следующий кодовый фрагмент показывает, как создать новую задачу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cs" >}}

### **Указание временной зоны**

Интерфейс [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) и [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/) предоставляют свойство [TimeZoneId](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/timezoneid/) для установки информации о временной зоне при создании задачи. Следующий кодовый фрагмент показывает, как указать временную зону.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cs" >}}

### **Обновление задачи**

Следующие кодовые фрагменты показывают, как обновить задачу на сервере Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cs" >}}

### **Удаление задачи**

Следующий кодовый фрагмент показывает, как удалить задачу на сервере Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cs" >}}

### **Отправка запроса на задачу**

Сервис Aspose.Email Exchange предоставляет возможность отправлять запросы на задачи, аналогично Outlook. Следующий кодовый фрагмент показывает, как загрузить сообщение запроса на задачу с диска и отправить его с использованием [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cs" >}}

### **Сохранение задачи на диск**

Aspose.Email также позволяет сохранять задачи Exchange на диск в формате Outlook MSG. Следующий кодовый фрагмент показывает, как сохранить задачу на диск.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cs" >}}

### **Получение задач с сервера Exchange**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) предоставляет метод [ListTasks](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listtasks/#listtasks/), который можно использовать для получения задач из веб-сервиса Exchange. Он имеет несколько перегрузок, которые могут быть использованы для извлечения списка задач из конкретной папки или с использованием некоторых критериев поиска. Приведенный ниже кодовый пример иллюстрирует получение всех или конкретных задач из папки задач.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListTasksFromExchangeServer-ListTasksFromExchangeServerWithEWS.cs" >}}

### **Фильтрация задач с сервера Exchange**

Aspose.Email предоставляет возможность извлекать конкретные задачи с сервера, а не извлекать все задачи с сервера. API может использоваться для извлечения задач по статусу задачи, таким как Завершено, Отложено, В процессе, Не начато или Ожидание от других. Класс [ExchangeQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder/) может использоваться для указания желаемых критериев с использованием свойства Status. Он также позволяет указывать несколько условий для извлечения желаемых задач с сервера Exchange. Это демонстрируется следующим кодовым примером.