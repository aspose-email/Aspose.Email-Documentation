---
title: Managing Outlook Items via Aspose.Email Graph Client
ArticleTitle: Managing Outlook Items via Aspose.Email Graph Client
type: docs
weight: 50
url: /net/manage-outlook-items-via-graph-client/
---


## **Manage Calendar Events**

Aspose.Email provides APIs to access, manage, and interact with calendar events. For these purposes, it offers the following methods in the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListCalendars()** - Retrieves a collection of calendar information.
- **ListCalendarItems(string id)** - Retrieves a collection of calendar items associated with the specified calendar ID.
- **FetchCalendarItem(string id)** - Retrieves a specific calendar item based on the provided ID.
- **CreateCalendarItem(string calId, MapiCalendar mapiCalendar)** - Creates a new calendar item in the specified calendar.
- **UpdateCalendarItem(MapiCalendar mapiCalendar)** - Updates an existing calendar item.
- **UpdateCalendarItem(MapiCalendar mapiCalendar, UpdateSettings updateSettings)** - Updates an existing calendar item with specified update settings.

The following code sample demonstrates how to interact with calendar events in a Microsoft Graph API client using the methods provided by Aspose.Email:

```cs

// List Calendars
CalendarInfoCollection calendars = graphClient.ListCalendars();

// List Calendar Items
MapiCalendarCollection calendarItems = graphClient.ListCalendarItems("calendarId");

// Fetch Calendar Item
MapiCalendar calendarItem = graphClient.FetchCalendarItem("calendarItemId");

// Create Calendar Item
MapiCalendar newCalendarItem = new MapiCalendar(
    location: "Conference Room",
    summary: "Team Meeting",
    description: "Discuss project status and updates.",
    startDate: startDate,
    endDate: endDate
);

MapiCalendar createdCalendarItem = graphClient.CreateCalendarItem("calendarId", newCalendarItem);

// Update Calendar Item
createdCalendarItem.Location = "Zoom Meeting";
MapiCalendar updatedCalendarItem = graphClient.UpdateCalendarItem(createdCalendarItem);
```

## **Manage Message Categories**

To manage categories with MS Graph by Aspose.Email for .NET, use the following methods and try the code sample below:

