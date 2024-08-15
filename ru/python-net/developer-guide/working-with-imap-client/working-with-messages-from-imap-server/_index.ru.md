---
title: "Работа с сообщениями с сервера IMAP"
url: /ru/python-net/working-with-messages-from-imap-server/
weight: 70
type: docs
---


## **Получение идентификационной информации для сообщений, полученных из почтового ящика**

При получении и обработке сообщений электронной почты вы можете получить подробную информацию о сообщениях, используя их порядковые номера.

Для взаимодействия с почтовым ящиком IMAP используются следующие функции:

- [Aspose.Email.ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) class — представляет идентификационную информацию о сообщении в почтовом ящике.

- [Aspose.Email.ImapMessageInfo.sequence_number](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) свойство - порядковый номер сообщения.

- [Aspose.Email.ImapMessageInfo.unique_id](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) свойство - уникальный идентификатор сообщения.


В приведенном ниже фрагменте кода показано, как получить идентификационную информацию о сообщениях:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

msg_infos = client.list_messages("INBOX")

for msg_info in msg_infos:
    # fetch by sequence number
    msg = client.fetch_message(msg_info.sequence_number)

    # fetch by unique id
    msg = client.fetch_message(msg_info.unique_id)
```


## **Отображение идентификаторов сообщений MIME с сервера**
IMapMessageInfo предоставляет MIME MessageID для идентификации сообщения без извлечения всего сообщения. В следующем фрагменте кода показано, как указать MIME MessageID.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.py" >}}

## **Список сообщений с сервера**

Метод 'list_messages' [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс извлекает список всех сообщений из выбранной в данный момент папки (в данном случае «Входящие»). Этот список содержит объекты метаданных сообщений, которые обычно включают такую информацию, как идентификаторы сообщений, порядковые номера, идентификаторы UID и, возможно, сводные данные, такие как темы или сведения об отправителе.

В приведенном ниже фрагменте кода показано, как извлечь метаданные сообщений из папки «Входящие» и распечатать общее количество содержащихся в них сообщений:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")

messages = client.list_messages()
print(f"Total Messages: {len(messages)}")
```

## **Рекурсивный список сообщений с сервера**
Протокол IMAP поддерживает рекурсивный список сообщений из папки почтового ящика. Это также помогает отображать сообщения из подпапок папки. В следующем фрагменте кода показано, как рекурсивно перечислять сообщения.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.py" >}}

## **Список сообщений с помощью MultiConnection**

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс предоставляет свойство use_multi_connection для использования нескольких подключений для высоконагруженных операций. Можно также задать количество подключений в режиме нескольких подключений с помощью свойства 'connections_quantity'. Приведенный ниже фрагмент кода демонстрирует использование режима нескольких подключений в списках сообщений: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")
client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

message_info_col = client.list_messages(True)
```
*Обратите внимание, что использование этого режима не обязательно должно приводить к повышению производительности.*

## **Получайте сообщения в порядке убывания**

Задача решается путем определения параметров разбиения на страницы для извлечения сообщений. Для этого используйте свойство 'ascending_sorting' в поле [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class) класс, входящий в модуль клиента IMAP. Задайте атрибуту ascending_sorting в объекте PageSettings значение False. Это означает, что во время извлечения сообщения по умолчанию следует сортировать в порядке убывания. В следующем фрагменте кода показано, как извлекать сообщения в порядке убывания:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

page_settings = ae.clients.imap.PageSettings
page_settings.ascending_sorting = False
page_info = client.list_messages_by_page(5, page_settings)
messages = page_info.items

for message in messages:
    print(message.subject)
```

## **Получение сообщений с сервера и сохранение на диск**
Класс IMAPClient может получать сообщения с сервера IMAP и сохранять сообщения в формате EML на локальный диск. Для сохранения сообщений на диск необходимо выполнить следующие шаги:

1. Создайте экземпляр класса IMAPClient.
1. Укажите имя хоста, имя пользователя и пароль в конструкторе IMapClient.
1. Выберите папку с помощью метода selectFolder ().
1. Вызовите метод ListMessages, чтобы получить объект IMapMessageInfoCollection.
1. Просмотрите коллекцию IMapMessageInfoCollection, вызовите метод saveMessage () и укажите путь к выходным данным и имя файла.

В следующем фрагменте кода показано, как получать сообщения электронной почты с сервера и сохранять их.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FetchEmailMessageFromServer-FetchEmailMessageFromServer.py" >}}
## **Сохранение сообщений в формате MSG**
В приведенном выше примере электронные письма сохраняются в формате EML. Чтобы сохранить электронные письма в формате MSG, необходимо вызвать метод IMAPClient.fetchMessage (). Он возвращает сообщение в экземпляре класса MailMessage. Затем можно вызвать метод MailMessage.save () для сохранения сообщения в MSG. В следующем фрагменте кода показано, как сохранять сообщения в формате MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SavingMessageFromIMAPServer-SavingMessageFromIMAPServer.py" >}}

## **Получайте сообщения по порядковому номеру или уникальному идентификатору**

