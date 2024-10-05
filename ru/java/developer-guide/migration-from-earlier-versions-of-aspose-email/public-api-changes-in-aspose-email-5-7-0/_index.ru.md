---
title: "Изменения в публичном API Aspose.Email 5.7.0"
url: /ru/java/public-api-changes-in-aspose-email-5-7-0/
weight: 180
type: docs
---

Следующий список содержит все изменения, внесенные в публичный API, такие как добавленные, переименованные, удаленные или устаревшие члены, а также любые несовместимые изменения, внесенные в Aspose.Email для .NET. Если у вас есть замечания по любому из перечисленных изменений, пожалуйста, поднимите это на форуме поддержки Aspose.Email.
## **Добавленные API**
- Класс `ImapMonitoringEventArgs`
- Класс `ImapMonitoringEventHandler`
- Класс `EmlLoadOptions`
- Класс `EmlxLoadOptions`
- Класс `HtmlLoadOptions`
- Класс `LoadOptions`
- Класс `MhtmlLoadOptions`
- Класс `MsgLoadOptions`
- Класс `MessageKind`
- Перечисление `MessageKind.FolderAssociatedInformation`
- Перечисление `MessageKind.Normal`
- Метод `IEWSClient.addHeader(String name, String value)`
- Метод `IEWSClient.removeHeader(String name)`
- Метод `ImapClient.startMonitoring(ImapMonitoringEventHandler callback)`
- Метод `ImapClient.startMonitoring(final String folderName, final ImapMonitoringEventHandler callback)`
- Метод `ImapClient.stopMonitoring(String folderName)`
- Метод `ImapClient.stopMonitoring()`
- Метод `MailMessage.load(InputStream stream,LoadOptions options)`
- Метод `Aspose.Email.Mail.MailMessage.load(String fileName, MailMessageLoadOptions options)`
- Метод `Aspose.Email.Mail.TemplateEngine.merge(DataRow row)`
- Метод `FolderInfo.getContents(MessageKind)`
- Свойство `ExchangeQueryBuilder.getMessageId()`
- Свойство `IEWSClient.getHeaders()`
- Свойство `ImapMonitoringEventArgs.getDeletedMessages()`
- Свойство `ImapMonitoringEventArgs.getError()`
- Свойство `ImapMonitoringEventArgs.getFolderName()`
- Свойство `ImapMonitoringEventArgs.getNewMessages()`
- Свойство `EmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Свойство `HtmlLoadOptions.getPathToResources(), setPathToResources()`
- Свойство `HtmlLoadOptions.setShouldAddPlainTextView(), getShouldAddPlainTextView()`
- Свойство `LoadOptions.getMessageFormat(), setMessageFormat()`
- Свойство `LoadOptions.getPrefferedTextEncoding(), setPrefferedTextEncoding()`
- Свойство `MessageFormat.getHtml()`
- Свойство `MhtmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Свойство `MsgLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Свойство `PersonalStorageQueryBuilder.getMessageId()`
## **Удаленные API**
- Класс `Pop3Authentication`
- Метод `FolderInfo.deleteChildMessages(MessageInfoCollection)`