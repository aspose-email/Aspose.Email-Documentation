---
title: Manage Contacts in Microsoft Graph with Aspose.Email for Java
ArticleTitle: Manage Contacts in Microsoft Graph
type: docs
weight: 20
url: /java/manage-contacts-in-microsoft-graph/
---

Refer to [Azure AD Setup and Microsoft Graph Authentication](https://docs.aspose.com/email/java/microsoft-graph-authentication/) article to learn how to integrate your application with Microsoft Graph. 


**Aspose.Email for Java** provides support for managing contacts through Microsoft Graph. You can list, fetch, create, and update contacts directly from contact folders.

The code sample below demonstrates how to manage contact items using the following methods of the library:

- `listContacts(String id)` — Retrieves a collection of contacts from the specified folder.
- `fetchContact(String id)` — Retrieves a contact by its ID.
- `createContact(String folderId, MapiContact contact)` — Creates a new contact in a folder.
- `updateContact(MapiContact contact)` — Updates an existing contact.


```java
IGraphClient graphClient = null;

// List Contacts
MapiContactCollection contacts = graphClient.listContacts("contactFolderId");

// Fetch Contact
MapiContact contact = graphClient.fetchContact("contactId");

// Create Contact
MapiContact newContact = new MapiContact("Jane Smith", "jane.smith@example.com", "XYZ Corporation", "777-888-999");
MapiContact createdContact = graphClient.createContact("contactFolderId", newContact);

// Update Contact
createdContact.getTelephones().setPrimaryTelephoneNumber("888-888-999");
MapiContact updatedContact = graphClient.updateContact(createdContact);
```