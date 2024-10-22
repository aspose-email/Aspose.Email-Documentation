---
title: Trabajando con Tareas en Exchange Server
type: docs
weight: 100
url: /cpp/working-with-tasks-on-exchange-server/
---

## **Trabajando con Tareas**

Aspose.Email admite el procesamiento de tareas en Exchange Server utilizando la clase _ExchangeTask_. Se pueden utilizar diferentes propiedades expuestas por _ExchangeTask_, como _Subject_, _Status_, _DueDate_ y _Priority_, para configurar la tarea en Exchange. La clase [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) expone funciones como [CreateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a25420465dd38d784ce78428818ea2b78), [UpdateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a4ed6fe13e1278778cc28b867c3ef9dea) y [DeleteTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2bd114b07afa5e97649788a9a9dd9cda), que se utilizan para procesar tareas en el servidor de Exchange. Este artículo muestra cómo:

-   Crear una nueva tarea.
-   Establecer la zona horaria de una tarea.
-   Actualizar una tarea.
-   Eliminar una tarea.
-   Enviar Solicitud de Tarea
-   Guardar Tarea en Disco

### **Crear Nueva Tarea**

El siguiente fragmento de código muestra cómo crear una nueva tarea.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cpp" >}}

### **Especificando la Zona Horaria**

La interfaz [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) y _ExchangeTask_ proporcionan la propiedad [TimeZoneId](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a650927ee2f7ae45babc217f148640148) para establecer información de zona horaria al crear una tarea. El siguiente fragmento de código muestra cómo especificar la Zona Horaria.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cpp" >}}

### **Actualizar Tarea**

Los siguientes fragmentos de código muestran cómo actualizar una tarea en el servidor de Exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cpp" >}}

### **Eliminar Tarea**

El siguiente fragmento de código muestra cómo eliminar una tarea en el servidor de Exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cpp" >}}

### **Enviando Solicitud de Tarea**

El servicio Aspose.Email Exchange proporciona la capacidad de enviar solicitudes de tarea similares a Outlook. El siguiente fragmento de código muestra cómo cargar un mensaje de solicitud de tarea desde el disco y enviarlo utilizando el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cpp" >}}

### **Guardar Tarea en Disco**

Aspose.Email también permite guardar Tareas de Exchange en disco en formato MSG de Outlook. El siguiente fragmento de código muestra cómo guardar una tarea en disco.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cpp" >}}

