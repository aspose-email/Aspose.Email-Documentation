---
title: "Программирование с Thunderbird"
url: /ru/java/programming-with-thunderbird/
weight: 100
type: docs
---

## **Чтение сообщений от MBOX**
[Мозилла Тандерберд](https://www.thunderbird.net/en-US/) это кроссплатформенный почтовый клиент с открытым исходным кодом, разработанный Mozilla Foundation. Он хранит электронные письма в собственной файловой структуре, управляя индексами сообщений и подпапками с помощью собственных форматов файлов. Aspose.Email может работать со структурами хранения почты Thunderbird. [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) класс позволяет разработчикам читать сообщения из файла почтового хранилища Мозилла Тандерберд. В этой статье показано, как читать сообщения из хранилища электронной почты Thunderbird:

1. Откройте файл хранилища Thunderbird в *FileStream*.
1. Создайте экземпляр [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) класс и передайте указанный выше поток конструктору.
1. Call [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) чтобы получить первое сообщение.
1. Используйте то же самое [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) через некоторое время, чтобы прочитать все сообщения.
1. Закройте все ручьи.

В следующем фрагменте кода показано, как читать все сообщения из почтового хранилища Thunderbird.
~~~Java
//Getting Marker information while reading messages from Mbox storage file
try (FileInputStream stream = new FileInputStream(dataDir + "Outlook.pst")) {
    MboxLoadOptions lo = new MboxLoadOptions();
    lo.setLeaveOpen(false);
    try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
        MailMessage msg;
        String[] fromMarker = {null};
        while ((msg = reader.readNextMessage(/* out */fromMarker)) != null) {
            System.out.println(fromMarker[0]);
        }
    }
}
~~~

### **Настройка параметров загрузки при чтении сообщений из MBOX**

Aspose.Email API позволяет выполнять следующие манипуляции с сообщениями при чтении их из файла MBOX:

