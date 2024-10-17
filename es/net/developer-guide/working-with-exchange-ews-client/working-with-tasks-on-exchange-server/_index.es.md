---
title: "Trabajando con Tareas en Exchange Server"
url: /es/net/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---

## **Trabajando con Tareas**

Aspose.Email admite el procesamiento de tareas en Exchange utilizando la clase [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/). Diferentes propiedades expuestas por [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/), como [Subject](https://reference.aspose.com/email/net/aspose.email.calendar/task/subject/), [Status](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/status/), [DueDate](https://reference.aspose.com/email/net/aspose.email.calendar/task/duedate/) y [Priority](https://reference.aspose.com/email/net/aspose.email.calendar/task/priority/), se pueden usar para configurar la tarea en Exchange. La clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) expone funciones como [CreateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createtask/#createtask/), [UpdateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatetask/#updatetask/) y [DeleteTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteitem/) que se utilizan para procesar tareas en Exchange. Este artículo muestra cómo:

- Crear una nueva tarea.
- Establecer la zona horaria de una tarea.
- Actualizar una tarea.
- Eliminar una tarea.
- Enviar una Solicitud de Tarea
- Guardar Tarea en Disco
  
### **Crear Nueva Tarea**

El siguiente fragmento de código muestra cómo crear una nueva tarea.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cs" >}}

### **Especificar Zona Horaria**

La interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) y [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/) proporcionan la propiedad [TimeZoneId](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/timezoneid/) para establecer la información de zona horaria al crear una tarea. El siguiente fragmento de código muestra cómo especificar la Zona Horaria.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cs" >}}

### **Actualizar Tarea**

Los siguientes fragmentos de código muestran cómo actualizar una tarea en un servidor Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cs" >}}

### **Eliminar Tarea**

El siguiente fragmento de código muestra cómo eliminar una tarea en un servidor Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cs" >}}

### **Enviando Solicitud de Tarea**

El servicio de Exchange de Aspose.Email proporciona la capacidad de enviar solicitudes de tareas similares a Outlook. El siguiente fragmento de código muestra cómo cargar un mensaje de solicitud de tarea desde el disco y enviarlo utilizando el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cs" >}}

### **Guardar Tarea en Disco**

Aspose.Email también permite guardar Tareas de Exchange en disco en formato MSG de Outlook. El siguiente fragmento de código muestra cómo guardar una tarea en disco.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cs" >}}

### **Listando Tareas desde el Servidor de Exchange**

[IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) proporciona el método [ListTasks](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listtasks/#listtasks/) que se puede utilizar para obtener tareas de un Servicio Web de Exchange. Tiene varias sobrecargas que se pueden usar para recuperar la lista de tareas de una carpeta específica o utilizando algunos criterios de búsqueda. El siguiente ejemplo de código ilustra cómo obtener todas o tareas específicas de la carpeta de Tareas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListTasksFromExchangeServer-ListTasksFromExchangeServerWithEWS.cs" >}}

### **Filtrando Tareas desde el Servidor de Exchange**

Aspose.Email proporciona la capacidad de recuperar tareas específicas del servidor en lugar de recuperar todas las tareas del servidor. La API se puede utilizar para recuperar tareas por estado de tarea como Completadas, Diferidas, En Progreso, No iniciadas o Esperando a otros. La clase [ExchangeQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder/) se puede utilizar para especificar el criterio deseado utilizando la propiedad Status. También permite especificar múltiples condiciones para recuperar tareas deseadas del Servidor de Exchange. Esto se demuestra en el siguiente ejemplo de código.