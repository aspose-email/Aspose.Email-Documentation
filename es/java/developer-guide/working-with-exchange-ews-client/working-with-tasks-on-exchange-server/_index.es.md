---
title: "Trabajar con tareas en Exchange Server"
url: /es/java/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---


## **Trabajando con tareas**
Aspose.Email admite el procesamiento de tareas en Exchange mediante [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) clase. Diferentes propiedades expuestas por [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask), como [Subject](https://apireference.aspose.com/email/java/com.aspose.email/Task#getSubject\(\)), [Status](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeTask#getStatus\(\)), [DueDate](https://apireference.aspose.com/email/java/com.aspose.email/Task#getDueDate\(\)), y [Priority](https://apireference.aspose.com/email/java/com.aspose.email/Task#getPriority\(\)), se puede usar para configurar la tarea en Exchange. El [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) la clase expone funciones como [createTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createTask\(com.aspose.email.ExchangeTask\)), [updateTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateTask\(com.aspose.email.ExchangeTask\)), and [deleteTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteTask\(java.lang.String\)) que se utilizan para procesar tareas en Exchange. En este artículo se muestra cómo:

- Crea una nueva tarea.
- Establece la zona horaria de una tarea.
- Actualiza una tarea.
- Eliminar una tarea.
- Enviar solicitud de tarea
- Guardar tarea en disco
### **Crear nueva tarea**
El siguiente fragmento de código muestra cómo usar la opción Crear una nueva tarea.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create Exchange task object
ExchangeTask task = new ExchangeTask();

// Set task subject and status to In progress
task.setSubject("New-Test");
task.setStatus(ExchangeTaskStatus.InProgress);
client.createTask(client.getMailboxInfo().getTasksUri(), task);
~~~
### **Especificación de la zona horaria**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) interfaz y [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) proporcione la propiedad TimeZoneID para establecer la información de la zona horaria al crear una tarea. El siguiente fragmento de código muestra cómo especificar la zona horaria.



~~~Java
client.setTimezoneId("Central Europe Standard Time");
~~~
### **Tarea de actualización**
Los siguientes fragmentos de código muestran cómo actualizar una tarea en un servidor de Exchange.



~~~Java
// Create instance of ExchangeClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get all tasks info collection from exchange
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Parse all the tasks info in the list
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Fetch task from exchange using current task info
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Update the task status to NotStarted
    task.setStatus(ExchangeTaskStatus.NotStarted);

    // Set the task due date
    SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
    task.setDueDate(sdf.parse("26/02/2013 00:00:00"));

    // Set task priority
    task.setPriority(MailPriority.Low.getValue());

    // Update task on exchange
    client.updateTask(task);
}
~~~
### **Eliminar tarea**
En el siguiente fragmento de código se muestra cómo eliminar una tarea en un servidor de Exchange.



~~~Java
// Create instance of ExchangeClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get all tasks info collection from exchange
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Parse all the tasks info in the list
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Fetch task from exchange using current task info
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Check if the current task fulfills the search criteria
    if (task.getSubject().equals("test")) {
        // Delete task from exchange
        client.deleteItem(task.getUniqueUri(), DeletionOptions.getDeletePermanently());
    }
}
~~~
### **Envío de solicitud de tarea**
El servicio Aspose.Email Exchange ofrece la capacidad de enviar solicitudes de tareas similares a las de Outlook. El siguiente fragmento de código muestra cómo cargar un mensaje de solicitud de tarea desde el disco y enviarlo mediante el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



~~~Java
// Create instance of ExchangeClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveTnefAttachments(true);

// load task from .msg file
MailMessage eml = MailMessage.load(dataDir + "task.msg", options);
eml.setFrom(MailAddress.to_MailAddress("firstname.lastname@domain.com"));
eml.getTo().clear();
eml.getTo().addMailAddress(new MailAddress("firstname.lastname@domain.com"));
client.send(eml);
~~~
### **Guardar la tarea en un disco**
Aspose.Email también permite guardar las tareas de Exchange en un disco en formato Outlook MSG. El siguiente fragmento de código muestra cómo guardar una tarea en un disco.



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
### **Listado de tareas de Exchange Server**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) proporciona la [listTasks](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listTasks\(\)) método que se puede usar para obtener tareas de un servicio web de Exchange. Tiene varias sobrecargas que se pueden utilizar para recuperar la lista de tareas de una carpeta específica o mediante algunos criterios de búsqueda. El siguiente ejemplo de código muestra cómo obtener todas las tareas o algunas de ellas de la carpeta Tareas.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Listing Tasks from Server
client.setTimezoneId("Central Europe Standard Time");
TaskCollection taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri());

// print retrieved tasks' details
int iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}

// Listing Tasks from server based on Query - Completed and In-Progress
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };
ExchangeQueryBuilder queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
MailQuery query = queryBuilder.getQuery();

taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri(), query);

// print retrieved tasks' details
iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}
~~~
### **Filtrado de tareas desde Exchange Server**
Aspose.Email ofrece la capacidad de recuperar tareas específicas del servidor en lugar de recuperar todas las tareas del servidor. La API se puede usar para recuperar las tareas según el estado de la tarea, como Completada, Aplazada, En curso, No iniciada o Esperando a otras. El [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder) la clase se puede usar para especificar el criterio deseado utilizando la propiedad Status. También permite especificar varias condiciones para recuperar las tareas deseadas de Exchange Server. Esto se demuestra en el siguiente ejemplo de código.


~~~Java
// Create instance of ExchangeClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Set timezone for tasks
client.setTimezoneId("Central Europe Standard Time");

// We use these status values for specifying in queries
Integer[] values = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.Deferred, ExchangeTaskStatus.InProgress, ExchangeTaskStatus.NotStarted,
        ExchangeTaskStatus.WaitingOnOthers };

messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri());

// Now retrieve the tasks with specific statuses
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().equals(status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
    fetchedTask = client.fetchTask(messageInfoCol.get_Item(0).getUniqueUri());
}

// retrieve all other than specified
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().notEquals((int) status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
}

// specifying multiple criterion
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };

queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);

// list all those which are not in our specified statuses
queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().notIn(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
~~~