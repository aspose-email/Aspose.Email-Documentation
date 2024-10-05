---
title: "Изменения в публичном API Aspose.Email 5.0.0"
url: /ru/java/public-api-changes-in-aspose-email-5-0-0/
weight: 110
type: docs
---

Следующий список содержит любые изменения, внесенные в публичный API, такие как добавление, переименование, удаление или устаревшие члены, а также любые изменения, несовместимые с предыдущими версиями, внесенные в Aspose.Email для Java. Если у вас есть замечания по любому из перечисленных изменений, пожалуйста, поднимите этот вопрос на форуме поддержки Aspose.Email.

- Enum `ReminderAction.None`

- Класс `MessageStore`

- Свойство `PersonalStorage.getStore()`

- Свойство `PersonalStorage.getStore().getDisplayName()`
- Свойство `PersonalStorage.getStore().getProperties()`

- Метод `PersonalStorage.getStore().changeDisplayName(String)`
- Метод `PersonalStorage.getStore().setProperty(MapiProperty)`

**Устаревшие**

- Свойство `PersonalStorage.getDisplayName()` - Пожалуйста, используйте `PersonalStorage.getStore().getDisplayName()` вместо
- Свойство `PersonalStorage.getMessageStoreProperties()` - Пожалуйста, используйте `PersonalStorage.getStore().getProperties()` вместо
- Метод `PersonalStorage.changeDisplayName(String newName)` - Пожалуйста, используйте метод `PersonalStorage.getStore().changeDisplayName()` вместо