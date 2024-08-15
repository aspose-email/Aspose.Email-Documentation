---
title: "Cambios en la API pública en Aspose.Email 6.0.0"
url: /es/java/public-api-changes-in-aspose-email-6-0-0/
weight: 210
type: docs
---

La siguiente es una lista de todos los cambios realizados en la API pública, como la adición, el cambio de nombre, la eliminación o la desaprobación de miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email for.NET. Si tienes dudas sobre algún cambio de la lista, comunícalo en el foro de soporte de Aspose.Email.
## **API añadidas**
- Class `ExchangeDistributionList`
- Method `ExchangeDistributionList.#ctor`
- Method `ExchangeDistributionList.toMailAddress`
- Method `IEWSClient.addToDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Method `IEWSClient.createDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Method `IEWSClient.deleteDistributionList( ExchangeDistributionList, boolean)`
- Method `IEWSClient.deleteFromDistributionList( ExchangeDistributionList, MailAddressCollection)`
- Method `IEWSClient.expandDistributionList(MailAddress)`
- Method `IEWSClient.fetchDistributionList(ExchangeDistributionList)`
- Method `IEWSClient.listDistributionLists`
- Property `ExchangeDistributionList.getChangeKey(), setChangeKey(String)`
- Property `ExchangeDistributionList.getDisplayName(), setDisplayName(String)`
- Property `ExchangeDistributionList.getId(), setId(String)`
- Property `MailAddress.Id`

- Class `ForwardMessageBuilder`
- Class `OriginalMessageAdditionMode`
- Class `ReplyMessageBuilder`
- Class `ResponseMessageBuilder`
- Enum `OriginalMessageAdditionMode.Attachment`
- Enum `OriginalMessageAdditionMode.None`
- Enum `OriginalMessageAdditionMode.Textpart`
- Enum `Outlook.MapiPropertyTag.PR_ATTACHMENT_HIDDEN`
- Method `ForwardMessageBuilder.#ctor`
- Method `ForwardMessageBuilder.buildResponse(MailMessage)`
- Method `ForwardMessageBuilder.buildResponse(MapiMessage)`
- Method `ReplyMessageBuilder.#ctor`
- Method `ReplyMessageBuilder.buildResponse(MailMessage)`
- Method `ReplyMessageBuilder.buildResponse(MapiMessage)`
- Method `ResponseMessageBuilder.#ctor`
- Method `ResponseMessageBuilder.buildResponse(MailMessage)`
- Method `ResponseMessageBuilder.buildResponse(MapiMessage)`
- Property `ReplyMessageBuilder.getReplyAll, setReplyAll(boolean)`
- Property `ResponseMessageBuilder.getAdditionMode, setAdditionMode(int)`
- Property `ResponseMessageBuilder.getResponseText, setResponseText(String)`
- Property `ResponseMessageBuilder.getSender, setSender(MailAddress)`

- Enum `MhtFormatOptions.SkipByteOrderMarkInBody`

- Class `MailMessageEventArgs`
- Method `MailMessageEventArgs.#ctor(MailMessage)`
- Property `MailMessageEventArgs.getMessage`
- Method `IEWSClient.listMessages(IGenericEnumerable<String>)`

- Method `MapiAttachmentCollection.removeAt(int)`
- Method `PersonalStorage.splitInto(long, String)`
## **API eliminadas**
- Method `PersonalStorage.ыplitInto(int, String)`
- Property `SmtpClientBulkSendEventArgs.getMessage`
