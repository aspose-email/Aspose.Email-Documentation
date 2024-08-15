---
title: "Программирование с Thunderbird"
url: /ru/python-net/programming-with-thunderbird/
weight: 80
type: docs
---


## **Чтение сообщений**
Mozilla Thunderbird — это кроссплатформенный почтовый клиент с открытым исходным кодом, разработанный Mozilla Foundation. Он хранит электронные письма в собственной файловой структуре, управляя индексами сообщений и подпапками с помощью собственных форматов файлов. Aspose.Email может работать со структурами хранения почты Thunderbird. Класс MboxRDStorageReader позволяет разработчикам читать сообщения из файла почтового хранилища Mozilla Thunderbird. В этой статье показано, как читать сообщения из хранилища электронной почты Thunderbird:

1. Откройте файл хранилища Thunderbird
1. Создайте экземпляр класса MboxRDStorageReader и передайте указанный выше поток в конструктор.
1. Вызовите read_next_message (), чтобы получить первое сообщение.
1. Используйте один и тот же цикл read_next_message () in a while для чтения всех сообщений.
1. Закройте все ручьи.

В следующем фрагменте кода показано, как читать все сообщения из почтового хранилища Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.py" >}}

### **Получение свойств сообщения**

Для чтения и извлечения информации из файла Mbox Aspose.Email предоставляет [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) класс для создания объекта чтения для файла Mbox и [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) класс для загрузки файла. Следующие свойства файла [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) класс можно использовать для доступа к конкретным сведениям о сообщении и их отображения:

- 'date' — возвращает дату сообщения.
- 'from_address' — получает адрес отправителя.
- 'subject' — получает тему сообщения.
- 'to' — возвращает коллекцию адресов, содержащую получателей сообщения.
- 'cc' — получает коллекцию адресов, содержащую получателей CC.
- 'bcc' — получает коллекцию адресов, содержащую BCC-получателей сообщения.

В следующем примере кода показано использование этих свойств для чтения и извлечения информации о сообщениях из файла Mbox:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader(file_name, ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    print(f"Subject: {mbox_message_info.subject}")
    print(f"Date: {mbox_message_info.date}")
    print(f"From: {mbox_message_info.from_address}")
    print(f"To: {mbox_message_info.to}")
    print(f"CC: {mbox_message_info.cc}")
    print(f"Bcc: {mbox_message_info.bcc}")
```
### **Извлечение сообщений из MBOX по идентификаторам**

Чтобы читать сообщения из файла MBOX, Aspose.Email предоставляет метод create_reader () [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) класс для создания объекта чтения для файла. Он принимает имя файла и [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) в качестве аргументов, позволяющих пользователю при необходимости загрузить файл MBOX с определенными параметрами.

Для извлечения сообщений используются следующие методы и свойства:

- метод 'enumerate_message_info () ' [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class — выполняет итерацию по каждому сообщению в файле MBOX.
- метод 'extract_message ()» [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class - извлекает каждое сообщение по идентификатору записи.
- свойство 'entry_id' [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class - Получает идентификатор записи.

Наконец, сообщение преобразуется в формат EML с помощью [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

В приведенном ниже примере кода показано использование этих функций для чтения и извлечения сообщений из файла MBOX:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader("my.mbox", ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    eml = reader.extract_message(mbox_message_info.entry_id, ae.EmlLoadOptions())

```
### **Настройка параметров загрузки при чтении сообщений из MBOX**

С помощью электронной почты Aspose.Email [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) класс, вы можете указать дополнительные параметры при загрузке MailMessage из формата Eml. Например, вы можете настроить опцию сохранения вложений TNEF при загрузке файла EML с помощью свойства 'preserve_tnef_attachments' [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) class.

Вы можете прочитать следующее сообщение электронной почты из файла mbox, используя указанные параметры загрузки с помощью метода read_next_message в [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) класс и конвертируйте файл в формат PST с помощью метода mbox_to_pst [MailStorageConverter](https://reference.aspose.com/email/python-net/aspose.email.storage/mailstorageconverter/#mailstorageconverter-class) класс.

В приведенном ниже примере кода показано использование этих методов и свойств для работы с файлами хранения электронной почты, включая чтение сообщений из формата mbox, сохранение вложений TNEF и преобразование сообщений из формата mbox в pst:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxrdStorageReader(fileName, ae.storage.mbox.MboxLoadOptions())
# Read messages preserving tnef attachments.
load_options = ae.EmlLoadOptions()
load_options.preserve_tnef_attachments = True
eml = reader.read_next_message(load_options)
ae.storage.MailStorageConverter.MboxMessageOptions(load_options)
# Convert messages from mbox to pst preserving tnef attachments.
pst = ae.storage.MailStorageConverter.mbox_to_pst("Input.mbox", "Output.pst")
```
### **Настройка предпочтительной кодировки текста при загрузке файлов Mbox для чтения**

Можно указать текстовую кодировку, которая будет использоваться при загрузке файла MBOX. Свойство 'preferred_text_encoding' доступно для [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) класс задает дополнительную опцию и гарантирует, что сообщение с закодированным содержимым будет правильно прочитано и обработано.

В следующем фрагменте кода показано, как использовать эту функцию в проекте:

```py
import aspose.email as ae

load_options = ae.storage.mbox.MboxLoadOptions()
load_options.preferred_text_encoding = 'utf-8'
reader = ae.storage.mbox.MboxrdStorageReader("sample.mbox", load_options)
message = reader.read_next_message()
```
### **Преобразование MBOX в PST Сохранение или удаление подписи**

Чтобы удалить подпись из файла в процессе преобразования, задайте свойству MboxTopstConversionOptions.remove_signature значение true.

В следующем примере кода показано, как использовать это свойство:
```py
import aspose.email as ae

personalStorage = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)
conversion_options = ae.storage.MboxToPstConversionOptions()
conversion_options.remove_signature = True
ae.storage.MailStorageConverter.mbox_to_pst( ae.storage.mbox.MboxrdStorageReader("source.mbox", ae.storage.mbox.MboxLoadOptions()), personalStorage, "Inbox", conversion_options)
```

## **Написание сообщений**
Класс MboxRDStorageWriter позволяет записывать новые сообщения в файл почтового хранилища Thunderbird. Чтобы писать сообщения, выполните следующие действия:

1. Откройте файл хранилища Thunderbird в FileStream.
1. Создайте экземпляр класса MboxRDStorageWriter и передайте указанный выше поток в конструктор.
1. Подготовьте новое сообщение с помощью класса MailMessage.
1. Вызовите метод write_message () и передайте указанный выше экземпляр MailMessage, чтобы добавить сообщение в хранилище Thunderbird.
1. Закройте все трансляции.

В следующем фрагменте кода показано, как записывать сообщения в почтовое хранилище Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-CreateNewMessagesToThunderbird-CreateNewMessagesToThunderbird.py" >}}
## **Получение общего количества сообщений из файла MBox**
Класс MboxRDStorageReader предоставляет возможность считывать количество элементов, доступных в файле MBox. Это можно использовать для разработки приложений для отображения хода выполнения действий при обработке такого файла.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.py" >}}
## **Получить текущий размер сообщения**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.py" >}}
