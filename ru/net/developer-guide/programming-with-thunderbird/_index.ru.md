---
title: "Программирование с Thunderbird"
url: /ru/net/programming-with-thunderbird/
weight: 110
type: docs
---


## **Чтение файлов MBOX**

[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) — это клиент электронной почты с открытым исходным кодом и кроссплатформенной поддержкой, разработанный фондом Mozilla. Он хранит электронные письма в собственной файловой структуре, управляя индексами сообщений и подпапками через собственные форматы файлов. Aspose.Email может работать со структурами хранения почты Thunderbird. Класс [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) позволяет разработчикам читать сообщения из файла хранения электронной почты Mozilla Thunderbird. В этой статье показано, как читать сообщения из хранилища электронной почты Thunderbird:

1. Откройте файл хранения Thunderbird в *FileStream*.
1. Создайте экземпляр класса [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) и передайте вышеуказанный поток в конструктор.
1. Вызовите [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) чтобы получить первое сообщение.
1. Используйте тот же [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) в цикле while, чтобы прочитать все сообщения.
1. Закройте все потоки.

Следующий фрагмент кода показывает, как прочитать все сообщения из хранилища почты Thunderbird.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read);
// Create an instance of the MboxrdStorageReader class and pass the stream
var reader = new MboxrdStorageReader(stream, false);
// Start reading messages
var message = reader.ReadNextMessage();

// Read all messages in a loop
while (message != null)
{
    // Manipulate message - show contents
    Console.WriteLine("Subject: " + message.Subject);
    // Save this message in EML or MSG format
    message.Save(message.Subject + ".eml", SaveOptions.DefaultEml);
    message.Save(message.Subject + ".msg", SaveOptions.DefaultMsgUnicode);

    // Get the next message
    message = reader.ReadNextMessage();
}

// Close the streams
reader.Dispose();
stream.Close();
```

### **Получение свойств сообщения**

Класс [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) содержит следующие свойства для получения информации о сообщении:

- DateTime [Date](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/date/#mboxmessageinfodate-property) - Получает дату сообщения
- MailAddress [From](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/from/#mboxmessageinfofrom-property) - Получает адрес отправителя
- string [Subject](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/subject/) - Получает тему сообщения
- MailAddressCollection [To](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/to/) - Получает коллекцию адресов, содержащую получателей сообщения
- MailAddressCollection [CC](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/cc/) - Получает коллекцию адресов, содержащую адресаты CC
- MailAddressCollection [Bcc](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/bcc/) - Получает коллекцию адресов, содержащую адресаты BCC сообщения

**Пример кода**

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader(fileName, new MboxLoadOptions());

foreach (var mboxMessageInfo in reader.EnumerateMessageInfo())
{
    Console.Writeline($"Subject: {mboxMessageInfo.Subject}");
    Console.Writeline($"Date: {mboxMessageInfo.Date}");
    Console.Writeline($"From: {mboxMessageInfo.From}");
    Console.Writeline($"To: {mboxMessageInfo.To}");
    Console.Writeline($"CC: {mboxMessageInfo.CC}");
    Console.Writeline($"Bcc: {mboxMessageInfo.Bcc}");
}
```

### **Извлечение сообщений из MBOX по идентификаторам**

Класс [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) включает метод [EnumerateMessageInfo()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/), который позволяет перебирать каждое сообщение в файле MBOX. С помощью этого метода становится возможным извлечение отдельных сообщений без необходимости повторного прохода по всему хранилищу. Это улучшает производительность и снижает время обработки.

Класс [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) предоставляет свойство [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/entryid/), которое предоставляет доступ к уникальным идентификаторам для каждого сообщения в файле MBOX. Этот идентификатор может быть сохранен в базе данных или использован в качестве ссылки для быстрого поиска и извлечения конкретных сообщений по мере необходимости.

Метод [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) в классе [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) позволяет разработчикам извлекать сообщения на основе их уникального EntryId. С помощью метода [ExtractMessage(string id)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) вы можете использовать сохраненный EntryId для извлечения соответствующего сообщения и выполнения с ним дополнительных операций.

Следующий пример кода демонстрирует, как извлечь сообщения из файла MBOX с использованием идентификаторов:

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader("my.mbox", new MboxLoadOptions());

