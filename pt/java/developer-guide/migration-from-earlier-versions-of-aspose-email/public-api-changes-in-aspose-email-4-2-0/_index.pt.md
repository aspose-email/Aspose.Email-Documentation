---
title: "Mudanças na API Pública no Aspose.Email 4.2.0"
url: /pt/java/public-api-changes-in-aspose-email-4-2-0/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

A seguir está uma lista de quaisquer mudanças feitas na API pública, como membros [adicionados](/email/java/public-api-changes-in-aspose-email-4-2-0/), renomeados, removidos ou [deprecados](/email/java/public-api-changes-in-aspose-email-4-2-0/), bem como qualquer alteração não compatível com versões anteriores feita no Aspose.Email para Java. Se você tiver preocupações sobre qualquer mudança listada, por favor, levante-a no fórum de suporte do Aspose.Email.
## **Métodos Adicionados**
**`FollowUpOptions.getCategories()` e `FollowUpOptions.setCategories()` Métodos**
Obtém ou define uma string que representa uma lista de categorias, separadas por ponto e vírgula.

**`FollowUpOptions.getVotingButtons()` e `FollowUpOptions.setVotingButtons()` Métodos**
Obtém ou define uma string que representa uma lista dos nomes dos botões de votação, separados por ponto e vírgula.

**`FollowUpManager.setOptions(MapiMessage message, FollowUpOptions options)` e `FollowUpManager.getOptions(MapiMessage message)` Métodos**
Obtém e define as opções adicionais de acompanhamento para uma mensagem. 

Os métodos existentes `FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` e `FollowUpManager.getFlag(MapiMessage message)` estão marcados como [deprecados](/email/java/public-api-changes-in-aspose-email-4-2-0/).
Por favor, use os métodos `getOptions(MapiMessage message)` e `setOptions(MapiMessage message, FollowUpOptions options)` em seu lugar.

- **`FollowUpManager.addVotingButton(MapiMessage message, String displayName)` Método**
Adiciona um botão de votação a um MapiMessage.
- **`FollowUpManager.removeVotingButton(MapiMessage message, String displayName)` Método**
Remove um botão de votação específico de um MapiMessage.
- **`FollowUpManager.clearVotingButtons(MapiMessage message)` Método**
Remove botões de votação de um MapiMessage.
- **`FollowUpManager.getVotingButtons(MapiMessage message)` Método**
Obtém os botões de votação disponíveis para a mensagem.
- **`MapiTask.getAttachments` e `MapiTask.setAttachments` Métodos**
Obtém a coleção de `MapiAttachments` em um `MapiTask`.
## **Métodos Deprecados**
**`FollowUpManager.setFlag(MapiMessage message, FollowUpOptions options)` e `FollowUpManager.getFlag(MapiMessage message)`**
Por favor, use os métodos `getOptions(MapiMessage message)` e `setOptions(MapiMessage message, FollowUpOptions options)` em seu lugar, [como mencionado acima](/email/java/public-api-changes-in-aspose-email-4-2-0/).

{{% /alert %}}