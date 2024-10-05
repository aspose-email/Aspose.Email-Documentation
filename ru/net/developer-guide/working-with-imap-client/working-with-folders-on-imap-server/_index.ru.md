---
title: "Работа с папками на IMAP сервере"
url: /ru/net/working-with-folders-on-imap-server/
weight: 60
type: docs
---


## **Получение информации о папках**

Получение информации о папках с IMAP сервера очень просто с помощью Aspose.Email. Вызовите метод [ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listfolders/#listfolders/) класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Он возвращает объект типа [ImapFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection/). Переберите эту коллекцию и получите информацию о отдельных папках в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подпапок. Следующий фрагмент кода показывает, как получить информацию о папке с IMAP сервера, используя Aspose.Email и описанный метод.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GettingFoldersInformation-GettingFoldersInformation.cs" >}}

## **Удаление и переименование папок**

Папку на IMAP сервере можно удалить или переименовать в одну строчку с помощью Aspose.Email:

- Метод [`DeleteFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolder/#deletefolder/) принимает имя папки в качестве параметра.
- Для метода [`RenameFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/renamefolder/#renamefolder/) вам нужно передать текущее имя папки и новое имя папки.

Следующий фрагмент кода показывает, как удалить папку с IMAP сервера и как переименовать папку. Каждая операция выполняется одной строкой кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-DeletingAndRenamingFolders-DeletingAndRenamingFolders.cs" >}}

## **Добавление нового сообщения в папку**

Вы можете добавить новое сообщение в папку, используя классы [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Сначала создайте объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) с указанием темы, а также адресов "Кому" и "От". Затем подпишитесь на папку и добавьте сообщение в неё. Следующий фрагмент кода показывает, как добавить новое сообщение в папку.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-AddingNewMessage-AddingNewMessageToFolder.cs" >}}

## **Добавление нескольких сообщений с поддержкой многоподключения**

Вы можете добавить несколько сообщений, используя метод [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Метод [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) принимает список [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и добавляет его в текущую папку, если папка не была предоставлена как параметр. ImapClient также поддерживает режим многоподключения для высоконагруженных операций. Следующий фрагмент кода показывает, как добавить несколько сообщений, используя режим многоподключения.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapGroupAppendWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Обратите внимание, что использование режима многоподключения не гарантирует увеличение производительности.

{{% /alert %}} 

## **Перемещение сообщений в другую папку почтового ящика**

Aspose.Email для .NET позволяет перемещать сообщения из одной папки почтового ящика в другую с помощью API [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Метод [MoveMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/movemessage/#movemessage/) использует уникальный идентификатор сообщения и имя папки назначения для перемещения сообщения в папку назначения. Следующий фрагмент кода показывает, как перемещать сообщения в другую папку почтового ящика.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-MoveMessage-MoveMessage.cs" >}}

## **Копирование сообщений в другую папку почтового ящика**

API Aspose.Email предоставляет возможность копировать сообщения из одной папки почтового ящика в другую. Он позволяет копировать как одно, так и несколько сообщений, используя методы [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessage/#copymessage/) и [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/). Метод [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) предоставляет возможность копировать несколько сообщений из папки источника почтового ящика в папку назначения. Следующий фрагмент кода показывает, как копировать сообщения в другую папку почтового ящика.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CopyMultipleMessagesFromOneFoldertoAnother-CopyMultipleMessagesFromOneFoldertoAnother.cs" >}}

## **Работа со специальными папками почтового ящика**

Некоторые хранилища IMAP-сообщений включают специальные почтовые ящики, такие как те, которые используются для хранения черновиков или отправленных сообщений. Многие почтовые клиенты позволяют пользователям указывать, куда должны помещаться черновики или отправленные сообщения, но для их настройки требуется, чтобы пользователь знал, какие почтовые ящики сервер зарезервировал для этих целей. Aspose.Email может идентифицировать эти специальные почтовые ящики, используя класс [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/), чтобы упростить работу с ними. Следующий пример кода демонстрирует, как получить доступ к этим специальным почтовым ящикам, используя класс [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/).

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapSpecialUseMailboxes-1.cs" >}}