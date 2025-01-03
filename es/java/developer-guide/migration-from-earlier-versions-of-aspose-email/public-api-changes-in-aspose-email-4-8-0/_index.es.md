---
title: "Cambios en la API Pública en Aspose.Email 4.8.0"
url: /es/java/public-api-changes-in-aspose-email-4-8-0/
weight: 100
type: docs
---

La siguiente es una lista de cualquier cambio realizado en la API pública, como miembros añadidos, renombrados, eliminados o en desuso, así como cualquier cambio no compatible hacia atrás realizado en Aspose.Email para Java. Si tiene inquietudes sobre algún cambio listado, por favor, planteelo en el foro de soporte de Aspose.Email.

**Nuevas clases:**

- `ContactLoadFormat`
- `MapiContactOtherPropertySet`
- `MapiMessageItemBase`

Se añadieron la clase base SaveOptions y las clases particulares EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions para configuraciones adicionales de guardado de MailMessage:

- `SaveOptions`
- `EmlSaveOptions`
- `HtmlSaveOptions`
- `MhtSaveOptions`
- `MsgSaveOptions`

Las siguientes clases están solo en `aspose-email-4.8.0.0-jdk17.jar`:

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

**Nuevos métodos en la clase Contact:**

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

**Nuevos métodos en la clase MailMessage:**

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

**Métodos en desuso en la clase MailMessage:**

- `public boolean getPreserveOriginalBoundaries(), public void setPreserveOriginalBoundaries(boolean value)` - Use el método `save(Stream stream, SaveOptions options)` con la configuración `EmlSaveOptions.PreserveOriginalBoundaries` en lugar de esta propiedad.
- `public boolean getPreserveOriginalDates(), public void setPreserveOriginalDates(boolean value)` - Use el método `save(Stream stream, SaveOptions options)` con la configuración `MsgSaveOptions.PreserveOriginalDates` en lugar de esta propiedad.
- `void save(String fileName, MailMessageSaveType savetype)`
- `void save(String fileName, MailMessageSaveType savetype, int saveOptions)`
- `void save(String fileName, MessageFormat format)`
- `void save(String fileName, MessageFormat format, int saveOptions)`