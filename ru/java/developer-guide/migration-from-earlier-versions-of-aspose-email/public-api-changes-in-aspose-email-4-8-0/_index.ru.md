---
title: "Изменения в публичном API в Aspose.Email 4.8.0"
url: /ru/java/public-api-changes-in-aspose-email-4-8-0/
weight: 100
type: docs
---

Ниже приведен список всех изменений, внесенных в общедоступный API, таких как добавление, переименование, удаление или устаревание членов, а также любых изменений, не совместимых с обратной совместимостью, внесенных в Aspose.Email для Java. Если у вас есть сомнения по поводу каких-либо перечисленных изменений, сообщите об этом на форуме поддержки Aspose.Email.

**Новые классы:**

- `ContactLoadFormat`
- `MapiContactOtherPropertySet`
- `MapiMessageItemBase`

Добавлены базовый класс SaveOptions и отдельные классы EMLSaveOptions, MsgSaveOptions, MHTSaveOptions, HTSaveOptions, HTMLSaveOptions для дополнительных настроек сохранения MailMessage:

- `SaveOptions`
- `EmlSaveOptions`
- `HtmlSaveOptions`
- `MhtSaveOptions`
- `MsgSaveOptions`

Следующие классы входят в `aspose-email-4.8.0.0-jdk17.jar` only:

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

- `public boolean getPreserveOriginalBoundaries(), public void setPreserveOriginalBoundaries(boolean value)` - Метод использования `save(Stream stream, SaveOptions options)` с настройкой `EmlSaveOptions.PreserveOriginalBoundaries` вместо этого свойства.
- `public boolean getPreserveOriginalDates(), public void setPreserveOriginalDates(boolean value)` - Метод использования `save(Stream stream, SaveOptions options)` с настройкой `MsgSaveOptions.PreserveOriginalDates` вместо этого свойства.
- `void save(String fileName, MailMessageSaveType savetype)`
- `void save(String fileName, MailMessageSaveType savetype, int saveOptions)`
- `void save(String fileName, MessageFormat format)`
- `void save(String fileName, MessageFormat format, int saveOptions)`
