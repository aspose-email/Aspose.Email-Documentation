---
title: "Работа с сообщениями с сервера IMAP"
url: /ru/net/working-with-messages-from-imap-server/
weight: 20
type: docs
---

## **Получение идентификационной информации для сообщений, полученных из почтового ящика**

При получении и обработке сообщений электронной почты вы можете получить сведения об этих сообщениях, используя их порядковые номера.
Для взаимодействия с почтовым ящиком IMAP используются следующие функции:

- `Aspose.Email.MailboxInfo` class — представляет идентификационную информацию о сообщении в почтовом ящике.

    - `Aspose.Email.MailboxInfo.SequenceNumber` свойство - порядковый номер сообщения.

    - `Aspose.Email.MailboxInfo.UniqueId` свойство - уникальный идентификатор сообщения.

- `Aspose.Email.MailMessage.ItemId` свойство — представляет идентификационную информацию о сообщении в почтовом ящике.

В приведенном ниже фрагменте кода показано, как получить идентификационную информацию о сообщениях:

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

## **Отображение идентификаторов сообщений MIME с сервера**

[ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) предоставляет MIME [MessageId](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/messageid/) для идентификации сообщения без извлечения всего сообщения. В следующем фрагменте кода показано, как указать MIME MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.cs" >}}

## **Список сообщений с сервера**

Aspose.Email предоставляет перегруженный вариант из 2 человек [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_12) для получения заданного количества сообщений на основе запроса. В следующем фрагменте кода показано, как составить список сообщений.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ListMessagesWithMaximumNumberOfMessages-ListMessagesWithMaximumNumberOfMessages.cs" >}}

## **Рекурсивный список сообщений с сервера**

Протокол IMAP поддерживает рекурсивный список сообщений из папки почтового ящика. Это также помогает отображать сообщения из подпапок папки. В следующем фрагменте кода показано, как рекурсивно перечислять сообщения.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.cs" >}}

## **Список сообщений с помощью MultiConnection**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) обеспечивает [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) свойство, которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете настроить количество подключений, которое будет использоваться в режиме нескольких подключений, используя [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). В следующем фрагменте кода показано использование режима нескольких подключений для перечисления сообщений и сравнивается его производительность с режимом одиночного подключения.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Получайте сообщения в порядке убывания**

Aspose.Email предоставляет [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) метод, который перечисляет сообщения с поддержкой пейджинга. Некоторые перегрузки [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) accept [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) в качестве параметра. [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) обеспечивает [`AscendingSorting`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) свойство, которое, если установлено значение **false**, возвращает электронные письма в порядке убывания.

Следующий пример кода демонстрирует использование [AscendingSorting](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) собственность [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) класс для изменения порядка писем.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ChangeOrderOfEmails-1.cs" >}}

## **Получение сообщений с сервера и сохранение на диск**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) класс может получать сообщения с сервера IMAP и сохранять сообщения в формате EML на локальный диск. Для сохранения сообщений на диск необходимо выполнить следующие шаги:

1. Создайте экземпляр [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Укажите имя хоста, порт, имя пользователя и пароль в iMapClient [constructor](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor).
1. Выберите папку, используя [SelectFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/selectfolder/#selectfolder/) method.
1. Позвоните [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) метод получения [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) object.
1. Пройдите итерацию через [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) коллекция, позвоните в [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/savemessage/#savemessage/) метод и укажите выходной путь и имя файла.

В следующем фрагменте кода показано, как получать сообщения электронной почты с сервера и сохранять их.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FetchEmailMessagesFromIMAPServer-FetchEmailMessagesFromIMAPServer.cs" >}}

## **Сохранение сообщений в формате MSG**

[В приведенном выше примере](#fetch-messages-from-server-and-save-to-disc), электронные письма сохраняются в формате EML. Чтобы сохранить электронные письма в формате MSG, [ImapClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessage/#fetchmessage/) метод должен быть вызван. Он возвращает сообщение в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) Затем можно вызвать метод для сохранения сообщения в MSG. В следующем фрагменте кода показано, как сохранять сообщения в формате MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SavingMessagesFromIMAPServer-SavingMessagesFromIMAPServer.cs" >}}

## **Групповая выборка сообщений**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) обеспечивает [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) метод, который принимает итерацию последовательных номеров или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Следующий фрагмент кода демонстрирует использование [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) метод получения сообщений по порядковым номерам и уникальному идентификатору.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapFetchGroupMessages-1.cs" >}}


## **Список сообщений с поддержкой пейджинга**

В сценариях, когда почтовый сервер содержит большое количество сообщений в почтовом ящике, часто требуется перечислить или получить сообщения с поддержкой пейджинга. API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) позволяет получать сообщения с сервера с поддержкой пейджинга.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.cs" >}}

## **Список вложений к сообщениям**

Чтобы получить информацию о вложениях, таких как имя и размер, без извлечения данных вложения, попробуйте использовать следующие API:

- *Aspose.Email.Clients.Imap.ImapAttachmentInfo* - Представляет собой информацию о вложении.
- *Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection* - Представляет собой коллекцию [ImapAttachmentInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) class.
- *Вложения aspose.email.clients.imap.List (целочисленный порядковый номер)* - Получает информацию о каждом вложении в сообщении.

Пример кода со следующими шагами покажет вам, как использовать API:

1. Позвоните [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/) метод на объекте IMapClient. Этот метод вернет коллекцию IMapMessageInfoCollection, содержащую информацию о сообщениях в почтовом ящике.
2. Просмотрите каждое сообщение в коллекции MessageInfoCollection, используя цикл foreach.
3. Позвоните [ListAttachments()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/#imapclientlistattachments-method) метод на объекте IMapClient, передающий свойство SequenceNumber объекта сообщения в качестве параметра. Этот метод вернет коллекцию IMAPAttachmentInfoCollection, содержащую информацию о вложениях в сообщении.
4. Просмотрите каждое вложение в коллекции AttachmentInfoCollection, используя цикл foreach.
5. Во внутреннем цикле вы можете получить доступ к информации о каждом вложении, используя свойства объекта AttachmentInfo. В этом примере имя и размер каждого вложения регистрируются в консоли с помощью `Console.WriteLine()`.
  
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

## **Получение папок и рекурсивное чтение сообщений**

В этой статье большинство [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) функции используются для создания приложения, рекурсивно перечисляющего все папки и подпапки с сервера IMAP. Оно также сохраняет сообщения в каждой папке и подпапке в формате MSG на локальном диске. На диске папки и сообщения создаются и сохраняются в той же иерархической структуре, что и на сервере IMAP. В следующем фрагменте кода показано, как рекурсивно получать информацию о сообщениях и подпапках.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ReadMessagesRecursively-ReadMessagesRecursively.cs" >}}

## **Получение дополнительных параметров в виде сводной информации**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrieveExtraParameters-RetrieveExtraParametersAsSummaryInformation.cs" >}}

## **Получение информации в заголовке списка «Отказаться от подписки»**

Заголовок List-Unsubscribe содержит URL-адрес для отказа от подписки на списки рассылки, например на рекламные объявления, информационные бюллетени и т. д. Чтобы получить заголовок List-Unsubscribe, используйте [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) собственность [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) класс. В следующем примере показано использование [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) свойство для получения заголовка List-Unsubscribe.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-GetListUnsubscribeHeader-1.cs" >}}
