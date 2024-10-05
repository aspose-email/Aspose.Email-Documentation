---
title: "Конвертация HTML в другие форматы"
url: /ru/net/converting-between-formats/convert-html-to-other-formats
weight: 60
type: docs
---

## **Конвертация HTML в EML**

Aspose.Email для .NET предоставляет метод для конвертации HTML файлов в формат EML с использованием методов [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) и [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) для загрузки существующего HTML файла и сохранения его в формате EML соответственно:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.eml", SaveOptions.DefaultEml);
```

В приведенном примере [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) позволяет указать дополнительные параметры при загрузке MailMessage из HTML формата. Следующий пример кода демонстрирует использование этого класса. В примере задается текстовое представление тела сообщения:

```cs
// Создание экземпляра HtmlLoadOptions
var loadOptions = new HtmlLoadOptions();

// Установка свойства ShouldAddPlainTextView в true для генерации представления в простом тексте вместе с HTML
loadOptions.ShouldAddPlainTextView = true;

// Загрузка HTML файла
var mailMessage = MailMessage.Load("input.html", loadOptions);

// Доступ к представлению в простом тексте email сообщения
var plainTextView = mailMessage.GetAlternateViewContent("text/plain");

// Печать или дальнейшая обработка представления в простом тексте
Console.WriteLine("Представление в простом тексте:");
Console.WriteLine(plainTextView);
```

## **Конвертация HTML в EMLX**

Вы можете легко конвертировать HTML файлы в EMLX. Все свойства и классы, предоставляемые API для конвертации HTML в EML, доступны и для этого типа конвертации:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.emlx", SaveOptions.DefaultEmlx);
```
Для дополнительных настроек см. параграф [Конвертация HTML в EML](#convert-html-to-eml).

## **Конвертация HTML в ICS**

Для выполнения задачи библиотека предлагает класс [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) для представления и управления календарными событиями. Следующий пример кода демонстрирует, как создать встречу из HTML контента и сохранить её в формате ICS (iCalendar):

```cs
// Пример HTML контента
var htmlContent = File.ReadAllText("content.html");

// Создание и инициализация экземпляра класса Appointment
var appointment = new Appointment(
    "Комната для переговоров 3 в главном офисе", // Место
    "Ежемесячная встреча",                          // Резюме
    "Пожалуйста, подтвердите вашу доступность.",    // Описание
    new DateTime(2015, 2, 8, 13, 0, 0),            // Дата начала
    new DateTime(2015, 2, 8, 14, 0, 0),            // Дата окончания
    "from@domain.com",                             // Организатор
    "attendees@domain.com")
{
    HtmlDescription = htmlContent
};

// Сохранение события в ICS файл
appointment.Save("output.ics", AppointmentSaveFormat.Ics);
```

## **Генерация MBOX из HTML контента**

Для выполнения конвертации HTML в MBOX используйте метод [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class), указав путь к HTML контенту и экземпляр [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Этот метод анализирует HTML контент и создаёт соответствующий объект MailMessage, сохраняя структуру и форматирование оригинального HTML. После загрузки HTML контента в объект MailMessage запишите сообщение в файл MBOX с помощью класса [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class):

```cs
using (var eml = MailMessage.Load("content.html", new HtmlLoadOptions())){
    using (var writer = new MboxrdStorageWriter("output.mbox", false)){
        writer.WriteMessage(eml);
    }
}
```

## **Конвертация HTML в MHTML**

Используйте метод [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) для загрузки существующего файла, указав путь к нему и экземпляр [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Этот метод анализирует HTML контент и создаёт соответствующий объект MailMessage, сохраняя структуру и форматирование оригинального HTML. После загрузки HTML контента в объект MailMessage разработчики могут сохранить его как MHTML файл, используя метод [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), указав желаемый путь к выходному файлу и используя опцию [SaveOptions.DefaultMhtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmhtml/):

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.mhtml", SaveOptions.DefaultMhtml);
```

Класс [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) предоставляет различные параметры для настройки поведения и настроек выходного MHTML файла вместо SaveOptions.DefaultMhtml. С его помощью можно указать дополнительные опции при сохранении MailMessage в формате MHTML.
Наиболее популярные из них:

- [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/mhtformatoptions/) - Позволяет настроить, как email сообщение сохраняется в формате MHT, чтобы наилучшим образом соответствовать вашим потребностям.
- [SaveAttachments](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveattachments/) - Получает или устанавливает значение, указывающее, нужно ли сохранять вложения.
- [SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Определяет, нужно ли сохранять все заголовки в выходном mhtml или нет. Значение по умолчанию - false.
- [PreserveOriginalDate](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/preserveoriginaldate/) - Определяет, нужно ли сохранять оригинальную дату в mail сообщении при сохранении или нет. Значение по умолчанию - true.

Следующий пример кода демонстрирует, как можно использовать эти свойства:

```cs
var mhtSaveOprtions = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader,
    SaveAttachments = true,
    SaveAllHeaders = true,
    PreserveOriginalDate = true
}
```

## **Конвертация HTML в MSG**

После загрузки HTML контента в объект MailMessage сохраните его как файл MSG, используя метод [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), указав желаемый путь к выходному файлу и используя опцию [SaveOptions.DefaultMsgUnicode](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmsgunicode/). Эта опция гарантирует, что выходной файл сохранен в формате MSG с кодировкой Unicode.

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.msg", SaveOptions.DefaultMsgUnicode);
```
Кроме того, Aspose.Email для .NET предлагает множество расширенных функций и опций для конвертации HTML в MSG:

## **Конвертация HTML в OFT**

После загрузки HTML контента в объект MailMessage сохраните его как файл OFT, используя метод [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), указав желаемый путь к выходному файлу и используя опцию [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/):

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("template.oft", SaveOptions.DefaultOft);
```

## **Добавление сообщения с исходным HTML контентом в PST**

Конвертация HTML в PST включает создание нового файла PST (Таблица персонального хранилища) с новой папкой, загрузку HTML файла и добавление его в новую папку:

1. Создайте экземпляр объекта PersonalStorage, представляющего новый файл PST, с помощью метода [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) класса [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
2. Получите корневую папку файла PST и добавьте к ней подпапку с помощью метода [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder) класса [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class).
3. Загрузите содержимое HTML файла в объект [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) с помощью метода [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) с экземпляром [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class), чтобы указать, что содержимое в формате HTML.
4. Добавьте загруженный объект MapiMessage (представляющий HTML контент) в папку в пределах файла PST с помощью метода [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/).

```cs
using (var pst = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
{ 
    var inbox = pst.RootFolder.AddSubFolder("Входящие");
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    inbox.AddMessage(msg);
}
```

## **Добавление сообщения с исходным HTML контентом в OST**

Следующий пример кода с этапами покажет, как эти компоненты работают вместе, чтобы добавить HTML контент в файл OST:

1. Загрузите существующий файл OST с помощью метода [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) класса [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class), который будет представлять файл хранения, в котором будут храниться email сообщения.
2. Загрузите HTML файл с помощью метода [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) класса [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class), представляющего email сообщение в формате Microsoft Outlook.
3. Укажите [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class), чтобы включить дополнительные опции при загрузке MailMessage из HTML формата.
4. Получите корневую папку файла OST, используя свойство [RootFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/rootfolder/) объекта [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
5. Получите папку Входящие в рамках файла OST, используя метод [GetSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder) на корневой папке.
6. Добавьте загруженный объект MapiMessage (представляющий HTML контент) в папку Входящие с помощью метода [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) на папке.

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    var folderInfo = ost.RootFolder.GetSubFolder("Входящие");
    folderInfo.AddMessage(msg);
}
``` 

## **Конвертация HTML в VCF**

Следующий пример кода демонстрирует, как создать элемент контакта, заполнить его HTML контентом и сохранить в файл VCF:

1. Прочитайте содержимое HTML файла в строковую переменную, используя метод File.ReadAllText.
2. Создайте новый объект MapiContact, инстанцируя класс [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/#mapicontact-class).
3. Установите свойства контакта: отображаемое имя, адрес электронной почты.
4. Установите тело контента контакта в HTML, используя [SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/setbodycontent/#setbodycontent).
5. Сохраните контакт как файл VCF, используя метод [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_4).

```cs
var content = File.ReadAllText("content.html");
            
// Создайте новый MapiContact
var contact = new MapiContact();
contact.NameInfo.DisplayName = "Джон Доу";
contact.ElectronicAddresses.Email1.EmailAddress = "john.doe@example.com";
contact.SetBodyContent(content, BodyContentType.Html);

// Сохраните контакт в файл VCF
contact.Save("contact.vcf", ContactSaveFormat.VCard)
```