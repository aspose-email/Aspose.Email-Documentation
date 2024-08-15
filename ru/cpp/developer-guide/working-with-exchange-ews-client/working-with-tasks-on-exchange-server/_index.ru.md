---
title: "Работа с задачами на сервере Exchange"
url: /ru/cpp/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---

## **Работа с задачами**
Aspose.Email поддерживает обработку задач на сервере Exchange с использованием *ExchangeTask* класс. Различные свойства, проявляемые *ExchangeTask*, как *Subject*, *Status*, *DueDate*, и *Priority*, можно использовать для настройки задачи в Exchange. [IEWSClient ](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)класс предоставляет такие функции, как [CreateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a25420465dd38d784ce78428818ea2b78), [UpdateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a4ed6fe13e1278778cc28b867c3ef9dea), and [DeleteTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2bd114b07afa5e97649788a9a9dd9cda) которые используются для обработки задач на сервере Exchange. В этой статье показано, как:

- Создайте новую задачу.
- Задайте часовой пояс задачи.
- Обновите задачу.
- Удалить задачу.
- Отправить запрос на задание
- Сохранить задачу на диске
### **Создать новую задачу**
В следующем фрагменте кода показано, как использовать функцию «Создать новую задачу».



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cpp" >}}
### **Указание часового пояса**
The [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) интерфейс и *ExchangeTask* предоставьте [TimeZoneId](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a650927ee2f7ae45babc217f148640148) свойство для установки информации о часовом поясе при создании задачи. В следующем фрагменте кода показано, как указать часовой пояс.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cpp" >}}
### **Обновить задачу**
В следующих фрагментах кода показано, как обновить задачу на сервере Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cpp" >}}
### **Удалить задачу**
В следующем фрагменте кода показано, как удалить задачу на сервере Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cpp" >}}
### **Отправка запроса на задание**
Сервис Aspose.Email Exchange предоставляет возможность отправлять запросы на выполнение задач аналогично Outlook. В следующем фрагменте кода показано, как загрузить сообщение с запросом на задание с диска и отправить его с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cpp" >}}
### **Сохранение задачи на диск**
Aspose.Email также позволяет сохранять задачи Exchange на диск в формате Outlook MSG. В следующем фрагменте кода показано, как сохранить задачу на диск.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cpp" >}}
