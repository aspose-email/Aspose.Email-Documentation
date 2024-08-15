---
title: "Cambios en la API pública en Aspose.Email 5.7.0"
url: /es/java/public-api-changes-in-aspose-email-5-7-0/
weight: 180
type: docs
---

La siguiente es una lista de todos los cambios realizados en la API pública, como la adición, el cambio de nombre, la eliminación o la desaprobación de miembros, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email for.NET. Si tienes dudas sobre algún cambio de la lista, comunícalo en el foro de soporte de Aspose.Email.
## **API añadidas**
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
## **API eliminadas**
- Class `Pop3Authentication`
- Method `FolderInfo.deleteChildMessages(MessageInfoCollection)`
