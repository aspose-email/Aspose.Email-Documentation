---
title: "Изменения в публичном API в Aspose.Email 5.7.0"
url: /ru/java/public-api-changes-in-aspose-email-5-7-0/
weight: 180
type: docs
---

Ниже приведен список любых изменений, внесенных в общедоступный API, таких как добавление, переименование, удаление или устаревание участников, а также любых изменений, не совместимых с обратной совместимостью, внесенных в Aspose.Email for .NET. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.
## **Добавлены API**
- Class `ImapMonitoringEventArgs`
- Class `ImapMonitoringEventHandler`
- Class `EmlLoadOptions`
- Class `EmlxLoadOptions`
- Class `HtmlLoadOptions`
- Class `LoadOptions`
- Class `MhtmlLoadOptions`
- Class `MsgLoadOptions`
- Class `MessageKind`
- Enum `MessageKind.FolderAssociatedInformation`
- Enum `MessageKind.Normal`
- Method `IEWSClient.addHeader(String name, String value)`
- Method `IEWSClient.removeHeader(String name)`
- Method `ImapClient.startMonitoring(ImapMonitoringEventHandler callback)`
- Method `ImapClient.startMonitoring(final String folderName, final ImapMonitoringEventHandler callback)`
- Method `ImapClient.stopMonitoring(String folderName)`
- Method `ImapClient.stopMonitoring()`
- Method `MailMessage.load(InputStream stream,LoadOptions options)`
- Method `Aspose.Email.Mail.MailMessage.load(String fileName, MailMessageLoadOptions options)`
- Method `Aspose.Email.Mail.TemplateEngine.merge(DataRow row)`
- Method `FolderInfo.getContents(MessageKind)`
- Property `ExchangeQueryBuilder.getMessageId()`
- Property `IEWSClient.getHeaders()`
- Property `ImapMonitoringEventArgs.getDeletedMessages()`
- Property `ImapMonitoringEventArgs.getError()`
- Property `ImapMonitoringEventArgs.getFolderName()`
- Property `ImapMonitoringEventArgs.getNewMessages()`
- Property `EmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Property `HtmlLoadOptions.getPathToResources(), setPathToResources()`
- Property `HtmlLoadOptions.setShouldAddPlainTextView(), getShouldAddPlainTextView()`
- Property `LoadOptions.getMessageFormat(), setMessageFormat()`
- Property `LoadOptions.getPrefferedTextEncoding(), setPrefferedTextEncoding()`
- Property `MessageFormat.getHtml()`
- Property `MhtmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Property `MsgLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Property `PersonalStorageQueryBuilder.getMessageId()`
## **Удаленные API**
- Class `Pop3Authentication`
- Method `FolderInfo.deleteChildMessages(MessageInfoCollection)`
