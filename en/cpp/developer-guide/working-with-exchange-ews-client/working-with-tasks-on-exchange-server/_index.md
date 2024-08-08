---
title: Working with Tasks on Exchange Server
type: docs
weight: 100
url: /cpp/working-with-tasks-on-exchange-server/
---

## **Working with Tasks**
Aspose.Email supports processing tasks on Exchange Server using the *ExchangeTask* class. Different properties exposed by *ExchangeTask*, like *Subject*, *Status*, *DueDate*, and *Priority*, can be used to configure the task on Exchange. The [IEWSClient ](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)class exposes functions like [CreateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a25420465dd38d784ce78428818ea2b78), [UpdateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a4ed6fe13e1278778cc28b867c3ef9dea), and [DeleteTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2bd114b07afa5e97649788a9a9dd9cda) which are used to process tasks on the Exchange Server. This article shows how to:

- Create a new task.
- Set a task's timezone.
- Update a task.
- Delete a task.
- Send Task Request
- Save Task to Disc
### **Create New Task**
The following code snippet shows you how to use create a new task.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cpp" >}}
### **Specifying Timezone**
The [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) interface and *ExchangeTask* provide the [TimeZoneId](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a650927ee2f7ae45babc217f148640148) property for setting timezone information when creating a task. The following code snippet shows you how to specify Timezone.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cpp" >}}
### **Update Task**
The following code snippets show how to update a task on the Exchange server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cpp" >}}
### **Delete Task**
The following code snippet shows you how to delete a task on the Exchange server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cpp" >}}
### **Sending Task Request**
Aspose.Email Exchange service provides the capability to send task requests similar to Outlook. The following code snippet shows you how to load a task request message from the disc and send it using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cpp" >}}
### **Saving Task to Disc**
Aspose.Email also allows saving Exchange Tasks to disc in Outlook MSG format. The following code snippet shows you how to save a task to disc.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cpp" >}}
