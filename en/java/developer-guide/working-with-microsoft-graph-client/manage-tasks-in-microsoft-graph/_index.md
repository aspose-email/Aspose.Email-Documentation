---
title: Manage Tasks in Microsoft Graph with Aspose.Email for Java
ArticleTitle: Manage Tasks in Microsoft Graph
type: docs
weight: 20
url: /java/manage-tasks-in-microsoft-graph/
---

Refer to [Azure AD Setup and Microsoft Graph Authentication](https://docs.aspose.com/email/java/microsoft-graph-authentication/) article to learn how to integrate your application with Microsoft Graph. 


**Aspose.Email for Java** provides support for managing tasks through Microsoft Graph. You can enumerate task lists, create or delete them, and manage tasks with flexible update options.

The code sample below demonstrates how to manage task lists and tasks using the following methods of the [GraphClient](https://reference.aspose.com/email/java/com.aspose.email/graphclient/) class:

- `listTaskLists()` — Retrieves all task lists.
- `getTaskList(String id)` — Retrieves a specific task list.
- `deleteTaskList(String id)` — Deletes a task list.
- `listTasks(String id)` — Retrieves tasks for a given task list.
- `fetchTask(String id)` — Retrieves a task by its ID.
- `createTask(MapiTask task, String taskListUri)` — Creates a task in a specific task list.
- `updateTask(MapiTask task)` — Updates an existing task.
- `updateTask(MapiTask task, UpdateSettings updateSettings)` — Updates a task with specific update settings.

```java
// List Task Lists
GraphTaskListInfoCollection taskLists = graphClient.listTaskLists();
for (GraphTaskListInfo tList : taskLists) {
    System.out.println("Task List: " + tList.getDisplayName());
}

// Get Task List
GraphTaskListInfo taskList = graphClient.getTaskList("taskListId");

// Delete Task List
graphClient.deleteTaskList("taskListId");

// List Tasks in a Task List
MapiTaskCollection tasks = graphClient.listTasks("taskListId");

// Fetch Task
MapiTask task = graphClient.fetchTask("taskId");

// Create Task
MapiTask newTask = new MapiTask();
newTask.setSubject("New Task");
newTask.setDueDate(new Date());
newTask.setStatus(MapiTaskStatus.NotStarted);

MapiTask createdTask = graphClient.createTask(newTask, "taskListUri");

// Update Task
createdTask.setSubject("Updated Task Subject");
MapiTask updatedTask = graphClient.updateTask(createdTask);

// Update Task with UpdateSettings
UpdateSettings updateSettings = new UpdateSettings();
updateSettings.setSkipAttachments(true);
MapiTask updatedTaskWithSettings = graphClient.updateTask(createdTask, updateSettings);
```