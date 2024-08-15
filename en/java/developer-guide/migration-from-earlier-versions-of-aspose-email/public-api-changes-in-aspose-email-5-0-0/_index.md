---
title: Public API Changes in Aspose.Email 5.0.0
type: docs
weight: 110
url: /java/public-api-changes-in-aspose-email-5-0-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for Java. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.

- Enum `ReminderAction.None`

- Class `MessageStore`

- Property `PersonalStorage.getStore()`

- Property `PersonalStorage.getStore().getDisplayName()`
- Property `PersonalStorage.getStore().getProperties()`

- Method `PersonalStorage.getStore().changeDisplayName(String)`
- Method `PersonalStorage.getStore().setProperty(MapiProperty)`

**Deprecated**

- Property `PersonalStorage.getDisplayName()` - Please use `PersonalStorage.getStore().getDisplayName()` instead
- Property `PersonalStorage.getMessageStoreProperties()` - Please use `PersonalStorage.getStore().getProperties()` instead
- Method `PersonalStorage.changeDisplayName(String newName)` - Please use `PersonalStorage.getStore().changeDisplayName()` method instead
