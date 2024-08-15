---
title: "Работа с задачами на сервере Exchange"
url: /ru/net/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---


## **Работа с задачами**

Aspose.Email поддерживает обработку задач на Exchange с помощью [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/) класс. Различные свойства, проявляемые [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/), как [Subject](https://reference.aspose.com/email/net/aspose.email.calendar/task/subject/), [Status](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/status/), [DueDate](https://reference.aspose.com/email/net/aspose.email.calendar/task/duedate/), и [Priority](https://reference.aspose.com/email/net/aspose.email.calendar/task/priority/), можно использовать для настройки задачи в Exchange. [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс предоставляет такие функции, как [CreateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createtask/#createtask/), [UpdateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatetask/#updatetask/), and [DeleteTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteitem/) которые используются для обработки задач в Exchange. В этой статье показано, как:

- Создайте новую задачу.
- Задайте часовой пояс задачи.
- Обновите задачу.
- Удалить задачу.
- Отправить запрос на задание
- Сохранить задачу на диске
 
### **Создать новую задачу**

В следующем фрагменте кода показано, как создать новую задачу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cs" >}}

### **Указание часового пояса**

The [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) интерфейс и [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/) предоставьте [TimeZoneId](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/timezoneid/) свойство для установки информации о часовом поясе при создании задачи. В следующем фрагменте кода показано, как указать часовой пояс.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cs" >}}

### **Обновить задачу**

В следующих фрагментах кода показано, как обновить задачу на сервере Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cs" >}}

### **Удалить задачу**

В следующем фрагменте кода показано, как удалить задачу на сервере Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cs" >}}

### **Отправка запроса на задание**

Сервис Aspose.Email Exchange предоставляет возможность отправлять запросы на выполнение задач аналогично Outlook. В следующем фрагменте кода показано, как загрузить сообщение с запросом на задание с диска и отправить его с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cs" >}}

### **Сохранение задачи на диск**

Aspose.Email также позволяет сохранять задачи Exchange на диск в формате Outlook MSG. В следующем фрагменте кода показано, как сохранить задачу на диск.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cs" >}}

### **Вывод списка задач с сервера Exchange**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) обеспечивает [ListTasks](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listtasks/#listtasks/) метод, который можно использовать для получения задач из веб-службы Exchange. Он имеет несколько перегрузок, которые можно использовать для извлечения списка задач из определенной папки или использования некоторых критериев поиска. Приведенный ниже пример кода иллюстрирует получение всех или отдельных задач из папки «Задачи».

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListTasksFromExchangeServer-ListTasksFromExchangeServerWithEWS.cs" >}}

### **Фильтрация задач с сервера Exchange**

Aspose.Email предоставляет возможность извлекать определенные задачи с сервера вместо получения всех задач с сервера. API можно использовать для поиска задач по статусам задач, таким как «Выполнено», «Отложено», «Выполнено», «Не запущено» или «Ожидает» других задач. [ExchangeQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder/) класс можно использовать для указания желаемого критерия с помощью свойства Status. Он также позволяет указать несколько условий для получения желаемых задач с сервера Exchange. Об этом свидетельствует следующий пример кода.
