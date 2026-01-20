---
title: Manage Calendar Items in Microsoft Graph
ArticleTitle: Manage Calendar Items in Microsoft Graph
type: docs
weight: 20
url: /java/manage-calendar-items-in-microsoft-graph/
---

Refer to [Azure AD Setup and Microsoft Graph Authentication](https://docs.aspose.com/email/java/microsoft-graph-authentication/) article to learn how to integrate your application with Microsoft Graph. 


**Aspose.Email for Java** provides support for managing calendar items via Microsoft Graph. You can list calendars, work with calendar events, and update items with or without update settings.

The code sample below demonstrates how to manage calendar items using the following methods of the [GraphClient](https://reference.aspose.com/email/java/com.aspose.email/graphclient/) class:

- `listCalendars()` — Retrieves a collection of available calendars.
- `listCalendarItems(String id)` — Retrieves calendar items for a specific calendar.
- `fetchCalendarItem(String id)` — Retrieves a calendar item by its ID.
- `createCalendarItem(String calId, MapiCalendar mapiCalendar)` — Creates a new calendar item.
- `updateCalendarItem(MapiCalendar mapiCalendar)` — Updates an existing calendar item.
- `updateCalendarItem(MapiCalendar mapiCalendar, UpdateSettings updateSettings)` — Updates a calendar item with custom update settings.


```java
// List Calendars
GraphCalendarInfoCollection calendars = graphClient.listCalendars();

// List Calendar Items
MapiCalendarCollection calendarItems = graphClient.listCalendarItems("calendarId");

// Fetch Calendar Item
MapiCalendar calendarItem = graphClient.fetchCalendarItem("calendarItemId");

// Create Calendar Item
MapiCalendar newCalendarItem = new MapiCalendar();
newCalendarItem.setLocation("Conference Room");
newCalendarItem.setSubject("Team Meeting");
newCalendarItem.setBody("Discuss project status and updates.");
newCalendarItem.setStartDate(startDate);
newCalendarItem.setEndDate(endDate);

MapiCalendar createdCalendarItem = graphClient.createCalendarItem("calendarId", newCalendarItem);

// Update Calendar Item
createdCalendarItem.setLocation("Zoom Meeting");
MapiCalendar updatedCalendarItem = graphClient.updateCalendarItem(createdCalendarItem);
```