---
title: "Программирование с Thunderbird"
url: /ru/java/programming-with-thunderbird/
weight: 100
type: docs
---

## **Чтение сообщений из MBOX**
[Mozilla Thunderbird](https://www.thunderbird.net/en-US/) — это кросс-платформенный почтовый клиент с открытым исходным кодом, разработанный Фондом Mozilla. Он хранит электронные письма в собственной файловой структуре, управляя индексами сообщений и подпапками через собственные форматы файлов. Aspose.Email может работать со структурами хранения почты Thunderbird. Класс [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) позволяет разработчикам читать сообщения из файла хранения почты Mozilla Thunderbird. В этой статье показано, как читать сообщения из хранилища почты Thunderbird:

1. Откройте файл хранения Thunderbird в *FileStream*.
1. Создайте экземпляр класса [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) и передайте вышеупомянутый поток в конструктор.
1. Вызовите [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)), чтобы получить первое сообщение.
1. Используйте тот же [ReadNextMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageReader#readNextMessage\(\)) в цикле while, чтобы прочитать все сообщения.
1. Закройте все потоки.

Следующий фрагмент кода показывает, как прочитать все сообщения из хранилища почты Thunderbird.
```Java
//Получение информации о маркере при чтении сообщений из файла хранения Mbox
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
```

### **Настройка параметров загрузки при чтении сообщений из MBOX**

API Aspose.Email позволяет выполнять следующие манипуляции с сообщениями при их чтении из файла MBOX:

**Преобразование сообщений из MBOX в PST с сохранением вложений TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailStorageConverter.setMboxMessageOptions(emlLoadOptions);
// Преобразование сообщений из mbox в pst с сохранением вложений tnef.
PersonalStorage storage = MailStorageConverter.mboxToPst("Input.mbox", "Output.pst");
```
[MailStorageConverter.MboxMessageOptions()](https://reference.aspose.com/email/java/com.aspose.email/mailstorageconverter/) свойство - Получает или задает параметры загрузки электронных писем при разборе хранилища Mbox.

**Чтение сообщений с сохранением вложений TNEF**

```java
MboxrdStorageReader reader = new MboxrdStorageReader("Input.mbox", new MboxLoadOptions());
// Чтение сообщений с сохранением вложений tnef.
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
MailMessage eml = reader.readNextMessage(emlLoadOptions);
```
[MboxrdStorageReader.readNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/emlloadoptions/#getPreserveTnefAttachments--) метод - Параметр EmlLoadOptions задает параметры при чтении сообщения из хранилища Mbox.

**Перечисление сообщений с сохранением вложений TNEF**

```java
EmlLoadOptions emlLoadOptions = new EmlLoadOptions();
emlLoadOptions.setPreserveTnefAttachments(true);
// Перечисление сообщений с сохранением вложений tnef.
for (MailMessage message : reader.enumerateMessages(emlLoadOptions)) {
    // выполнить что-то
}
```
[MboxrdStorageReader.enumerateMessages(EmlLoadOptions options)](https://reference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader/#enumerateMessages--) метод - Указывает EmlLoadOptions при чтении сообщения из хранилища Mbox.

## **Извлечение сообщений из MBOX по идентификаторам**

Иногда необходимо извлечь выбранные сообщения по идентификаторам. Например, ваше приложение хранит идентификаторы в базе данных и извлекает сообщения по запросу. Это эффективный способ избежать перебора всего хранилища каждый раз для поиска конкретного сообщения для извлечения. Чтобы реализовать эту функцию для файлов MBOX, Aspose.Email предоставляет следующие методы и классы:

- Класс [MboxMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/) с свойством [EntryId](https://reference.aspose.com/email/java/com.aspose.email/mboxmessageinfo/#getEntryId--) - Получает идентификатор записи.
- Метод [enumerateMessageInfo()](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#enumerateMessageInfo--) класса [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) - Предоставляет перечислитель, который поддерживает итерацию сообщений в хранилище.
- Метод [extractMessage(String id)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#extractMessage-java.lang.String-com.aspose.email.EmlLoadOptions-) класса [MboxStorageReader](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/) - Получает сообщение из MBOX.

Пример кода ниже демонстрирует, как извлечь сообщения из MBOX по идентификаторам:

```java
MboxStorageReader reader = MboxStorageReader.createReader("my.mbox", new MboxLoadOptions());

for (MboxMessageInfo msgInfo : reader.enumerateMessageInfo()) {
    MailMessage eml = reader.extractMessage(msgInfo.getEntryId(), new EmlLoadOptions());
}
```
**Примечание:** Идентификатор сообщения уникален в пределах файла хранилища. Идентификаторы создаются Aspose.Email и не могут быть использованы в других сторонних библиотеках или приложениях для обработки MBOX.

## **Запись сообщений**
Класс [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) предоставляет возможность записывать новые сообщения в файл хранения почты Thunderbird. Чтобы записать сообщения:

1. Откройте файл хранения Thunderbird в *FileStream*.
1. Создайте экземпляр класса [MboxrdStorageWriter](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragewriter) и передайте вышеупомянутый поток в конструктор.
1. Подготовьте новое сообщение, используя класс [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage).
1. Вызовите метод [WriteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/MboxrdStorageWriter#writeMessage\(com.aspose.email.MailMessage\)) и передайте вышеупомянутый экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage), чтобы добавить сообщение в хранилище Thunderbird.
1. Закройте все потоки.

Следующий фрагмент кода показывает, как записать сообщения в хранилище почты Thunderbird.
```Java
//Получение информации о маркере при записи сообщений в файл хранения Mbox
try (FileOutputStream writeStream = new FileOutputStream(dataDir + "inbox")) {
    try (MboxrdStorageWriter writer = new MboxrdStorageWriter(writeStream, false)) {
        MailMessage msg = MailMessage.load(dataDir + "Message.msg");
        String[] fromMarker = {null};
        writer.writeMessage(msg, fromMarker);
        System.out.println(fromMarker[0]);
    }
}
```

## **Получение общего числа сообщений из файла MBox**
Класс [MboxrdStorageReader](https://apireference.aspose.com/email/java/com.aspose.email/mboxrdstoragereader) предоставляет возможность прочитать количество доступных элементов в файле MBox. Это может быть использовано для разработки приложений, показывающих прогресс действия при обработке такого файла.
```Java
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader("inbox.dat", lo)) {
    System.out.println("Общее количество сообщений в файле Mbox: " + reader.getTotalItemsCount());
}
```

## **Получение текущего размера сообщения**
```Java
FileInputStream stream = new FileInputStream(dataDir + "ExampleMbox.mbox");
MboxLoadOptions lo = new MboxLoadOptions();
try (MboxrdStorageReader reader = new MboxrdStorageReader(stream, lo)) {
    MailMessage msg = null;
    while ((msg = reader.readNextMessage()) != null) {
        //возвращает количество прочитанных байт
        long currentDataSize = reader.getCurrentDataSize();
        System.out.println("Прочитанные байты: " + currentDataSize);
    }
}
```

## **Установка предпочтительной текстовой кодировки при загрузке файлов Mbox**

Метод [setPreferredTextEncoding(Charset value)](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/#setPreferredTextEncoding-java.nio.charset.Charset-) класса [MboxLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/mboxloadoptions/) получает или задает предпочтительное кодирование для сообщений. Создайте читатель для файла Mbox с заданными параметрами загрузки, и ваши сообщения с закодированным содержимым будут правильно прочитаны и обработаны. Следующий пример кода показывает, как реализовать эту функцию в проекте:

```Java
MboxLoadOptions lo = new MboxLoadOptions();
lo.setPreferredTextEncoding(Charset.forName("utf-8"));
MboxrdStorageReader reader = new MboxrdStorageReader("sample.mbox", lo);
MailMessage message = reader.readNextMessage();
```

## **Разделение хранилища Mbox на меньшие части**

Aspose.Email предоставляет следующие компоненты, предназначенные для более точного управления обработкой хранилища Mbox, позволяя вам разбивать большие файлы на управляемые части и реализовывать пользовательские действия в процессе:

- Метод [MboxStorageReader.SplitInto(long chunkSize, String outputPath)](https://reference.aspose.com/email/java/com.aspose.email/mboxstoragereader/#splitInto-long-java.lang.String-) - Позволяет вам разделить хранилище Mbox на меньшие части, упрощая управление и обработку больших файлов Mbox.

MboxStorageReader.SplitInto(long chunkSize, String outputPath, String partFileNamePrefix) Вариант предыдущего метода, этот также позволяет вам указать пользовательский префикс для имен файлов разделенных Mbox.

MboxStorageReader.setEmlCopyingEventHandler Событие, которое происходит перед тем, как электронное письмо копируется в новый файл Mbox. Вы можете настроить действия перед обработкой электронных писем.

MboxStorageReader.setEmlCopiedEventHandler Событие, которое происходит после того, как электронное письмо скопировано в новый файл Mbox. Вы можете выполнить действия после обработки электронных писем.

MboxStorageReader.setMboxFileCreatedEventHandler Событие, которое происходит, когда создается новый файл Mbox. Вы можете обработать это событие, чтобы реагировать на создание файла.

MboxStorageReader.setMboxFileFilledEventHandler Событие, которое происходит, когда новый файл Mbox заполняется электронными письмами. Вы можете реагировать на заполнение файла электронными письмами.

NewStorageEventHandler(Object sender, NewStorageEventArgs e) Представляет делегат для обработки событий, которые происходят после создания или обработки нового файла хранилища.

MimeItemCopyEventHandler(Object sender, MimeItemCopyEventArgs e) Представляет делегат для обработки событий, связанных с копированием элементов Mime, обычно используемый в сценариях, когда объект MailMessage копируется из одного хранилища в другое.

NewStorageEventArgs Представляет аргументы, используемые в событиях, которые вызываются после создания нового файла хранилища или после его обработки.

MimeItemCopyEventArgs Представляет аргументы события, связанные с копированием объекта MailMessage из одного хранилища в другое, как до начала копирования, так и после его завершения.

Пример кода ниже демонстрирует, как взаимодействовать с файлами Mbox, обрабатывать события, связанные с этими файлами, и выполнять операции, такие как разделение хранилища Mbox на меньшие части, при этом отслеживая количество сообщений и частей:

```java
messageCount = 0;
partCount = 0;

// Создание экземпляра MboxrdStorageReader
MboxLoadOptions lo = new MboxLoadOptions();
lo.setLeaveOpen(false);
MboxrdStorageReader mbox = new MboxrdStorageReader("my.mbox", lo);

// Подписка на события
mbox.setMboxFileCreatedEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Создан новый файл Mbox: " + e.getFileName());
        partCount++;
    }
});

mbox.setMboxFileFilledEventHandler(new NewStorageEventHandler() {
    public void invoke(Object sender, NewStorageEventArgs e) {
        System.out.println("Файл Mbox заполнен сообщениями: " + e.getFileName());
    }
});

mbox.setEmlCopiedEventHandler(new MimeItemCopyEventHandler() {
    public void invoke(Object sender, MimeItemCopyEventArgs e) {
        System.out.println("Сообщение добавлено в новый файл Mbox. Тема: " + e.getItem().getSubject());
        messageCount++;
    }
});

// Разделение хранилища Mbox на меньшие части
mbox.splitInto(10000000, testOutPath, "Prefix");

// Вывод окончательного количества сообщений и частей
System.out.println("Всего добавленных сообщений: " + messageCount);
System.out.println("Всего созданных частей: " + partCount);
```