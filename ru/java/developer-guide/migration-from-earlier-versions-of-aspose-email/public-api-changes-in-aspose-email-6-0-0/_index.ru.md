---
title: "Изменения в общественном API Aspose.Email 6.0.0"
url: /ru/java/public-api-changes-in-aspose-email-6-0-0/
weight: 210
type: docs
---

Следующий список содержит изменения, внесенные в общественный API, такие как добавление, переименование, удаление или устаревание членов, а также любые изменения, несовместимые с предыдущими версиями, внесенные в Aspose.Email для .NET. Если у вас есть сомнения по поводу любого из перечисленных изменений, пожалуйста, поднимите их на форуме поддержки Aspose.Email.
## **Добавленные API**
- Класс `ExchangeDistributionList`
- Метод `ExchangeDistributionList.#ctor`
- Метод `ExchangeDistributionList.toMailAddress`
- Метод `IEWSClient.addToDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Метод `IEWSClient.createDistributionList(ExchangeDistributionList, MailAddressCollection)`
- Метод `IEWSClient.deleteDistributionList( ExchangeDistributionList, boolean)`
- Метод `IEWSClient.deleteFromDistributionList( ExchangeDistributionList, MailAddressCollection)`
- Метод `IEWSClient.expandDistributionList(MailAddress)`
- Метод `IEWSClient.fetchDistributionList(ExchangeDistributionList)`
- Метод `IEWSClient.listDistributionLists`
- Свойство `ExchangeDistributionList.getChangeKey(), setChangeKey(String)`
- Свойство `ExchangeDistributionList.getDisplayName(), setDisplayName(String)`
- Свойство `ExchangeDistributionList.getId(), setId(String)`
- Свойство `MailAddress.Id`

- Класс `ForwardMessageBuilder`
- Класс `OriginalMessageAdditionMode`
- Класс `ReplyMessageBuilder`
- Класс `ResponseMessageBuilder`
- Перечисление `OriginalMessageAdditionMode.Attachment`
- Перечисление `OriginalMessageAdditionMode.None`
- Перечисление `OriginalMessageAdditionMode.Textpart`
- Перечисление `Outlook.MapiPropertyTag.PR_ATTACHMENT_HIDDEN`
- Метод `ForwardMessageBuilder.#ctor`
- Метод `ForwardMessageBuilder.buildResponse(MailMessage)`
- Метод `ForwardMessageBuilder.buildResponse(MapiMessage)`
- Метод `ReplyMessageBuilder.#ctor`
- Метод `ReplyMessageBuilder.buildResponse(MailMessage)`
- Метод `ReplyMessageBuilder.buildResponse(MapiMessage)`
- Метод `ResponseMessageBuilder.#ctor`
- Метод `ResponseMessageBuilder.buildResponse(MailMessage)`
- Метод `ResponseMessageBuilder.buildResponse(MapiMessage)`
- Свойство `ReplyMessageBuilder.getReplyAll, setReplyAll(boolean)`
- Свойство `ResponseMessageBuilder.getAdditionMode, setAdditionMode(int)`
- Свойство `ResponseMessageBuilder.getResponseText, setResponseText(String)`
- Свойство `ResponseMessageBuilder.getSender, setSender(MailAddress)`

- Перечисление `MhtFormatOptions.SkipByteOrderMarkInBody`

- Класс `MailMessageEventArgs`
- Метод `MailMessageEventArgs.#ctor(MailMessage)`
- Свойство `MailMessageEventArgs.getMessage`
- Метод `IEWSClient.listMessages(IGenericEnumerable<String>)`

- Метод `MapiAttachmentCollection.removeAt(int)`
- Метод `PersonalStorage.splitInto(long, String)`
## **Удаленные API**
- Метод `PersonalStorage.ыplitInto(int, String)`
- Свойство `SmtpClientBulkSendEventArgs.getMessage`