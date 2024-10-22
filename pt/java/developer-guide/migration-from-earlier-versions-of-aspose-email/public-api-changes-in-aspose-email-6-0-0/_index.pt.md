---
title: "Mudanças na API Pública no Aspose.Email 6.0.0"
url: /pt/java/public-api-changes-in-aspose-email-6-0-0/
weight: 210
type: docs
---

A seguir está uma lista de quaisquer mudanças feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como quaisquer alterações não compatíveis com versões anteriores feitas no Aspose.Email para .NET. Se você tiver preocupações sobre qualquer mudança listada, por favor, levante no fórum de suporte do Aspose.Email.
## **APIs Adicionadas**
- Classe `ExchangeDistributionList`
- Método `ExchangeDistributionList.#ctor`
- Método `ExchangeDistributionList.toMailAddress`
- Método `IEWSClient.addToDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Método `IEWSClient.createDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Método `IEWSClient.deleteDistributionList( ExchangeDistributionList, boolean)`
- Método `IEWSClient.deleteFromDistributionList( ExchangeDistributionList, MailAddressCollection)`
- Método `IEWSClient.expandDistributionList(MailAddress)`
- Método `IEWSClient.fetchDistributionList(ExchangeDistributionList)`
- Método `IEWSClient.listDistributionLists`
- Propriedade `ExchangeDistributionList.getChangeKey(), setChangeKey(String)`
- Propriedade `ExchangeDistributionList.getDisplayName(), setDisplayName(String)`
- Propriedade `ExchangeDistributionList.getId(), setId(String)`
- Propriedade `MailAddress.Id`

- Classe `ForwardMessageBuilder`
- Classe `OriginalMessageAdditionMode`
- Classe `ReplyMessageBuilder`
- Classe `ResponseMessageBuilder`
- Enumeração `OriginalMessageAdditionMode.Attachment`
- Enumeração `OriginalMessageAdditionMode.None`
- Enumeração `OriginalMessageAdditionMode.Textpart`
- Enumeração `Outlook.MapiPropertyTag.PR_ATTACHMENT_HIDDEN`
- Método `ForwardMessageBuilder.#ctor`
- Método `ForwardMessageBuilder.buildResponse(MailMessage)`
- Método `ForwardMessageBuilder.buildResponse(MapiMessage)`
- Método `ReplyMessageBuilder.#ctor`
- Método `ReplyMessageBuilder.buildResponse(MailMessage)`
- Método `ReplyMessageBuilder.buildResponse(MapiMessage)`
- Método `ResponseMessageBuilder.#ctor`
- Método `ResponseMessageBuilder.buildResponse(MailMessage)`
- Método `ResponseMessageBuilder.buildResponse(MapiMessage)`
- Propriedade `ReplyMessageBuilder.getReplyAll, setReplyAll(boolean)`
- Propriedade `ResponseMessageBuilder.getAdditionMode, setAdditionMode(int)`
- Propriedade `ResponseMessageBuilder.getResponseText, setResponseText(String)`
- Propriedade `ResponseMessageBuilder.getSender, setSender(MailAddress)`

- Enumeração `MhtFormatOptions.SkipByteOrderMarkInBody`

- Classe `MailMessageEventArgs`
- Método `MailMessageEventArgs.#ctor(MailMessage)`
- Propriedade `MailMessageEventArgs.getMessage`
- Método `IEWSClient.listMessages(IGenericEnumerable<String>)`

- Método `MapiAttachmentCollection.removeAt(int)`
- Método `PersonalStorage.splitInto(long, String)`
## **APIs Removidas**
- Método `PersonalStorage.ыplitInto(int, String)`
- Propriedade `SmtpClientBulkSendEventArgs.getMessage`