---
title: "Программирование с Thunderbird"
url: /ru/net/programming-with-thunderbird/
weight: 110
type: docs
---


## **Чтение файлов MBOX**

[Мозилла Тандерберд](https://www.thunderbird.net/en-US/) это кроссплатформенный почтовый клиент с открытым исходным кодом, разработанный Mozilla Foundation. Он хранит электронные письма в собственной файловой структуре, управляя индексами сообщений и подпапками с помощью собственных форматов файлов. Aspose.Email может работать со структурами хранения почты Thunderbird. [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) класс позволяет разработчикам читать сообщения из файла почтового хранилища Мозилла Тандерберд. В этой статье показано, как читать сообщения из хранилища электронной почты Thunderbird:

1. Откройте файл хранилища Thunderbird в *FileStream*.
1. Создайте экземпляр [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) класс и передайте указанный выше поток конструктору.
1. Call [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) чтобы получить первое сообщение.
1. Используйте то же самое [ReadNextMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage/) через некоторое время, чтобы прочитать все сообщения.
1. Закройте все ручьи.

В следующем фрагменте кода показано, как читать все сообщения из почтового хранилища Thunderbird.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read);
// Создайте экземпляр MboxrdStorageReader class and pass the stream
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

[MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) класс содержит следующие свойства для получения информации о сообщении:

- DateTime [Date](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/date/#mboxmessageinfodate-property) - Получает дату сообщения
- MailAddress [From](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/from/#mboxmessageinfofrom-property) - Получает адрес отправителя
- string [Subject](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/subject/) - Получает тему сообщения
- MailAddressCollection [To](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/to/) - Получает коллекцию адресов, содержащую получателей сообщения
- MailAddressCollection [CC](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/cc/) - Получает коллекцию адресов, содержащую получателей CC
- MailAddressCollection [Bcc](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/bcc/) - Получает коллекцию адресов, содержащую получателей сообщения BCC

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

The [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) класс включает [EnumerateMessageInfo()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/enumeratemessageinfo/) метод, позволяющий перебирать каждое сообщение в файле MBOX. Используя этот метод, можно извлекать отдельные сообщения без необходимости многократного перемещения по всему хранилищу. Это повышает производительность и сокращает время обработки.

The [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) класс предоставляет [EntryId](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/entryid/) свойство, обеспечивающее доступ к уникальным идентификаторам для каждого сообщения в файле MBOX. Этот идентификатор можно сохранить в базе данных или использовать в качестве справочника для быстрого поиска и извлечения определенных сообщений при необходимости.

The [Извлечь сообщение (строковый идентификатор)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) метод в [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) класс позволяет разработчикам извлекать сообщения на основе их уникального EntryID. С помощью [Извлечь сообщение (строковый идентификатор)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/extractmessage/) Метод, вы можете использовать сохраненный EntryID для получения соответствующего сообщения и выполнения дополнительных операций с ним.

В следующем примере кода показано, как извлекать сообщения из файла MBOX с помощью идентификаторов:

```cs
MboxStorageReader reader = MboxStorageReader.CreateReader("my.mbox", new MboxLoadOptions());

foreach (MboxMessageInfo msgInfo in reader.EnumerateMessageInfo())
{
    MailMessage eml = reader.ExtractMessage(msgInfo.EntryId, new EmlLoadOptions());
}
```

### **Настройка параметров загрузки при чтении сообщений из MBOX**

Следующие функции позволят вам указать различные параметры, связанные с загрузкой и обработкой сообщений:

- Свойство MailStorageConverter.mboxMessageOptions — определяет или задает параметры загрузки электронной почты при анализе хранилища Mbox.

- Метод MboxRDStorageReader.ReadNextMessage (параметры EMLLoadOptions) — параметр emlloadOptions указывает параметры при чтении сообщения из хранилища Mbox.

**Пример кода**

```cs
var reader = new MboxrdStorageReader(fileName, new MboxLoadOptions());
// Read messages preserving tnef attachments.
var eml = reader.ReadNextMessage(new EmlLoadOptions {PreserveTnefAttachments = true});
MailStorageConverter.MboxMessageOptions(new EmlLoadOptions {PreserveTnefAttachments = true});
// Convert messages from mbox to pst preserving tnef attachments.
var pst = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```

### **Настройка предпочтительной кодировки текста при загрузке файлов Mbox для чтения**

Опция кодирования доступна для класса MboxRDStorageReader. Это предоставляет дополнительные возможности для загрузки файла mbox и обеспечивает правильное чтение и обработку сообщений с закодированным содержимым. В следующем фрагменте кода показано, как настроить кодировку текста в соответствии с вашими потребностями:

```cs
var reader = new MboxrdStorageReader("sample.mbox", new MboxLoadOptions() { PreferredTextEncoding = Encoding.UTF8});
var message = reader.ReadNextMessage();
```

### **Получение общего количества сообщений из файла MBox**

The [MboxrdStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/) класс предоставляет возможность считывать количество элементов, доступных в файле MBox. Это можно использовать для разработки приложений, показывающих ход выполнения действий при обработке такого файла.

```cs
// The path to the File directory.
var dataDir = RunExamples.GetDataDir_Thunderbird();

using (var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Read))
using (var reader = new MboxrdStorageReader(stream, false))
{
    Console.WriteLine("Total number of messages in Mbox file: " + reader.GetTotalItemsCount());
}
```

### **Получить текущий размер сообщения**

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

### **Преобразование MBOX в PST Сохранение или удаление подписи**

Чтобы удалить подпись из файла в процессе преобразования, установите [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/) недвижимость для *true*.

В следующем примере кода показано, как использовать это свойство:

```cs
var pstDataStream = new MemoryStream();
var personalStorage = PersonalStorage.Create(pstDataStream, FileFormatVersion.Unicode);
MailStorageConverter.MboxToPst(new MboxrdStorageReader(new FileStream(fileName, FileMode.Open, FileAccess.Read), new MboxLoadOptions()),
personalStorage,
    "Inbox",
new MboxToPstConversionOptions() { RemoveSignature = true });
```

## **Запись файлов MBOX**

The [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) класс предоставляет возможность записывать новые сообщения в файл почтового хранилища Thunderbird. Чтобы писать сообщения, выполните следующие действия:

1. Откройте файл хранилища Thunderbird в *FileStream*.
1. Создайте экземпляр [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/) класс и передайте указанный выше поток конструктору.
1. Подготовьте новое сообщение, используя [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Позвоните [WriteMessage()](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/writemessage/#writemessage/) метод и передайте вышеуказанное [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) экземпляр для добавления сообщения в хранилище Thunderbird.
1. Закройте все трансляции.

В следующем фрагменте кода показано, как писать сообщения в почтовое хранилище Thunderbird.

```cs
// Open the storage file with FileStream
var stream = new FileStream(dataDir + "ExampleMbox.mbox", FileMode.Open, FileAccess.Write);

// Initialize MboxStorageWriter and pass the above stream to it
var writer = new MboxrdStorageWriter(stream, false);
// Подготовьте новое сообщение, используя MailMessage class
var message = new MailMessage("from@domain.com", "to@domain.com", Guid.NewGuid().ToString(), "added from Aspose.Email");
message.IsDraft = false;
// Add this message to storage
writer.WriteMessage(message);
// Close all related streams
writer.Dispose();
stream.Close();
```

