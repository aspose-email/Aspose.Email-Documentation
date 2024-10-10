---
title: "Работа с сообщениями с IMAP-сервера"
url: /ru/python-net/working-with-messages-from-imap-server/
weight: 70
type: docs
---


## **Получение идентификационной информации для сообщений, полученных из почтового ящика**

При получении и обработке электронных писем вы можете извлекать детали сообщений с помощью их последовательных номеров.

Для взаимодействия с IMAP-почтовым ящиком используются следующие функции:

- [Aspose.Email.ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) класс - представляет идентификационную информацию о сообщении в почтовом ящике.

- [Aspose.Email.ImapMessageInfo.sequence_number](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) свойство - последовательный номер сообщения.

- [Aspose.Email.ImapMessageInfo.unique_id](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) свойство - уникальный идентификатор сообщения.


Ниже приведен фрагмент кода, показывающий, как получить идентификационную информацию о сообщениях:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

msg_infos = client.list_messages("INBOX")

for msg_info in msg_infos:
    # извлечение по последовательному номеру
    msg = client.fetch_message(msg_info.sequence_number)

    # извлечение по уникальному идентификатору
    msg = client.fetch_message(msg_info.unique_id)
```


## **Список MIME-идентификаторов сообщений с сервера**
ImapMessageInfo предоставляет MIME MessageId для идентификации сообщений без извлечения полного сообщения. Ниже приведен фрагмент кода, показывающий, как перечислить MIME messageId.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.py" >}}

## **Список сообщений с сервера**

Метод 'list_messages' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) извлекает список всех сообщений из текущей выбранной папки (в данном случае "Входящие"). Этот список содержит объекты метаданных сообщений, которые обычно включают информацию, такую как идентификаторы сообщений, последовательные номера, UIDs и, возможно, сводные данные, такие как темы сообщений или информация о отправителе.

Ниже приведен фрагмент кода, демонстрирующий, как извлечь метаданные сообщений из Входящих и напечатать общее количество содержащихся в них сообщений:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")

messages = client.list_messages()
print(f"Всего сообщений: {len(messages)}")
```

## **Рекурсивный список сообщений с сервера**
Протокол IMAP поддерживает рекурсивное перечисление сообщений из папки почтового ящика. Это помогает перечислить сообщения из подпапок. Ниже приведен фрагмент кода, показывающий, как рекурсивно перечислить сообщения.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.py" >}}

## **Список сообщений с помощью MultiConnection**

Класс [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) предоставляет свойство 'use_multi_connection' для использования нескольких соединений для операций с высокой нагрузкой. Вы также можете установить количество соединений в режиме многосоединения, используя свойство 'connections_quantity'. Ниже приведен фрагмент кода, демонстрирующий использование режима многосоединения при перечислении сообщений:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")
client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

message_info_col = client.list_messages(True)
```
*Пожалуйста, имейте в виду, что использование этого режима не обязательно приведет к увеличению производительности.*

## **Получение сообщений в порядке убывания**

Задача достигается путем определения настроек страницы для извлечения сообщений. Для этой цели используйте свойство 'ascending_sorting' класса [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class), который является частью модуля IMAP-клиента. Установите атрибут 'ascending_sorting' на объекте PageSettings в False. Это указывает на то, что сообщения должны быть отсортированы по убыванию по умолчанию при извлечении. Ниже приведен фрагмент кода, показывающий, как извлечь сообщения в порядке убывания:

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

## **Извлечение сообщений с сервера и сохранение на диск**
Класс ImapClient может извлекать сообщения с IMAP-сервера и сохранять сообщения в формате EML на локальном диске. Для сохранения сообщений на диск требуется выполнить следующие шаги:

1. Создайте экземпляр класса ImapClient.
1. Укажите имя хоста, имя пользователя и пароль в конструкторе ImapClient.
1. Выберите папку, используя метод SelectFolder().
1. Вызовите метод ListMessages для получения объекта ImapMessageInfoCollection.
1. Переберите коллекцию ImapMessageInfoCollection, вызовите метод SaveMessage() и укажите путь к выходному файлу и имя файла.

Ниже приведен фрагмент кода, показывающий, как извлечь электронные письма с сервера и сохранить их.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FetchEmailMessageFromServer-FetchEmailMessageFromServer.py" >}}

## **Сохранение сообщений в формате MSG**
В приведенном выше примере электронные письма сохраняются в формате EML. Чтобы сохранить электронные письма в формате MSG, необходимо вызвать метод ImapClient.FetchMessage(). Он возвращает сообщение в экземпляре класса MailMessage. Затем можно вызвать метод MailMessage.Save(), чтобы сохранить сообщение в формате MSG. Ниже приведен фрагмент кода, показывающий, как сохранить сообщения в формате MSG.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SavingMessageFromIMAPServer-SavingMessageFromIMAPServer.py" >}}

## **Извлечение сообщений по последовательному номеру или уникальному идентификатору**

Библиотека позволяет генерировать два списка сообщений: один с последовательными номерами, другой с уникальными идентификаторами всех сообщений во входящих. Чтобы извлечь сообщения с IMAP-сервера по этим идентификаторам, используйте метод 'fetch_messages' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class). Ниже приведен фрагмент кода, демонстрирующий, как перечислить сообщения по идентификаторам:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Перечисление сообщений
message_info_col = client.list_messages()
print("Количество ListMessages:", message_info_col.count)

# Получаем последовательные номера и уникальные идентификаторы
sequence_number_ar = [mi.sequence_number for mi in message_info_col]
unique_id_ar = [mi.unique_id for mi in message_info_col]

# Извлечение сообщений по последовательному номеру
fetched_messages_by_snum = client.fetch_messages(sequence_number_ar)
print("FetchMessages-sequenceNumberAr Count:", len(fetched_messages_by_snum))

# Извлечение сообщений по UID
fetched_messages_by_uid = client.fetch_messages(unique_id_ar)
print("FetchMessages-uniqueIdAr Count:", len(fetched_messages_by_uid))
```

