---
title: "Trabajando con Tareas en Exchange Server"
url: /es/java/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---


## **Trabajando con Tareas**
Aspose.Email admite el procesamiento de tareas en Exchange utilizando la clase [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask). Las diferentes propiedades expuestas por [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask), como [Subject](https://apireference.aspose.com/email/java/com.aspose.email/Task#getSubject\(\)), [Status](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeTask#getStatus\(\)), [DueDate](https://apireference.aspose.com/email/java/com.aspose.email/Task#getDueDate\(\)), y [Priority](https://apireference.aspose.com/email/java/com.aspose.email/Task#getPriority\(\)), pueden utilizarse para configurar la tarea en Exchange. La clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) expone funciones como [createTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createTask\(com.aspose.email.ExchangeTask\)), [updateTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateTask\(com.aspose.email.ExchangeTask\)), y [deleteTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteTask\(java.lang.String\)) que se utilizan para procesar tareas en Exchange. Este artículo muestra cómo:

- Crear una nueva tarea.
- Establecer la zona horaria de una tarea.
- Actualizar una tarea.
- Eliminar una tarea.
- Enviar Solicitud de Tarea
- Guardar Tarea en Disco
### **Crear Nueva Tarea**
El siguiente fragmento de código te muestra cómo crear una nueva tarea.

~~~Java
// Crear instancia de la clase EWSClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Crear objeto de tarea de Exchange
ExchangeTask task = new ExchangeTask();

// Establecer el asunto y el estado de la tarea a En progreso
task.setSubject("Nueva-Prueba");
task.setStatus(ExchangeTaskStatus.InProgress);
client.createTask(client.getMailboxInfo().getTasksUri(), task);
~~~
### **Especificando la Zona Horaria**
La interfaz [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) y [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) proporcionan la propiedad TimeZoneId para establecer información de zona horaria al crear una tarea. El siguiente fragmento de código te muestra cómo especificar la Zona Horaria.

~~~Java
client.setTimezoneId("Hora Estándar de Europa Central");
~~~
### **Actualizar Tarea**
Los siguientes fragmentos de código muestran cómo actualizar una tarea en un servidor Exchange.

~~~Java
// Crear instancia de la clase ExchangeClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener toda la colección de información de tareas del intercambio
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Analizar toda la información de las tareas en la lista
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Obtener tarea del intercambio utilizando la información actual de la tarea
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Actualizar el estado de la tarea a No Comenzada
    task.setStatus(ExchangeTaskStatus.NotStarted);

    // Establecer la fecha de vencimiento de la tarea
    SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
    task.setDueDate(sdf.parse("26/02/2013 00:00:00"));

    // Establecer la prioridad de la tarea
    task.setPriority(MailPriority.Low.getValue());

    // Actualizar tarea en el intercambio
    client.updateTask(task);
}
~~~
### **Eliminar Tarea**
El siguiente fragmento de código te muestra cómo eliminar una tarea en un servidor Exchange.

~~~Java
// Crear instancia de la clase ExchangeClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener toda la colección de información de tareas del intercambio
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Analizar toda la información de las tareas en la lista
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Obtener tarea del intercambio utilizando la información actual de la tarea
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Verificar si la tarea actual cumple con los criterios de búsqueda
    if (task.getSubject().equals("test")) {
        // Eliminar tarea del intercambio
        client.deleteItem(task.getUniqueUri(), DeletionOptions.getDeletePermanently());
    }
}
~~~
### **Enviando Solicitud de Tarea**
El servicio Exchange de Aspose.Email proporciona la capacidad de enviar solicitudes de tarea similar a Outlook. El siguiente fragmento de código te muestra cómo cargar un mensaje de solicitud de tarea desde el disco y enviarlo usando el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).

~~~Java
// Crear instancia de la clase ExchangeClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveTnefAttachments(true);

// cargar tarea desde archivo .msg
MailMessage eml = MailMessage.load(dataDir + "task.msg", options);
eml.setFrom(MailAddress.to_MailAddress("firstname.lastname@domain.com"));
eml.getTo().clear();
eml.getTo().addMailAddress(new MailAddress("firstname.lastname@domain.com"));
client.send(eml);
~~~
### **Guardar Tarea en Disco**
Aspose.Email también permite guardar Tareas de Exchange en disco en formato MSG de Outlook. El siguiente fragmento de código te muestra cómo guardar una tarea en el disco.

~~~Java
ExchangeTask task = new ExchangeTask();
task.setSubject("TASK-ID - " + UUID.randomUUID());
task.setStatus(ExchangeTaskStatus.InProgress);

Calendar cal = Calendar.getInstance();
task.setStartDate(cal.getTime());
cal.add(Calendar.DATE, 3);
task.setDueDate(cal.getTime());
task.save(dstEmail);
~~~
### **Listar Tareas desde el Servidor Exchange**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) proporciona el método [listTasks](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listTasks\(\)) que se puede utilizar para obtener tareas de un Servicio Web de Exchange. Tiene varias sobrecargas que se pueden usar para recuperar la lista de tareas de una carpeta específica o utilizando ciertos criterios de búsqueda. El siguiente ejemplo de código ilustra cómo obtener todas o tareas específicas de la carpeta de Tareas.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Listando Tareas desde el Servidor
client.setTimezoneId("Hora Estándar de Europa Central");
TaskCollection taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri());

// imprimir detalles de las tareas recuperadas
int iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}

// Listando Tareas desde el servidor basadas en Consulta - Completadas y En Progreso
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };
ExchangeQueryBuilder queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
MailQuery query = queryBuilder.getQuery();

taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri(), query);

// imprimir detalles de las tareas recuperadas
iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}
~~~
### **Filtrando Tareas desde el Servidor Exchange**
Aspose.Email proporciona la capacidad de recuperar tareas específicas del servidor en lugar de recuperar todas las tareas del servidor. La API se puede utilizar para recuperar tareas por estado de la tarea, como Completada, Diferida, En Progreso, No Comenzada o Esperando a otros. La clase [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder) se puede utilizar para especificar el criterio deseado utilizando la propiedad Estado. También permite especificar múltiples condiciones para recuperar las tareas deseadas del Servidor Exchange. Esto se demuestra en el siguiente ejemplo de código.

~~~Java
// Crear instancia de la clase ExchangeClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Establecer zona horaria para las tareas
client.setTimezoneId("Hora Estándar de Europa Central");

// Usamos estos valores de estado para especificar en las consultas
Integer[] values = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.Deferred, ExchangeTaskStatus.InProgress, ExchangeTaskStatus.NotStarted,
        ExchangeTaskStatus.WaitingOnOthers };

messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri());

// Ahora recuperar las tareas con estados específicos
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().equals(status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
    fetchedTask = client.fetchTask(messageInfoCol.get_Item(0).getUniqueUri());
}

// recuperar todas las demás que no sean las especificadas
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().notEquals((int) status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
}

// especificando múltiples criterios
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };

queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);

// listar todos aquellos que no están en nuestros estados especificados
queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().notIn(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
~~~