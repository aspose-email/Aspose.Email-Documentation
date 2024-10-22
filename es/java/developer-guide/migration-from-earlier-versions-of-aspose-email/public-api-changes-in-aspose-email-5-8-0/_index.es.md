---
title: "Cambios en la API pública en Aspose.Email 5.8.0"
url: /es/java/public-api-changes-in-aspose-email-5-8-0/
weight: 190
type: docs
---

La siguiente es una lista de cualquier cambio realizado en la API pública, como miembros añadidos, renombrados, eliminados o en desuso, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para .NET. Si tiene inquietudes sobre algún cambio listado, por favor, hágalo en el foro de soporte de Aspose.Email.
## **APIs Añadidas**
- Clase `TnefLoadOptions`
- Método `IEWSClient.listMessages(String, ExchangeMessageInfoCollection, Integer, Integer)`
- Método `IEWSClient.listMessages(String, Integer)`
- Método `IEWSClient.listMessages(String, Integer, Integer)`
- Método `IEWSClient.listSubFolders(String, ExchangeFolderInfoCollection, Integer, Integer)`
- Método `IEWSClient.listSubFolders(String, Integer)`
- Método `IEWSClient.listSubFolders(String, Integer, Integer)`
- Propiedad `ExchangeFolderInfoCollection.getLastItemOffset, setLastItemOffset`
- Propiedad `ExchangeFolderInfoCollection.getLastPage, setLastPage`
- Propiedad `ExchangeFolderInfoCollection.getTotalCount, setTotalCount`
- Propiedad `ExchangeMessageInfoCollection.getLastItemOffset, setLastItemOffset`
- Propiedad `ExchangeMessageInfoCollection.getLastPage, setLastPage`
- Propiedad `ExchangeMessageInfoCollection.getTotalCount, setTotalCount`
- Propiedad `IEWSClient.getEnableDecompression, setEnableDecompression(boolean)`
- Propiedad `MessageFormat.getTnef`
## **APIs Eliminadas**
- Método `LoadOptions.#ctor(MessageFormat)`