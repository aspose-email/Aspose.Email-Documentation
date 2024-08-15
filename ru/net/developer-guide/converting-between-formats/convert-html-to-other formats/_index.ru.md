---
title: "Конвертируйте HTML в другие форматы"
url: /ru/net/converting-between-formats/convert-html-to-other-formats
weight: 60
type: docs
---

## **Конвертировать HTML в EML**

Aspose.Email для .NET предоставляет метод преобразования файлов HTML в формат EML с помощью [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) and [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) методы загрузки существующего HTML-файла и его сохранения в формате EML соответственно:


```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.eml", SaveOptions.DefaultEml);
```

В примере кода [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) класс позволяет указать дополнительные параметры при загрузке MailMessage из формата HTML. Следующий пример кода демонстрирует использование этого класса. В примере задано текстовое представление тела сообщения:

```cs
// Create an instance of HtmlLoadOptions
var loadOptions = new HtmlLoadOptions();

// Set the ShouldAddPlainTextView property to true to generate a plain text view along with HTML
loadOptions.ShouldAddPlainTextView = true;

// Load an HTML file
var mailMessage = MailMessage.Load("input.html", loadOptions);

// Access the plain text view of the email message
var plainTextView = mailMessage.GetAlternateViewContent("text/plain");

// Print or further process the plain text view
Console.WriteLine("Plain Text View:");
Console.WriteLine(plainTextView);
```

## **Конвертируйте HTML в EMLX**

Вы можете легко конвертировать HTML-файлы в EMLX. Для этого типа преобразования также доступны все свойства и классы, предоставляемые API для преобразования HTML в EML:

