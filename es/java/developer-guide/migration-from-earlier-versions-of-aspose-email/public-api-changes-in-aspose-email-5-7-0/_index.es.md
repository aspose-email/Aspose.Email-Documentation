---
title: "Cambios en la API Pública en Aspose.Email 5.7.0"
url: /es/java/public-api-changes-in-aspose-email-5-7-0/
weight: 180
type: docs
---

La siguiente es una lista de cualquier cambio realizado en la API pública, como miembros añadidos, renombrados, eliminados o en desuso, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para .NET. Si tienes preocupaciones sobre algún cambio listado, por favor, notifícalo en el foro de soporte de Aspose.Email.
## **APIs Añadidas**
- Clase `ImapMonitoringEventArgs`
- Clase `ImapMonitoringEventHandler`
- Clase `EmlLoadOptions`
- Clase `EmlxLoadOptions`
- Clase `HtmlLoadOptions`
- Clase `LoadOptions`
- Clase `MhtmlLoadOptions`
- Clase `MsgLoadOptions`
- Clase `MessageKind`
- Enum `MessageKind.FolderAssociatedInformation`
- Enum `MessageKind.Normal`
- Método `IEWSClient.addHeader(String name, String value)`
- Método `IEWSClient.removeHeader(String name)`
- Método `ImapClient.startMonitoring(ImapMonitoringEventHandler callback)`
- Método `ImapClient.startMonitoring(final String folderName, final ImapMonitoringEventHandler callback)`
- Método `ImapClient.stopMonitoring(String folderName)`
- Método `ImapClient.stopMonitoring()`
- Método `MailMessage.load(InputStream stream,LoadOptions options)`
- Método `Aspose.Email.Mail.MailMessage.load(String fileName, MailMessageLoadOptions options)`
- Método `Aspose.Email.Mail.TemplateEngine.merge(DataRow row)`
- Método `FolderInfo.getContents(MessageKind)`
- Propiedad `ExchangeQueryBuilder.getMessageId()`
- Propiedad `IEWSClient.getHeaders()`
- Propiedad `ImapMonitoringEventArgs.getDeletedMessages()`
- Propiedad `ImapMonitoringEventArgs.getError()`
- Propiedad `ImapMonitoringEventArgs.getFolderName()`
- Propiedad `ImapMonitoringEventArgs.getNewMessages()`
- Propiedad `EmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Propiedad `HtmlLoadOptions.getPathToResources(), setPathToResources()`
- Propiedad `HtmlLoadOptions.setShouldAddPlainTextView(), getShouldAddPlainTextView()`
- Propiedad `LoadOptions.getMessageFormat(), setMessageFormat()`
- Propiedad `LoadOptions.getPrefferedTextEncoding(), setPrefferedTextEncoding()`
- Propiedad `MessageFormat.getHtml()`
- Propiedad `MhtmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Propiedad `MsgLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Propiedad `PersonalStorageQueryBuilder.getMessageId()`
## **APIs Eliminadas**
- Clase `Pop3Authentication`
- Método `FolderInfo.deleteChildMessages(MessageInfoCollection)`