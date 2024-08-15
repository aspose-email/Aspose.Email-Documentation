---
title: "Cambios en la API pública en Aspose.Email 5.8.0"
url: /es/java/public-api-changes-in-aspose-email-5-8-0/
weight: 190
type: docs
---

La siguiente es una lista de todos los cambios realizados en la API pública, como la adición, el cambio de nombre, la eliminación o la desaprobación de miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email for.NET. Si tienes dudas sobre algún cambio de la lista, comunícalo en el foro de soporte de Aspose.Email.
## **API añadidas**
- Class `TnefLoadOptions`
- Method `IEWSClient.listMessages(String, ExchangeMessageInfoCollection, Integer, Integer)`
- Method `IEWSClient.listMessages(String, Integer)`
- Method `IEWSClient.listMessages(String, Integer, Integer)`
- Method `IEWSClient.listSubFolders(String, ExchangeFolderInfoCollection, Integer, Integer)`
- Method `IEWSClient.listSubFolders(String, Integer)`
- Method `IEWSClient.listSubFolders(String, Integer, Integer)`
- Property `ExchangeFolderInfoCollection.getLastItemOffset, setLastItemOffset`
- Property `ExchangeFolderInfoCollection.getLastPage, setLastPage`
- Property `ExchangeFolderInfoCollection.getTotalCount, setTotalCount`
- Property `ExchangeMessageInfoCollection.getLastItemOffset, setLastItemOffset`
- Property `ExchangeMessageInfoCollection.getLastPage, setLastPage`
- Property `ExchangeMessageInfoCollection.getTotalCount, setTotalCount`
- Property `IEWSClient.getEnableDecompression, setEnableDecompression(boolean)`
- Property `MessageFormat.getTnef`
## **API eliminadas**
- Method `LoadOptions.#ctor(MessageFormat)`
