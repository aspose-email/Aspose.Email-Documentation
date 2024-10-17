---
title: "Cambios en la API Pública en Aspose.Email 6.0.0"
url: /es/java/public-api-changes-in-aspose-email-6-0-0/
weight: 210
type: docs
---

La siguiente es una lista de cualquier cambio realizado en la API pública, como miembros añadidos, renombrados, eliminados o desaprobados, así como cualquier cambio no compatible hacia atrás realizado en Aspose.Email para .NET. Si tiene preocupaciones sobre cualquier cambio listado, por favor comuníquelo en el foro de soporte de Aspose.Email.
## **APIs añadidas**
- Clase `ExchangeDistributionList`
- Método `ExchangeDistributionList.#ctor`
- Método `ExchangeDistributionList.toMailAddress`
- Método `IEWSClient.addToDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Método `IEWSClient.createDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Método `IEWSClient.deleteDistributionList( ExchangeDistributionList, boolean)`
- Método `IEWSClient.deleteFromDistributionList( ExchangeDistributionList, MailAddressCollection)`
- Método `IEWSClient.expandDistributionList(MailAddress)`
- Método `IEWSClient.fetchDistributionList(ExchangeDistributionList)`
- Método `IEWSClient.listDistributionLists`
- Propiedad `ExchangeDistributionList.getChangeKey(), setChangeKey(String)`
- Propiedad `ExchangeDistributionList.getDisplayName(), setDisplayName(String)`
- Propiedad `ExchangeDistributionList.getId(), setId(String)`
- Propiedad `MailAddress.Id`

- Clase `ForwardMessageBuilder`
- Clase `OriginalMessageAdditionMode`
- Clase `ReplyMessageBuilder`
- Clase `ResponseMessageBuilder`
- Enum `OriginalMessageAdditionMode.Attachment`
- Enum `OriginalMessageAdditionMode.None`
- Enum `OriginalMessageAdditionMode.Textpart`
- Enum `Outlook.MapiPropertyTag.PR_ATTACHMENT_HIDDEN`
- Método `ForwardMessageBuilder.#ctor`
- Método `ForwardMessageBuilder.buildResponse(MailMessage)`
- Método `ForwardMessageBuilder.buildResponse(MapiMessage)`
- Método `ReplyMessageBuilder.#ctor`
- Método `ReplyMessageBuilder.buildResponse(MailMessage)`
- Método `ReplyMessageBuilder.buildResponse(MapiMessage)`
- Método `ResponseMessageBuilder.#ctor`
- Método `ResponseMessageBuilder.buildResponse(MailMessage)`
- Método `ResponseMessageBuilder.buildResponse(MapiMessage)`
- Propiedad `ReplyMessageBuilder.getReplyAll, setReplyAll(boolean)`
- Propiedad `ResponseMessageBuilder.getAdditionMode, setAdditionMode(int)`
- Propiedad `ResponseMessageBuilder.getResponseText, setResponseText(String)`
- Propiedad `ResponseMessageBuilder.getSender, setSender(MailAddress)`

- Enum `MhtFormatOptions.SkipByteOrderMarkInBody`

- Clase `MailMessageEventArgs`
- Método `MailMessageEventArgs.#ctor(MailMessage)`
- Propiedad `MailMessageEventArgs.getMessage`
- Método `IEWSClient.listMessages(IGenericEnumerable<String>)`

- Método `MapiAttachmentCollection.removeAt(int)`
- Método `PersonalStorage.splitInto(long, String)`
## **APIs eliminadas**
- Método `PersonalStorage.ыplitInto(int, String)`
- Propiedad `SmtpClientBulkSendEventArgs.getMessage`