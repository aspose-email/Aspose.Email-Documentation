---
title: "Mudanças na API Pública no Aspose.Email 5.8.0"
url: /pt/java/public-api-changes-in-aspose-email-5-8-0/
weight: 190
type: docs
---

A seguir está uma lista de quaisquer alterações feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como qualquer mudança não compatível com versões anteriores feita no Aspose.Email para .NET. Se você tiver preocupações sobre alguma mudança listada, por favor, levante-a no fórum de suporte do Aspose.Email.
## **APIs Adicionadas**
- Classe `TnefLoadOptions`
- Método `IEWSClient.listMessages(String, ExchangeMessageInfoCollection, Integer, Integer)`
- Método `IEWSClient.listMessages(String, Integer)`
- Método `IEWSClient.listMessages(String, Integer, Integer)`
- Método `IEWSClient.listSubFolders(String, ExchangeFolderInfoCollection, Integer, Integer)`
- Método `IEWSClient.listSubFolders(String, Integer)`
- Método `IEWSClient.listSubFolders(String, Integer, Integer)`
- Propriedade `ExchangeFolderInfoCollection.getLastItemOffset, setLastItemOffset`
- Propriedade `ExchangeFolderInfoCollection.getLastPage, setLastPage`
- Propriedade `ExchangeFolderInfoCollection.getTotalCount, setTotalCount`
- Propriedade `ExchangeMessageInfoCollection.getLastItemOffset, setLastItemOffset`
- Propriedade `ExchangeMessageInfoCollection.getLastPage, setLastPage`
- Propriedade `ExchangeMessageInfoCollection.getTotalCount, setTotalCount`
- Propriedade `IEWSClient.getEnableDecompression, setEnableDecompression(boolean)`
- Propriedade `MessageFormat.getTnef`
## **APIs Removidas**
- Método `LoadOptions.#ctor(MessageFormat)`