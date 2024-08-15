---
title: "Работа с папками на сервере IMAP"
url: /ru/net/working-with-folders-on-imap-server/
weight: 60
type: docs
---


## **Получение информации о папках**

С Aspose.Email очень просто получать информацию о папках с сервера IMAP. Позвоните в [ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listfolders/#listfolders/) метод [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс. Он возвращает объект [ImapFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection/) тип. Изучите эту коллекцию и получайте информацию об отдельных папках в цикле. Метод перегружен. Вы можете передать имя папки в качестве параметра, чтобы получить список подпапок. В следующем фрагменте кода показано, как получить информацию о папке с сервера IMAP с помощью Aspose.Email, используя метод, описанный в информации.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GettingFoldersInformation-GettingFoldersInformation.cs" >}}

## **Удаление и переименование папок**

Папку на сервере IMAP можно удалить или переименовать в одну строку с помощью Aspose.Email:

- The [`DeleteFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolder/#deletefolder/) метод принимает имя папки в качестве параметра.
- Для [`RenameFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/renamefolder/#renamefolder/) метод, вам нужно передать текущее имя папки и новое имя папки.

В следующем фрагменте кода показано, как удалить папку с сервера IMAP и переименовать папку. Каждая операция выполняется с помощью одной строки кода.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-DeletingAndRenamingFolders-DeletingAndRenamingFolders.cs" >}}

## **Добавление нового сообщения в папку**

Вы можете добавить новое сообщение в папку, используя [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) and [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) классы. Сначала создайте [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) возражать, предоставляя субъекту ценности и исходя из них. Затем подпишитесь на папку и добавьте в нее сообщение. В следующем фрагменте кода показано, как добавить новое сообщение в папку.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-AddingNewMessage-AddingNewMessageToFolder.cs" >}}

## **Добавьте несколько сообщений с поддержкой нескольких подключений**

Вы можете добавить несколько сообщений, используя [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) метод, предоставленный [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) классы. [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) метод принимает список [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и добавляет его в текущую папку, если папка не указана в качестве параметра. IMapClient также поддерживает режим MultiConnection для высоконагруженных операций. В следующем фрагменте кода показано, как добавить несколько сообщений в режиме MultiConnection.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapGroupAppendWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Переместить сообщения в другую папку почтового ящика**

Aspose.Email for .NET позволяет перемещать сообщения из одной папки почтового ящика в другую с помощью [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) API. [MoveMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/movemessage/#movemessage/) метод использует уникальный идентификатор сообщения и имя целевой папки для перемещения сообщения в папку назначения. В следующем фрагменте кода показано, как перемещать сообщения в другую папку почтового ящика.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-MoveMessage-MoveMessage.cs" >}}

## **Копирование сообщений в другую папку почтового ящика**

Aspose.Email API предоставляет возможность копировать сообщения из одной папки почтового ящика в другую. Это позволяет копировать как одно, так и несколько сообщений с помощью [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessage/#copymessage/) and [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) методы. [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) Метод предоставляет возможность копировать несколько сообщений из исходной папки почтового ящика в папку почтового ящика назначения. В следующем фрагменте кода показано, как копировать сообщения в другую папку почтового ящика.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CopyMultipleMessagesFromOneFoldertoAnother-CopyMultipleMessagesFromOneFoldertoAnother.cs" >}}

## **Работа с папками почтовых ящиков специального назначения**

В некоторых хранилищах сообщений IMAP есть специальные почтовые ящики, например, для хранения черновиков или отправленных сообщений. Многие почтовые клиенты позволяют пользователям указывать, куда следует помещать черновики или отправленные сообщения, но для их настройки пользователь должен знать, какие почтовые ящики сервер выделил для этих целей. Aspose.Email может идентифицировать эти специальные почтовые ящики с помощью [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) класс, чтобы с ними было удобнее работать. В следующем примере кода показано, как получить доступ к этим специальным почтовым ящикам с помощью [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) class.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapSpecialUseMailboxes-1.cs" >}}