```cs
var eml = MailMessage.Load("myContent.html", new HtmlLoadOptions());
eml.Save("output.emlx", SaveOptions.DefaultEmlx);
```
Дополнительные настройки см. [Конвертировать HTML в EML](#convert-html-to-eml) paragraph.

## **Конвертируйте HTML в ICS**

Для выполнения задачи библиотека предлагает [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) класс для представления календарных событий и управления ими. В следующем примере кода показано, как создать HTML-содержимое формы встречи и сохранить его в формате файла ICS (iCalendar):

```cs
// Sample HTML content
var htmlContent = File.ReadAllText("content.html");

// Create and initialize an instance of the Appointment class
var appointment = new Appointment(
    "Meeting Room 3 at Office Headquarters",// Location
    "Monthly Meeting",                      // Summary
    "Please confirm your availability.",    // Description
    new DateTime(2015, 2, 8, 13, 0, 0),     // Start date
    new DateTime(2015, 2, 8, 14, 0, 0),     // End date
    "from@domain.com",                      // Organizer
    "attendees@domain.com")
{
    HtmlDescription = htmlContent
};

// Save the event to an ICS file
appointment.Save("output.ics", AppointmentSaveFormat.Ics);
```


## **Генерация MBOX из HTML-контента**

Чтобы выполнить преобразование HTML в MBOX, используйте [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) метод [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) класс, указывающий путь к файлу содержимого HTML и экземпляр [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Этот метод анализирует содержимое HTML и генерирует соответствующий объект MailMessage, сохраняя структуру и форматирование исходного HTML. После загрузки содержимого HTML в объект MailMessage запишите сообщение в файл MBOX, используя [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) class:


```cs
using (var eml = MailMessage.Load("content.html", new HtmlLoadOptions())){
    using (var writer = new MboxrdStorageWriter("output.mbox", false)){
        writer.WriteMessage(eml);
    }
}
```

## **Конвертировать HTML в MHTML**

Используйте [Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_3) метод [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) класс для загрузки существующего файла с указанием пути к нему и экземпляра [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/). Этот метод анализирует содержимое HTML и генерирует соответствующий объект MailMessage, сохраняя структуру и форматирование исходного HTML. После загрузки содержимого HTML в объект MailMessage разработчики могут сохранить его в виде файла MHTML, используя [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод, указывающий желаемый путь к выходному файлу и использующий [SaveOptions.DefaultMhtml](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmhtml/) option:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.mhtml", SaveOptions.DefaultMhtml);
```

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) класс предоставляет множество опций для настройки поведения и параметров выходного файла MHTML вместо SaveOptions.defaultMhtml. С его помощью [properties](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#properties), вы можете указать дополнительные параметры при сохранении MailMessage в формате MHTML.
Самые популярные из них:

- [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/mhtformatoptions/) - Позволяет настроить способ сохранения сообщения электронной почты в формате MHT в соответствии с вашими потребностями.
- [SaveAttachments](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveattachments/) - Определяет или задает значение, указывающее, следует ли сохранять вложения.
- [SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Определяет, нужно ли сохранять все заголовки в выходном файле mhtml или нет. Значение по умолчанию — false.
- [PreserveOriginalDate](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/preserveoriginaldate/) - Определяет, нужно ли сохранять исходную дату в почтовом сообщении при сохранении или нет. Значение по умолчанию — true.

В следующем примере кода показано, как можно использовать эти свойства:

```cs
var mhtSaveOprtions = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader,
    SaveAttachments = true,
    SaveAllHeaders = true,
    PreserveOriginalDate = true
}
```

## **Конвертировать HTML в MSG**

После загрузки содержимого HTML в объект MailMessage сохраните его как файл MSG, используя [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод, указывающий желаемый путь к выходному файлу и использующий [SaveOptions.DefaultMsgUnicode](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultmsgunicode/) вариант. Эта опция гарантирует сохранение выходного файла в формате MSG с кодировкой Unicode.

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("output.msg", SaveOptions.DefaultMsgUnicode);
```
Кроме того, Aspose.Email для .NET предлагает ряд дополнительных функций и опций для преобразования HTML в MSG:

## **Конвертируйте HTML в OFT**

После загрузки содержимого HTML в объект MailMessage сохраните его как файл OFT, используя [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод, указывающий желаемый путь к выходному файлу и использующий [SaveOptions.DefaultOft](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaultoft/) option:

```cs
var eml = MailMessage.Load("content.html", new HtmlLoadOptions());
eml.Save("template.oft", SaveOptions.DefaultOft);
```

## **Добавить сообщение с исходным HTML-содержимым в PST**

Преобразование HTML в PST включает создание нового файла PST (Personal Storage Table) с новой папкой, загрузку HTML-файла и добавление его в новую папку:

1. Создайте экземпляр объекта PersonalStorage, представляющего новый файл PST, используя [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) метод [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.
2. Откройте корневую папку файла PST и добавьте в нее подпапку, используя [AddSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addsubfolder/#addsubfolder) метод [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) class.
3. Загрузите содержимое HTML-файла в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) объект, использующий [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) метод с экземпляром [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) чтобы указать, что содержимое находится в формате HTML.
4. Добавьте загруженный объект MapiMessage (представляющий содержимое HTML) в папку в файле PST, используя [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method.

```cs
using (var pst = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
{
    var inbox = pst.RootFolder.AddSubFolder("Inbox");
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    inbox.AddMessage(msg);
}
```

## **Добавить сообщение с исходным HTML-содержимым в OST**

В следующем примере кода с пошаговыми инструкциями показано, как эти компоненты работают вместе для добавления HTML-содержимого в OST-файл:

1. Загрузите существующий OST-файл с помощью [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) метод [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) класс, используемый для представления файла хранения, в котором будут храниться сообщения электронной почты.
2. Загрузите HTML-файл с помощью [Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) метод [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) класс, представляющий сообщение электронной почты в формате Microsoft Outlook.
3. Specify [HtmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/htmlloadoptions/#htmlloadoptions-class) чтобы включить дополнительные опции при загрузке MailMessage из формата HTML.
4. Извлеките корневую папку OST-файла с помощью [RootFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/rootfolder/) собственность [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) object.
5. Получите папку «Входящие» в OST-файле, используя [GetSubFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder) метод в корневой папке.
6. Добавьте загруженный объект MapiMessage (представляющий содержимое HTML) в папку «Входящие», используя [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) метод в папке.

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    var msg = MapiMessage.Load("content.html", new HtmlLoadOptions());
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```

## **Конвертировать HTML в VCF**

В следующем примере кода показано, как создать контактный элемент, заполнить его содержимым HTML и сохранить в файле VCF:

1. Прочитайте содержимое HTML-файла в строковую переменную с помощью метода File.readAllText.
2. Создайте новый объект MapiContact, создав экземпляр [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/#mapicontact-class) class.
3. Задайте свойства контакта: отображаемое имя, адрес электронной почты.
4. Настройте содержимое тела контакта в формате HTML, используя [SetBodyContent](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/setbodycontent/#setbodycontent).
5. Сохраните контакт в виде файла VCF, используя [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_4) method.

```cs
var content = File.ReadAllText("content.html");
           
// Create a new MapiContact
var contact = new MapiContact();
contact.NameInfo.DisplayName = "John Doe";
contact.ElectronicAddresses.Email1.EmailAddress = "john.doe@example.com";
contact.SetBodyContent(content, BodyContentType.Html);

// Save the contact to a VCF file
contact.Save("contact.vcf", ContactSaveFormat.VCard)
```
