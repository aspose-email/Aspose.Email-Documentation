---
title: "Изменения в публичном API Aspose.Email 4.8.0"
url: /ru/java/public-api-changes-in-aspose-email-4-8-0/
weight: 100
type: docs
---

Следующий список содержит изменения, внесенные в публичный API, такие как добавленные, переименованные, удаленные или устаревшие члены, а также любые изменения, несовместимые с предыдущими версиями, внесенные в Aspose.Email для Java. Если у вас есть вопросы по любому из перечисленных изменений, пожалуйста, поднимите их на форуме поддержки Aspose.Email.

**Новые классы:**

- `ContactLoadFormat`
- `MapiContactOtherPropertySet`
- `MapiMessageItemBase`

Базовый класс SaveOptions и конкретные классы EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions для дополнительных настроек сохранения MailMessage были добавлены:

- `SaveOptions`
- `EmlSaveOptions`
- `HtmlSaveOptions`
- `MhtSaveOptions`
- `MsgSaveOptions`

Следующие классы доступны только в `aspose-email-4.8.0.0-jdk17.jar`:

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

**Новые методы в классе Contact:**

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

**Новые методы в классе MailMessage:**

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

**Устаревшие методы в классе MailMessage:**

- `public boolean getPreserveOriginalBoundaries(), public void setPreserveOriginalBoundaries(boolean value)` - Используйте метод `save(Stream stream, SaveOptions options)` с установкой `EmlSaveOptions.PreserveOriginalBoundaries` вместо этого свойства.
- `public boolean getPreserveOriginalDates(), public void setPreserveOriginalDates(boolean value)` - Используйте метод `save(Stream stream, SaveOptions options)` с установкой `MsgSaveOptions.PreserveOriginalDates` вместо этого свойства.
- `void save(String fileName, MailMessageSaveType savetype)`
- `void save(String fileName, MailMessageSaveType savetype, int saveOptions)`
- `void save(String fileName, MessageFormat format)`
- `void save(String fileName, MessageFormat format, int saveOptions)`