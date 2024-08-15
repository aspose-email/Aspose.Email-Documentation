---
title: "Конвертировать EML в HTML"
url: /ru/net/converting-between-formats/
weight: 60
type: docs
---

## **Конвертировать EML в HTML**

Для интеграции содержимого электронной почты в веб-приложения преобразование EML в HTML является правильным выбором, обеспечивающим визуально привлекательную презентацию электронной почты.

Чтобы преобразовать EML в HTML, вам понадобятся следующие классы:

- [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс используется для создания объекта, представляющего сообщение электронной почты. Он позволяет получить доступ к свойствам сообщения, таким как тема, текст, адреса отправителя и получателя и т. д. С его помощью вы можете создавать, загружать и анализировать, изменять, сохранять электронные письма или выполнять другие манипуляции с ними.
- [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) класс предоставляет возможности для сохранения сообщений электронной почты в различных форматах. Он позволяет пользователям настраивать способ сохранения сообщений электронной почты в разных форматах. С помощью этого класса пользователи могут указать параметры сохранения вложений, заголовков, метаданных и свойств сообщений электронной почты, задать параметры кодирования или выбрать, следует ли сохранять сообщения с шифрованием или нет.

В приведенном ниже примере кода эти классы совместно загружают существующий файл EML и задают формат сообщения как EML. Затем загруженное сообщение электронной почты сохраняется в виде HTML-файла, используя указанные по умолчанию параметры сохранения HTML:

1. Используйте [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) метод загрузки существующего файла в объект MailMessage с указанием формата сообщения.
2. Сохраните загруженный объект MailMessage в виде HTML-файла, используя [save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод. Использование [SaveOptions.DefaultHtml()](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) чтобы указать параметры сохранения для формата HTML.

```cs
// Initialize and Load an existing EML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.eml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

### **Сохранение ресурсов EML в отдельном файле**

Aspose.Email предоставляет [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) перечисление, позволяющее разработчикам управлять ресурсами в HTML-файле. В приведенном ниже примере кода это перечисление используется для сохранения ресурсов в файле и вставки в HTML тега src с путем к этому файлу:

1. Загрузите сообщение электронной почты из исходного файла, используя [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method.
2. Создайте экземпляр [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) с заданными параметрами рендеринга и ресурсов.
3. Сохраните загруженное сообщение электронной почты в виде HTML-файла в целевом месте, используя [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) метод с параметром htmlSaveOptions.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
UseRelativePathToResources = true
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

### **Встраивание ресурсов в HTML-файл**

В некоторых случаях требуется встраивать ресурсы, например изображения, непосредственно в HTML-файл для беспрепятственного распространения и презентации. С помощью Aspose.Email для .NET вы можете легко сделать это, используя [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration) enumeration:

1. Загрузите сообщение электронной почты из исходного файла, используя [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2) method.
2. Создайте новый [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) создайте объект и задайте свойству ResourceRenderingMode значение EmbedInToHTML.
3. Сохраните загруженное сообщение электронной почты в виде HTML-файла, используя [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) метод, указывающий путь к целевому файлу и передающий объект HTMLSaveOptions в качестве параметра для встраивания ресурсов в HTML-файл.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.EmbedIntoHtml
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

## **Конвертируйте EML в ICS**

В следующем примере кода показано, как извлечь данные календарных событий из файла EML и сохранить их в отдельном файле ICS для дальнейшего использования или обработки.

```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// If an ICS view is found, save it to a file
if (icsView != null)
{
    File.WriteAllText("appointment.ics", icsView);
}
```
### **Customization**

Aspose.Email for .NET предоставляет инструменты для настройки содержимого ICS (iCalendar), извлеченного из файлов EML (электронная почта).

**Настройте детали мероприятия**

В следующем примере кода показано, как задать различные детали встречи, такие как краткое описание, место и описание. В коде используется [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) класс, который представляет календарные встречи или события в формате ICS (iCalendar). Класс предоставляет свойства и методы для программного создания, изменения календарных событий и управления ими.

```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// If an ICS view is found, load it to Appointment class object
var appointment = Appointment.Load(new MemoryStream(Encoding.UTF8.GetBytes(icsView)));

// Настройте детали мероприятия
appointment.Summary = "Customized Event Summary";
appointment.Location = "Customized Location";
appointment.Description = "Customized Event Description";

// Add or modify attendees as needed
appointment.Attendees.Clear();
appointment.Attendees.Add("custom@example.com");

// Save the customized ICS content to a file
appointment.Save("customized_appointment.ics");
```
**Создайте шаблон повторения**

В следующем примере кода показано, как создать режим еженедельного повторения визита, при котором прием проводится каждые 5 недель по субботам. В коде используется [Recurrence](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/recurrence/#appointmentrecurrence-property) собственность [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) класс, который получает или задает шаблон повторения.

```cs
var pattern = new  WeeklyRecurrencePattern(5, 7);
pattern. EndDate = new DateTime(2023, 8, 7);

appointment.Recurrence = pattern;
```

## **Добавить EML в MBOX**

MBOX — это широко используемый формат для хранения нескольких сообщений электронной почты в одном файле, что делает его пригодным для архивирования и миграции электронной почты. Используйте [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class) класс для записи сообщений электронной почты в файл MBOX. В следующем примере кода показано, как выполнить эту задачу:

```cs
using (var message = MailMessage.Load("inputFile.eml")){
	using (var writer = new MboxrdStorageWriter("output.mbox", false)){
			writer.WriteMessage(message);
	}
}
```

## **Конвертируйте EML в MHTML**

С помощью Aspose.Email для .NET вы можете легко конвертировать файлы EML в формат MHTML для различных целей, таких как архивирование, совместимость, просмотр в автономном режиме и т. д. Загрузите сообщение электронной почты с помощью [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2), затем используйте [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) класс в качестве параметра для [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод указания формата выходного файла при сохранении сообщения в виде отдельного файла:

```cs
// Initialize and Load an existing EML file by specifying the MessageFormat
var message = MailMessage.Load("myMessage.eml");
var mhtSaveOptions = new MhtSaveOptions;
message.Save("output.mhtml", mhtSaveOptions);
```

The [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) класс предоставляет различные варианты настройки выходных файлов MHTML в соответствии с вашими конкретными требованиями:

- Сохраните исходное форматирование даты. В процессе конвертации вы можете сохранить исходное форматирование сообщений электронной почты:

  ```cs
  saveOptions.PreserveOriginalDate = true;
  ```

- Задайте выходную кодировку. Можно указать кодировку, которая будет использоваться при записи выходных файлов MHTML:

  ```cs
  saveOptions.OutputEncoding = Encoding.UTF8;
  ```

- Включите вложения. Это может быть полезно, если вы хотите сохранить вложения при преобразовании писем в формат MHTML:

  ```cs
  saveOptions.SaveAttachments = true;
  ```

## **Конвертировать EML в MSG**

Если вам нужно перенести данные электронной почты, архивировать сообщения или интегрироваться с Microsoft Outlook, Aspose.Email предлагает решения для достижения ваших целей. Файлы MSG широко используются в Microsoft Outlook. Для преобразования EML в MSG используйте [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) метод загрузки существующего файла EML с указанием способа его загрузки [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class).

В следующем примере кода показано, как конвертировать файлы EML в формат MSG:

```cs
// Load mail message
using (var message = MailMessage.Load("sourceFile.eml", new EmlLoadOptions())){
// Save as MSG
var msgSaveOptions = new MsgSaveOptions;
message.Save("output.msg", MsgSaveOptions);
}
```

## **Конвертируйте EML в OFT**

Чтобы преобразовать файлы EML в формат Outlook Template (OFT), загрузите существующее сообщение электронной почты, используя [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) метод и сохраните его с помощью [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) указание параметров по умолчанию для сохранения сообщения в формате OFT:

```cs
// load the EML file to be converted
var message = MailMessage.Load("My File.eml");
// save EML as a OFT
message.Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Добавить EML в PST**

Чтобы преобразовать файлы EML в формат Personal Storage Table (PST), загрузите сообщение, используя [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3) метод, создайте выходной файл с помощью [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) и добавьте электронное письмо в созданную папку «Входящие» в файле хранилища, используя [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/):

```cs
using (var msg = MapiMessage.Load("sourceFile.eml", new EmlLoadOptions()))
{
    using (var personalStorage = PersonalStorage.Create("outputFile.pst", FileFormatVersion.Unicode))
  {
        var inbox = personalStorage.RootFolder.AddSubFolder("Inbox");
        inbox.AddMessage(msg);
  }
}
```

## **Добавить EML в OST**

Разработчики могут легко конвертировать файлы EML в формат таблицы автономного хранилища Outlook (OST), обеспечивая интеграцию с Microsoft Outlook. В следующем примере кода показано, как добавить сообщение EML в OST-файл:

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    // Load the EML file
    var msg = MapiMessage.Load("message.eml", new EmlLoadOptions());

    // Add the EML message to the OST file
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```
The [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class) параметр указывает дополнительные параметры загрузки файлов EML, такие как сохранение встроенных форматов сообщений, удаление подписей и многое другое.


## **Конвертировать EML в VCF**

Aspose.Email for .NET предлагает функцию преобразования файлов EML в формат vCard (VCF), что позволяет разработчикам извлекать контактную информацию из сообщений электронной почты. Для этого библиотека предлагает [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) метод [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) класс, позволяющий разработчикам получать доступ к альтернативным представлениям сообщений электронной почты и извлекать содержимое VCF, встроенное в файлы EML, для дальнейшего использования:


```cs
// Load the EML file
var eml = MailMessage.Load("message.eml");
// Find the alternate view with MediaType "text/vcard" (VCF)
var vcfView = eml.GetAlternateViewContent("text/vcard");
// If an VCF view is found, save it to a file
if (vcfView != null)
{
    File.WriteAllText("contact.vcf", vcfView);
}
```
