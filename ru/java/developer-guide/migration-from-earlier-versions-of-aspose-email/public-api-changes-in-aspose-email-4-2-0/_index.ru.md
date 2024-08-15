---
title: "Изменения в публичном API в Aspose.Email 4.2.0"
url: /ru/java/public-api-changes-in-aspose-email-4-2-0/
weight: 40
type: docs
---

{{% alert color="primary" %}}

Ниже приведен список любых изменений, внесенных в общедоступный API, таких как: [added](/email/java/public-api-changes-in-aspose-email-4-2-0/), переименован, удален или [deprecated](/email/java/public-api-changes-in-aspose-email-4-2-0/) участников, а также любые изменения, не совместимые с обратной совместимостью, внесенные в Aspose.Email для Java. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.
## **Добавленные методы**
**`FollowUpOptions.getCategories()` and `FollowUpOptions.setCategories()` Methods**
Возвращает или задает строку, представляющую список категорий, разделенных точками с запятой.

**`FollowUpOptions.getVotingButtons()` and `FollowUpOptions.setVotingButtons()` Methods**
Возвращает или задает строку, представляющую список имен кнопок голосования, разделенных точкой с запятой.

**`FollowUpManager.setOptions(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getOptions(MapiMessage message)` Methods**
Получает и задает дополнительные параметры отслеживания сообщения.

Существующие методы `FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getFlag(MapiMessage message)` помечено как [deprecated](/email/java/public-api-changes-in-aspose-email-4-2-0/).
Пожалуйста, используйте `getOptions(MapiMessage message)` and `setOptions(MapiMessage message, FollowUpOptions options)` методы вместо этого.

- **`FollowUpManager.addVotingButton(MapiMessage message, String displayName)` Method**
Добавляет кнопку голосования в MapiMessage.
- **`FollowUpManager.removeVotingButton(MapiMessage message, String displayName)` Method**
Удаляет указанную кнопку голосования из MapiMessage.
- **`FollowUpManager.clearVotingButtons(MapiMessage message)` Method**
Удаляет кнопки голосования из MapiMessage.
- **`FollowUpManager.getVotingButtons(MapiMessage message)` Method**
Получите доступные кнопки голосования за сообщения.
- **`MapiTask.getAttachments` and `MapiTask.setAttachments` Methods**
Получите коллекцию `MapiAttachments` в `MapiTask`.
## **Устаревшие методы**
**`FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getFlag(MapiMessage message)`**
Пожалуйста, используйте getOptions (`MapiMessage` сообщение) и `setOptions(MapiMessage message, FollowUpOptions options)` вместо этого методы, [как указано выше](/email/java/public-api-changes-in-aspose-email-4-2-0/).

{{% /alert %}}
