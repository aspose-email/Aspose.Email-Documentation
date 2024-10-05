---
title: "Операция резервного копирования и восстановления IMAP на Python"
url: /ru/python-net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email для Python предлагает следующие методы класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) для резервного копирования и восстановления сообщений:

- Метод **'backup'**
- Метод **'restore'**

В этой статье показано, как резервировать и восстанавливать сообщения с использованием класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class).

## **Резервное копирование сообщений**

Пример кода ниже демонстрирует, как реализовать возможность резервного копирования в вашем проекте с использованием метода 'backup' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

# Создайте экземпляр класса ImapClient
imap_client = ae.clients.imap.ImapClient()

# Укажите хост, имя пользователя, пароль и задайте порт для вашего клиента
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.AUTO

# Получите информацию о почтовом ящике
mailbox_info = imap_client.mailbox_info

# Получите информацию о папке входящих
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Создайте ImapFolderInfoCollection и добавьте информацию о папке входящих
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Укажите путь к каталогу
data_dir = "path/to/your/data/directory"

# Выполните операцию резервного копирования
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

## **Восстановление сообщений**

Пример кода ниже демонстрирует, как реализовать возможность восстановления в вашем проекте с использованием метода 'restore' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

# Создайте экземпляр класса ImapClient
imap_client = ae.clients.imap.ImapClient()

# Укажите хост, имя пользователя, пароль и задайте порт для вашего клиента
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Создайте RestoreSettings с Recursive, установленным в true
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Укажите путь к каталогу
data_dir = "path/to/your/data/directory"

# Загрузите файл PST
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\ImapBackup.pst")

# Выполните операцию восстановления
imap_client.restore(pst, settings)
```

## **Операция резервного копирования и восстановления IMAP с MultiConnection**

Для задач, связанных с большим объемом данных или множеством электронных писем, Aspose.Email предлагает свойство 'use_multi_connection' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) для оптимизации выполнения операций IMAP, позволяя IMAP-клиенту одновременно открывать несколько соединений с почтовым сервером. Когда режим MultiConnection включен, IMAP-клиент может выполнять различные задачи (такие как получение электронных писем, синхронизация папок и резервное копирование данных) параллельно через разные соединения. Это может привести к значительному сокращению общего времени, необходимого для выполнения операций. Следующие примеры кода демонстрируют, как включить режим MultiConnection для операций резервного копирования и восстановления.

Однако важно отметить, что использование нескольких соединений может ограничиваться правилами и политиками, установленными почтовым сервером. Некоторые серверы могут вводить ограничения на количество одновременных соединений, которые могут быть сделаны с одной учетной записи пользователя, чтобы избежать перегрузки сервера. Всегда проверяйте условия обслуживания или политику вашего почтового провайдера, чтобы убедиться в соблюдении их правил использования перед включением режима MultiConnection.

### **Резервное копирование сообщений с MultiConnection**

Следующий фрагмент кода демонстрирует операцию резервного копирования с включенным режимом MultiConnection:

```py
import aspose.email as ae

# Создайте экземпляр класса ImapClient
imap_client = ae.clients.imap.ImapClient()

# Укажите хост, имя пользователя, пароль и задайте порт для вашего клиента
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Включите MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Получите информацию о почтовом ящике
mailbox_info = imap_client.mailbox_info

# Получите информацию о папке входящих
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Создайте ImapFolderInfoCollection и добавьте информацию о папке входящих
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Укажите путь к каталогу
data_dir = "path/to/your/data/directory"

# Выполните операцию резервного копирования
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

### **Восстановление сообщений с MultiConnection**

Следующий фрагмент кода демонстрирует операцию восстановления с включенным режимом MultiConnection.

```py
import aspose.email as ae

# Создайте экземпляр класса ImapClient
imap_client = ae.clients.imap.ImapClient()

# Укажите хост, имя пользователя, пароль и задайте порт для вашего клиента
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Включите MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Создайте RestoreSettings с Recursive, установленным в true
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Укажите путь к каталогу
data_dir = "path/to/your/data/directory"

# Загрузите файл PST
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\Outlook.pst")

# Выполните операцию восстановления
imap_client.restore(pst, settings)
```