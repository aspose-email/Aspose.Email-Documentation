---
title: "Operación de respaldo y restauración de IMAP en Python"
url: /es/python-net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email para Python ofrece los siguientes métodos de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para respaldar y restaurar mensajes:

- **método 'backup'**
- **método 'restore'**

Este artículo demuestra cómo respaldar y restaurar mensajes utilizando la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class).

## **Respaldar Mensajes**

El siguiente ejemplo de código demuestra cómo implementar la capacidad de respaldo en su proyecto utilizando el método 'backup' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

# Crear una instancia de la clase ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar el host, nombre de usuario, contraseña y establecer el puerto para su cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.AUTO

# Obtener información del buzón
mailbox_info = imap_client.mailbox_info

# Obtener información de la carpeta de la bandeja de entrada
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Crear una ImapFolderInfoCollection y agregar la información de la carpeta de la bandeja de entrada
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Especificar la ruta al directorio
data_dir = "path/to/your/data/directory"

# Realizar la operación de respaldo
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

## **Restaurar Mensajes**

El siguiente ejemplo de código demuestra cómo implementar la capacidad de restauración en su proyecto utilizando el método 'restore' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

# Crear una instancia de la clase ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar el host, nombre de usuario, contraseña y establecer el puerto para su cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Crear RestoreSettings con Recursivo establecido en verdadero
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Especificar la ruta al directorio
data_dir = "path/to/your/data/directory"

# Cargar el archivo PST
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\ImapBackup.pst")

# Realizar la operación de restauración
imap_client.restore(pst, settings)
```

## **Operación de Respaldo y Restauración de IMAP con MultiConnection**

Para tareas que involucran una gran cantidad de datos o numerosos mensajes de correo electrónico, Aspose.Email ofrece la propiedad 'use_multi_connection' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para optimizar el rendimiento de las operaciones IMAP permitiendo que el cliente IMAP abra múltiples conexiones al servidor de correo simultáneamente. Cuando MultiConnectionMode está habilitado, el cliente IMAP puede llevar a cabo diversas tareas (como obtener correos electrónicos, sincronizar carpetas y respaldar datos) en paralelo a través de diferentes conexiones. Esto puede llevar a una reducción significativa del tiempo total requerido para completar las operaciones. Los siguientes fragmentos de código demuestran cómo habilitar el modo MultiConnection para las operaciones de respaldo y restauración.

Sin embargo, es importante tener en cuenta que el uso de múltiples conexiones puede estar sujeto a limitaciones y políticas establecidas por el servidor de correo. Algunos servidores pueden imponer restricciones sobre el número de conexiones concurrentes que se pueden realizar desde una única cuenta de usuario para evitar sobrecargar el servidor. Siempre verifique los términos de servicio o políticas del proveedor de correo electrónico para asegurar el cumplimiento de sus directrices de uso antes de habilitar MultiConnectionMode.

### **Respaldar Mensajes con MultiConnection**

El siguiente fragmento de código demuestra una operación de respaldo con el modo MultiConnection habilitado:

```py
import aspose.email as ae

# Crear una instancia de la clase ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar el host, nombre de usuario, contraseña y establecer el puerto para su cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Habilitar MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Obtener información del buzón
mailbox_info = imap_client.mailbox_info

# Obtener información de la carpeta de la bandeja de entrada
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Crear una ImapFolderInfoCollection y agregar la información de la carpeta de la bandeja de entrada
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Especificar la ruta al directorio
data_dir = "path/to/your/data/directory"

# Realizar la operación de respaldo
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

### **Restaurar Mensajes con MultiConnection**

El siguiente fragmento de código demuestra una operación de restauración con el modo MultiConnection habilitado.

```py
import aspose.email as ae

# Crear una instancia de la clase ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar el host, nombre de usuario, contraseña y establecer el puerto para su cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Habilitar MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Crear RestoreSettings con Recursivo establecido en verdadero
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Especificar la ruta al directorio
data_dir = "path/to/your/data/directory"

# Cargar el archivo PST
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\Outlook.pst")

# Realizar la operación de restauración
imap_client.restore(pst, settings)
```