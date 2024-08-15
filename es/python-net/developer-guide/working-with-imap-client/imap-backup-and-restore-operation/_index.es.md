---
title: "Operación de copia de seguridad y restauración de IMAP en Python"
url: /es/python-net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email para Python ofrece los siguientes métodos de [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) clase para hacer copias de seguridad y restaurar mensajes:

- **'backup'** method
- **'restore'** method

En este artículo se muestra cómo hacer copias de seguridad y restaurar los mensajes mediante el [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class.

## **Mensajes de respaldo**

El ejemplo de código que aparece a continuación demuestra cómo implementar la capacidad de copia de seguridad en su proyecto mediante el método de «copia de seguridad» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:

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

## **Restaurar mensajes**

El ejemplo de código que aparece a continuación demuestra cómo implementar la capacidad de restauración en su proyecto mediante el método de «restauración» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:

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

## **Operación de respaldo y restauración de IMAP con MultiConnection**

Para las tareas que implican una gran cantidad de datos o numerosos mensajes de correo electrónico, Aspose.Email ofrece la propiedad 'use_multi_connection' del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) clase para optimizar el rendimiento de las operaciones IMAP al permitir que el cliente IMAP abra varias conexiones al servidor de correo electrónico simultáneamente. Cuando MultiConnectionMode está habilitado, el cliente IMAP puede llevar a cabo varias tareas (como buscar correos electrónicos, sincronizar carpetas y hacer copias de seguridad de los datos) en paralelo en diferentes conexiones. Esto puede llevar a una reducción significativa del tiempo total necesario para completar las operaciones. Los siguientes fragmentos de código muestran cómo habilitar el modo de conexión múltiple para las operaciones de respaldo y restauración.

Sin embargo, es importante tener en cuenta que el uso de múltiples conexiones puede estar sujeto a las limitaciones y políticas establecidas por el servidor de correo electrónico. Algunos servidores pueden imponer restricciones a la cantidad de conexiones simultáneas que se pueden realizar desde una sola cuenta de usuario para evitar sobrecargar el servidor. Consulta siempre las condiciones del servicio o las políticas del proveedor de correo electrónico para garantizar el cumplimiento de sus directrices de uso antes de habilitar el modo multiconexión.

### **Mensajes de respaldo con MultiConnection**

El siguiente fragmento de código muestra una operación de copia de seguridad con el modo multiconexión activado:

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

### **Restaurar mensajes con MultiConnection**

El siguiente fragmento de código muestra una operación de restauración con el modo multiconexión activado.

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
