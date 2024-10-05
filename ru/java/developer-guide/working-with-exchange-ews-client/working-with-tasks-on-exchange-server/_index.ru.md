---
title: "Работа с задачами на Exchange Server"
url: /ru/java/working-with-tasks-on-exchange-server/
weight: 100
type: docs
---


## **Работа с задачами**
Aspose.Email поддерживает обработку задач на Exchange с помощью класса [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask). Разные свойства, предоставляемые [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask), такие как [Subject](https://apireference.aspose.com/email/java/com.aspose.email/Task#getSubject\(\)), [Status](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeTask#getStatus\(\)), [DueDate](https://apireference.aspose.com/email/java/com.aspose.email/Task#getDueDate\(\)) и [Priority](https://apireference.aspose.com/email/java/com.aspose.email/Task#getPriority\(\)), могут использоваться для настройки задачи на Exchange. Класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) предоставляет функции, такие как [createTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createTask\(com.aspose.email.ExchangeTask\)), [updateTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateTask\(com.aspose.email.ExchangeTask\)), и [deleteTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteTask\(java.lang.String\)), которые используются для обработки задач на Exchange. Эта статья показывает, как:

- Создать новую задачу.
- Установить часовой пояс задачи.
- Обновить задачу.
- Удалить задачу.
- Отправить запрос на задачу.
- Сохранить задачу на диск.
### **Создание новой задачи**
Приведенный ниже фрагмент кода показывает, как создать новую задачу.



~~~Java
// Создание экземпляра класса EWSClient с указанием учетных данных
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Создание объекта задачи Exchange
ExchangeTask task = new ExchangeTask();

// Установка темы и статуса задачи в "В процессе"
task.setSubject("New-Test");
task.setStatus(ExchangeTaskStatus.InProgress);
client.createTask(client.getMailboxInfo().getTasksUri(), task);
~~~
### **Указание часового пояса**
Интерфейс [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) и [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) предоставляют свойство TimeZoneId для установки информации о часовом поясе при создании задачи. Приведенный ниже фрагмент кода показывает, как указать часовой пояс.



~~~Java
client.setTimezoneId("Central Europe Standard Time");
~~~
### **Обновление задачи**
Приведенные ниже фрагменты кода показывают, как обновить задачу на сервере Exchange.



~~~Java
// Создание экземпляра класса ExchangeClient с указанием учетных данных
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получение информации обо всех задачах из Exchange
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Обработка информации обо всех задачах из списка
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Получение задачи из Exchange с использованием текущей информации о задаче
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Обновление статуса задачи на Не начато
    task.setStatus(ExchangeTaskStatus.NotStarted);

    // Установка срока выполнения задачи
    SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
    task.setDueDate(sdf.parse("26/02/2013 00:00:00"));

    // Установка приоритета задачи
    task.setPriority(MailPriority.Low.getValue());

    // Обновление задачи на Exchange
    client.updateTask(task);
}
~~~
### **Удаление задачи**
Приведенный ниже фрагмент кода показывает, как удалить задачу на сервере Exchange.



~~~Java
// Создание экземпляра класса ExchangeClient с указанием учетных данных
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получение информации обо всех задачах из Exchange
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Обработка информации обо всех задачах из списка
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Получение задачи из Exchange с использованием текущей информации о задаче
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Проверка, выполняет ли текущая задача критерии поиска
    if (task.getSubject().equals("test")) {
        // Удаление задачи из Exchange
        client.deleteItem(task.getUniqueUri(), DeletionOptions.getDeletePermanently());
    }
}
~~~
### **Отправка запроса на задачу**
Служба Exchange Aspose.Email предоставляет возможность отправки запросов на задачи, аналогично Outlook. Приведенный ниже фрагмент кода показывает, как загрузить сообщение запроса на задачу с диска и отправить его с использованием [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



~~~Java
// Создание экземпляра класса ExchangeClient с указанием учетных данных
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveTnefAttachments(true);

// Загрузка задачи из .msg файла
MailMessage eml = MailMessage.load(dataDir + "task.msg", options);
eml.setFrom(MailAddress.to_MailAddress("firstname.lastname@domain.com"));
eml.getTo().clear();
eml.getTo().addMailAddress(new MailAddress("firstname.lastname@domain.com"));
client.send(eml);
~~~
### **Сохранение задачи на диск**
Aspose.Email также позволяет сохранять задачи Exchange на диск в формате Outlook MSG. Приведенный ниже фрагмент кода показывает, как сохранить задачу на диск.



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
### **Список задач с сервера Exchange**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) предоставляет метод [listTasks](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listTasks\(\)), который можно использовать для получения задач из веб-сервиса Exchange. У него есть несколько перегрузок, которые можно использовать для получения списка задач из конкретной папки или с использованием некоторых критериев поиска. Пример кода ниже иллюстрирует получение всех или конкретных задач из папки задач.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Список задач с сервера
client.setTimezoneId("Central Europe Standard Time");
TaskCollection taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri());

// Печать деталей полученных задач
int iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}

// Список задач с сервера на основе запроса - Завершено и В процессе
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };
ExchangeQueryBuilder queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
MailQuery query = queryBuilder.getQuery();

taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri(), query);

// Печать деталей полученных задач
iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}
~~~
### **Фильтрация задач с сервера Exchange**
Aspose.Email предоставляет возможность извлекать определенные задачи с сервера, вместо того чтобы получать все задачи с сервера. API можно использовать для получения задач по статусу, таким как Завершено, Отложено, В процессе, Не начато или Ожидание других. Класс [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder) можно использовать для указания желаемого критерия с использованием свойства Status. Он также позволяет указывать несколько условий для извлечения нужных задач с сервера Exchange. Это продемонстрировано следующему примеру кода.


~~~Java
// Создание экземпляра класса ExchangeClient с указанием учетных данных
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Установка часового пояса для задач
client.setTimezoneId("Central Europe Standard Time");

// Мы используем эти значения статуса для указания в запросах
Integer[] values = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.Deferred, ExchangeTaskStatus.InProgress, ExchangeTaskStatus.NotStarted,
        ExchangeTaskStatus.WaitingOnOthers };

messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri());

// Теперь извлекаем задачи с указанными статусами
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().equals(status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
    fetchedTask = client.fetchTask(messageInfoCol.get_Item(0).getUniqueUri());
}

// извлечение всех, кроме указанных
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().notEquals((int) status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
}

// указание нескольких критериев
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };

queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);

// список всех тех, которые не соответствуют нашим указанным статусам
queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().notIn(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
~~~