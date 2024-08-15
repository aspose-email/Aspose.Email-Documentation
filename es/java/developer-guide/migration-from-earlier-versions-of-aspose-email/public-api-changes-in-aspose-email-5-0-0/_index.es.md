---
title: "Cambios en la API pública en Aspose.Email 5.0.0"
url: /es/java/public-api-changes-in-aspose-email-5-0-0/
weight: 110
type: docs
---

La siguiente es una lista de todos los cambios realizados en la API pública, como la adición, el cambio de nombre, la eliminación o la desaprobación de miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tienes dudas sobre algún cambio de la lista, comunícalo en el foro de soporte de Aspose.Email.

- Enum `ReminderAction.None`

- Class `MessageStore`

- Property `PersonalStorage.getStore()`

- Property `PersonalStorage.getStore().getDisplayName()`
- Property `PersonalStorage.getStore().getProperties()`

- Method `PersonalStorage.getStore().changeDisplayName(String)`
- Method `PersonalStorage.getStore().setProperty(MapiProperty)`

**Deprecated**

- Property `PersonalStorage.getDisplayName()` - Utilice por favor `PersonalStorage.getStore().getDisplayName()` instead
- Property `PersonalStorage.getMessageStoreProperties()` - Utilice por favor `PersonalStorage.getStore().getProperties()` instead
- Method `PersonalStorage.changeDisplayName(String newName)` - Utilice por favor `PersonalStorage.getStore().changeDisplayName()` método en su lugar
