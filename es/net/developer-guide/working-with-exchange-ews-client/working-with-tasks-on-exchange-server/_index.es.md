---
title: "Trabajar con tareas en Exchange Server"
url: /es/net/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---


## **Trabajando con tareas**

Aspose.Email admite el procesamiento de tareas en Exchange mediante [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/) clase. Diferentes propiedades expuestas por [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/), como [Subject](https://reference.aspose.com/email/net/aspose.email.calendar/task/subject/), [Status](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/status/), [DueDate](https://reference.aspose.com/email/net/aspose.email.calendar/task/duedate/), y [Priority](https://reference.aspose.com/email/net/aspose.email.calendar/task/priority/), se puede usar para configurar la tarea en Exchange. El [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) la clase expone funciones como [CreateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createtask/#createtask/), [UpdateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatetask/#updatetask/), and [DeleteTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteitem/) que se utilizan para procesar tareas en Exchange. En este artículo se muestra cómo:

- Crea una nueva tarea.
- Establece la zona horaria de una tarea.
- Actualiza una tarea.
- Eliminar una tarea.
- Enviar solicitud de tarea
- Guardar tarea en disco
 
### **Crear nueva tarea**

El siguiente fragmento de código muestra cómo crear una nueva tarea.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cs" >}}

### **Especificación de la zona horaria**

The [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interfaz y [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/) proporcionar el [TimeZoneId](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/timezoneid/) propiedad para configurar la información de la zona horaria al crear una tarea. El siguiente fragmento de código muestra cómo especificar la zona horaria.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cs" >}}

### **Tarea de actualización**

Los siguientes fragmentos de código muestran cómo actualizar una tarea en un servidor de Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cs" >}}

### **Eliminar tarea**

En el siguiente fragmento de código se muestra cómo eliminar una tarea en un servidor de Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cs" >}}

### **Envío de solicitud de tarea**

El servicio Aspose.Email Exchange ofrece la capacidad de enviar solicitudes de tareas similares a las de Outlook. El siguiente fragmento de código muestra cómo cargar un mensaje de solicitud de tarea desde el disco y enviarlo mediante el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cs" >}}

### **Guardar la tarea en un disco**

Aspose.Email también permite guardar las tareas de Exchange en un disco en formato Outlook MSG. El siguiente fragmento de código muestra cómo guardar una tarea en un disco.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cs" >}}

### **Listado de tareas de Exchange Server**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) proporciona la [ListTasks](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listtasks/#listtasks/) método que se puede usar para obtener tareas de un servicio web de Exchange. Tiene varias sobrecargas que se pueden utilizar para recuperar la lista de tareas de una carpeta específica o mediante algunos criterios de búsqueda. El siguiente ejemplo de código muestra cómo obtener todas las tareas o algunas de ellas de la carpeta Tareas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListTasksFromExchangeServer-ListTasksFromExchangeServerWithEWS.cs" >}}

### **Filtrado de tareas desde Exchange Server**

Aspose.Email ofrece la capacidad de recuperar tareas específicas del servidor en lugar de recuperar todas las tareas del servidor. La API se puede usar para recuperar las tareas por estado, como completadas, aplazadas, en curso, no iniciadas o en espera de otras. El [ExchangeQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder/) la clase se puede usar para especificar el criterio deseado utilizando la propiedad Status. También permite especificar varias condiciones para recuperar las tareas deseadas de Exchange Server. Esto se demuestra en el siguiente ejemplo de código.
