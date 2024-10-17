---
title: "Cambios en la API Pública en Aspose.Email 5.0.0"
url: /es/java/public-api-changes-in-aspose-email-5-0-0/
weight: 110
type: docs
---

A continuación se presenta una lista de los cambios realizados en la API pública, como miembros añadidos, renombrados, eliminados o en desuso, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para Java. Si tiene preocupaciones sobre algún cambio listado, por favor, mándelo al foro de soporte de Aspose.Email.

- Enum `ReminderAction.None`

- Clase `MessageStore`

- Propiedad `PersonalStorage.getStore()`

- Propiedad `PersonalStorage.getStore().getDisplayName()`
- Propiedad `PersonalStorage.getStore().getProperties()`

- Método `PersonalStorage.getStore().changeDisplayName(String)`
- Método `PersonalStorage.getStore().setProperty(MapiProperty)`

**En desuso**

- Propiedad `PersonalStorage.getDisplayName()` - Por favor, use `PersonalStorage.getStore().getDisplayName()` en su lugar
- Propiedad `PersonalStorage.getMessageStoreProperties()` - Por favor, use `PersonalStorage.getStore().getProperties()` en su lugar
- Método `PersonalStorage.changeDisplayName(String newName)` - Por favor, use el método `PersonalStorage.getStore().changeDisplayName()` en su lugar