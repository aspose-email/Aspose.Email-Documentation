---
title: Working with Tasks on Exchange Server
type: docs
weight: 100
url: /java/working-with-tasks-on-exchange-server/
---


## **Working with Tasks**
Aspose.Email supports processing tasks on Exchange using the [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) class. Different properties exposed by [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask), like [Subject](https://apireference.aspose.com/email/java/com.aspose.email/Task#getSubject\(\)), [Status](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeTask#getStatus\(\)), [DueDate](https://apireference.aspose.com/email/java/com.aspose.email/Task#getDueDate\(\)), and [Priority](https://apireference.aspose.com/email/java/com.aspose.email/Task#getPriority\(\)), can be used to configure the task on Exchange. The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class exposes functions like [createTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createTask\(com.aspose.email.ExchangeTask\)), [updateTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateTask\(com.aspose.email.ExchangeTask\)), and [deleteTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteTask\(java.lang.String\)) which are used to process tasks on Exchange. This article shows how to:

- Create a new task.
- Set a task's timezone.
- Update a task.
- Delete a task.
- Send Task Request
- Save Task to Disc
### **Create New Task**
The following code snippet shows you how to use create a new task.



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
### **Specifying Timezone**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) interface and [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) provide the TimeZoneId property for setting timezone information when creating a task. The following code snippet shows you how to specify Timezone.



~~~Java
client.setTimezoneId("Central Europe Standard Time");
~~~
### **Update Task**
The following code snippets show how to update a task on an Exchange server.



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
### **Delete Task**
The following code snippet shows you how to delete a task on an Exchange server.



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
### **Sending Task Request**
Aspose.Email Exchange service provides the capability to send task requests similar to Outlook. The following code snippet shows you how to load a task request message from the disc and send it using the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



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
### **Saving Task to Disc**
Aspose.Email also allows saving Exchange Tasks to disc in Outlook MSG format. The following code snippet shows you how to save a task to disc.



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
### **Listing Tasks from Exchange Server**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) provides the [listTasks](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listTasks\(\)) method that can be used to fetch tasks from an Exchange Web Service. It has several overloads that can be used to retrieve the list of tasks from a specific folder or using some search criteria. The below code sample illustrates getting all or specific tasks from the Tasks folder.



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
### **Filtering Tasks from Exchange Server**
Aspose.Email provides the capability to retrieve specific tasks from the server instead of retrieving all tasks from the server. The API can be used to retrieve tasks by task's status such as Completed, Deferred, In Progress, Not started or Waiting on others. The [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder) class can be used to specify the desired criterion utilizing the Status property. It also allows specifying multiple conditions for retrieving desired tasks from Exchange Server. This is demonstrated by the following code sample.


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