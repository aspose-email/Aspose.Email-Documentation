---
title: "Изменения в публичном API в Aspose.Email 5.8.0"
url: /ru/java/public-api-changes-in-aspose-email-5-8-0/
weight: 190
type: docs
---

Ниже приведен список любых изменений, внесенных в общедоступный API, таких как добавление, переименование, удаление или устаревание участников, а также любых изменений, не совместимых с обратной совместимостью, внесенных в Aspose.Email for .NET. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.
## **Добавлены API**
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
## **Удаленные API**
- Method `LoadOptions.#ctor(MessageFormat)`
