---
title: Public API Changes in Aspose.Email 5.7.0
type: docs
weight: 180
url: /java/public-api-changes-in-aspose-email-5-7-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for .NET. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added APIs**
Class ImapMonitoringEventArgs
Class ImapMonitoringEventHandler
Class EmlLoadOptions
Class EmlxLoadOptions
Class HtmlLoadOptions
Class LoadOptions
Class MhtmlLoadOptions
Class MsgLoadOptions
Class MessageKind
Enum MessageKind.FolderAssociatedInformation
Enum MessageKind.Normal
Method IEWSClient.addHeader(String name, String value)
Method IEWSClient.removeHeader(String name)
Method ImapClient.startMonitoring(ImapMonitoringEventHandler callback)
Method ImapClient.startMonitoring(final String folderName, final ImapMonitoringEventHandler callback)
Method ImapClient.stopMonitoring(String folderName)
Method ImapClient.stopMonitoring()
Method MailMessage.load(InputStream stream,LoadOptions options)
Method Aspose.Email.Mail.MailMessage.load(String fileName, MailMessageLoadOptions options)
Method Aspose.Email.Mail.TemplateEngine.merge(DataRow row)
Method FolderInfo.getContents(MessageKind)
Property ExchangeQueryBuilder.getMessageId()
Property IEWSClient.getHeaders()
Property ImapMonitoringEventArgs.getDeletedMessages()
Property ImapMonitoringEventArgs.getError()
Property ImapMonitoringEventArgs.getFolderName()
Property ImapMonitoringEventArgs.getNewMessages()
Property EmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()
Property HtmlLoadOptions.getPathToResources(), setPathToResources()
Property HtmlLoadOptions.setShouldAddPlainTextView(), getShouldAddPlainTextView()
Property LoadOptions.getMessageFormat(), setMessageFormat()
Property LoadOptions.getPrefferedTextEncoding(), setPrefferedTextEncoding()
Property MessageFormat.getHtml()
Property MhtmlLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()
Property MsgLoadOptions.getPreserveTnefAttachments(), setPreserveTnefAttachments()
Property PersonalStorageQueryBuilder.getMessageId()
## **Removed APIs**
Class Pop3Authentication
Method FolderInfo.deleteChildMessages(MessageInfoCollection)
