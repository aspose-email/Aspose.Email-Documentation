---
title: "Работа с задачами на Exchange Server"
url: /ru/cpp/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---

## **Работа с задачами**
Aspose.Email поддерживает обработку задач на Exchange Server с помощью класса *ExchangeTask*. Разные свойства, выставленные *ExchangeTask*, такие как *Subject*, *Status*, *DueDate* и *Priority*, могут быть использованы для настройки задачи на Exchange. Класс [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) предоставляет функции, такие как [CreateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a25420465dd38d784ce78428818ea2b78), [UpdateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a4ed6fe13e1278778cc28b867c3ef9dea) и [DeleteTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2bd114b07afa5e97649788a9a9dd9cda), которые используются для обработки задач на Exchange Server. Эта статья показывает, как:

- Создать новую задачу.
- Установить часовой пояс задачи.
- Обновить задачу.
- Удалить задачу.
- Отправить запрос задачи.
- Сохранить задачу на диск.

### **Создать новую задачу**
Следующий фрагмент кода показывает, как создать новую задачу.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cpp" >}}
### **Указание часового пояса**
Интерфейс [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) и *ExchangeTask* предоставляют свойство [TimeZoneId](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a650927ee2f7ae45babc217f148640148) для установки информации о часовом поясе при создании задачи. Следующий фрагмент кода показывает, как указать часовой пояс.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cpp" >}}
### **Обновить задачу**
Следующие фрагменты кода показывают, как обновить задачу на сервере Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cpp" >}}
### **Удалить задачу**
Следующий фрагмент кода показывает, как удалить задачу на сервере Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cpp" >}}
### **Отправка запроса задачи**
Сервис Exchange Aspose.Email предоставляет возможность отправки запросов задач, аналогичных Outlook. Следующий фрагмент кода показывает, как загрузить сообщение о запросе задачи с диска и отправить его с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cpp" >}}
### **Сохранение задачи на диск**
Aspose.Email также позволяет сохранять задачи Exchange на диск в формате MSG Outlook. Следующий фрагмент кода показывает, как сохранить задачу на диск.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cpp" >}}