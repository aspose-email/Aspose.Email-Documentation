---
title: Mailbox Management with Microsoft Graph
ArticleTitle: Mailbox Management with Microsoft Graph
type: docs
weight: 20
url: /java/mailbox-management-with-microsoft-graph/
---


In addition to working with messages, folders, and attachments, **Aspose.Email for Java** also allows you to manage mailbox-level features such as categories, focused inbox overrides, and rules. You can also work with multiple mailboxes by switching the resource context. These operations are available through the Graph API integration.


## **How to Work with Outlook Categories**

Categories in Outlook allow you to group and label messages for easier organization. With Aspose.Email, you can create, fetch, update, list, and delete categories programmatically.

~~~Java
String categoryName = "Test Category";
int preset = CategoryPreset.Preset10;

// create a new category
OutlookCategory category = client.createCategory(categoryName, preset);

// fetch a category
OutlookCategory fetchedCategory = client.fetchCategory(category.getId());

// list categories
List<OutlookCategory> categories = client.listCategories();

// update a category
fetchedCategory.setDisplayName("Update Category");
fetchedCategory.setPreset(CategoryPreset.Preset11);
OutlookCategory updatedCategory = client.updateCategory(fetchedCategory);

// delete a category
client.delete(category.getId());
~~~

## **How to Work with Overrides**

Overrides control how messages from certain senders are treated in the Focused Inbox. For example, you can force messages from a specific sender to always appear in the focused view.


~~~Java
int focusedType = ClassificationType.Focused;

// create or update an override for a sender
ClassificationOverride override = client.createOrUpdateOverride(
    new MailAddress("testUser@host.com", "testUser"), focusedType
);

// list overrides
List<ClassificationOverride> list = client.listOverrides();
for (ClassificationOverride item : list)
    System.out.println(item.getSender().getAddress());

// update override classification
ClassificationOverride fetchedOverride = list.get(0);
fetchedOverride.setClassifyAs(ClassificationType.Other);
fetchedOverride.getSender().setDisplayName("testUser_1");
ClassificationOverride updatedOverride = client.createOrUpdateOverride(fetchedOverride);

// reset classification
fetchedOverride.setClassifyAs(ClassificationType.Focused);
updatedOverride = client.updateOverride(fetchedOverride);

// delete override
client.delete(updatedOverride.getId());
~~~


## **How to Work with Outlook Rules**

Mailbox rules allow you to automate actions such as forwarding messages or filtering based on conditions. The Graph API allows creating, fetching, updating, listing, and deleting inbox rules.


~~~Java
// create a new rule
InboxRule rule = new InboxRule();
rule.setDisplayName("Test rule");
rule.setPriority(1);
rule.setEnabled(true);
rule.setConditions(new RulePredicates());
rule.getConditions().containsSenderStrings(new StringCollection());
rule.getConditions().containsSenderStrings().addItem("testUser");

// define actions
rule.setActions(new RuleActions());
rule.getActions().setForwardToRecipients(new MailAddressCollection());
rule.getActions().getForwardToRecipients()
    .addMailAddress(new MailAddress("testUser@host.com", "testUser", true));
rule.getActions().setStopProcessingRules(true);

InboxRule createdRule = client.createRule(rule);

// list rules
List<InboxRule> listedRules = client.listRules();
for (InboxRule item : listedRules)
    System.out.println(item.getDisplayName());

// fetch and update a rule
InboxRule fetchedRule = client.fetchRule(createdRule.getRuleId());
createdRule.setDisplayName("Test rule 1");
createdRule.setEnabled(false);
InboxRule updatedRule = client.updateRule(createdRule);

// delete rule
client.delete(createdRule.getRuleId());
~~~

## **Working with Multiple Mailboxes - Switching Mailbox Context**

By default, operations are performed against the current user’s mailbox. You can switch the context to another mailbox (for example, to list messages from a shared mailbox) by setting the resource type and resource ID.

~~~Java
// switch to another mailbox
client.setResource(ResourceType.Users);
client.setResourceId("mailbox");
client.listMessages("mailfolder");

// switch back to the current user mailbox
client.setResource(ResourceType.Me);
~~~

## **OData Queries with Microsoft Graph**

Aspose.Email for Java provides support for OData queries when working with Microsoft Graph. It allows you to perform advanced filtering, ordering, selection, paging, and expansion when retrieving resources such as folders, messages, contacts, and calendar items. The `ODataQueryBuilder` class allows you to construct OData query parameters in a structured and reusable way instead of manually building query strings. The following methods can be applied for counting and searching across large datasets:

- `Select` to retrieve only the properties you need.
- `Filter` to apply filters.
- `OrderBy` to sort results.
- `Top` and `Skip` for pagination.
- `Expand` to expand related entities in a single query.

Several [GraphClient](https://reference.aspose.com/email/java/com.aspose.email/graphclient/#methods) methods accept an optional `ODataQueryBuilder` parameter for applying OData queries, including:

- listFolders
- listMessages
- listContacts
- listCalendarItems
- listAttachments
- listCategories
- listOverrides
- listRules
- listTaskLists
- listTasks
- listNotebooks


The following code sample shows how to use `ODataQueryBuilder` to query folders and retrieve messages with advanced filters and paging:

```java
IGraphClient client = GraphClient.GetClient();

client.setResource(ResourceType.Users);
client.setResourceId(username);
client.setEndpoint("https://graph.microsoft.com");

// Example 1: List folders ordered by name
ODataQueryBuilder builder = new ODataQueryBuilder();
builder.setOrderBy("name asc");

GraphFolderInfoCollection folders = client.listFolders(builder);
for (GraphFolderInfo folder : folders) {
    System.out.println(folder.getDisplayName());
}

String folderId = folders.get(0).getItemId();

// Example 2: Retrieve filtered and paged messages
builder = new ODataQueryBuilder();
{
    builder.setFilter("startswith(name,'A')");
    builder.setOrderBy("name asc");
    builder.setTop(10);
    builder.setSkip(5);
    builder.setSelect(new String[]{"name", "age"});
    builder.setExpand(new String[]{"children", "parents"});
    builder.setCount(true);
    builder.setSearch("\"John Doe\"");
    builder.setFormat("json");
};

GraphMessageInfoCollection msgs = client.listMessages(folderId, builder);
for (GraphMessageInfo msg : msgs) {
    System.out.println(msg.getSubject());
}
```