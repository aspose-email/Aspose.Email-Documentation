---
title: "Cambios en la API pública en Aspose.Email 4.2.0"
url: /es/java/public-api-changes-in-aspose-email-4-2-0/
weight: 40
type: docs
---

{{% alert color="primary" %}}

La siguiente es una lista de los cambios realizados en la API pública, como [added](/email/java/public-api-changes-in-aspose-email-4-2-0/), renombrado, eliminado o [deprecated](/email/java/public-api-changes-in-aspose-email-4-2-0/) miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tiene dudas sobre algún cambio de la lista, hágalo saber en el foro de soporte de Aspose.Email.
## **Métodos añadidos**
**`FollowUpOptions.getCategories()` and `FollowUpOptions.setCategories()` Methods**
Obtiene o establece una cadena que representa una lista de las categorías, separadas por punto y coma.

**`FollowUpOptions.getVotingButtons()` and `FollowUpOptions.setVotingButtons()` Methods**
Obtiene o establece una cadena que representa una lista de los nombres de los botones de votación, separados por punto y coma.

**`FollowUpManager.setOptions(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getOptions(MapiMessage message)` Methods**
Obtiene y establece las opciones de seguimiento adicionales de un mensaje.

Los métodos existentes `FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getFlag(MapiMessage message)` marcado como [deprecated](/email/java/public-api-changes-in-aspose-email-4-2-0/).
Por favor, utilice el `getOptions(MapiMessage message)` and `setOptions(MapiMessage message, FollowUpOptions options)` métodos en su lugar.

- **`FollowUpManager.addVotingButton(MapiMessage message, String displayName)` Method**
Añade un botón de votación a un MapiMessage.
- **`FollowUpManager.removeVotingButton(MapiMessage message, String displayName)` Method**
Elimina un botón de votación especificado de un MapiMessage.
- **`FollowUpManager.clearVotingButtons(MapiMessage message)` Method**
Elimina los botones de votación de un MAPIMessage.
- **`FollowUpManager.getVotingButtons(MapiMessage message)` Method**
Obtenga los botones de votación de mensajes disponibles.
- **`MapiTask.getAttachments` and `MapiTask.setAttachments` Methods**
Consigue la colección de `MapiAttachments` en un `MapiTask`.
## **Métodos obsoletos**
**`FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` and `FollowUpManager.getFlag(MapiMessage message)`**
Utilice getOptions (`MapiMessage` mensaje) y `setOptions(MapiMessage message, FollowUpOptions options)` métodos en lugar de eso, [como se mencionó anteriormente](/email/java/public-api-changes-in-aspose-email-4-2-0/).

{{% /alert %}}