foreach (MboxMessageInfo msgInfo in reader.EnumerateMessageInfo())
{
    MailMessage eml = reader.ExtractMessage(msgInfo.EntryId, new EmlLoadOptions());
}
```

### **Настройка параметров загрузки при чтении сообщений из MBOX** 

Следующие функции позволят вам указать различные параметры, связанные с загрузкой и обработкой сообщений:

- Свойство MailStorageConverter.MboxMessageOptions - Получает или задает параметры загрузки электронной почты при парсинге хранения Mbox.

- Метод MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options) - Параметр EmlLoadOptions указывает параметры при чтении сообщения из хранения Mbox.

**Пример кода**

```cs
var reader = new MboxrdStorageReader(fileName, new MboxLoadOptions());
// Read messages preserving tnef attachments.
var eml = reader.ReadNextMessage(new EmlLoadOptions {PreserveTnefAttachments = true});
MailStorageConverter.MboxMessageOptions(new EmlLoadOptions {PreserveTnefAttachments = true});
// Convert messages from mbox to pst preserving tnef attachments.
var pst = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```

### **Установка предпочтительной кодировки текста при загрузке файлов Mbox для чтения**

Опция кодировки доступна для класса MboxrdStorageReader. Это обеспечивает дополнительные параметры для загрузки файла mbox и гарантирует, что сообщения с закодированным содержимым будут правильно прочитаны и обработаны. Следующий фрагмент кода показывает, как можно установить кодировку текста, которая удовлетворяет вашим потребностям:

```cs
var reader = new MboxrdStorageReader("sample.mbox", new MboxLoadOptions() { PreferredTextEncoding = Encoding.UTF8});
var message = reader.ReadNextMessage();
```

### **Получение общего количества сообщений из файла MBox**

Класс [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) предоставляет возможность прочитать количество элементов, доступных в файле MBox. Это можно использовать для разработки приложений, показывающих процесс выполнения операции над таким файлом.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    Console.WriteLine("Total number of messages in Mbox file: " + reader.GetTotalItemsCount());
}
```

### **Получение текущего размера сообщения**

```cs
using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    MailMessage msg;
    while ((msg = reader.ReadNextMessage()) != null)
    {
        long currentDataSize = reader.CurrentDataSize;

        msg.Dispose();
    }
}
```

### **Преобразование MBOX в PST с сохранением или удалением подписи**

Чтобы удалить подпись из файла в процессе преобразования, установите свойство [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage.mboxtopstconversionoptions/removesignature/) в *true*.

Следующий пример кода показывает, как использовать это свойство:

```cs
var pstDataStream = new MemoryStream();
var personalStorage = PersonalStorage.Create(pstDataStream, FileFormatVersion.Unicode);
MailStorageConverter.MboxToPst(new MboxrdStorageReader(new FileStream(fileName, FileMode.Open, FileAccess.Read), new MboxLoadOptions()),
personalStorage,
    "Inbox",
new MboxToPstConversionOptions() { RemoveSignature = true });
```

## **Запись файлов MBOX**

Класс [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) предоставляет возможность записывать новые сообщения в файл хранения электронной почты Thunderbird. Чтобы записать сообщения:

1. Откройте файл хранения Thunderbird в *FileStream*.
1. Создайте экземпляр класса [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) и передайте вышеуказанный поток в конструктор.
1. Подготовьте новое сообщение с помощью класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Вызовите метод [WriteMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage/) и передайте вышеуказанный экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) для добавления сообщения в хранилище Thunderbird.
1. Закройте все потоки.

Следующий фрагмент кода показывает, как записывать сообщения в хранилище электронной почты Thunderbird.

```cs
// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Write);

// Initialize MboxStorageWriter and pass the above stream to it
var writer = new MboxrdStorageWriter(stream, false);
// Prepare a new message using the MailMessage class
var message = new MailMessage("from@domain.com", "to@domain.com", Guid.NewGuid().ToString(), "added from Aspose.Email");
message.IsDraft = false;
// Add this message to storage
writer.WriteMessage(message);
// Close all related streams
writer.Dispose();
stream.Close();
```