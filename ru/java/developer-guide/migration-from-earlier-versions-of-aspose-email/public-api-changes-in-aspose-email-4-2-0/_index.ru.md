---
title: "Изменения в публичном API Aspose.Email 4.2.0"
url: /ru/java/public-api-changes-in-aspose-email-4-2-0/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

Следующий список содержит изменения, внесенные в публичный API, такие как [добавленные](/email/java/public-api-changes-in-aspose-email-4-2-0/), переименованные, удаленные или [устаревшие](/email/java/public-api-changes-in-aspose-email-4-2-0/) элементы, а также любые изменения, не совместимые с предыдущими версиями, внесенные в Aspose.Email для Java. Если у вас есть опасения по поводу какого-либо из перечисленных изменений, пожалуйста, обсудите это на форуме поддержки Aspose.Email.
## **Добавленные методы**
**`FollowUpOptions.getCategories()` и `FollowUpOptions.setCategories()` Методы**
Получает или устанавливает строку, представляющую список категорий, разделенных точками с запятой.

**`FollowUpOptions.getVotingButtons()` и `FollowUpOptions.setVotingButtons()` Методы**
Получает или устанавливает строку, представляющую список имен кнопок голосования, разделенных точками с запятой.

**`FollowUpManager.setOptions(MapiMessage message, FollowUpOptions options)` и `FollowUpManager.getOptions(MapiMessage message)` Методы**
Получает и устанавливает дополнительные параметры последующего действия для сообщения.

Существующие методы `FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` и `FollowUpManager.getFlag(MapiMessage message)` помечены как [устаревшие](/email/java/public-api-changes-in-aspose-email-4-2-0/).
Пожалуйста, используйте методы `getOptions(MapiMessage message)` и `setOptions(MapiMessage message, FollowUpOptions options)` вместо них.

- **`FollowUpManager.addVotingButton(MapiMessage message, String displayName)` Метод**
Добавляет кнопку голосования в MapiMessage.
- **`FollowUpManager.removeVotingButton(MapiMessage message, String displayName)` Метод**
Удаляет указанную кнопку голосования из MapiMessage.
- **`FollowUpManager.clearVotingButtons(MapiMessage message)` Метод**
Удаляет кнопки голосования из MapiMessage.
- **`FollowUpManager.getVotingButtons(MapiMessage message)` Метод**
Получает доступные кнопки голосования для сообщения.
- **`MapiTask.getAttachments` и `MapiTask.setAttachments` Методы**
Получает коллекцию `MapiAttachments` в `MapiTask`.
## **Устаревшие методы**
**`FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` и `FollowUpManager.getFlag(MapiMessage message)`**
Пожалуйста, используйте методы getOptions(`MapiMessage` message) и `setOptions(MapiMessage message, FollowUpOptions options)` вместо них, [как указано выше](/email/java/public-api-changes-in-aspose-email-4-2-0/).

{{% /alert %}}