## **Перечисление сообщений с поддержкой постраничной навигации**
В ситуациях, когда почтовый сервер содержит большое количество сообщений в почтовом ящике, часто требуется перечислить или извлечь сообщения с поддержкой постраничной навигации. API Aspose.Email для ImapClient позволяет вам извлекать сообщения с сервера с поддержкой постраничной навигации.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.py" >}}

## **Список вложений сообщений**

Чтобы получить информацию о вложениях, такую как имя, размер без извлечения данных вложения, используйте следующие ресурсы библиотеки:

- [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class) класс - представляет информацию о вложении (размер, имя, тип медиа).

- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfocollection/#imapattachmentinfocollection-class) класс - представляет коллекцию [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class).

- '`list_attachments(sequence_number)`' метод класса [`ImapClient`](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) - получает итерабельную или коллекцию информации о вложениях для сообщения.

```py
# Перечисление сообщений
message_info_col = client.list_messages()

# Перебор каждого сообщения
for message_info in message_info_col:
    print(f"Вложения для сообщения с последовательным номером {message_info.sequence_number}:")

    # Перечисление вложений для текущего сообщения
    attachment_info_col = client.list_attachments(message_info.sequence_number)

    # Перебор каждого вложения
    for attachment_info in attachment_info_col:
        print(f"Вложение: {attachment_info.name} (размер: {attachment_info.size})")
```
## **Получение папок и чтение сообщений рекурсивно**

[ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) использует рекурсивный метод для перечисления папок и подпапок с IMAP-сервера. Тот же метод также используется для чтения и сохранения сообщений на локальный диск в формате MSG. Папки и сообщения создаются и сохраняются в той же иерархической структуре, что и на IMAP-сервере. Ниже приведен фрагмент кода, показывающий, как получить папки и сообщения рекурсивно:

```py
import aspose.email as ae
import os

# Рекурсивный метод для получения сообщений из папок и подпапок
def list_messages_in_folder(folder_info, root_folder, client):
    # Создаем папку на диске (такое же имя, как на IMAP-сервере)
    current_folder = os.path.join(root_folder, folder_info.name)
    os.makedirs(current_folder, exist_ok=True)

    # Чтение сообщений из текущей папки, если она может быть выбрана
    if folder_info.selectable:
        # Отправить команду статуса для получения информации о папке
        folder_info_status = client.get_folder_info(folder_info.name)
        print(
            f"Папка {folder_info_status.name} выбрана. Новые сообщения: {folder_info_status.new_message_count}, "
            f"Всего сообщений: {folder_info_status.total_message_count}"
        )

        # Выберите текущую папку и перечислите сообщения
        client.select_folder(folder_info.name)
        msg_info_coll = client.list_messages()
        print("Перечисление сообщений....")
        for msg_info in msg_info_coll:
            # Получение темы и других свойств сообщения
            print("Тема:", msg_info.subject)
            print(
                f"Прочитано: {msg_info.is_read}, Последнее: {msg_info.recent}, Ответили: {msg_info.answered}"
            )

            # Избавление от символов, таких как ? и :, которые не должны быть включены в имя файла
            # Сохранение сообщения в формате MSG
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
        print(f"{folder_info.name} не может быть выбрана.")

    try:
        # Если у этой папки есть подпапки, рекурсивно вызовите этот метод для получения сообщений
        folder_info_collection = client.list_folders(folder_info.name)
        for subfolder_info in folder_info_collection:
            list_messages_in_folder(subfolder_info, root_folder, client)
    except Exception:
        pass

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

try:
    # Корневая папка (которая будет создана на диске) состоит из хоста и имени пользователя
    root_folder = f"{client.host}-{client.username}"

    # Создаем корневую папку и перечисляем все папки с IMAP-сервера
    os.makedirs(root_folder, exist_ok=True)
    folder_info_collection = client.list_folders()
    for folder_info in folder_info_collection:
        # Вызываем рекурсивный метод для чтения сообщений и получения подпапок
        list_messages_in_folder(folder_info, root_folder, client)
except Exception as ex:
        print("\n", ex)

print("\nЗагружены сообщения рекурсивно с IMAP-сервера.")
```


## **Извлечение дополнительных параметров как сводной информации**

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetreiveExtraParametersAsSummaryInformation-RetreiveExtraParametersAsSummaryInformation.py" >}}

## **Получение информации заголовка List-Unsubscribe**

Заголовок "ListUnsubscribe" обычно включается в заголовки электронных сообщений, отправленных почтовыми рассылками или автоматизированными системами. Он предоставляет ссылку или адрес электронной почты, который получатели могут использовать для отказа от рассылки или автоматических писем. Aspose.Email предоставляет свойство 'list_unsubscribe' класса [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) для получения этого заголовка. Ниже приведен фрагмент кода, демонстрирующий использование этого свойства и который может быть использован как часть системы для автоматизации процесса отказа от нежелательных электронных писем:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

message_info_col = client.list_messages()

# Перебор каждого сообщения
for imap_message_info in message_info_col:
    print("Заголовок ListUnsubscribe:", imap_message_info.list_unsubscribe)
```