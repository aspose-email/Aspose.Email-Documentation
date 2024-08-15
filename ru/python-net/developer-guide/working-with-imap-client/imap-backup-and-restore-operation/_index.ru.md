---
title: "Операция резервного копирования и восстановления IMAP в Python"
url: /ru/python-net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email для Python предлагает следующие методы [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс для резервного копирования и восстановления сообщений:

- **'backup'** method
- **'restore'** method

В этой статье показано, как создавать резервные копии и восстанавливать сообщения с помощью [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class.

## **Резервные сообщения**

В приведенном ниже примере кода показано, как реализовать возможность резервного копирования в ваш проект с помощью метода «резервного копирования» [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.AUTO

# Get mailbox info
mailbox_info = imap_client.mailbox_info

# Get folder info for the Inbox folder
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Create an ImapFolderInfoCollection and add the Inbox folder info
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Perform the backup operation
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

## **Восстановить сообщения**

В приведенном ниже примере кода показано, как реализовать возможность восстановления в вашем проекте с помощью метода «restore» [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Create RestoreSettings with Recursive set to true
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Load the PST file
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\ImapBackup.pst")

# Perform the restore operation
imap_client.restore(pst, settings)
```

## **Операция резервного копирования и восстановления IMAP с помощью MultiConnection**

Для задач, связанных с большим объемом данных или многочисленными сообщениями электронной почты, Aspose.Email предлагает свойство use_multi_connection [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс для оптимизации производительности операций IMAP, позволяя клиенту IMAP одновременно открывать несколько подключений к почтовому серверу. Когда включен режим MultiConnectionMode, клиент IMAP может параллельно выполнять различные задачи (например, получение писем, синхронизацию папок и резервное копирование данных) через разные соединения. Это может привести к значительному сокращению общего времени, необходимого для выполнения операций. В следующих фрагментах кода показано, как включить режим MultiConnection для операций резервного копирования и восстановления.

Однако важно отметить, что использование нескольких подключений может быть связано с ограничениями и политиками, установленными почтовым сервером. Некоторые серверы могут налагать ограничения на количество одновременных подключений, которые могут быть выполнены с помощью одной учетной записи пользователя, чтобы избежать перегрузки сервера. Перед включением режима MultiConnectionMode всегда проверяйте условия обслуживания или политики поставщика услуг электронной почты, чтобы убедиться в соблюдении правил его использования.

### **Резервное копирование сообщений с использованием нескольких подключений**

Следующий фрагмент кода демонстрирует операцию резервного копирования с включенным режимом MultiConnection:

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Enable MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Get mailbox info
mailbox_info = imap_client.mailbox_info

# Get folder info for the Inbox folder
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Create an ImapFolderInfoCollection and add the Inbox folder info
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Perform the backup operation
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

### **Восстановление сообщений с помощью MultiConnection**

В следующем фрагменте кода показана операция восстановления с включенным режимом MultiConnection.

```py
import aspose.email as ae

# Create an instance of the ImapClient class
imap_client = ae.clients.imap.ImapClient()

# Specify host, username, password, and set port for your client
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Enable MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Create RestoreSettings with Recursive set to true
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Specify the path to the directory
data_dir = "path/to/your/data/directory"

# Load the PST file
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\Outlook.pst")

# Perform the restore operation
imap_client.restore(pst, settings)
```
