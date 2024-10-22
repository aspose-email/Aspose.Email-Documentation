---
title: "Cambios en la API pública en Aspose.Email 4.2.0"
url: /es/java/cambios-en-la-api-publica-en-aspose-email-4-2-0/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

La siguiente es una lista de cualquier cambio realizado en la API pública, como miembros [agregados](/email/java/cambios-en-la-api-publica-en-aspose-email-4-2-0/), renombrados, eliminados o [desfasados](/email/java/cambios-en-la-api-publica-en-aspose-email-4-2-0/), así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tiene preocupaciones sobre algún cambio listado, por favor, infórmelo en el foro de soporte de Aspose.Email.
## **Métodos Agregados**
**`FollowUpOptions.getCategories()` y `FollowUpOptions.setCategories()` Métodos**
Obtiene o establece una cadena que representa una lista de las categorías, separadas por punto y coma.

**`FollowUpOptions.getVotingButtons()` y `FollowUpOptions.setVotingButtons()` Métodos**
Obtiene o establece una cadena que representa una lista de los nombres de los botones de votación, separados por punto y coma.

**`FollowUpManager.setOptions(MapiMessage message, FollowUpOptions options)` y `FollowUpManager.getOptions(MapiMessage message)` Métodos**
Obtiene y establece las opciones adicionales de seguimiento para un mensaje.

Los métodos existentes `FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` y `FollowUpManager.getFlag(MapiMessage message)` están marcados como [desfasados](/email/java/cambios-en-la-api-publica-en-aspose-email-4-2-0/).
Por favor, use los métodos `getOptions(MapiMessage message)` y `setOptions(MapiMessage message, FollowUpOptions options)` en su lugar.

- **`FollowUpManager.addVotingButton(MapiMessage message, String displayName)` Método**
Añade un botón de votación en un MapiMessage.
- **`FollowUpManager.removeVotingButton(MapiMessage message, String displayName)` Método**
Elimina un botón de votación específico de un MapiMessage.
- **`FollowUpManager.clearVotingButtons(MapiMessage message)` Método**
Elimina los botones de votación de un MapiMessage.
- **`FollowUpManager.getVotingButtons(MapiMessage message)` Método**
Obtiene los botones de votación disponibles para el mensaje.
- **`MapiTask.getAttachments` y `MapiTask.setAttachments` Métodos**
Obtiene la colección de `MapiAttachments` en un `MapiTask`.
## **Métodos Desfasados**
**`FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` y `FollowUpManager.getFlag(MapiMessage message)`**
Por favor, use los métodos getOptions(`MapiMessage` message) y `setOptions(MapiMessage message, FollowUpOptions options)` en su lugar, [como se mencionó anteriormente](/email/java/cambios-en-la-api-publica-en-aspose-email-4-2-0/).

{{% /alert %}}