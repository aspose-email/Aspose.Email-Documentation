---
title: "Изменения в публичном API в Aspose.Email 5.8.0"
url: /ru/java/public-api-changes-in-aspose-email-5-8-0/
weight: 190
type: docs
---

Следующий список содержит изменения, внесенные в публичный API, такие как добавление, переименование, удаление или устаревание членов, а также любые изменения, несовместимые с ранее существовавшими версиями Aspose.Email для .NET. Если у вас есть сомнения относительно какого-либо изменения в списке, пожалуйста, поднимите этот вопрос на форуме поддержки Aspose.Email.
## **Добавленные API**
- Класс `TnefLoadOptions`
- Метод `IEWSClient.listMessages(String, ExchangeMessageInfoCollection, Integer, Integer)`
- Метод `IEWSClient.listMessages(String, Integer)`
- Метод `IEWSClient.listMessages(String, Integer, Integer)`
- Метод `IEWSClient.listSubFolders(String, ExchangeFolderInfoCollection, Integer, Integer)`
- Метод `IEWSClient.listSubFolders(String, Integer)`
- Метод `IEWSClient.listSubFolders(String, Integer, Integer)`
- Свойство `ExchangeFolderInfoCollection.getLastItemOffset, setLastItemOffset`
- Свойство `ExchangeFolderInfoCollection.getLastPage, setLastPage`
- Свойство `ExchangeFolderInfoCollection.getTotalCount, setTotalCount`
- Свойство `ExchangeMessageInfoCollection.getLastItemOffset, setLastItemOffset`
- Свойство `ExchangeMessageInfoCollection.getLastPage, setLastPage`
- Свойство `ExchangeMessageInfoCollection.getTotalCount, setTotalCount`
- Свойство `IEWSClient.getEnableDecompression, setEnableDecompression(boolean)`
- Свойство `MessageFormat.getTnef`
## **Удаленные API**
- Метод `LoadOptions.#ctor(MessageFormat)`