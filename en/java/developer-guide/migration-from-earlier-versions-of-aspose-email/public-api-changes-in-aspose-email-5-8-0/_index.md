---
title: Public API Changes in Aspose.Email 5.8.0
type: docs
weight: 190
url: /java/public-api-changes-in-aspose-email-5-8-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for .NET. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added APIs**
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
## **Removed APIs**
- Method `LoadOptions.#ctor(MessageFormat)`
