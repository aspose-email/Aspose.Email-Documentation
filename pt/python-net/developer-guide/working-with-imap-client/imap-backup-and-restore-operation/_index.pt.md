---
title: "Operação de Backup e Restauração IMAP em Python"
url: /pt/python-net/imap-backup-and-restore-operation/
weight: 120
type: docs
---


Aspose.Email para Python oferece os seguintes métodos da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para backup e restauração de mensagens:

- **método 'backup'**
- **método 'restore'**

Este artigo demonstra como fazer backup e restaurar mensagens usando a classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class).

## **Backup de Mensagens**

O exemplo de código abaixo demonstra como implementar a capacidade de backup em seu projeto usando o método 'backup' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

# Criar uma instância da classe ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar host, nome de usuário, senha e definir porta para seu cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.AUTO

# Obter informações da caixa de correio
mailbox_info = imap_client.mailbox_info

# Obter informações da pasta da Caixa de Entrada
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Criar uma ImapFolderInfoCollection e adicionar as informações da pasta da Caixa de Entrada
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Especificar o caminho para o diretório
data_dir = "path/to/your/data/directory"

# Realizar a operação de backup
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

## **Restauração de Mensagens**

O exemplo de código abaixo demonstra como implementar a capacidade de restauração em seu projeto usando o método 'restore' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

# Criar uma instância da classe ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar host, nome de usuário, senha e definir porta para seu cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Criar RestoreSettings com Recursive definido como verdadeiro
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Especificar o caminho para o diretório
data_dir = "path/to/your/data/directory"

# Carregar o arquivo PST
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\ImapBackup.pst")

# Realizar a operação de restauração
imap_client.restore(pst, settings)
```

## **Operação de Backup e Restauração IMAP com MultiConnection**

Para tarefas que envolvem uma grande quantidade de dados ou numerosas mensagens de email, Aspose.Email oferece a propriedade 'use_multi_connection' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para otimizar o desempenho das operações IMAP, permitindo que o cliente IMAP abra várias conexões com o servidor de email simultaneamente. Quando o MultiConnectionMode está ativado, o cliente IMAP pode realizar várias tarefas (como buscar emails, sincronizar pastas e fazer backup de dados) em paralelo por meio de diferentes conexões. Isso pode resultar em uma redução significativa no tempo total necessário para concluir as operações. Os seguintes trechos de código demonstram como habilitar o modo MultiConnection para operações de backup e restauração.

No entanto, é importante notar que o uso de várias conexões pode estar sujeito a limitações e políticas estabelecidas pelo servidor de email. Alguns servidores podem impor restrições ao número de conexões simultâneas que podem ser feitas a partir de uma única conta de usuário para evitar sobrecarregar o servidor. Sempre verifique os termos de serviço ou políticas do provedor de email para garantir a conformidade com suas diretrizes de uso antes de habilitar o MultiConnectionMode.

### **Backup de Mensagens com MultiConnection**

O seguinte trecho de código demonstra uma operação de backup com o modo MultiConnection ativado:

```py
import aspose.email as ae

# Criar uma instância da classe ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar host, nome de usuário, senha e definir porta para seu cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Ativar o MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Obter informações da caixa de correio
mailbox_info = imap_client.mailbox_info

# Obter informações da pasta da Caixa de Entrada
inbox_info = imap_client.get_folder_info(mailbox_info.inbox.name)

# Criar uma ImapFolderInfoCollection e adicionar as informações da pasta da Caixa de Entrada
infos = ae.clients.imap.ImapFolderInfoCollection()
infos.add(inbox_info)

# Especificar o caminho para o diretório
data_dir = "path/to/your/data/directory"

# Realizar a operação de backup
settings = ae.clients.imap.BackupSettings
settings.execute_recursively = True
imap_client.backup(infos, data_dir + "\\ImapBackup.pst", settings)
```

### **Restauração de Mensagens com MultiConnection**

O seguinte trecho de código demonstra uma operação de restauração com o modo MultiConnection ativado.

```py
import aspose.email as ae

# Criar uma instância da classe ImapClient
imap_client = ae.clients.imap.ImapClient()

# Especificar host, nome de usuário, senha e definir porta para seu cliente
imap_client.host = "imap.gmail.com"
imap_client.username = username
imap_client.password = password
imap_client.port = 993
imap_client.security_options = ae.clients.SecurityOptions.Auto

# Ativar o MultiConnectionMode
imap_client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

# Criar RestoreSettings com Recursive definido como verdadeiro
settings = ae.clients.imap.RestoreSettings()
settings.recursive = True

# Especificar o caminho para o diretório
data_dir = "path/to/your/data/directory"

# Carregar o arquivo PST
pst = ae.storage.pst.PersonalStorage.from_file(data_dir + "\\Outlook.pst")

# Realizar a operação de restauração
imap_client.restore(pst, settings)
```