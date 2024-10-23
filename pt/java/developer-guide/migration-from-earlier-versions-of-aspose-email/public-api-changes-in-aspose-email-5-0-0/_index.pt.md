---
title: "Mudanças na API Pública no Aspose.Email 5.0.0"
url: /pt/java/public-api-changes-in-aspose-email-5-0-0/
weight: 110
type: docs
---

A seguir está uma lista de quaisquer alterações feitas na API pública, como membros adicionados, renomeados, removidos ou depreciados, bem como qualquer alteração não compatível com versões anteriores feita no Aspose.Email para Java. Se você tiver preocupações sobre alguma mudança listada, por favor, apresente-a no fórum de suporte do Aspose.Email.

- Enum `ReminderAction.None`

- Classe `MessageStore`

- Propriedade `PersonalStorage.getStore()`

- Propriedade `PersonalStorage.getStore().getDisplayName()`
- Propriedade `PersonalStorage.getStore().getProperties()`

- Método `PersonalStorage.getStore().changeDisplayName(String)`
- Método `PersonalStorage.getStore().setProperty(MapiProperty)`

**Depreciado**

- Propriedade `PersonalStorage.getDisplayName()` - Por favor, use `PersonalStorage.getStore().getDisplayName()` em vez disso
- Propriedade `PersonalStorage.getMessageStoreProperties()` - Por favor, use `PersonalStorage.getStore().getProperties()` em vez disso
- Método `PersonalStorage.changeDisplayName(String newName)` - Por favor, use o método `PersonalStorage.getStore().changeDisplayName()` em vez disso