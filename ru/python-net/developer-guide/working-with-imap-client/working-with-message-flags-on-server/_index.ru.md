---
title: "Работа с флагами сообщений на сервере"
url: /ru/python-net/working-with-message-flags-on-server/
weight: 60
type: docs
---


## **Изменение флагов сообщений**
Вы можете изменить флаги сообщений с помощью метода changeMessageFlags (). Этот метод принимает два параметра.

1. Порядковый номер или уникальный идентификатор сообщения.
1. MessageFlag.

Можно установить следующие флаги:

- Answered
- Deleted
- Draft
- Empty
- Flagged
- IsRead
- Recent
### **Настройка флагов сообщений**
В следующем фрагменте кода показано, как изменить флаги сообщений на сервере IMAP с помощью Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SettingMessageFlags-SettingMessageFlags.py" >}}

### **Удаление флагов сообщений**

API также предоставляет метод remove_message_flags для [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс для удаления предопределенных системных флагов, таких как\ Seen (соответствует прочитанному сообщению),\ Answered (на сообщение получен ответ),\ Flagged (сообщение помечено как важное),\ Удалено (сообщение помечено как удаленное) и\ Draft (сообщение сохранено как черновик), а также настраиваемых флагов ключевых слов, определенных пользователями. Метод принимает следующие параметры: уникальный идентификатор (UID) или порядковый номер сообщения вместе с флагами, которые вы хотите удалить. В приведенном ниже примере кода показано, как удалить флаг is_read с помощью всего одной строки кода:

```py
# Remove the message flag
client.remove_message_flags(1, ae.clients.imap.ImapMessageFlags.is_read)
```
### **Настройка собственных флагов**
Вы также можете установить собственные флаги для сообщения, используя [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) API. Его метод add_message_flags позволяет устанавливать собственные флаги в сообщениях.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Create a message
message = ae.MailMessage("user@domain1.com", "user@domain2.com", "subject", "message")

# Append the message to mailbox
uid = client.append_message(ae.clients.imap.ImapFolderInfo.IN_BOX, message)

# Add custom flags to the added message
client.add_message_flags(uid, ae.clients.imap.ImapMessageFlags.keyword("custom1") | ae.clients.imap.ImapMessageFlags.keyword("custom1_0"))

# Retreive the messages for checking the presence of custom flag
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)

messageInfos = client.ListMessages()

for inf in messageInfos:
  flags = inf.flags.split()
  if inf.contains_keyword("custom1"):
        print("Keyword found")
```
