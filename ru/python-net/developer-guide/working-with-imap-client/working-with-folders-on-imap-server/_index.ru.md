---
title: "Работа с папками на сервере IMAP"
url: /ru/python-net/working-with-folders-on-imap-server/
weight: 50
type: docs
---


## **Получение информации о папках**
С Aspose.Email очень просто получать информацию о папках с сервера IMAP. Вызовите метод listFolders () пространства имен Aspose.Email.Imap. Он возвращает объект [ImapFolderInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection) тип. Изучите эту коллекцию и получайте информацию об отдельных папках в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подпапок. В следующем фрагменте кода показано, как получить информацию о папке с сервера IMAP с помощью Aspose.Email, используя метод, описанный в информации.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}

## **Удаление и переименование папок**

Следующие методы [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс, связанный с управлением папками на почтовом сервере с помощью IMAP, можно легко внедрить в свой проект с помощью Aspose.Email:

- Метод delete_folder — безвозвратно удаляет папку и все содержащиеся в ней сообщения.
- Метод rename_folder — изменяет имя папки без изменения содержимого папки.

В приведенном ниже фрагменте кода показано, как программно удалять или переименовывать папки на сервере IMAP:

```py
# Delete a folder and Rename a folder
client.delete_folder("foldername")
client.rename_folder("foldername", "newfoldername")
```

## **Добавление нового сообщения в папку**
Можно добавить новое сообщение в папку, используя класс MailMessage и классы IMapClient. Сначала создайте объект MailMessage, указав значения темы, «откуда» и «откуда». Затем подпишитесь на папку и добавьте в нее сообщение. В следующем фрагменте кода показано, как добавить новое сообщение в папку.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}

## **Установление мультисоединения при выполнении пакетных операций**

Aspose.Email позволяет настроить клиент для установки нескольких одновременных подключений к серверу IMAP. Это не обязательно повышает производительность, но это надежное решение для параллельных операций. Это особенно полезно, если клиенту необходимо одновременно выполнять несколько задач, таких как загрузка разных папок электронной почты, синхронизация больших объемов данных или одновременная обработка нескольких сообщений.

В приведенном ниже фрагменте кода показано, как установить несколько подключений к серверу IMAP при загрузке коллекции сообщений электронной почты с помощью метода append_messages [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.append_messages(messages)
```

## **Переместить сообщения в другую папку почтового ящика**
Aspose.Email for .NET позволяет перемещать сообщения из одной папки почтового ящика в другую с помощью IMapClient API. Метод MoveMessage использует уникальный идентификатор сообщения и имя целевой папки для перемещения сообщения в папку назначения. В следующем фрагменте кода показано, как перемещать сообщения в другую папку почтового ящика.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}
## **Копирование сообщений в другую папку почтового ящика**
Aspose.Email API предоставляет возможность копировать сообщения из одной папки почтового ящика в другую. Он позволяет копировать как одно, так и несколько сообщений с помощью методов CopyMessage и CopyMessages. Метод CopyMessages позволяет копировать несколько сообщений из исходной папки почтового ящика в целевую папку почтового ящика. В следующем фрагменте кода показано, как копировать сообщения в другую папку почтового ящика.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}

## **Работа с папками почтовых ящиков специального назначения**

Почтовые ящики специального назначения — это предварительно назначенные папки в системе электронной почты, используемые для определенных типов сообщений, таких как «Отправленные», «Черновики», «Нежелательная почта», «Корзина» и «Архив». Библиотека Aspose.Email позволяет получить доступ к этим почтовым ящикам, присвоив клиенту атрибуты, связанные с их ролями и целями. После этого клиенты могут автоматически обнаруживать и представлять эти папки без вмешательства пользователя.

В следующем фрагменте кода показано, как запрашивать информацию о важных специальных почтовых ящиках (входящие, черновики, нежелательные сообщения, отправленные и корзина), используя свойства [ImapMailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmailboxinfo/#imapmailboxinfo-class) класс и распечатайте следующую информацию:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

mailboxInfo = client.mailbox_info
print(mailboxInfo.inbox)
print(mailboxInfo.draft_messages)
print(mailboxInfo.junk_messages)
print(mailboxInfo.sent_messages)
print(mailboxInfo.trash)
```