**Конвертируйте сообщения из MBOX в PST с сохранением вложений TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailStorageConverter.setMboxMessageOptions(emlLoadOptions);
// Convert messages from mbox to pst preserving tnef attachments.
PersonalStorage storage = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```
[MailStorageConverter.MboxMessageOptions()](https://reference.aspose.com/email/java/com.aspose.email/mailstorageconverter/) свойство - Определяет или задает параметры загрузки электронной почты при анализе хранилища Mbox.

**Чтение сообщений с сохранением вложений TNEF**

```java
MboxrdStorageReader reader = new MboxrdStorageReader("Input.mbox", new MboxLoadOptions());
// Read messages preserving tnef attachments.
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailMessage eml = reader.readNextMessage(emlLoadOptions);
```
[MBOXRD StorageReader. Прочитайте следующее сообщение (опции загрузки EMLO)](https://reference.aspose.com/email/java/com.aspose.email/emlloadoptions/#getPreserveTnefAttachments--) метод - параметр EmlloadOptions задает параметры при чтении сообщения из хранилища Mbox.

**Перечисление сообщений с сохранением вложений TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
// Enumerate messages preserving tnef attachments.
for (MailMessage message : reader.enumerateMessages(emlLoadOptions)) {
    // do something
}
```
[MBOXRD StorageReader. перечисление сообщений (опции загрузки EMLO)](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader/#enumerateMessages--) метод — указывает параметры EMLLoadOptions при чтении сообщения из хранилища Mbox.

## **Извлечение сообщений из MBOX по идентификаторам**

Иногда требуется извлечь выбранные сообщения по идентификаторам. Например, ваше приложение хранит идентификаторы в базе данных и извлекает сообщение по запросу. Это эффективный способ избежать необходимости каждый раз просматривать все хранилище в поисках нужного сообщения для извлечения. Чтобы реализовать эту функцию для файлов MBOX, Aspose.Email предоставляет следующие методы и классы:

- [MboxMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/) класс с [EntryId](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/#getEntryId--) свойство - получает идентификатор записи.
- [enumerateMessageInfo()](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#enumerateMessageInfo--) метод [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) class - предоставляет перечислитель, который поддерживает итерацию сообщений в хранилище.
- [Извлечь сообщение (строковый идентификатор)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#extractMessage-java.lang.String-com.aspose.email.EmlLoadOptions-) метод [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) class - получает сообщение от MBOX.

В приведенном ниже примере кода показано, как извлекать сообщения из MBOX по идентификаторам:

```java
MboxStorageReader reader = MboxStorageReader.createReader("my.mbox", new MboxLoadOptions());

for (MboxMessageInfo msgInfo : reader.enumerateMessageInfo()) {
    MailMessage eml = reader.extractMessage(msgInfo.getEntryId(), new EmlLoadOptions());
}
```
**Note:** Идентификатор сообщения уникален в файле хранилища. Идентификаторы создаются Aspose.Email и не могут использоваться в других сторонних библиотеках или приложениях для обработки MBOX.

## **Написание сообщений**
The [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) класс предоставляет возможность записывать новые сообщения в файл почтового хранилища Thunderbird. Чтобы писать сообщения, выполните следующие действия:

1. Откройте файл хранилища Thunderbird в *FileStream*.
1. Создайте экземпляр [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) класс и передайте указанный выше поток конструктору.
1. Подготовьте новое сообщение, используя [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) class.
1. Позвоните [WriteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageWriter#writeMessage\(com.aspose.email.MailMessage\)) метод и передайте вышеуказанное [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) экземпляр для добавления сообщения в хранилище Thunderbird.
1. Закройте все трансляции.

В следующем фрагменте кода показано, как записывать сообщения в почтовое хранилище Thunderbird.
~~~Java
//Getting marker information while writing messages to Mbox storage file
try (FileOutputStream writeStream = new FileOutputStream(dataDir + "inbox")) {
    try (MboxrdStorageWriter writer = new MboxrdStorageWriter(writeStream, false)) {
        MailMessage msg = MailMessage.load(dataDir + "Message.msg");
        String[] fromMarker = {null};
        writer.writeMessage(msg, fromMarker);
        System.out.println(fromMarker[0]);
    }
}
~~~

## **Получение общего количества сообщений из файла MBox**
The [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) класс предоставляет возможность считывать количество элементов, доступных в файле MBox. Это можно использовать для разработки приложений, показывающих ход выполнения действий при обработке такого файла.
~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader("inbox.dat", lo)) {
    System.out.println("Total number of messages in Mbox file: " + reader.getTotalItemsCount());
}
~~~

## **Получить текущий размер сообщения**
~~~Java
FileInputStream stream = new FileInputStream(dataDir + "ExampleMbox.mbox");
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
    MailMessage msg = null;
    while ((msg = reader.readNextMessage()) != null) {
        //returns the number of bytes read
        long currentDataSize = reader.getCurrentDataSize();
        System.out.println("Bytes read: " + currentDataSize);
    }
}
~~~

## **Установите предпочтительную кодировку текста при загрузке файлов Mbox**

The [Задайте предпочтительную кодировку текста (значение кодировки)](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/#setPreferredTextEncoding-java.nio.charset.Charset-) метод [MboxLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/) класс получает или задает предпочтительную кодировку для сообщений. Создайте программу для чтения файла Mbox с заданными параметрами загрузки, и ваши сообщения с закодированным содержимым будут правильно прочитаны и обработаны. В следующем примере кода показано, как реализовать эту функцию в проекте:

~~~Java
MboxLoadOptions lo = new MboxLoadOptions();
lo.setPreferredTextEncoding(Charset.forName("utf-8"));
MboxrdStorageReader reader = new MboxrdStorageReader("sample.mbox", lo);
MailMessage message = reader.readNextMessage();
~~~

## **Разделите хранилище Mbox на более мелкие части**

Aspose.Email предоставляет следующие компоненты, разработанные для большего контроля над обработкой хранилища Mbox, позволяющие разбивать большие файлы на управляемые части и выполнять собственные действия во время процесса:

- [MBOX StorageReader.Splitin (длинный размер блока, путь к строковому выходу)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#splitInto-long-java.lang.String-) метод — позволяет разделить хранилище Mbox на более мелкие части, что упрощает управление большими файлами Mbox и их обработку.

MboxStorageReader.splitinto (long ChunkSize, String OutputPath, String PartFilenamePrefix) Этот вариант предыдущего метода также позволяет указать собственный префикс для разделенных имен файлов Mbox.

Событие MboxStorageReader.setEmlCopyingEventHandler Это событие происходит перед копированием электронного письма в новый файл Mbox. Можно настроить действия перед обработкой электронных писем.

Событие MboxStorageReader.setEmlCopiedEventHandler Это событие возникает после копирования электронного письма в новый файл Mbox. С электронными письмами можно выполнять действия по последующей обработке.

Событие MboxStorageReader.setMboxFileCreatedEventHandler Это событие возникает при создании нового файла Mbox. Это событие можно обработать, чтобы отреагировать на создание файла.

Событие MboxStorageReader.setMboxFilleFilleDeventHandler Это событие возникает, когда новый файл Mbox заполняется электронными письмами. Вы можете ответить на заполнение файла электронными письмами.

NewStorageEventHandler (отправитель объекта, NewStorageEventArgs e) представляет собой делегата для обработки событий, возникающих после создания или обработки нового файла хранилища.

MimeItemCopyEventHandler (отправитель объекта, MimeItemCopyEventArgs e) представляет собой делегата для обработки событий, связанных с копированием элементов Mime, обычно используемых в сценариях копирования объекта MailMessage из одного хранилища в другое.

NewStorageEventArgs представляет собой аргументы, используемые в событиях, возникающих после создания или обработки нового файла хранилища.

MimeItemCopyEventArgs представляет собой аргументы события, связанные с копированием объекта MailMessage из одного хранилища в другое до начала или после завершения копирования.

В приведенном ниже примере кода показано, как работать с файлами Mbox, обрабатывать события, связанные с этими файлами, и выполнять такие операции, как разделение хранилища Mbox на более мелкие части при одновременном отслеживании количества сообщений и количества частей:

```java
messageCount = 0;
partCount = 0;

// Create an instance of MboxrdStorageReader
MboxLoadOptions lo = new MboxLoadOptions();
lo.setLeaveOpen(false);
MboxrdStorageReader mbox = new MboxrdStorageReader("my.mbox", lo);

// Subscribe to events
mbox.setMboxFileCreatedEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("New Mbox file created: " + e.getFileName());
        partCount++;
    }
});

mbox.setMboxFileFilledEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Mbox file filled with messages: " + e.getFileName());
    }
});

mbox.setEmlCopiedEventHandler(new MimeItemCopyEventHandler() {
    public void invoke(Object sender, MimeItemCopyEventArgs e) {
        System.out.println("Message added to new Mbox file. Subject: " + e.getItem().getSubject());
        messageCount++;
    }
});

// Split the Mbox storage into smaller parts
mbox.splitInto(10000000, testOutPath, "Prefix");

// Output the final messageCount and partCount
System.out.println("Total messages added: " + messageCount);
System.out.println("Total parts created: " + partCount);
```