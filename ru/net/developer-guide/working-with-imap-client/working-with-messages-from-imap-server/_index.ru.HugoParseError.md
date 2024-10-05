---
title: Работа с сообщениями с IMAP-сервера
type: docs
weight: 20
url: /net/working-with-messages-from-imap-server/
---

## **Получение идентификационной информации для сообщений, полученных из почтового ящика**

При извлечении и обработке электронных писем вы можете получить детали этих сообщений, используя их последовательные номера. Для взаимодействия с IMAP-почтовым ящиком используются следующие функции:

- `Aspose.Email.MailboxInfo` класс - Представляет идентификационную информацию о сообщении в почтовом ящике.

    - `Aspose.Email.MailboxInfo.SequenceNumber` свойство - Последовательный номер сообщения.

    - `Aspose.Email.MailboxInfo.UniqueId` свойство - Уникальный идентификатор сообщения.

- `Aspose.Email.MailMessage.ItemId` свойство - Представляет идентификационную информацию о сообщении в почтовом ящике.

Приведенный ниже фрагмент кода показывает, как получить идентификационную информацию о сообщениях:

```cs
using (var client = new ImapClient(imapHost, port, emailAddress, password, securityOption))
{
    var msgs = client.ListMessages("INBOX").Take(5);
    var seqIds = msgs.Select(t => t.SequenceNumber);
    var msgsViaFetch = client.FetchMessages(seqIds);
	
    for (var i = 0; i < 5; i++)
    {
        var thisMsg = msgsViaFetch[i];
        Console.WriteLine($"Message ID:{seqIds.ElementAt(i)} SequenceNumber: {thisMsg.ItemId.SequenceNumber} Subject:{thisMsg.Subject}");
    }
}
```

## **Перечисление идентификаторов MIME-сообщений с сервера**

[ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) предоставляет MIME [MessageId](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/messageid/) для идентификации сообщения без извлечения полного сообщения. Приведенный ниже фрагмент кода показывает, как перечислить идентификаторы MIME-сообщений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.cs" >}}

## **Перечисление сообщений с сервера**

Aspose.Email предоставляет перегруженный вариант [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_12) с 2 членами, чтобы извлечь определенное количество сообщений на основе запроса. Приведенный ниже фрагмент кода показывает, как перечислить сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ListMessagesWithMaximumNumberOfMessages-ListMessagesWithMaximumNumberOfMessages.cs" >}}

## **Перечисление сообщений с сервера рекурсивно**

Протокол IMAP поддерживает рекурсивное перечисление сообщений из папки почтового ящика. Это также помогает перечислять сообщения из подпапок папки. Приведенный ниже фрагмент кода показывает, как рекурсивно перечислять сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.cs" >}}

## **Перечисление сообщений с использованием многосоединений**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет свойство [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/), которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете установить количество соединений, которые будут использоваться в режиме многосоединения, используя [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). Приведенный ниже фрагмент кода демонстрирует использование режима многосоединения для перечисления сообщений и сравнивает его производительность с режимом одного соединения.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Обратите внимание, что использование режима многосоединения не гарантирует повышения производительности.

{{% /alert %}} 

## **Получение сообщений в порядке убывания**

Aspose.Email предоставляет метод [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/), который перечисляет сообщения с поддержкой постраничной навигации. Некоторые перегрузки [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) принимают [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) как параметр. [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) предоставляет свойство [`AscendingSorting`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/), которое, когда установлено в **false**, возвращает электронные письма в порядке убывания.

Пример кода ниже демонстрирует использование [AscendingSorting](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) свойства класса [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) для изменения порядка электронных писем.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ChangeOrderOfEmails-1.cs" >}}

## **Извлечение сообщений с сервера и сохранение на диск**

Класс [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) может извлекать сообщения с IMAP-сервера и сохранять сообщения в формате EML на локальном диске. Для сохранения сообщений на диск необходимо выполнить следующие шаги:

1. Создайте экземпляр класса [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
1. Укажите имя хоста, порт, имя пользователя и пароль в [конструкторе](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor) ImapClient.
1. Выберите папку, используя метод [SelectFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/selectfolder/#selectfolder/).
1. Вызовите метод [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages), чтобы получить объект [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/).
1. Переберите коллекцию [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), вызовите метод [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/savemessage/#savemessage/) и укажите выходной путь и имя файла.

Приведенный ниже фрагмент кода показывает, как извлекать электронные письма с сервера и сохранять их.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FetchEmailMessagesFromIMAPServer-FetchEmailMessagesFromIMAPServer.cs" >}}

## **Сохранение сообщений в формате MSG**

[В приведенном выше примере](#fetch-messages-from-server-and-save-to-disc) электронные письма сохраняются в формате EML. Чтобы сохранить электронные письма в формате MSG, необходимо вызвать метод [ImapClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessage/#fetchmessage/). Он возвращает сообщение в экземпляре класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Затем можно вызвать метод [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/), чтобы сохранить сообщение в формате MSG. Приведенный ниже фрагмент кода показывает, как сохранять сообщения в формате MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SavingMessagesFromIMAPServer-SavingMessagesFromIMAPServer.cs" >}}

## **Групповое извлечение сообщений**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет метод [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/), который принимает итерируемый набор последовательных номеров или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Приведенный ниже фрагмент кода демонстрирует использование метода [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) для извлечения сообщений по последовательным номерам и уникальным идентификаторам.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapFetchGroupMessages-1.cs" >}}

## **Перечисление сообщений с поддержкой постраничной навигации**

В ситуациях, когда почтовый сервер содержит большое количество сообщений в почтовом ящике, часто возникает желание перечислять или извлекать сообщения с поддержкой постраничной навигации. API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) позволяет извлекать сообщения с сервера с поддержкой постраничной навигации.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.cs" >}}

## **Перечисление вложений сообщений** 

Чтобы получить информацию о вложениях, таких как имя, размер, не извлекая данные вложения, попробуйте следующие API:

- *Aspose.Email.Clients.Imap.ImapAttachmentInfo* - Представляет информацию о вложении. 
- *Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection* - Представляет коллекцию класса [ImapAttachmentInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/). 
- *Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)* - Получает информацию для каждого вложения в сообщении.

Пример кода с шагами ниже покажет, как использовать эти API:

1. Вызовите метод [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/) на объекте imapClient. Этот метод вернет ImapMessageInfoCollection с информацией о сообщениях в почтовом ящике.
2. Переберите каждое сообщение в messageInfoCollection, используя цикл foreach.
3. Вызовите метод [ListAttachments()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/#imapclientlistattachments-method) на объекте imapClient, передавая свойство SequenceNumber объекта сообщения в качестве параметра. Этот метод вернет ImapAttachmentInfoCollection с информацией о вложениях в сообщении.
4. Переберите каждое вложение в attachmentInfoCollection, используя цикл foreach.
5. Внутри внешнего цикла вы можете получить доступ к информации о каждом вложении, используя свойства объекта attachmentInfo. В этом примере имя и размер каждого вложения выводятся в консоль с помощью `Console.WriteLine()`.

   `Console.WriteLine("Attachment: {0} (size: {1})", attachmentInfo.Name, attachmentInfo.Size);`
```cs
var messageInfoCollection = imapClient.ListMessages();
    
foreach (var message in messageInfoCollection)
{
    var attachmentInfoCollection = imapClient.ListAttachments(message.SequenceNumber);

    foreach (var attachmentInfo in attachmentInfoCollection)
    {
        Console.WriteLine("Attachment: {0} (size: {1})", attachmentInfo.Name, attachmentInfo.Size);
    }
}
```

## **Получение папок и чтение сообщений рекурсивно**

В этой статье используются большинство функций [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) для создания приложения, которое рекурсивно перечисляет все папки и подпапки с IMAP-сервера. Оно также сохраняет сообщения в каждой папке и подпапке в формате MSG на локальном диске. На диске папки и сообщения создаются и сохраняются в той же иерархической структуре, что и на IMAP-сервере. Приведенный ниже фрагмент кода показывает, как получить информацию о сообщениях и подпапках рекурсивно.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ReadMessagesRecursively-ReadMessagesRecursively.cs" >}}

## **Извлечение дополнительных параметров в качестве сводной информации**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrieveExtraParameters-RetrieveExtraParametersAsSummaryInformation.cs" >}}

## **Получение информации заголовка List-Unsubscribe**

Заголовок List-Unsubscribe содержит URL-адрес для отписки от списков рассылки, например, рекламных, информационных и т. д. Для получения заголовка List-Unsubscribe используйте свойство [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) класса [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/). Приведенный ниже пример показывает использование свойства [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) для получения заголовка List-Unsubscribe.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-GetListUnsubscribeHeader-1.cs" >}}
