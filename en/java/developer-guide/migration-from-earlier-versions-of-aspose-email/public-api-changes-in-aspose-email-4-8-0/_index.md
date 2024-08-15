---
title: Public API Changes in Aspose.Email 4.8.0
type: docs
weight: 100
url: /java/public-api-changes-in-aspose-email-4-8-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for Java. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.

**New classes:**

- `ContactLoadFormat`
- `MapiContactOtherPropertySet`
- `MapiMessageItemBase`

Base class SaveOptions and particular classes EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions for additional settings of saving MailMessage were added:

- `SaveOptions`
- `EmlSaveOptions`
- `HtmlSaveOptions`
- `MhtSaveOptions`
- `MsgSaveOptions`

The following classes are in `aspose-email-4.8.0.0-jdk17.jar` only:

- `ValidationResult`
- `ValidationResponseCode`
- `ValidationPolicy`
- `TokenType`
- `SyntaxValidatingEventHandler`
- `SyntaxValidatingEventArgs`
- `SocksVersion`
- `SocksProxy`
- `SocksAuthenticationMethods`
- `SmtpStatusCode`
- `SmtpSslSecurityMode`
- `SmtpFailedRecipientsException`
- `SmtpFailedBulkSendException`
- `SmtpException`
- `SmtpDeliveryMethod`
- `SmtpClientBulkSendEventArgs`
- `SmtpClientBulkSendAgent`
- `SmtpClient`
- `SmtpAuthentication`
- `SimpleSeqSet`
- `SequenceSetField`
- `SequenceSetBaseValue`
- `SendCompletedEventHandler`
- `SecurityOptions`
- `ReadLinesTimeoutException`
- `RangeSeqSet`
- `Pop3SslSecurityMode`
- `Pop3MessageInfo`
- `Pop3MailboxInfo`
- `Pop3ListFields`
- `Pop3Exception`
- `Pop3ConnectionState`
- `Pop3Client`
- `Pop3Authentication`
- `OAuthToken`
- `MailServerValidatingEventHandler`
- `MailServerValidatingEventArgs`
- `MailClientTask`
- `ImapStatusCode`
- `ImapSslSecurityMode`
- `ImapResponse`
- `ImapQueryBuilder`
- `ImapMessageInfoCollection`
- `ImapMessageInfo`
- `ImapMessageFlags`
- `ImapFolderInfoCollection`
- `ImapFolderInfo`
- `ImapException`
- `ImapCommandResult`
- `ImapClient`
- `ImapAuthentication`
- `ITokenProvider`
- `IOAuthServiceClient`
- `IMailTransferAgent`
- `IFeedEntry`
- `ICommand`
- `IAsyncCommand`
- `GoogleTokenProvider`
- `GmailContactPostalAddress`
- `GmailContactPhoneNumber`
- `GmailContactOrganization`
- `GmailContactName`
- `GmailContactInfoCollection`
- `GmailContactInfo`
- `GmailContactIm`
- `GmailContactGroup`
- `GmailContactEmail`
- `GmailContact`
- `GmailClientException`
- `GmailClientAuthorization`
- `GmailClient`
- `FetchTimeoutException`
- `FeedEntryCollection`
- `DomainValidatingEventHandler`
- `DomainValidatingEventArgs`
- `CredentialsByHostClient`
- `ConnectionState`
- `CommandStatus`
- `BaseCommand`
- `AsyncCommandResults`
- `AsposeInvalidDataException`

**New methods in Contact class:**

- `load(Stream)`
- `load(Stream,int)`
- `load(String)`
- `load(String,int)`
- `save(Stream)`
- `save(Stream,Aspose.Email.Outlook.ContactSaveFormat)`
- `save(Stream,Aspose.Email.Outlook.ContactSaveOptions)`
- `save(System.String)`
- `save(System.String,int)`
- `save(System.String,int)`

**New methods in MailMessage class:**

- `save(Stream, SaveOptions)`
- `save(String, SaveOptions)`
- `decrypt(byte[],java.lang.String)`
- `decrypt()`
- `encrypt(byte[],java.lang.String)`
- `attachSignature(byte[],java.lang.String)`
- `checkSignature()`
- `checkSignature(java.lang.String)`
- `checkSignature(java.io.InputStream)`
- `removeSignature()`

**Deprecated methods in MailMessage class:**

- `public boolean getPreserveOriginalBoundaries(), public void setPreserveOriginalBoundaries(boolean value)` - Use method `save(Stream stream, SaveOptions options)` with setting `EmlSaveOptions.PreserveOriginalBoundaries` instead this propery.
- `public boolean getPreserveOriginalDates(), public void setPreserveOriginalDates(boolean value)` - Use method `save(Stream stream, SaveOptions options)` with setting `MsgSaveOptions.PreserveOriginalDates` instead this propery.
- `void save(String fileName, MailMessageSaveType savetype)`
- `void save(String fileName, MailMessageSaveType savetype, int saveOptions)`
- `void save(String fileName, MessageFormat format)`
- `void save(String fileName, MessageFormat format, int saveOptions)`
