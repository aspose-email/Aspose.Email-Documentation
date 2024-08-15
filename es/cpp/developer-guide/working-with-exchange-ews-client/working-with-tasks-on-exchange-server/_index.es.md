---
title: "Trabajar con tareas en Exchange Server"
url: /es/cpp/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---

## **Trabajando con tareas**
Aspose.Email admite el procesamiento de tareas en Exchange Server mediante *ExchangeTask* clase. Diferentes propiedades expuestas por *ExchangeTask*, como *Subject*, *Status*, *DueDate*, y *Priority*, se puede usar para configurar la tarea en Exchange. El [IEWSClient ](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client)la clase expone funciones como [CreateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a25420465dd38d784ce78428818ea2b78), [UpdateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a4ed6fe13e1278778cc28b867c3ef9dea), and [DeleteTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2bd114b07afa5e97649788a9a9dd9cda) que se utilizan para procesar tareas en el servidor Exchange. En este artículo se muestra cómo:

- Crea una nueva tarea.
- Establece la zona horaria de una tarea.
- Actualiza una tarea.
- Eliminar una tarea.
- Enviar solicitud de tarea
- Guardar tarea en disco
### **Crear nueva tarea**
El siguiente fragmento de código muestra cómo usar la opción Crear una nueva tarea.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cpp" >}}
### **Especificación de la zona horaria**
The [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) interfaz y *ExchangeTask* proporcionar el [TimeZoneId](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a650927ee2f7ae45babc217f148640148) propiedad para configurar la información de la zona horaria al crear una tarea. El siguiente fragmento de código muestra cómo especificar la zona horaria.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cpp" >}}
### **Tarea de actualización**
Los siguientes fragmentos de código muestran cómo actualizar una tarea en el servidor Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cpp" >}}
### **Eliminar tarea**
El siguiente fragmento de código muestra cómo eliminar una tarea en el servidor Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cpp" >}}
### **Envío de solicitud de tarea**
El servicio Aspose.Email Exchange ofrece la capacidad de enviar solicitudes de tareas similares a las de Outlook. El siguiente fragmento de código muestra cómo cargar un mensaje de solicitud de tarea desde el disco y enviarlo mediante el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cpp" >}}
### **Guardar la tarea en un disco**
Aspose.Email también permite guardar las tareas de Exchange en un disco en formato Outlook MSG. El siguiente fragmento de código muestra cómo guardar una tarea en un disco.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cpp" >}}
