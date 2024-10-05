---
title: "Изменения в общедоступном API в Aspose.Email 5.9.0"
url: /ru/java/public-api-changes-in-aspose-email-5-9-0/
weight: 200
type: docs
---

Следующий список включает в себя все изменения, внесенные в общедоступный API, такие как добавленные, переименованные, удаленные или устаревшие члены, а также любые несовместимые изменения, сделанные в Aspose.Email для Java. Если у вас есть сомнения по поводу каких-либо включенных изменений, пожалуйста, поднимите этот вопрос на форуме поддержки Aspose.Email.

- Класс `MapiCalendarRecurrencePatternFactory`

- Метод `MapiCalendarRecurrencePatternFactory.fromString(String)`

- Поле `MapiPropertyTag.PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE`

- Поле `MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME`

- Поле `MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY`

- Поле `MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ`

- Метод `IEWSClient.appendMessage(MailMessage)`

- Интерфейс `IConnection`

**`EWSClient`:**

- Метод getEWSClient(ExchangeVersion, `boolean, String, String, ICredentials, WebProxy)`

- Метод `getEWSClient(ExchangeVersion, String, ICredentials, WebProxy)`

**`ImapClient`:**

- Метод `addMessageFlags(IConnection, int, ImapMessageFlags)`

- Метод `addMessageFlags(IConnection, String, ImapMessageFlags)`

- Метод `appendMessage(IConnection, MailMessage)`

- Метод `appendMessage(IConnection, String)`

- Метод `appendMessage(IConnection, String, MailMessage)`

- Метод `appendMessage(IConnection, String, String)`

- Метод `appendMessage(String)`

- Метод `backup(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions)`

- Метод `backup(IConnection, ImapFolderInfoCollection, String, BackupOptions)`

- Метод `beginAddMessageFlags(IConnection, int, ImapMessageFlags)`

- Метод `beginAddMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback)`

- Метод `beginAddMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginAddMessageFlags(IConnection, String, ImapMessageFlags)`

- Метод `beginAddMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback)`

- Метод `beginAddMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginAddMessageFlags(int, ImapMessageFlags, AsyncCallback)`

- Метод `beginAddMessageFlags(String, ImapMessageFlags)`

- Метод `beginAddMessageFlags(String, ImapMessageFlags, AsyncCallback)`

- Метод `beginAddMessageFlags(String, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginAppendMessage(IConnection, MailMessage)`

- Метод `beginAppendMessage(IConnection, String)`

- Метод `beginAppendMessage(IConnection, String, MailMessage)`

- Метод `beginAppendMessage(IConnection, String, MailMessage, AsyncCallback)`

- Метод `beginAppendMessage(IConnection, String, MailMessage, AsyncCallback, Object)`

- Метод `beginAppendMessage(IConnection, String, String)`

- Метод `beginAppendMessage(IConnection, String, String, AsyncCallback)`

- Метод `beginAppendMessage(IConnection, String, String, AsyncCallback, Object)`

- Метод `beginAppendMessage(MailMessage)`

- Метод `beginAppendMessage(String)`

- Метод `beginAppendMessage(String, MailMessage)`

- Метод `beginAppendMessage(String, MailMessage, AsyncCallback)`

- Метод `beginAppendMessage(String, MailMessage, AsyncCallback, Object)`

- Метод `beginAppendMessage(String, String)`

- Метод `beginAppendMessage(String, String, AsyncCallback)`

- Метод `beginAppendMessage(String, String, AsyncCallback, Object)`

- Метод `beginChangeMessageFlags(IConnection, int, ImapMessageFlags)`

- Метод `beginChangeMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback)`

- Метод `beginChangeMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginChangeMessageFlags(IConnection, String, ImapMessageFlags)`

- Метод `beginChangeMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback)`

- Метод `beginChangeMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginChangeMessageFlags(int, ImapMessageFlags, AsyncCallback)`

- Метод `beginChangeMessageFlags(String, ImapMessageFlags)`

- Метод `beginChangeMessageFlags(String, ImapMessageFlags, AsyncCallback)`

- Метод `beginChangeMessageFlags(String, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginCommitDeletes`

- Метод `beginCommitDeletes(IConnection)`

- Метод `beginCommitDeletes(IConnection, AsyncCallback)`

- Метод `beginCommitDeletes(IConnection, AsyncCallback, Object)`

- Метод `beginCommitDeletes(IConnection, int)`

- Метод `beginCommitDeletes(IConnection, int, AsyncCallback, Object)`

- Метод `beginCommitDeletes(AsyncCallback)`

- Метод `beginCommitDeletes(AsyncCallback, Object)`

- Метод `beginCommitDeletes(int)`

- Метод `beginCommitDeletes(int, AsyncCallback, Object)`

- Метод `beginCopyMessage(IConnection, int, String)`

- Метод `beginCopyMessage(IConnection, int, String, AsyncCallback)`

- Метод `beginCopyMessage(IConnection, int, String, AsyncCallback, Object)`

- Метод `beginCopyMessage(IConnection, String, String)`

- Метод `beginCopyMessage(IConnection, String, String, AsyncCallback)`

- Метод `beginCopyMessage(IConnection, String, String, AsyncCallback, Object)`

- Метод `beginCopyMessage(int, String, AsyncCallback)`

- Метод `beginCopyMessage(String, String, AsyncCallback)`

- Метод `beginCreateFolder(IConnection, String)`

- Метод `beginCreateFolder(IConnection, String, AsyncCallback)`

- Метод `beginCreateFolder(IConnection, String, AsyncCallback, Object)`

- Метод `beginCreateFolder(String, AsyncCallback)`

- Метод `beginDeleteFolder(IConnection, String)`

- Метод `beginDeleteFolder(IConnection, String, AsyncCallback)`

- Метод `beginDeleteFolder(IConnection, String, AsyncCallback, Object)`

- Метод `beginDeleteFolder(String, AsyncCallback)`

- Метод `beginDeleteMessage(IConnection, int)`

- Метод `beginDeleteMessage(IConnection, int, AsyncCallback)`

- Метод `beginDeleteMessage(IConnection, int, AsyncCallback, Object)`

- Метод `beginDeleteMessage(IConnection, String)`

- Метод `beginDeleteMessage(IConnection, String, AsyncCallback)`

- Метод `beginDeleteMessage(IConnection, String, AsyncCallback, Object)`

- Метод `beginDeleteMessage(int, AsyncCallback)`

- Метод `beginDeleteMessage(String, AsyncCallback)`

- Метод `beginFetchAttachment(IConnection, int, String)`

- Метод `beginFetchAttachment(IConnection, int, String, AsyncCallback)`

- Метод `beginFetchAttachment(IConnection, int, String, AsyncCallback, Object)`

- Метод `beginFetchAttachment(int, String, AsyncCallback)`

- Метод `beginFetchMessage(IConnection, int)`

- Метод `beginFetchMessage(IConnection, int, AsyncCallback)`

- Метод `beginFetchMessage(IConnection, int, AsyncCallback, Object)`

- Метод `beginFetchMessage(IConnection, int, boolean)`

- Метод `beginFetchMessage(IConnection, int, boolean, AsyncCallback)`

- Метод `beginFetchMessage(IConnection, int, boolean, AsyncCallback, Object)`

- Метод `beginFetchMessage(IConnection, String)`

- Метод `beginFetchMessage(IConnection, String, AsyncCallback)`

- Метод `beginFetchMessage(IConnection, String, AsyncCallback, Object)`

- Метод `beginFetchMessage(int, AsyncCallback)`

- Метод `beginFetchMessage(int, boolean)`

- Метод `beginFetchMessage(int, boolean, AsyncCallback)`

- Метод `beginFetchMessage(int, boolean, AsyncCallback, Object)`

- Метод `beginFetchMessage(String, AsyncCallback)`

- Метод `beginGetFolderInfo(IConnection, String)`

- Метод `beginGetFolderInfo(IConnection, String, AsyncCallback)`

- Метод `beginGetFolderInfo(IConnection, String, AsyncCallback, Object)`

- Метод `beginGetFolderInfo(String)`

- Метод `beginGetFolderInfo(String, AsyncCallback)`

- Метод `beginGetFolderInfo(String, AsyncCallback, Object)`

- Метод `beginListFolders`

- Метод `beginListFolders(IConnection)`

- Метод `beginListFolders(IConnection, AsyncCallback)`

- Метод `beginListFolders(IConnection, AsyncCallback, Object)`

- Метод `beginListFolders(IConnection, boolean)`

- Метод `beginListFolders(IConnection, boolean, AsyncCallback)`

- Метод `beginListFolders(IConnection, boolean, AsyncCallback, Object)`

- Метод `beginListFolders(IConnection, String)`

- Метод `beginListFolders(IConnection, String, AsyncCallback)`

- Метод `beginListFolders(IConnection, String, AsyncCallback, Object)`

- Метод `beginListFolders(IConnection, String, boolean)`

- Метод `beginListFolders(IConnection, String, boolean, AsyncCallback)`

- Метод `beginListFolders(IConnection, String, boolean, AsyncCallback, Object)`

- Метод `beginListFolders(AsyncCallback)`

- Метод `beginListFolders(AsyncCallback, Object)`

- Метод `beginListFolders(boolean)`

- Метод `beginListFolders(boolean, AsyncCallback)`

- Метод `beginListFolders(boolean, AsyncCallback, Object)`

- Метод `beginListFolders(String)`

- Метод `beginListFolders(String, AsyncCallback)`

- Метод `beginListFolders(String, AsyncCallback, Object)`

- Метод `beginListFolders(String, boolean)`

- Метод `beginListFolders(String, boolean, AsyncCallback)`

- Метод `beginListFolders(String, boolean, AsyncCallback, Object)`

- Метод `beginListMessage(IConnection, int)`

- Метод `beginListMessage(IConnection, int, AsyncCallback)`

- Метод `beginListMessage(IConnection, int, AsyncCallback, Object)`

- Метод `beginListMessage(IConnection, String)`

- Метод `beginListMessage(IConnection, String, AsyncCallback)`

- Метод `beginListMessage(IConnection, String, AsyncCallback, Object)`

- Метод `beginListMessage(int, AsyncCallback)`

- Метод `beginListMessage(String)`

- Метод `beginListMessage(String, AsyncCallback)`

- Метод `beginListMessage(String, AsyncCallback, Object)`

- Метод `beginListMessages(AsyncCallback)`

- Метод `beginListMessages(String, MailQuery, int, AsyncCallback)`

- Метод `beginListMessages(String, AsyncCallback)`

- Метод `beginNoop`

- Метод `beginNoop(IConnection)`

- Метод `beginNoop(IConnection, AsyncCallback)`

- Метод `beginNoop(IConnection, AsyncCallback, Object)`

- Метод `beginNoop(AsyncCallback)`

- Метод `beginNoop(AsyncCallback, Object)`

- Метод `beginRemoveMessageFlags(IConnection, int, ImapMessageFlags)`

- Метод `beginRemoveMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback)`

- Метод `beginRemoveMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginRemoveMessageFlags(IConnection, String, ImapMessageFlags)`

- Метод `beginRemoveMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback)`

- Метод `beginRemoveMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginRemoveMessageFlags(int, ImapMessageFlags, AsyncCallback)`

- Метод `beginRemoveMessageFlags(String, ImapMessageFlags)`

- Метод `beginRemoveMessageFlags(String, ImapMessageFlags, AsyncCallback)`

- Метод `beginRemoveMessageFlags(String, ImapMessageFlags, AsyncCallback, Object)`

- Метод `beginRenameFolder(IConnection, String, String)`

- Метод `beginRenameFolder(IConnection, String, String, AsyncCallback)`

- Метод `beginRenameFolder(IConnection, String, String, AsyncCallback, Object)`

- Метод `beginRenameFolder(String, String, AsyncCallback)`

- Метод `beginRequestCheckpoint`

- Метод `beginRequestCheckpoint(IConnection)`

- Метод `beginRequestCheckpoint(IConnection, AsyncCallback)`

- Метод `beginRequestCheckpoint(IConnection, AsyncCallback, Object)`

- Метод `beginRequestCheckpoint(AsyncCallback)`

- Метод `beginRequestCheckpoint(AsyncCallback, Object)`

- Метод `beginRestore(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions)`

- Метод `beginRestore(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback, Object)`

- Метод `beginRestore(IConnection, ImapFolderInfoCollection, String, BackupOptions)`

- Метод `beginRestore(IConnection, ImapFolderInfoCollection, String, BackupOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, ImapFolderInfoCollection, String, BackupOptions, AsyncCallback, Object)`

- Метод `beginRestore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions)`

- Метод `beginRestore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(IConnection, PersonalStorage, RestoreOptions)`

- Метод `beginRestore(IConnection, PersonalStorage, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, PersonalStorage, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions)`

- Метод `beginRestore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(IConnection, OutputStream, RestoreOptions)`

- Метод `beginRestore(IConnection, OutputStream, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, OutputStream, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(IConnection, String, ImapFolderInfoCollection, RestoreOptions)`

- Метод `beginRestore(IConnection, String, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, String, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(IConnection, String, RestoreOptions)`

- Метод `beginRestore(IConnection, String, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(IConnection, String, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(ImapFolderInfoCollection, OutputStream, BackupOptions)`

- Метод `beginRestore(ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback)`

- Метод `beginRestore(ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback, Object)`

- Метод `beginRestore(ImapFolderInfoCollection, String, BackupOptions)`

- Метод `beginRestore(ImapFolderInfoCollection, String, BackupOptions, AsyncCallback)`

- Метод `beginRestore(ImapFolderInfoCollection, String, BackupOptions, AsyncCallback, Object)`

- Метод `beginRestore(PersonalStorage, ImapFolderInfoCollection, RestoreOptions)`

- Метод `beginRestore(PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(PersonalStorage, RestoreOptions)`

- Метод `beginRestore(PersonalStorage, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(PersonalStorage, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(OutputStream, ImapFolderInfoCollection, RestoreOptions)`

- Метод `beginRestore(OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(OutputStream, RestoreOptions)`

- Метод `beginRestore(OutputStream, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(OutputStream, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(String, ImapFolderInfoCollection, RestoreOptions)`

- Метод `beginRestore(String, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(String, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Метод `beginRestore(String, RestoreOptions)`

- Метод `beginRestore(String, RestoreOptions, AsyncCallback)`

- Метод `beginRestore(String, RestoreOptions, AsyncCallback, Object)`

- Метод `beginSaveMessage(IConnection, int, OutputStream)`

- Метод `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback)`

- Метод `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback, Object)`

- Метод `beginSaveMessage(IConnection, int, String)`

- Метод `beginSaveMessage(IConnection, int, String, AsyncCallback)`

- Метод `beginSaveMessage(IConnection, int, String, AsyncCallback, Object)`

- Метод `beginSaveMessage(IConnection, String, OutputStream)`

- Метод `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback)`

- Метод `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback, Object)`

- Метод `beginSaveMessage(IConnection, String, String)`

- Метод `beginSaveMessage(IConnection, String, String, AsyncCallback)`

- Метод `beginSaveMessage(IConnection, String, String, AsyncCallback, Object)`

- Метод `beginSaveMessage(int, OutputStream)`

- Метод `beginSaveMessage(int, OutputStream, AsyncCallback)`

- Метод `beginSaveMessage(int, OutputStream, AsyncCallback, Object)`

- Метод `beginSaveMessage(int, String)`

- Метод `beginSaveMessage(int, String, AsyncCallback)`

- Метод `beginSaveMessage(int, String, AsyncCallback, Object)`

- Метод `beginSaveMessage(String, OutputStream, AsyncCallback)`

- Метод `beginSaveMessage(String, String)`

- Метод `beginSaveMessage(String, String, AsyncCallback)`

- Метод `beginSaveMessage(String, String, AsyncCallback, Object)`

- Метод `beginSelectFolder(IConnection, String)`

- Метод `beginSelectFolder(IConnection, String, AsyncCallback)`

- Метод `beginSelectFolder(IConnection, String, AsyncCallback, Object)`

- Метод `beginSelectFolder(IConnection, String, boolean, AsyncCallback, Object)`

- Метод `beginSelectFolder(String, AsyncCallback)`

- Метод `beginSelectFolder(String, boolean, AsyncCallback, Object)`

- Метод `beginSendCustomCommand(IConnection, String)`

- Метод `beginSendCustomCommand(IConnection, String, AsyncCallback)`

- Метод `beginSendCustomCommand(IConnection, String, AsyncCallback, Object)`

- Метод `beginSendCustomCommand(IConnection, String, String)`

- Метод `beginSendCustomCommand(IConnection, String, String, AsyncCallback)`

- Метод `beginSendCustomCommand(IConnection, String, String, AsyncCallback, Object)`

- Метод `beginSendCustomCommand(String)`

- Метод `beginSendCustomCommand(String, AsyncCallback)`

- Метод `beginSendCustomCommand(String, AsyncCallback, Object)`

- Метод `beginSendCustomCommand(String, String)`

- Метод `beginSendCustomCommand(String, String, AsyncCallback)`

- Метод `beginSendCustomCommand(String, String, AsyncCallback, Object)`

- Метод `beginSubscribeFolder(IConnection, String)`

- Метод `beginSubscribeFolder(IConnection, String, AsyncCallback)`

- Метод `beginSubscribeFolder(IConnection, String, AsyncCallback, Object)`

- Метод `beginSubscribeFolder(String)`

- Метод `beginSubscribeFolder(String, AsyncCallback)`

- Метод `beginSubscribeFolder(String, AsyncCallback, Object)`

- Метод `beginUndeleteMessage(IConnection, int)`

- Метод `beginUndeleteMessage(IConnection, int, AsyncCallback)`

- Метод `beginUndeleteMessage(IConnection, int, AsyncCallback, Object)`

- Метод `beginUndeleteMessage(IConnection, String)`

- Метод `beginUndeleteMessage(IConnection, String, AsyncCallback)`

- Метод `beginUndeleteMessage(IConnection, String, AsyncCallback, Object)`

- Метод `beginUndeleteMessage(int, AsyncCallback)`

- Метод `beginUndeleteMessage(String)`

- Метод `beginUndeleteMessage(String, AsyncCallback)`

- Метод `beginUndeleteMessage(String, AsyncCallback, Object)`

- Метод `beginUnselectFolder`

- Метод `beginUnselectFolder(IConnection)`

- Метод `beginUnselectFolder(IConnection, AsyncCallback)`

- Метод `beginUnselectFolder(IConnection, AsyncCallback, Object)`

- Метод `beginUnselectFolder(AsyncCallback)`

- Метод `beginUnselectFolder(AsyncCallback, Object)`

- Метод `beginUnsubscribeFolder(IConnection, String)`

- Метод `beginUnsubscribeFolder(IConnection, String, AsyncCallback)`

- Метод `beginUnsubscribeFolder(IConnection, String, AsyncCallback, Object)`

- Метод `beginUnsubscribeFolder(String)`

- Метод `beginUnsubscribeFolder(String, AsyncCallback)`

- Метод `beginUnsubscribeFolder(String, AsyncCallback, Object)`

- Метод `changeMessageFlags(IConnection, int, ImapMessageFlags)`

- Метод `changeMessageFlags(IConnection, String, ImapMessageFlags)`

- Метод `commitDeletes(IConnection)`

- Метод `commitDeletes(IConnection, int)`

- Метод `copyMessage(IConnection, int, String)`

- Метод `copyMessage(IConnection, String, String)`

- Метод `createFolder(IConnection, String)`

- Метод `deleteFolder(IConnection, String)`

- Метод `deleteMessage(IConnection, int)`

- Метод `deleteMessage(IConnection, String)`

- Метод `endAppendMessage(IAsyncResult)`

- Метод `endBackup(IAsyncResult)`

- Метод `endCommitDeletes(IAsyncResult)`

- Метод `endExistFolder(IAsyncResult)`

- Метод `endExistFolder(IAsyncResult, ImapFolderInfo@)`

- Метод `endGetFolderInfo(IAsyncResult)`

- Метод `endListFolders(IAsyncResult)`

- Метод `endNoop(IAsyncResult)`

- Метод `endRequestCheckpoint(IAsyncResult)`

- Метод `endRestore(IAsyncResult)`

- Метод `endSendCustomCommand(IAsyncResult)`

- Метод `endSubscribeFolder(IAsyncResult)`

- Метод `endUnselectFolder(IAsyncResult)`

- Метод `endUnsubscribeFolder(IAsyncResult)`

- Метод `fetchAttachment(IConnection, int, String)`

- Метод `fetchMessage(IConnection, int)`

- Метод `fetchMessage(IConnection, int, boolean)`

- Метод `fetchMessage(IConnection, String)`

- Метод `getFolderInfo(IConnection, String)`

- Метод `listFolders(IConnection)`

- Метод `listFolders(IConnection, boolean)`

- Метод `listFolders(IConnection, String)`

- Метод `listFolders(IConnection, String, boolean)`

- Метод `listMessage(IConnection, int)`

- Метод `listMessage(IConnection, String)`

- Метод `listMessages(IConnection)`

- Метод `listMessages(IConnection, MailQuery)`

- Метод `listMessages(IConnection, MailQuery, int)`

- Метод `listMessages(IConnection, boolean)`

- Метод `listMessages(IConnection, int)`

- Метод `listMessages(IConnection, String)`

- Метод `listMessages(IConnection, String, MailQuery, int)`

- Метод `listMessages(IConnection, String, boolean)`

- Метод `listMessages(String, MailQuery, int)`

- Метод `noop`

- Метод `noop(IConnection)`

- Метод `parseQuery(ImapMessageInfo, MailQuery)`

- Метод `removeMessageFlags(IConnection, int, ImapMessageFlags)`

- Метод `removeMessageFlags(IConnection, String, ImapMessageFlags)`

- Метод `renameFolder(IConnection, String, String)`

- Метод `requestCheckpoint(IConnection)`

- Метод `restore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions)`

- Метод `restore(IConnection, PersonalStorage, RestoreOptions)`

- Метод `restore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions)`

- Метод `restore(IConnection, OutputStream, RestoreOptions)`

- Метод `restore(IConnection, String, ImapFolderInfoCollection, RestoreOptions)`

- Метод `restore(IConnection, String, RestoreOptions)`

- Метод `saveMessage(IConnection, int, OutputStream)`

- Метод `saveMessage(IConnection, int, String)`

- Метод `saveMessage(IConnection, String, OutputStream)`

- Метод `saveMessage(IConnection, String, String)`

- Метод `selectFolder(IConnection, String)`

- Метод `selectFolder(IConnection, String, boolean)`

- Метод `sendCustomCommand(IConnection, String)`

- Метод `sendCustomCommand(IConnection, String, String)`

- Метод `subscribeFolder(IConnection, String)`

- Метод `undeleteMessage(IConnection, int)`

- Метод `undeleteMessage(IConnection, String)`

- Метод `unselectFolder(IConnection)`

- Метод `unsubscribeFolder(IConnection, String)`

**`SmtpClient`:**

- Метод `forward(String, MailAddressCollection, MailMessage)`

- Метод `forward(String, String, MailMessage)`

**`Pop3Client`:**

- Метод `beginCommitDeletes`

- Метод `beginCommitDeletes(IConnection)`

- Метод `beginCommitDeletes(IConnection, AsyncCallback)`

- Метод `beginCommitDeletes(IConnection, AsyncCallback, Object)`

- Метод `beginCommitDeletes(AsyncCallback)`

- Метод `beginCommitDeletes(AsyncCallback, Object)`

- Метод `beginDeleteMessage(IConnection, int)`

- Метод `beginDeleteMessage(IConnection, int, AsyncCallback)`

- Метод `beginDeleteMessage(IConnection, int, AsyncCallback, Object)`

- Метод `beginDeleteMessage(IConnection, String)`

- Метод `beginDeleteMessage(IConnection, String, AsyncCallback)`

- Метод `beginDeleteMessage(IConnection, String, AsyncCallback, Object)`

- Метод `beginDeleteMessage(int, AsyncCallback)`

- Метод `beginDeleteMessage(String, AsyncCallback)`

- Метод `beginDeleteMessages`

- Метод `beginDeleteMessages(IConnection)`

- Метод `beginDeleteMessages(IConnection, AsyncCallback)`

- Метод `beginDeleteMessages(IConnection, AsyncCallback, Object)`

- Метод `beginDeleteMessages(AsyncCallback)`

- Метод `beginDeleteMessages(AsyncCallback, Object)`

- Метод `beginFetchMessage(IConnection, int)`

- Метод `beginFetchMessage(IConnection, int, AsyncCallback)`

- Метод `beginFetchMessage(IConnection, int, AsyncCallback, Object)`

- Метод `beginFetchMessage(IConnection, String)`

- Метод `beginFetchMessage(IConnection, String, AsyncCallback)`

- Метод `beginFetchMessage(IConnection, String, AsyncCallback, Object)`

- Метод `beginFetchMessage(int, AsyncCallback)`

- Метод `beginFetchMessage(String, AsyncCallback)`

- Метод `beginGetMailboxInfo`

- Метод `beginGetMailboxInfo(IConnection)`

- Метод `beginGetMailboxInfo(IConnection, AsyncCallback)`

- Метод `beginGetMailboxInfo(IConnection, AsyncCallback, Object)`

- Метод `beginGetMailboxInfo(AsyncCallback)`

- Метод `beginGetMailboxInfo(AsyncCallback, Object)`

- Метод `beginGetMailboxSize(IConnection)`

- Метод `beginGetMailboxSize(IConnection, AsyncCallback)`

- Метод `beginGetMailboxSize(IConnection, AsyncCallback, Object)`

- Метод `beginGetMailboxSize(AsyncCallback)`

- Метод `beginGetMessageCount(IConnection)`

- Метод `beginGetMessageCount(IConnection, AsyncCallback)`

- Метод `beginGetMessageCount(IConnection, AsyncCallback, Object)`

- Метод `beginGetMessageCount(IConnection, boolean)`

- Метод `beginGetMessageCount(IConnection, boolean, AsyncCallback)`

- Метод `beginGetMessageCount(IConnection, boolean, AsyncCallback, Object)`

- Метод `beginGetMessageCount(AsyncCallback)`

- Метод `beginGetMessageCount(boolean)`

- Метод `beginGetMessageCount(boolean, AsyncCallback)`

- Метод `beginGetMessageCount(boolean, AsyncCallback, Object)`

- Метод `beginGetMessageHeaders(IConnection, int)`

- Метод `beginGetMessageHeaders(IConnection, int, AsyncCallback)`

- Метод `beginGetMessageHeaders(IConnection, int, AsyncCallback, Object)`

- Метод `beginGetMessageHeaders(int, AsyncCallback)`

- Метод `beginGetMessageInfo(IConnection, int)`

- Метод `beginGetMessageInfo(IConnection, int, Pop3ListFields)`

- Метод `beginGetMessageInfo(IConnection, int, Pop3ListFields, AsyncCallback)`

- Метод `beginGetMessageInfo(IConnection, int, Pop3ListFields, AsyncCallback, Object)`

- Метод `beginGetMessageInfo(IConnection, int, AsyncCallback)`

- Метод `beginGetMessageInfo(IConnection, int, AsyncCallback, Object)`

- Метод `beginGetMessageInfo(int)`

- Метод `beginGetMessageInfo(int, Pop3ListFields)`

- Метод `beginGetMessageInfo(int, Pop3ListFields, AsyncCallback)`

- Метод `beginGetMessageInfo(int, Pop3ListFields, AsyncCallback, Object)`

- Метод `beginGetMessageInfo(int, AsyncCallback)`

- Метод `beginGetMessageInfo(int, AsyncCallback, Object)`

- Метод `beginGetMessageSize(IConnection, int)`

- Метод `beginGetMessageSize(IConnection, int, AsyncCallback)`

- Метод `beginGetMessageSize(IConnection, int, AsyncCallback, Object)`

- Метод `beginGetMessageSize(int)`

- Метод `beginGetMessageSize(int, AsyncCallback)`

- Метод `beginGetMessageSize(int, AsyncCallback, Object)`

- Метод `beginGetMessageUniqueId(IConnection, int)`

- Метод `beginGetMessageUniqueId(IConnection, int, AsyncCallback)`

- Метод `beginGetMessageUniqueId(IConnection, int, AsyncCallback, Object)`

- Метод `beginGetMessageUniqueId(int)`

- Метод `beginGetMessageUniqueId(int, AsyncCallback)`

- Метод `beginGetMessageUniqueId(int, AsyncCallback, Object)`

- Метод `beginListMessages(IConnection)`

- Метод `beginListMessages(IConnection, MailQuery)`

- Метод `beginListMessages(IConnection, MailQuery, AsyncCallback)`

- Метод `beginListMessages(IConnection, MailQuery, AsyncCallback, Object)`

- Метод `beginListMessages(IConnection, AsyncCallback)`

- Метод `beginListMessages(IConnection, AsyncCallback, Object)`

- Метод `beginListMessages(MailQuery, AsyncCallback)`

- Метод `beginListMessages(AsyncCallback)`

- Метод `beginNoop`

- Метод `beginNoop(IConnection)`

- Метод `beginNoop(IConnection, AsyncCallback)`

- Метод `beginNoop(IConnection, AsyncCallback, Object)`

- Метод `beginNoop(AsyncCallback)`

- Метод `beginNoop(AsyncCallback, Object)`

- Метод `beginSaveMessage(IConnection, int, OutputStream)`

- Метод `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback)`

- Метод `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback, Object)`

- Метод `beginSaveMessage(IConnection, String, OutputStream)`

- Метод `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback)`

- Метод `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback, Object)`

- Метод `beginSaveMessage(int, OutputStream, AsyncCallback)`

- Метод `beginSaveMessage(String, OutputStream, AsyncCallback)`

- Метод `beginUndeleteMessages(IConnection)`

- Метод `beginUndeleteMessages(IConnection, AsyncCallback)`

- Метод `beginUndeleteMessages(IConnection, AsyncCallback, Object)`

- Метод `beginUndeleteMessages(AsyncCallback)`

- Метод `commitDeletes(IConnection)`

- Метод `deleteMessage(IConnection, int)`

- Метод `deleteMessage(IConnection, String)`

- Метод `deleteMessages`

- Метод `deleteMessages(IConnection)`

- Метод `endCommitDeletes(IAsyncResult)`

- Метод `endDeleteMessages(IAsyncResult)`

- Метод `endGetMailboxInfo(IAsyncResult)`

- Метод `endGetMessageInfo(IAsyncResult)`

- Метод `endGetMessageSize(IAsyncResult)`

- Метод `endGetMessageUniqueId(IAsyncResult)`

- Метод `endNoop(IAsyncResult)`

- Метод `fetchMessage(IConnection, int)`

- Метод `fetchMessage(IConnection, String)`

- Метод `getMailboxInfo(IConnection)`

- Метод `getMailboxInfo(IConnection, boolean)`

- Метод `getMailboxInfo(boolean)`

- Метод `getMailboxSize(IConnection)`

- Метод `getMessageCount(IConnection)`

- Метод `getMessageCount(IConnection, boolean)`

- Метод `getMessageHeaders(IConnection, int)`

- Метод `getMessageInfo(IConnection, int)`

- Метод `getMessageInfo(IConnection, int, Pop3ListFields)`

- Метод `getMessageInfo(int)`

- Метод `getMessageInfo(int, Pop3ListFields)`

- Метод `getMessageSize(IConnection, int)`

- Метод `getMessageUniqueId(IConnection, int)`

- Метод `noop`

- Метод `noop(IConnection)`

- Метод `saveMessage(IConnection, int, OutputStream)`

- Метод `saveMessage(IConnection, int, String)`

- Метод `saveMessage(IConnection, String, OutputStream)`

- Метод `saveMessage(IConnection, String, String)`

- Метод `saveMessage(String, String)`

- Метод `undeleteMessages(IConnection)`