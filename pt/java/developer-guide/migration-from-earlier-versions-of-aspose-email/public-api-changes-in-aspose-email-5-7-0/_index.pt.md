---
title: "Mudanças na API Pública no Aspose.Email 5.7.0"
url: /pt/java/public-api-changes-in-aspose-email-5-7-0/
weight: 180
type: docs
---

A seguir está uma lista de quaisquer mudanças feitas na API pública, como membros adicionados, renomeados, removidos ou depreciados, bem como qualquer mudança não compatível com versões anteriores feita no Aspose.Email para .NET. Se você tiver preocupações sobre qualquer mudança listada, por favor, manifeste no fórum de suporte do Aspose.Email.
## **APIs Adicionadas**
- Classe `ImapMonitoringEventArgs`
- Classe `ImapMonitoringEventHandler`
- Classe `EmlLoadOptions`
- Classe `EmlxLoadOptions`
- Classe `HtmlLoadOptions`
- Classe `LoadOptions`
- Classe `MhtmlLoadOptions`
- Classe `MsgLoadOptions`
- Classe `MessageKind`
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
- Propriedade `ExchangeQueryBuilder.getMessageId()`
- Propriedade `IEWSClient.getHeaders()`
- Propriedade `ImapMonitoringEventArgs.getDeletedMessages()`
- Propriedade `ImapMonitoringEventArgs.getError()`
- Propriedade `ImapMonitoringEventArgs.getFolderName()`
- Propriedade `ImapMonitoringEventArgs.getNewMessages()`
- Propriedade `EmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Propriedade `HtmlLoadOptions.getPathToResources(), setPathToResources()`
- Propriedade `HtmlLoadOptions.setShouldAddPlainTextView(), getShouldAddPlainTextView()`
- Propriedade `LoadOptions.getMessageFormat(), setMessageFormat()`
- Propriedade `LoadOptions.getPrefferedTextEncoding(), setPrefferedTextEncoding()`
- Propriedade `MessageFormat.getHtml()`
- Propriedade `MhtmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Propriedade `MsgLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()`
- Propriedade `PersonalStorageQueryBuilder.getMessageId()`
## **APIs Removidas**
- Classe `Pop3Authentication`
- Método `FolderInfo.deleteChildMessages(MessageInfoCollection)`