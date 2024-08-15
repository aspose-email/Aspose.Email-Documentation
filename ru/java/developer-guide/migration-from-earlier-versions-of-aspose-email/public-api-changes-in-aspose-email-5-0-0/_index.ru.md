---
title: "Изменения в публичном API в Aspose.Email 5.0.0"
url: /ru/java/public-api-changes-in-aspose-email-5-0-0/
weight: 110
type: docs
---

Ниже приведен список всех изменений, внесенных в общедоступный API, таких как добавление, переименование, удаление или устаревание членов, а также любых изменений, не совместимых с обратной совместимостью, внесенных в Aspose.Email для Java. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.

- Enum `ReminderAction.None`

- Class `MessageStore`

- Property `PersonalStorage.getStore()`

- Property `PersonalStorage.getStore().getDisplayName()`
- Property `PersonalStorage.getStore().getProperties()`

- Method `PersonalStorage.getStore().changeDisplayName(String)`
- Method `PersonalStorage.getStore().setProperty(MapiProperty)`

**Deprecated**

- Property `PersonalStorage.getDisplayName()` - Пожалуйста, используйте `PersonalStorage.getStore().getDisplayName()` instead
- Property `PersonalStorage.getMessageStoreProperties()` - Пожалуйста, используйте `PersonalStorage.getStore().getProperties()` instead
- Method `PersonalStorage.changeDisplayName(String newName)` - Пожалуйста, используйте `PersonalStorage.getStore().changeDisplayName()` метод вместо