* [CreateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createcategory/#createcategory)
* [FetchCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchcategory/#fetchcategory)
* [ListCategories](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listcategories/#listcategories)
* [UpdateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatecategory/#updatecategory)

```csharp
// create a custom category with Orange color
var category = client.CreateCategory("My custom category", CategoryPreset.Preset1);

// fetch a category
var fetchedCategory = client.FetchCategory(category.Id);

// update category (change color to brown)
fetchedCategory.Preset = CategoryPreset.Preset2;
var updatedCategory = client.UpdateCategory(fetchedCategory);

// list available categories
var categories = client.ListCategories();

foreach (var cat in categories)
{
    Console.WriteLine(cat.DisplayName);
}

// delete a category
client.Delete(fetchedCategory.Id);
```

## **Manage Contacts**

Aspose.Email provides APIs to access, manage, and interact with contact items. For these purposes, it offers the following methods in the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- **ListContacts(string id)** - Retrieves a collection of MAPI contacts associated with the specified folder ID.
- **FetchContact(string id)** - Retrieves a specific contact based on the provided item ID.
- **CreateContact(string folderId, MapiContact contact)** - Creates a new contact in the specified folder.
- **UpdateContact(MapiContact contact)** - Updates an existing contact.

The following code sample demonstrates how to interact with contacts in a Microsoft Graph API client using the methods provided by Aspose.Email:

```cs
// List Contacts
MapiContactCollection contacts = graphClient.ListContacts("contactFolderId");

// Fetch Contact
MapiContact contact = graphClient.FetchContact("contactId");

// Create Contact
MapiContact newContact = new MapiContact("Jane Smith", "jane.smith@example.com", "XYZ Corporation", "777-888-999");

MapiContact createdContact = graphClient.CreateContact("contactFolderId", newContact);

// Update Contact
createdContact.Telephones.PrimaryTelephoneNumber = "888-888-999";

MapiContact updatedContact = graphClient.UpdateContact(createdContact);
```

## **Manage Overrides**

To manage overrides with MS Graph by Aspose.Email for .NET, use the following methods:

* [CreateOrUpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createorupdateoverride/#createorupdateoverride) 
* [ListOverrides](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listoverrides/#listoverrides)
* [UpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updateoverride/#updateoverride)

```csharp
// Create an user's override
var userOverride = client.CreateOrUpdateOverride
    (new MailAddress("JohnBrown@someorg.com", "JohnBrown"), ClassificationType.Focused);

// list the overrides
var overrides = client.ListOverrides();

// update override
userOverride.Sender.DisplayName = "John Brown";
var updatedOverride = client.UpdateOverride(userOverride);

// delete override
client.Delete(updatedOverride.Id);
```

## **Manage Inbox Rules**

To manage rules with MS Graph by Aspose.Email for .NET, use the following methods:

* [CreateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createrule/#createrule)
* [FetchRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchrule/#fetchrule)
* [UpdateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updaterule/#updaterule)
* [ListRules](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listrules/#listrules)

```csharp
// Create a rule
var rule = PrepareRule("user@someorg.com", "User");
var createdRule = client.CreateRule(rule);

// List all rules defined for Inbox
var rules = client.ListRules();

// Fetch a rule
var fetchedRule = client.FetchRule(createdRule.RuleId);

// Update a rule
fetchedRule.DisplayName = "Renamed rule";
fetchedRule.IsEnabled = false;
var updatedRule = client.UpdateRule(createdRule);

// Delete a rule
client.Delete(updatedRule.RuleId);
```

```csharp
InboxRule PrepareRule(string email, string displayName)
{
    var rule = new InboxRule()
    {
        DisplayName = "My rule",
        Priority = 1,
        IsEnabled = true,
        Conditions = new RulePredicates(),
        Actions = new RuleActions()
    };

    rule.Conditions.ContainsSenderStrings = new StringCollection { displayName };
    rule.Actions.ForwardToRecipients = new MailAddressCollection
        { new MailAddress(email, displayName, true) };
    rule.Actions.StopProcessingRules = true;

    return rule;
}
```

## **Manage OneNote Notebooks**

To manage notebooks with MS Graph by Aspose.Email for .NET, use the following methods:

* [CreateNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createnotebook/#createnotebook)
* [CopyNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/copynotebook/#copynotebook)
* [FetchNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchnotebook/#fetchnotebook)
* [ListNotebooks](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listnotebooks/#listnotebooks)

```csharp
// create a OneNote notebook
var newNotebook = new Notebook()
{
    DisplayName = "My Notebook"
};
var createdNotebook = client.CreateNotebook(newNotebook);

// fetch a notebook
var fetchedNotebook = client.FetchNotebook(createdNotebook.Id);

// list the notebooks
var notebooks = client.ListNotebooks();
```

## **Manage Tasks in Microsoft Graph**

Aspose.Email provides developers with APIs to access, manage, and interact with users’ tasks and task lists using the following methods of the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/#igraphclient-interface) interface:

- [ListTaskLists()](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listtasklists/) - Retrieves a collection of task list information.
- [GetTaskList(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/gettasklist/) - Retrieves a specific task list based on the provided ID.
- [DeleteTaskList(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/deletetasklist/) - Deletes the specified task list.
-[ListTasks(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/listtasks/) - Retrieves a collection of tasks associated with the specified task list ID.
- [FetchTask(string id)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/fetchtask/) - Retrieves a specific task based on the provided ID.
- [CreateTask(MapiTask task, string taskListUri)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createtask/) - Creates a new task in the specified task list.
- [UpdateTask(MapiTask task)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatetask/#updatetask) - Updates an existing task with the provided information.
- [UpdateTask(MapiTask task, UpdateSettings updateSettings)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/updatetask/#updatetask_1) - Updates an existing task with specified update settings.

The following code sample demonstrates how to manage task lists:

```cs
// List Task Lists
var taskLists = graphClient.ListTaskLists();

foreach (var tList in taskLists)
{
    Console.WriteLine($"Task List: {tList.DisplayName}");
}

// Get Task List
var taskList = graphClient.GetTaskList("taskListId");

// Delete Task List
graphClient.DeleteTaskList("taskListId");
```

The following code sample demonstrates how to manage tasks:

```cs
// List Tasks in a Task List
MapiTaskCollection tasks = graphClient.ListTasks("taskListId");

// Fetch Task
MapiTask task = graphClient.FetchTask("taskId");

// Create Task
var newTask = new MapiTask
{
    Subject = "New Task",
    DueDate = new DateTime(2023, 12, 31),
    Status = MapiTaskStatus.NotStarted
};

MapiTask createdTask = graphClient.CreateTask(newTask, "taskListUri");

// Update Task
createdTask.Subject = "Updated Task Subject";
MapiTask updatedTask = graphClient.UpdateTask(createdTask);

// Update Task with UpdateSettings
var updateSettings = new UpdateSettings { SkipAttachments  = true };
MapiTask updatedTaskWithSettings = graphClient.UpdateTask(createdTask, updateSettings);
```
