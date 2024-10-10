---
title: "Программирование с Thunderbird"
url: /ru/python-net/programming-with-thunderbird/
weight: 80
type: docs
---


## **Чтение сообщений**
Mozilla Thunderbird — это клиент электронной почты с открытым исходным кодом и кроссплатформенной архитектурой, разработанный Фондом Mozilla. Он хранит электронные письма в собственной файловой структуре, управляя индексами сообщений и подпапками с помощью проприетарных форматов файлов. Aspose.Email может работать со структурами хранения почты Thunderbird. Класс MboxrdStorageReader позволяет разработчикам читать сообщения из файла хранения почты Mozilla Thunderbird. В этой статье показано, как читать сообщения из хранилища электронной почты Thunderbird:

1. Откройте файл хранения Thunderbird
1. Создайте экземпляр класса MboxrdStorageReader и передайте вышеуказанный поток в конструктор.
1. Вызовите метод read_next_message(), чтобы получить первое сообщение.
1. Используйте тот же метод read_next_message() в цикле while, чтобы прочитать все сообщения.
1. Закройте все потоки.

Следующий фрагмент кода показывает, как прочитать все сообщения из хранилища почты Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.py" >}}

### **Получение свойств сообщения**

Чтобы читать и извлекать информацию из файла Mbox, Aspose.Email предоставляет класс [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) для создания объекта чтения для файла Mbox и класс [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) для загрузки файла. Следующие свойства класса [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) могут быть использованы для доступа и отображения конкретных деталей сообщения:

- 'date' - Получает дату сообщения.
- 'from_address' - Получает адрес отправителя.
- 'subject' - Получает тему сообщения.
- 'to' - Получает коллекцию адресов, содержащую получателей сообщения.
- 'cc' - Получает коллекцию адресов, содержащую получателей CC.
- 'bcc' - Получает коллекцию адресов, содержащую получателей BCC сообщения.

Следующий кодовый пример демонстрирует использование этих свойств для чтения и извлечения информации о сообщениях из файла Mbox: 

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

Чтобы читать сообщения из файла MBOX, Aspose.Email предоставляет метод 'create_reader()' класса [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) для создания объекта чтения для файла. Он принимает имя файла и [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) в качестве параметров, позволяя пользователю загрузить файл MBOX с конкретными опциями при необходимости.

Чтобы извлечь сообщения, используются следующие методы и свойства:

- Метод 'enumerate_message_info()' класса [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) - Перебирает каждое сообщение в файле MBOX.
- Метод 'extract_message()' класса [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) - Извлекает каждое сообщение по его идентификатору.
- Свойство 'entry_id' класса [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) - Получает идентификатор записи.

Наконец, сообщение преобразуется в формат EML с использованием [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

Ниже приведен пример кода, демонстрирующий использование этих функций для чтения и извлечения сообщений из файла MBOX:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader("my.mbox", ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    eml = reader.extract_message(mbox_message_info.entry_id, ae.EmlLoadOptions())

```
### **Настройка параметров загрузки при чтении сообщений из MBOX**

С помощью класса Aspose.Email [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) вы можете задать дополнительные параметры при загрузке MailMessage из формата Eml. Например, вы можете установить параметр для сохранения вложений TNEF при загрузке файла EML с помощью свойства 'preserve_tnef_attachments' класса [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

Вы можете прочитать следующее электронное сообщение из файла mbox, используя указанные параметры загрузки с помощью метода 'read_next_message' класса [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) и преобразовать файл в формат PST с помощью метода 'mbox_to_pst' класса [MailStorageConverter](https://reference.aspose.com/email/python-net/aspose.email.storage/mailstorageconverter/#mailstorageconverter-class).

Ниже приведен пример кода, демонстрирующий использование этих методов и свойств для работы с файлами хранения электронной почты, включая чтение сообщений из формата mbox, сохранение вложений TNEF и преобразование сообщений из mbox в формат pst:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxrdStorageReader(fileName, ae.storage.mbox.MboxLoadOptions())
# Чтение сообщений с сохранением вложений tnef.
load_options = ae.EmlLoadOptions()
load_options.preserve_tnef_attachments = True
eml = reader.read_next_message(load_options)
ae.storage.MailStorageConverter.MboxMessageOptions(load_options)
# Преобразование сообщений из mbox в pst с сохранением вложений tnef.
pst = ae.storage.MailStorageConverter.mbox_to_pst("Input.mbox", "Output.pst")
```
### **Установка предпочтительного текстового кодирования при загрузке файлов Mbox для чтения**

Вы можете указать текстовое кодирование, которое будет использоваться при загрузке файла MBOX. Свойство 'preferred_text_encoding', доступное для класса [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class), устанавливает дополнительный параметр и гарантирует, что сообщение с закодированным содержимым будет правильно прочитано и обработано.

Следующий фрагмент кода показывает, как использовать эту функцию в проекте:

```py
import aspose.email as ae

load_options = ae.storage.mbox.MboxLoadOptions()
load_options.preferred_text_encoding = 'utf-8'
reader = ae.storage.mbox.MboxrdStorageReader("sample.mbox", load_options)
message = reader.read_next_message()
```
### **Преобразование MBOX в PST с сохранением или удалением подписи**

Чтобы удалить подпись из файла в процессе преобразования, установите свойство MboxToPstConversionOptions.remove_signature в true.

Следующий пример кода показывает, как использовать это свойство:
```py
import aspose.email as ae

personalStorage = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)
conversion_options = ae.storage.MboxToPstConversionOptions()
conversion_options.remove_signature = True
ae.storage.MailStorageConverter.mbox_to_pst( ae.storage.mbox.MboxrdStorageReader("source.mbox", ae.storage.mbox.MboxLoadOptions()), personalStorage, "Inbox", conversion_options)
```

## **Запись сообщений**
Класс MboxrdStorageWriter предоставляет возможность записывать новые сообщения в файл хранения почты Thunderbird. Для записи сообщений:

1. Откройте файл хранения Thunderbird в FileStream.
1. Создайте экземпляр класса MboxrdStorageWriter и передайте вышеуказанный поток в конструктор.
1. Подготовьте новое сообщение с помощью класса MailMessage.
1. Вызовите метод write_message() и передайте вышеуказанный экземпляр MailMessage, чтобы добавить сообщение в хранилище Thunderbird.
1. Закройте все потоки.

Следующий фрагмент кода показывает вам, как записывать сообщения в хранилище почты Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-CreateNewMessagesToThunderbird-CreateNewMessagesToThunderbird.py" >}}
## **Получение общего количества сообщений из файла MBox**
Класс MboxrdStorageReader предоставляет возможность прочитать количество элементов, доступных в файле MBox. Это можно использовать для разработки приложений, отображающих процесс активности во время обработки такого файла.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.py" >}}
## **Получить текущий размер сообщения**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.py" >}}