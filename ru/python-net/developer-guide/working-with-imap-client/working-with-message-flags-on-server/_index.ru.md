---
title: "Работа с флагами сообщений на сервере"
url: /ru/python-net/working-with-message-flags-on-server/
weight: 60
type: docs
---


## **Изменение флагов сообщений**
Вы можете изменять флаги сообщений, используя метод ChangeMessageFlags(). Этот метод принимает два параметра.

1. Последовательный номер сообщения или уникальный идентификатор.
1. MessageFlag.

Следующие флаги могут быть установлены:

- Ответлено
- Удалено
- Черновик
- Пусто
- Помечено
- Прочитано
- Недавнее
### **Установка флагов сообщений**
Следующий код показывает, как изменить флаги сообщений на IMAP-сервере с помощью Aspose.Email.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SettingMessageFlags-SettingMessageFlags.py" >}}

### **Удаление флагов сообщений**

API также предоставляет метод 'remove_message_flags' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) для удаления предопределенных системных флагов, таких как \Seen (что соответствует прочитанному сообщению), \Answered (на сообщение был дан ответ), \Flagged (сообщение помечено как важное), \Deleted (сообщение помечено для удаления) и \Draft (сообщение сохранено как черновик), а также пользовательских флагов ключевых слов, определенных пользователями. Метод принимает следующие параметры: уникальный идентификатор (UID) или последовательный номер сообщения вместе с флагами, которые вы хотите удалить. Пример кода ниже демонстрирует, как удалить флаг 'is_read' всего лишь одной строкой кода:

```py
# Удалить флаг сообщения
client.remove_message_flags(1, ae.clients.imap.ImapMessageFlags.is_read)
```
### **Установка пользовательских флагов**
Вы также можете установить пользовательские флаги для сообщения с помощью [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) API. Метод 'add_message_flags' предоставляет возможность установки пользовательских флагов на сообщения.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Создать сообщение
message = ae.MailMessage("user@domain1.com", "user@domain2.com", "subject", "message")

# Добавить сообщение в почтовый ящик
uid = client.append_message(ae.clients.imap.ImapFolderInfo.IN_BOX, message)

# Добавить пользовательские флаги к добавленному сообщению
client.add_message_flags(uid, ae.clients.imap.ImapMessageFlags.keyword("custom1") | ae.clients.imap.ImapMessageFlags.keyword("custom1_0"))

# Получить сообщения для проверки наличия пользовательского флага
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)

messageInfos = client.ListMessages()

for inf in messageInfos:
  flags = inf.flags.split()
  if inf.contains_keyword("custom1"):
        print("Ключевое слово найдено")
```