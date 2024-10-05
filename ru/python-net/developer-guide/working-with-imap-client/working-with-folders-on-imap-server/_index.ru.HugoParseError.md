---
title: Работа с папками на IMAP-сервере
type: docs
weight: 50
url: /python-net/working-with-folders-on-imap-server/
---


## **Получение информации о папках**
Получение информации о папках с IMAP-сервера очень просто с помощью Aspose.Email. Вызовите метод ListFolders() пространства имен Aspose.Email.Imap. Он возвращает объект типа [ImapFolderInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection). Переберите эту коллекцию и получите информацию о отдельных папках в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подпапок. Следующий фрагмент кода показывает, как получить информацию о папке с IMAP-сервера, используя Aspose.Email, с помощью описанного в информации метода.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}

## **Удаление и переименование папок**

Следующие методы класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class), связанные с управлением папками на почтовом сервере с использованием IMAP, можно легко реализовать в вашем проекте с помощью Aspose.Email:

- метод delete_folder - навсегда удаляет папку и все сообщения, содержащиеся в ней.
- метод rename_folder - изменяет имя папки, не изменяя содержимое внутри неё.

Ниже приведен фрагмент кода, показывающий, как программно удалить или переименовать папки на IMAP-сервере:

```py
# Удалить папку и переименовать папку
client.delete_folder("foldername")
client.rename_folder("foldername", "newfoldername")
```

## **Добавление нового сообщения в папку**
Вы можете добавить новое сообщение в папку, используя классы MailMessage и ImapClient. Сначала создайте объект MailMessage, указав значения темы, "кому" и "от кого". Затем подпишитесь на папку и добавьте сообщение в неё. Следующий фрагмент кода показывает, как добавить новое сообщение в папку.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}

## **Установление многосоединения при выполнении пакетных операций**

Aspose.Email позволяет настроить клиента для установления нескольких одновременных соединений с IMAP-сервером. Это не обязательно увеличивает производительность, но является надежным решением для параллельных операций. Это особенно полезно, если клиенту необходимо выполнять несколько задач одновременно, таких как получение различных почтовых папок, синхронизация больших объемов данных или одновременная обработка нескольких сообщений.

Ниже приведен фрагмент кода, показывающий, как установить несколько соединений с IMAP-сервером при загрузке коллекции электронных сообщений, используя метод 'append_messages' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.append_messages(messages)
```

## **Перемещение сообщений в другую папку почтового ящика**
Aspose.Email для .NET позволяет перемещать сообщения из одной папки почтового ящика в другую, используя API ImapClient. Метод MoveMessage использует уникальный идентификатор сообщения и имя папки назначения для перемещения сообщения в папку назначения. Следующий фрагмент кода показывает, как перемещать сообщения в другую папку почтового ящика.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}

## **Копирование сообщений в другую папку почтового ящика**
API Aspose.Email предоставляет возможность копировать сообщения из одной папки почтового ящика в другую. Он позволяет копировать как одно, так и несколько сообщений с использованием методов CopyMessage и CopyMessages. Метод CopyMessages обеспечивает возможность копирования нескольких сообщений из исходной папки почтового ящика в папку назначения. Следующий фрагмент кода показывает, как копировать сообщения в другую папку почтового ящика.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}

## **Работа со специальными папками почтового ящика**

Специальные почтовые ящики - это предварительно назначенные папки в электронной системе, используемые для определённых типов сообщений, таких как Отправленные, Черновики, Спам, Корзина и Архив. Библиотека Aspose.Email позволяет доступ к этим почтовым ящикам, присваивая атрибуты, связанные с их ролями и назначениями, клиенту. Затем клиенты могут автоматически обнаруживать и представлять эти папки соответствующим образом без вмешательства пользователя.

Ниже приведен фрагмент кода, показывающий, как запросить информацию о важных специальных почтовых ящиках (входящие, черновики, спам, отправленные и корзина) с использованием свойств класса [ImapMailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmailboxinfo/#imapmailboxinfo-class) и вывести эту информацию:

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