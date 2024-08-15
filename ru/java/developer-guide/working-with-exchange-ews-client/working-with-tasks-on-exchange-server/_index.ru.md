---
title: "Работа с задачами на сервере Exchange"
url: /ru/java/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---


## **Работа с задачами**
Aspose.Email поддерживает обработку задач на Exchange с помощью [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) класс. Различные свойства, проявляемые [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask), как [Subject](https://apireference.aspose.com/email/java/com.aspose.email/Task#getSubject\(\)), [Status](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeTask#getStatus\(\)), [DueDate](https://apireference.aspose.com/email/java/com.aspose.email/Task#getDueDate\(\)), и [Priority](https://apireference.aspose.com/email/java/com.aspose.email/Task#getPriority\(\)), можно использовать для настройки задачи в Exchange. [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс предоставляет такие функции, как [createTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createTask\(com.aspose.email.ExchangeTask\)), [updateTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateTask\(com.aspose.email.ExchangeTask\)), and [deleteTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteTask\(java.lang.String\)) которые используются для обработки задач в Exchange. В этой статье показано, как:

- Создайте новую задачу.
- Задайте часовой пояс задачи.
- Обновите задачу.
- Удалить задачу.
- Отправить запрос на задание
- Сохранить задачу на диске
### **Создать новую задачу**
В следующем фрагменте кода показано, как использовать функцию «Создать новую задачу».



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
### **Указание часового пояса**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) интерфейс и [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) укажите свойство timeZoneId для настройки информации о часовом поясе при создании задачи. В следующем фрагменте кода показано, как указать часовой пояс.



~~~Java
client.setTimezoneId("Central Europe Standard Time");
~~~
### **Обновить задачу**
В следующих фрагментах кода показано, как обновить задачу на сервере Exchange.



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
### **Удалить задачу**
В следующем фрагменте кода показано, как удалить задачу на сервере Exchange.



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
### **Отправка запроса на задание**
Сервис Aspose.Email Exchange предоставляет возможность отправлять запросы на выполнение задач аналогично Outlook. В следующем фрагменте кода показано, как загрузить сообщение с запросом на задание с диска и отправить его с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



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
### **Сохранение задачи на диск**
Aspose.Email также позволяет сохранять задачи Exchange на диск в формате Outlook MSG. В следующем фрагменте кода показано, как сохранить задачу на диск.



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
### **Вывод списка задач с сервера Exchange**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) обеспечивает [listTasks](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listTasks\(\)) метод, который можно использовать для получения задач из веб-службы Exchange. Он имеет несколько перегрузок, которые можно использовать для извлечения списка задач из определенной папки или использования некоторых критериев поиска. Приведенный ниже пример кода иллюстрирует получение всех или отдельных задач из папки «Задачи».



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
### **Фильтрация задач с сервера Exchange**
Aspose.Email предоставляет возможность извлекать определенные задачи с сервера вместо получения всех задач с сервера. API можно использовать для поиска задач по статусу задачи, например «Выполнено», «Отложено», «Выполнено», «Не запущено» или «Ожидает выполнения» других задач. [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder) класс можно использовать для указания желаемого критерия с помощью свойства Status. Он также позволяет указать несколько условий для получения желаемых задач с сервера Exchange. Об этом свидетельствует следующий пример кода.


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