Библиотека позволяет создать два списка сообщений, один из которых содержит порядковые номера, а другой — уникальные идентификаторы всех сообщений в папке «Входящие». Чтобы получать сообщения с сервера IMAP по этим идентификаторам, используйте метод fetch_messages [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс. В приведенном ниже фрагменте кода показано, как перечислить сообщения по идентификаторам:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# List messages
message_info_col = client.list_messages()
print("ListMessages Count:", message_info_col.count)

# Get sequence numbers and unique IDs
sequence_number_ar = [mi.sequence_number for mi in message_info_col]
unique_id_ar = [mi.unique_id for mi in message_info_col]

# Fetch messages by sequence number
fetched_messages_by_snum = client.fetch_messages(sequence_number_ar)
print("FetchMessages-sequenceNumberAr Count:", len(fetched_messages_by_snum))

# Fetch messages by UID
fetched_messages_by_uid = client.fetch_messages(unique_id_ar)
print("FetchMessages-uniqueIdAr Count:", len(fetched_messages_by_uid))
```

## **Список сообщений с поддержкой пейджинга**
В сценариях, когда почтовый сервер содержит большое количество сообщений в почтовом ящике, часто требуется перечислить или получить сообщения с поддержкой пейджинга. IMapClient API от Aspose.Email позволяет получать сообщения с сервера с поддержкой пейджинга.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.py" >}}

## **Список вложений к сообщениям**

Чтобы получить информацию о вложениях, такую как имя, размер, без извлечения данных вложений, используйте следующие ресурсы библиотеки:

- [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class) класс — представляет информацию о вложении (размер, имя, тип носителя).

- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfocollection/#imapattachmentinfocollection-class) класс - представляет собой коллекцию [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class).

- '`list_attachments(sequence_number)`'метод [`ImapClient`](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class - получает итерацию или набор вложенной информации для сообщения.

```py
# List messages
message_info_col = client.list_messages()

# Iterate through each message
for message_info in message_info_col:
    print(f"Attachments for message with sequence number {message_info.sequence_number}:")

    # List attachments for the current message
    attachment_info_col = client.list_attachments(message_info.sequence_number)

    # Iterate through each attachment
    for attachment_info in attachment_info_col:
        print(f"Attachment: {attachment_info.name} (size: {attachment_info.size})")
```
## **Получение папок и рекурсивное чтение сообщений**

[ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) использует рекурсивный метод для вывода списка папок и подпапок с сервера IMAP. Этот же метод также используется для чтения и сохранения сообщений на локальном диске в формате MSG. Папки и сообщения создаются и сохраняются в той же иерархической структуре, что и на сервере IMAP. В следующем фрагменте кода показано, как рекурсивно получать папки и сообщения:

```py
import aspose.email as ae
import os

# Recursive method to get messages from folders and sub-folders
def list_messages_in_folder(folder_info, root_folder, client):
    # Create the folder on disk (same name as on the IMAP server)
    current_folder = os.path.join(root_folder, folder_info.name)
    os.makedirs(current_folder, exist_ok=True)

    # Read the messages from the current folder, if it is selectable
    if folder_info.selectable:
        # Send a status command to get folder info
        folder_info_status = client.get_folder_info(folder_info.name)
        print(
            f"{folder_info_status.name} folder selected. New messages: {folder_info_status.new_message_count}, "
            f"Total messages: {folder_info_status.total_message_count}"
        )

        # Select the current folder and list messages
        client.select_folder(folder_info.name)
        msg_info_coll = client.list_messages()
        print("Listing messages....")
        for msg_info in msg_info_coll:
            # Get subject and other properties of the message
            print("Subject:", msg_info.subject)
            print(
                f"Read: {msg_info.is_read}, Recent: {msg_info.recent}, Answered: {msg_info.answered}"
            )

            # Get rid of characters like ? and :, which should not be included in a file name
            # Save the message in MSG format
            file_name = (
                msg_info.subject.replace(":", " ").replace("?", " ")
                + "-"
                + str(msg_info.sequence_number)
                + ".msg"
            )
            msg = client.fetch_message(msg_info.sequence_number)
            msg.save(
                os.path.join(current_folder, file_name),
                ae.SaveOptions.default_msg_unicode,
            )
        print("============================\n")
    else:
        print(f"{folder_info.name} is not selectable.")

    try:
        # If this folder has sub-folders, call this method recursively to get messages
        folder_info_collection = client.list_folders(folder_info.name)
        for subfolder_info in folder_info_collection:
            list_messages_in_folder(subfolder_info, root_folder, client)
    except Exception:
        pass



client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

try:
    # The root folder (which will be created on disk) consists of host and username
    root_folder = f"{client.host}-{client.username}"

    # Create the root folder and list all the folders from the IMAP server
    os.makedirs(root_folder, exist_ok=True)
    folder_info_collection = client.list_folders()
    for folder_info in folder_info_collection:
        # Call the recursive method to read messages and get sub-folders
        list_messages_in_folder(folder_info, root_folder, client)
except Exception as ex:
        print("\n", ex)

print("\nDownloaded messages recursively from IMAP server.")
```


## **Получение дополнительных параметров в виде сводной информации**


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetreiveExtraParametersAsSummaryInformation-RetreiveExtraParametersAsSummaryInformation.py" >}}

## **Получение информации в заголовке списка «Отказаться от подписки»**

Заголовок «ListUnsubscribe» обычно включается в заголовки сообщений электронной почты, отправляемых списками рассылки или автоматизированными системами электронной почты. В нем содержится ссылка или адрес электронной почты, по которым получатели могут отказаться от подписки на список рассылки или автоматические электронные письма. Aspose.Email предоставляет свойство list_unsubscribe, принадлежащее [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) класс для получения этого заголовка. Приведенный ниже фрагмент кода демонстрирует использование этого свойства и может использоваться как часть системы для автоматизации процесса отписки от нежелательных писем:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

message_info_col = client.list_messages()

# Iterate through each message
for imap_message_info in message_info_col:
    print("ListUnsubscribe Header:", imap_message_info.list_unsubscribe)
```
