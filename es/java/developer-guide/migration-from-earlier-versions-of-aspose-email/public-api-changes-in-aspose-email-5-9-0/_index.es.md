---
title: "Cambios en la API pública en Aspose.Email 5.9.0"
url: /es/java/public-api-changes-in-aspose-email-5-9-0/
weight: 200
type: docs
---

La siguiente es una lista de cualquier cambio realizado en la API pública, como miembros añadidos, renombrados, eliminados o en desuso, así como cualquier cambio no compatible hacia atrás realizado en Aspose.Email para Java. Si tiene inquietudes sobre algún cambio listado, por favor, notifíquelo en el foro de soporte de Aspose.Email.

- Clase `MapiCalendarRecurrencePatternFactory`

- Método `MapiCalendarRecurrencePatternFactory.fromString(String)`

- Campo `MapiPropertyTag.PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE`

- Campo `MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME`

- Campo `MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY`

- Campo `MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ`

- Método `IEWSClient.appendMessage(MailMessage)`

- Interfaz `IConnection`

**`EWSClient`:**

- Método getEWSClient(ExchangeVersion, `boolean, String, String, ICredentials, WebProxy)`

- Método `getEWSClient(ExchangeVersion, String, ICredentials, WebProxy)`

**`ImapClient`:**

- Método `addMessageFlags(IConnection, int, ImapMessageFlags)`

- Método `addMessageFlags(IConnection, String, ImapMessageFlags)`

- Método `appendMessage(IConnection, MailMessage)`

- Método `appendMessage(IConnection, String)`

- Método `appendMessage(IConnection, String, MailMessage)`

- Método `appendMessage(IConnection, String, String)`

- Método `appendMessage(String)`

- Método `backup(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions)`

- Método `backup(IConnection, ImapFolderInfoCollection, String, BackupOptions)`

- Método `beginAddMessageFlags(IConnection, int, ImapMessageFlags)`

- Método `beginAddMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback)`

- Método `beginAddMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginAddMessageFlags(IConnection, String, ImapMessageFlags)`

- Método `beginAddMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback)`

- Método `beginAddMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginAddMessageFlags(int, ImapMessageFlags, AsyncCallback)`

- Método `beginAddMessageFlags(String, ImapMessageFlags)`

- Método `beginAddMessageFlags(String, ImapMessageFlags, AsyncCallback)`

- Método `beginAddMessageFlags(String, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginAppendMessage(IConnection, MailMessage)`

- Método `beginAppendMessage(IConnection, String)`

- Método `beginAppendMessage(IConnection, String, MailMessage)`

- Método `beginAppendMessage(IConnection, String, MailMessage, AsyncCallback)`

- Método `beginAppendMessage(IConnection, String, MailMessage, AsyncCallback, Object)`

- Método `beginAppendMessage(IConnection, String, String)`

- Método `beginAppendMessage(IConnection, String, String, AsyncCallback)`

- Método `beginAppendMessage(IConnection, String, String, AsyncCallback, Object)`

- Método `beginAppendMessage(MailMessage)`

- Método `beginAppendMessage(String)`

- Método `beginAppendMessage(String, MailMessage)`

- Método `beginAppendMessage(String, MailMessage, AsyncCallback)`

- Método `beginAppendMessage(String, MailMessage, AsyncCallback, Object)`

- Método `beginAppendMessage(String, String)`

- Método `beginAppendMessage(String, String, AsyncCallback)`

- Método `beginAppendMessage(String, String, AsyncCallback, Object)`

- Método `beginChangeMessageFlags(IConnection, int, ImapMessageFlags)`

- Método `beginChangeMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback)`

- Método `beginChangeMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginChangeMessageFlags(IConnection, String, ImapMessageFlags)`

- Método `beginChangeMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback)`

- Método `beginChangeMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginChangeMessageFlags(int, ImapMessageFlags, AsyncCallback)`

- Método `beginChangeMessageFlags(String, ImapMessageFlags)`

- Método `beginChangeMessageFlags(String, ImapMessageFlags, AsyncCallback)`

- Método `beginChangeMessageFlags(String, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginCommitDeletes`

- Método `beginCommitDeletes(IConnection)`

- Método `beginCommitDeletes(IConnection, AsyncCallback)`

- Método `beginCommitDeletes(IConnection, AsyncCallback, Object)`

- Método `beginCommitDeletes(IConnection, int)`

- Método `beginCommitDeletes(IConnection, int, AsyncCallback, Object)`

- Método `beginCommitDeletes(AsyncCallback)`

- Método `beginCommitDeletes(AsyncCallback, Object)`

- Método `beginCommitDeletes(int)`

- Método `beginCommitDeletes(int, AsyncCallback, Object)`

- Método `beginCopyMessage(IConnection, int, String)`

- Método `beginCopyMessage(IConnection, int, String, AsyncCallback)`

- Método `beginCopyMessage(IConnection, int, String, AsyncCallback, Object)`

- Método `beginCopyMessage(IConnection, String, String)`

- Método `beginCopyMessage(IConnection, String, String, AsyncCallback)`

- Método `beginCopyMessage(IConnection, String, String, AsyncCallback, Object)`

- Método `beginCopyMessage(int, String, AsyncCallback)`

- Método `beginCopyMessage(String, String, AsyncCallback)`

- Método `beginCreateFolder(IConnection, String)`

- Método `beginCreateFolder(IConnection, String, AsyncCallback)`

- Método `beginCreateFolder(IConnection, String, AsyncCallback, Object)`

- Método `beginCreateFolder(String, AsyncCallback)`

- Método `beginDeleteFolder(IConnection, String)`

- Método `beginDeleteFolder(IConnection, String, AsyncCallback)`

- Método `beginDeleteFolder(IConnection, String, AsyncCallback, Object)`

- Método `beginDeleteFolder(String, AsyncCallback)`

- Método `beginDeleteMessage(IConnection, int)`

- Método `beginDeleteMessage(IConnection, int, AsyncCallback)`

- Método `beginDeleteMessage(IConnection, int, AsyncCallback, Object)`

- Método `beginDeleteMessage(IConnection, String)`

- Método `beginDeleteMessage(IConnection, String, AsyncCallback)`

- Método `beginDeleteMessage(IConnection, String, AsyncCallback, Object)`

- Método `beginDeleteMessage(int, AsyncCallback)`

- Método `beginDeleteMessage(String, AsyncCallback)`

- Método `beginFetchAttachment(IConnection, int, String)`

- Método `beginFetchAttachment(IConnection, int, String, AsyncCallback)`

- Método `beginFetchAttachment(IConnection, int, String, AsyncCallback, Object)`

- Método `beginFetchAttachment(int, String, AsyncCallback)`

- Método `beginFetchMessage(IConnection, int)`

- Método `beginFetchMessage(IConnection, int, AsyncCallback)`

- Método `beginFetchMessage(IConnection, int, AsyncCallback, Object)`

- Método `beginFetchMessage(IConnection, int, boolean)`

- Método `beginFetchMessage(IConnection, int, boolean, AsyncCallback)`

- Método `beginFetchMessage(IConnection, int, boolean, AsyncCallback, Object)`

- Método `beginFetchMessage(IConnection, String)`

- Método `beginFetchMessage(IConnection, String, AsyncCallback)`

- Método `beginFetchMessage(IConnection, String, AsyncCallback, Object)`

- Método `beginFetchMessage(int, AsyncCallback)`

- Método `beginFetchMessage(int, boolean)`

- Método `beginFetchMessage(int, boolean, AsyncCallback)`

- Método `beginFetchMessage(int, boolean, AsyncCallback, Object)`

- Método `beginFetchMessage(String, AsyncCallback)`

- Método `beginGetFolderInfo(IConnection, String)`

- Método `beginGetFolderInfo(IConnection, String, AsyncCallback)`

- Método `beginGetFolderInfo(IConnection, String, AsyncCallback, Object)`

- Método `beginGetFolderInfo(String)`

- Método `beginGetFolderInfo(String, AsyncCallback)`

- Método `beginGetFolderInfo(String, AsyncCallback, Object)`

- Método `beginListFolders`

- Método `beginListFolders(IConnection)`

- Método `beginListFolders(IConnection, AsyncCallback)`

- Método `beginListFolders(IConnection, AsyncCallback, Object)`

- Método `beginListFolders(IConnection, boolean)`

- Método `beginListFolders(IConnection, boolean, AsyncCallback)`

- Método `beginListFolders(IConnection, boolean, AsyncCallback, Object)`

- Método `beginListFolders(IConnection, String)`

- Método `beginListFolders(IConnection, String, AsyncCallback)`

- Método `beginListFolders(IConnection, String, AsyncCallback, Object)`

- Método `beginListFolders(IConnection, String, boolean)`

- Método `beginListFolders(IConnection, String, boolean, AsyncCallback)`

- Método `beginListFolders(IConnection, String, boolean, AsyncCallback, Object)`

- Método `beginListFolders(AsyncCallback)`

- Método `beginListFolders(AsyncCallback, Object)`

- Método `beginListFolders(boolean)`

- Método `beginListFolders(boolean, AsyncCallback)`

- Método `beginListFolders(boolean, AsyncCallback, Object)`

- Método `beginListFolders(String)`

- Método `beginListFolders(String, AsyncCallback)`

- Método `beginListFolders(String, AsyncCallback, Object)`

- Método `beginListFolders(String, boolean)`

- Método `beginListFolders(String, boolean, AsyncCallback)`

- Método `beginListFolders(String, boolean, AsyncCallback, Object)`

- Método `beginListMessage(IConnection, int)`

- Método `beginListMessage(IConnection, int, AsyncCallback)`

- Método `beginListMessage(IConnection, int, AsyncCallback, Object)`

- Método `beginListMessage(IConnection, String)`

- Método `beginListMessage(IConnection, String, AsyncCallback)`

- Método `beginListMessage(IConnection, String, AsyncCallback, Object)`

- Método `beginListMessage(int, AsyncCallback)`

- Método `beginListMessage(String)`

- Método `beginListMessage(String, AsyncCallback)`

- Método `beginListMessage(String, AsyncCallback, Object)`

- Método `beginListMessages(AsyncCallback)`

- Método `beginListMessages(String, MailQuery, int, AsyncCallback)`

- Método `beginListMessages(String, AsyncCallback)`

- Método `beginNoop`

- Método `beginNoop(IConnection)`

- Método `beginNoop(IConnection, AsyncCallback)`

- Método `beginNoop(IConnection, AsyncCallback, Object)`

- Método `beginNoop(AsyncCallback)`

- Método `beginNoop(AsyncCallback, Object)`

- Método `beginRemoveMessageFlags(IConnection, int, ImapMessageFlags)`

- Método `beginRemoveMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback)`

- Método `beginRemoveMessageFlags(IConnection, int, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginRemoveMessageFlags(IConnection, String, ImapMessageFlags)`

- Método `beginRemoveMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback)`

- Método `beginRemoveMessageFlags(IConnection, String, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginRemoveMessageFlags(int, ImapMessageFlags, AsyncCallback)`

- Método `beginRemoveMessageFlags(String, ImapMessageFlags)`

- Método `beginRemoveMessageFlags(String, ImapMessageFlags, AsyncCallback)`

- Método `beginRemoveMessageFlags(String, ImapMessageFlags, AsyncCallback, Object)`

- Método `beginRenameFolder(IConnection, String, String)`

- Método `beginRenameFolder(IConnection, String, String, AsyncCallback)`

- Método `beginRenameFolder(IConnection, String, String, AsyncCallback, Object)`

- Método `beginRenameFolder(String, String, AsyncCallback)`

- Método `beginRequestCheckpoint`

- Método `beginRequestCheckpoint(IConnection)`

- Método `beginRequestCheckpoint(IConnection, AsyncCallback)`

- Método `beginRequestCheckpoint(IConnection, AsyncCallback, Object)`

- Método `beginRequestCheckpoint(AsyncCallback)`

- Método `beginRequestCheckpoint(AsyncCallback, Object)`

- Método `beginRestore(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions)`

- Método `beginRestore(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback)`

- Método `beginRestore(IConnection, ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback, Object)`

- Método `beginRestore(IConnection, ImapFolderInfoCollection, String, BackupOptions)`

- Método `beginRestore(IConnection, ImapFolderInfoCollection, String, BackupOptions, AsyncCallback)`

- Método `beginRestore(IConnection, ImapFolderInfoCollection, String, BackupOptions, AsyncCallback, Object)`

- Método `beginRestore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions)`

- Método `beginRestore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Método `beginRestore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(IConnection, PersonalStorage, RestoreOptions)`

- Método `beginRestore(IConnection, PersonalStorage, RestoreOptions, AsyncCallback)`

- Método `beginRestore(IConnection, PersonalStorage, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions)`

- Método `beginRestore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Método `beginRestore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(IConnection, OutputStream, RestoreOptions)`

- Método `beginRestore(IConnection, OutputStream, RestoreOptions, AsyncCallback)`

- Método `beginRestore(IConnection, OutputStream, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(IConnection, String, ImapFolderInfoCollection, RestoreOptions)`

- Método `beginRestore(IConnection, String, ImapFolderInfoCollection, RestoreOptions,
  AsyncCallback)`

- Método `beginRestore(IConnection, String, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(IConnection, String, RestoreOptions)`

- Método `beginRestore(IConnection, String, RestoreOptions, AsyncCallback)`

- Método `beginRestore(IConnection, String, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(ImapFolderInfoCollection, OutputStream, BackupOptions)`

- Método `beginRestore(ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback)`

- Método `beginRestore(ImapFolderInfoCollection, OutputStream, BackupOptions, AsyncCallback,
  Object)`

- Método `beginRestore(ImapFolderInfoCollection, String, BackupOptions)`

- Método `beginRestore(ImapFolderInfoCollection, String, BackupOptions, AsyncCallback)`

- Método `beginRestore(ImapFolderInfoCollection, String, BackupOptions, AsyncCallback, Object)`

- Método `beginRestore(PersonalStorage, ImapFolderInfoCollection, RestoreOptions)`

- Método `beginRestore(PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Método `beginRestore(PersonalStorage, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(PersonalStorage, RestoreOptions)`

- Método `beginRestore(PersonalStorage, RestoreOptions, AsyncCallback)`

- Método `beginRestore(PersonalStorage, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(OutputStream, ImapFolderInfoCollection, RestoreOptions)`

- Método `beginRestore(OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Método `beginRestore(OutputStream, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(OutputStream, RestoreOptions)`

- Método `beginRestore(OutputStream, RestoreOptions, AsyncCallback)`

- Método `beginRestore(OutputStream, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(String, ImapFolderInfoCollection, RestoreOptions)`

- Método `beginRestore(String, ImapFolderInfoCollection, RestoreOptions, AsyncCallback)`

- Método `beginRestore(String, ImapFolderInfoCollection, RestoreOptions, AsyncCallback, Object)`

- Método `beginRestore(String, RestoreOptions)`

- Método `beginRestore(String, RestoreOptions, AsyncCallback)`

- Método `beginRestore(String, RestoreOptions, AsyncCallback, Object)`

- Método `beginSaveMessage(IConnection, int, OutputStream)`

- Método `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback)`

- Método `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback, Object)`

- Método `beginSaveMessage(IConnection, int, String)`

- Método `beginSaveMessage(IConnection, int, String, AsyncCallback)`

- Método `beginSaveMessage(IConnection, int, String, AsyncCallback, Object)`

- Método `beginSaveMessage(IConnection, String, OutputStream)`

- Método `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback)`

- Método `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback, Object)`

- Método `beginSaveMessage(IConnection, String, String)`

- Método `beginSaveMessage(IConnection, String, String, AsyncCallback)`

- Método `beginSaveMessage(IConnection, String, String, AsyncCallback, Object)`

- Método `beginSaveMessage(int, OutputStream)`

- Método `beginSaveMessage(int, OutputStream, AsyncCallback)`

- Método `beginSaveMessage(int, OutputStream, AsyncCallback, Object)`

- Método `beginSaveMessage(int, String)`

- Método `beginSaveMessage(int, String, AsyncCallback)`

- Método `beginSaveMessage(int, String, AsyncCallback, Object)`

- Método `beginSaveMessage(String, OutputStream, AsyncCallback)`

- Método `beginSaveMessage(String, String)`

- Método `beginSaveMessage(String, String, AsyncCallback)`

- Método `beginSaveMessage(String, String, AsyncCallback, Object)`

- Método `beginSelectFolder(IConnection, String)`

- Método `beginSelectFolder(IConnection, String, AsyncCallback)`

- Método `beginSelectFolder(IConnection, String, AsyncCallback, Object)`

- Método `beginSelectFolder(IConnection, String, boolean, AsyncCallback, Object)`

- Método `beginSelectFolder(String, AsyncCallback)`

- Método `beginSelectFolder(String, boolean, AsyncCallback, Object)`

- Método `beginSendCustomCommand(IConnection, String)`

- Método `beginSendCustomCommand(IConnection, String, AsyncCallback)`

- Método `beginSendCustomCommand(IConnection, String, AsyncCallback, Object)`

- Método `beginSendCustomCommand(IConnection, String, String)`

- Método `beginSendCustomCommand(IConnection, String, String, AsyncCallback)`

- Método `beginSendCustomCommand(IConnection, String, String, AsyncCallback, Object)`

- Método `beginSendCustomCommand(String)`

- Método `beginSendCustomCommand(String, AsyncCallback)`

- Método `beginSendCustomCommand(String, AsyncCallback, Object)`

- Método `beginSendCustomCommand(String, String)`

- Método `beginSendCustomCommand(String, String, AsyncCallback)`

- Método `beginSendCustomCommand(String, String, AsyncCallback, Object)`

- Método `beginSubscribeFolder(IConnection, String)`

- Método `beginSubscribeFolder(IConnection, String, AsyncCallback)`

- Método `beginSubscribeFolder(IConnection, String, AsyncCallback, Object)`

- Método `beginSubscribeFolder(String)`

- Método `beginSubscribeFolder(String, AsyncCallback)`

- Método `beginSubscribeFolder(String, AsyncCallback, Object)`

- Método `beginUndeleteMessage(IConnection, int)`

- Método `beginUndeleteMessage(IConnection, int, AsyncCallback)`

- Método `beginUndeleteMessage(IConnection, int, AsyncCallback, Object)`

- Método `beginUndeleteMessage(IConnection, String)`

- Método `beginUndeleteMessage(IConnection, String, AsyncCallback)`

- Método `beginUndeleteMessage(IConnection, String, AsyncCallback, Object)`

- Método `beginUndeleteMessage(int, AsyncCallback)`

- Método `beginUndeleteMessage(String)`

- Método `beginUndeleteMessage(String, AsyncCallback)`

- Método `beginUndeleteMessage(String, AsyncCallback, Object)`

- Método `beginUnselectFolder`

- Método `beginUnselectFolder(IConnection)`

- Método `beginUnselectFolder(IConnection, AsyncCallback)`

- Método `beginUnselectFolder(IConnection, AsyncCallback, Object)`

- Método `beginUnselectFolder(AsyncCallback)`

- Método `beginUnselectFolder(AsyncCallback, Object)`

- Método `beginUnsubscribeFolder(IConnection, String)`

- Método `beginUnsubscribeFolder(IConnection, String, AsyncCallback)`

- Método `beginUnsubscribeFolder(IConnection, String, AsyncCallback, Object)`

- Método `beginUnsubscribeFolder(String)`

- Método `beginUnsubscribeFolder(String, AsyncCallback)`

- Método `beginUnsubscribeFolder(String, AsyncCallback, Object)`

- Método `changeMessageFlags(IConnection, int, ImapMessageFlags)`

- Método `changeMessageFlags(IConnection, String, ImapMessageFlags)`

- Método `commitDeletes(IConnection)`

- Método `commitDeletes(IConnection, int)`

- Método `copyMessage(IConnection, int, String)`

- Método `copyMessage(IConnection, String, String)`

- Método `createFolder(IConnection, String)`

- Método `deleteFolder(IConnection, String)`

- Método `deleteMessage(IConnection, int)`

- Método `deleteMessage(IConnection, String)`

- Método `endAppendMessage(IAsyncResult)`

- Método `endBackup(IAsyncResult)`

- Método `endCommitDeletes(IAsyncResult)`

- Método `endExistFolder(IAsyncResult)`

- Método `endExistFolder(IAsyncResult, ImapFolderInfo@)`

- Método `endGetFolderInfo(IAsyncResult)`

- Método `endListFolders(IAsyncResult)`

- Método `endNoop(IAsyncResult)`

- Método `endRequestCheckpoint(IAsyncResult)`

- Método `endRestore(IAsyncResult)`

- Método `endSendCustomCommand(IAsyncResult)`

- Método `endSubscribeFolder(IAsyncResult)`

- Método `endUnselectFolder(IAsyncResult)`

- Método `endUnsubscribeFolder(IAsyncResult)`

- Método `fetchAttachment(IConnection, int, String)`

- Método `fetchMessage(IConnection, int)`

- Método `fetchMessage(IConnection, int, boolean)`

- Método `fetchMessage(IConnection, String)`

- Método `getFolderInfo(IConnection, String)`

- Método `listFolders(IConnection)`

- Método `listFolders(IConnection, boolean)`

- Método `listFolders(IConnection, String)`

- Método `listFolders(IConnection, String, boolean)`

- Método `listMessage(IConnection, int)`

- Método `listMessage(IConnection, String)`

- Método `listMessages(IConnection)`

- Método `listMessages(IConnection, MailQuery)`

- Método `listMessages(IConnection, MailQuery, int)`

- Método `listMessages(IConnection, boolean)`

- Método `listMessages(IConnection, int)`

- Método `listMessages(IConnection, String)`

- Método `listMessages(IConnection, String, MailQuery, int)`

- Método `listMessages(IConnection, String, boolean)`

- Método `listMessages(String, MailQuery, int)`

- Método `noop`

- Método `noop(IConnection)`

- Método `parseQuery(ImapMessageInfo, MailQuery)`

- Método `removeMessageFlags(IConnection, int, ImapMessageFlags)`

- Método `removeMessageFlags(IConnection, String, ImapMessageFlags)`

- Método `renameFolder(IConnection, String, String)`

- Método `requestCheckpoint(IConnection)`

- Método `restore(IConnection, PersonalStorage, ImapFolderInfoCollection, RestoreOptions)`

- Método `restore(IConnection, PersonalStorage, RestoreOptions)`

- Método `restore(IConnection, OutputStream, ImapFolderInfoCollection, RestoreOptions)`

- Método `restore(IConnection, OutputStream, RestoreOptions)`

- Método `restore(IConnection, String, ImapFolderInfoCollection, RestoreOptions)`

- Método `restore(IConnection, String, RestoreOptions)`

- Método `saveMessage(IConnection, int, OutputStream)`

- Método `saveMessage(IConnection, int, String)`

- Método `saveMessage(IConnection, String, OutputStream)`

- Método `saveMessage(IConnection, String, String)`

- Método `selectFolder(IConnection, String)`

- Método `selectFolder(IConnection, String, boolean)`

- Método `sendCustomCommand(IConnection, String)`

- Método `sendCustomCommand(IConnection, String, String)`

- Método `subscribeFolder(IConnection, String)`

- Método `undeleteMessage(IConnection, int)`

- Método `undeleteMessage(IConnection, String)`

- Método `unselectFolder(IConnection)`

- Método `unsubscribeFolder(IConnection, String)`

**`SmtpClient`:**

- Método `forward(String, MailAddressCollection, MailMessage)`

- Método `forward(String, String, MailMessage)`

**`Pop3Client`:**

- Método `beginCommitDeletes`

- Método `beginCommitDeletes(IConnection)`

- Método `beginCommitDeletes(IConnection, AsyncCallback)`

- Método `beginCommitDeletes(IConnection, AsyncCallback, Object)`

- Método `beginCommitDeletes(AsyncCallback)`

- Método `beginCommitDeletes(AsyncCallback, Object)`

- Método `beginDeleteMessage(IConnection, int)`

- Método `beginDeleteMessage(IConnection, int, AsyncCallback)`

- Método `beginDeleteMessage(IConnection, int, AsyncCallback, Object)`

- Método `beginDeleteMessage(IConnection, String)`

- Método `beginDeleteMessage(IConnection, String, AsyncCallback)`

- Método `beginDeleteMessage(IConnection, String, AsyncCallback, Object)`

- Método `beginDeleteMessage(int, AsyncCallback)`

- Método `beginDeleteMessage(String, AsyncCallback)`

- Método `beginDeleteMessages`

- Método `beginDeleteMessages(IConnection)`

- Método `beginDeleteMessages(IConnection, AsyncCallback)`

- Método `beginDeleteMessages(IConnection, AsyncCallback, Object)`

- Método `beginDeleteMessages(AsyncCallback)`

- Método `beginDeleteMessages(AsyncCallback, Object)`

- Método `beginFetchMessage(IConnection, int)`

- Método `beginFetchMessage(IConnection, int, AsyncCallback)`

- Método `beginFetchMessage(IConnection, int, AsyncCallback, Object)`

- Método `beginFetchMessage(IConnection, String)`

- Método `beginFetchMessage(IConnection, String, AsyncCallback)`

- Método `beginFetchMessage(IConnection, String, AsyncCallback, Object)`

- Método `beginFetchMessage(int, AsyncCallback)`

- Método `beginFetchMessage(String, AsyncCallback)`

- Método `beginGetMailboxInfo`

- Método `beginGetMailboxInfo(IConnection)`

- Método `beginGetMailboxInfo(IConnection, AsyncCallback)`

- Método `beginGetMailboxInfo(IConnection, AsyncCallback, Object)`

- Método `beginGetMailboxInfo(AsyncCallback)`

- Método `beginGetMailboxInfo(AsyncCallback, Object)`

- Método `beginGetMailboxSize(IConnection)`

- Método `beginGetMailboxSize(IConnection, AsyncCallback)`

- Método `beginGetMailboxSize(IConnection, AsyncCallback, Object)`

- Método `beginGetMailboxSize(AsyncCallback)`

- Método `beginGetMessageCount(IConnection)`

- Método `beginGetMessageCount(IConnection, AsyncCallback)`

- Método `beginGetMessageCount(IConnection, AsyncCallback, Object)`

- Método `beginGetMessageCount(IConnection, boolean)`

- Método `beginGetMessageCount(IConnection, boolean, AsyncCallback)`

- Método `beginGetMessageCount(IConnection, boolean, AsyncCallback, Object)`

- Método `beginGetMessageCount(AsyncCallback)`

- Método `beginGetMessageCount(boolean)`

- Método `beginGetMessageCount(boolean, AsyncCallback)`

- Método `beginGetMessageCount(boolean, AsyncCallback, Object)`

- Método `beginGetMessageHeaders(IConnection, int)`

- Método `beginGetMessageHeaders(IConnection, int, AsyncCallback)`

- Método `beginGetMessageHeaders(IConnection, int, AsyncCallback, Object)`

- Método `beginGetMessageHeaders(int, AsyncCallback)`

- Método `beginGetMessageInfo(IConnection, int)`

- Método `beginGetMessageInfo(IConnection, int, Pop3ListFields)`

- Método `beginGetMessageInfo(IConnection, int, Pop3ListFields, AsyncCallback)`

- Método `beginGetMessageInfo(IConnection, int, Pop3ListFields, AsyncCallback, Object)`

- Método `beginGetMessageInfo(IConnection, int, AsyncCallback)`

- Método `beginGetMessageInfo(IConnection, int, AsyncCallback, Object)`

- Método `beginGetMessageInfo(int)`

- Método `beginGetMessageInfo(int, Pop3ListFields)`

- Método `beginGetMessageInfo(int, Pop3ListFields, AsyncCallback)`

- Método `beginGetMessageInfo(int, Pop3ListFields, AsyncCallback, Object)`

- Método `beginGetMessageInfo(int, AsyncCallback)`

- Método `beginGetMessageInfo(int, AsyncCallback, Object)`

- Método `beginGetMessageSize(IConnection, int)`

- Método `beginGetMessageSize(IConnection, int, AsyncCallback)`

- Método `beginGetMessageSize(IConnection, int, AsyncCallback, Object)`

- Método `beginGetMessageSize(int)`

- Método `beginGetMessageSize(int, AsyncCallback)`

- Método `beginGetMessageSize(int, AsyncCallback, Object)`

- Método `beginGetMessageUniqueId(IConnection, int)`

- Método `beginGetMessageUniqueId(IConnection, int, AsyncCallback)`

- Método `beginGetMessageUniqueId(IConnection, int, AsyncCallback, Object)`

- Método `beginGetMessageUniqueId(int)`

- Método `beginGetMessageUniqueId(int, AsyncCallback)`

- Método `beginGetMessageUniqueId(int, AsyncCallback, Object)`

- Método `beginListMessages(IConnection)`

- Método `beginListMessages(IConnection, MailQuery)`

- Método `beginListMessages(IConnection, MailQuery, AsyncCallback)`

- Método `beginListMessages(IConnection, MailQuery, AsyncCallback, Object)`

- Método `beginListMessages(IConnection, AsyncCallback)`

- Método `beginListMessages(IConnection, AsyncCallback, Object)`

- Método `beginListMessages(MailQuery, AsyncCallback)`

- Método `beginListMessages(AsyncCallback)`

- Método `beginNoop`

- Método `beginNoop(IConnection)`

- Método `beginNoop(IConnection, AsyncCallback)`

- Método `beginNoop(IConnection, AsyncCallback, Object)`

- Método `beginNoop(AsyncCallback)`

- Método `beginNoop(AsyncCallback, Object)`

- Método `beginSaveMessage(IConnection, int, OutputStream)`

- Método `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback)`

- Método `beginSaveMessage(IConnection, int, OutputStream, AsyncCallback, Object)`

- Método `beginSaveMessage(IConnection, String, OutputStream)`

- Método `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback)`

- Método `beginSaveMessage(IConnection, String, OutputStream, AsyncCallback, Object)`

- Método `beginSaveMessage(int, OutputStream, AsyncCallback)`

- Método `beginSaveMessage(String, OutputStream, AsyncCallback)`

- Método `beginUndeleteMessages(IConnection)`

- Método `beginUndeleteMessages(IConnection, AsyncCallback)`

- Método `beginUndeleteMessages(IConnection, AsyncCallback, Object)`

- Método `beginUndeleteMessages(AsyncCallback)`

- Método `commitDeletes(IConnection)`

- Método `deleteMessage(IConnection, int)`

- Método `deleteMessage(IConnection, String)`

- Método `deleteMessages`

- Método `deleteMessages(IConnection)`

- Método `endCommitDeletes(IAsyncResult)`

- Método `endDeleteMessages(IAsyncResult)`

- Método `endGetMailboxInfo(IAsyncResult)`

- Método `endGetMessageInfo(IAsyncResult)`

- Método `endGetMessageSize(IAsyncResult)`

- Método `endGetMessageUniqueId(IAsyncResult)`

- Método `endNoop(IAsyncResult)`

- Método `fetchMessage(IConnection, int)`

- Método `fetchMessage(IConnection, String)`

- Método `getMailboxInfo(IConnection)`

- Método `getMailboxInfo(IConnection, boolean)`

- Método `getMailboxInfo(boolean)`

- Método `getMailboxSize(IConnection)`

- Método `getMessageCount(IConnection)`

- Método `getMessageCount(IConnection, boolean)`

- Método `getMessageHeaders(IConnection, int)`

- Método `getMessageInfo(IConnection, int)`

- Método `getMessageInfo(IConnection, int, Pop3ListFields)`

- Método `getMessageInfo(int)`

- Método `getMessageInfo(int, Pop3ListFields)`

- Método `getMessageSize(IConnection, int)`

- Método `getMessageUniqueId(IConnection, int)`

- Método `noop`

- Método `noop(IConnection)`

- Método `saveMessage(IConnection, int, OutputStream)`

- Método `saveMessage(IConnection, int, String)`

- Método `saveMessage(IConnection, String, OutputStream)`

- Método `saveMessage(IConnection, String, String)`

- Método `saveMessage(String, String)`

- Método `undeleteMessages(IConnection)`