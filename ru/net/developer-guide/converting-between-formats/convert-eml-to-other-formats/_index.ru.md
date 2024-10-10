---
title: "Конвертация EML в HTML"
url: /ru/net/converting-between-formats/
weight: 60
type: docs
---

## **Конвертация EML в HTML**

Для интеграции содержимого электронной почты в веб-приложения конвертация EML в HTML является правильным выбором, облегчающим визуально привлекательное представление электронной почты.

Чтобы конвертировать EML в HTML, вам понадобятся следующие классы:

- Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) используется для создания объекта, представляющего электронное сообщение. Он позволяет получить доступ к свойствам сообщения, таким как тема, тело, адрес отправителя и получателей и т. д. С его методами вы можете создавать, загружать и анализировать, изменять, сохранять электронные письма или выполнять с ними другие манипуляции. 
- Класс [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/) предоставляет параметры для сохранения электронных сообщений в различных форматах. Он позволяет пользователям настраивать способ сохранения электронных сообщений в разных форматах. С помощью этого класса пользователи могут задавать параметры для сохранения вложений, заголовков, метаданных и свойств электронных сообщений, устанавливать параметры кодирования или выбирать, сохранять сообщения с шифрованием или нет. 

В приведенном ниже образце кода эти классы работают вместе, чтобы загрузить существующий EML файл и указать формат сообщения как EML. Затем они сохраняют загруженное сообщение электронной почты в виде HTML файла, используя указанные параметры сохранения HTML по умолчанию:

1. Используйте метод [MailMessage.Load()](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) для загрузки существующего файла в объект MailMessage, указав формат сообщения. 
2. Сохраните загруженный объект MailMessage как HTML файл, используя метод [save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3). Используйте [SaveOptions.DefaultHtml()](https://reference.aspose.com/email/net/aspose.email/saveoptions/defaulthtml/) для указания параметров сохранения для HTML формата.

```cs
// Инициализировать и загрузить существующий EML файл, указав формат сообщения
var message = MailMessage.Load("myMessage.eml");
message.Save("output.html", SaveOptions.DefaultHtml);
```

### **Сохранение ресурсов EML в отдельный файл**

Aspose.Email предоставляет перечисление [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration), позволяющее разработчикам манипулировать ресурсами в HTML файле. В приведенном ниже образце кода это перечисление используется для сохранения ресурсов в файл и вставки в HTML тега 'src' с путем к этому файлу:

1. Загрузите сообщение электронной почты из исходного файла, используя метод [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2).
2. Создайте экземпляр [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) с указанными параметрами рендеринга и ресурсов.
3. Сохраните загруженное сообщение электронной почты как HTML файл в целевом месте, используя метод [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) с параметром HtmlSaveOptions.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
UseRelativePathToResources = true
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

### **Встраивание ресурсов в HTML файл**

В некоторых случаях необходимо встроить ресурсы, такие как изображения, непосредственно в HTML файл для бесшовного распределения и представления. С Aspose.Email для .NET вы можете легко достичь этого, используя перечисление [ResourceRenderingMode](https://reference.aspose.com/email/net/aspose.email/resourcerenderingmode/#resourcerenderingmode-enumeration):

1. Загрузите сообщение электронной почты из исходного файла, используя метод [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_2).
2. Создайте новый объект [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) и установите свойство ResourceRenderingMode в EmbedIntoHtml.
3. Сохраните загруженное сообщение электронной почты как HTML файл, используя метод [Save](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3), указав путь к целевому файлу и передав объект HtmlSaveOptions в качестве параметра для встраивания ресурсов в HTML файл.

```cs
var msg = MapiMessage.Load(sourceFileName);
var htmlSaveOptions = new HtmlSaveOptions
{
ResourceRenderingMode = ResourceRenderingMode.EmbedIntoHtml
};
msg.Save(Path.Combine("target.html"), htmlSaveOptions);
```

## **Конвертация EML в ICS**

Следующий пример кода демонстрирует, как извлечь данные о событии календаря из EML файла и сохранить их в отдельный ICS файл для дальнейшего использования или манипуляции.

```cs
// Загрузить EML файл
var eml = MailMessage.Load("message.eml");
// Найти альтернативный вид с MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// Если альтернативный вид ICS найден, сохраните его в файл
if (icsView != null)
{
    File.WriteAllText("appointment.ics", icsView);
}
```
### **Настройка**

Aspose.Email для .NET предоставляет инструменты для настройки содержимого ICS (iCalendar), извлеченного из EML (Электронная почта).

**Настройка деталей события**

Следующий пример кода демонстрирует, как установить различные детали назначения, такие как резюме, местоположение и описание. Код использует класс [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class), который представляет календарные назначения или события в формате ICS (iCalendar). Класс предоставляет свойства и методы для создания, изменения и управления календарными событиями программно.

```cs
// Загрузить EML файл
var eml = MailMessage.Load("message.eml");
// Найти альтернативный вид с MediaType "text/calendar" (ICS)
var icsView = eml.GetAlternateViewContent("text/calendar");
// Если альтернативный вид ICS найден, загрузите его в объект класса Appointment
var appointment = Appointment.Load(new MemoryStream(Encoding.UTF8.GetBytes(icsView)));

// Настройка деталей события
appointment.Summary = "На.Customized Event Summary";
appointment.Location = "Настроенное Местоположение";
appointment.Description = "Настроенное Описание События";

// Добавьте или измените участников по мере необходимости
appointment.Attendees.Clear();
appointment.Attendees.Add("custom@example.com");

// Сохраните настроенное содержание ICS в файл
appointment.Save("customized_appointment.ics");
```
**Создание паттерна повторения**

Следующий пример кода демонстрирует, как создать еженедельный паттерн повторения для назначения, которое происходит каждые 5 недель по субботам. Код использует свойство [Recurrence](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/recurrence/#appointmentrecurrence-property) класса [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class), которое получает или устанавливает паттерн повторения.

```cs
var pattern = new WeeklyRecurrencePattern(5, 7);
pattern.EndDate = new DateTime(2023, 8, 7);

appointment.Recurrence = pattern;
```

## **Добавление EML в MBOX**

MBOX — это общепринятый формат для хранения нескольких электронных сообщений в одном файле, что делает его подходящим для архивирования и миграции электронной почты. Используйте класс [MboxrdStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragewriter/#mboxrdstoragewriter-class), чтобы записать электронные сообщения в файл MBOX. Следующий пример кода демонстрирует, как выполнить эту задачу:

```cs
using (var message = MailMessage.Load("inputFile.eml")){
	using (var writer = new MboxrdStorageWriter("output.mbox", false)){
			writer.WriteMessage(message);
	}
} 
```

## **Конвертация EML в MHTML**

С Aspose.Email для .NET вы можете легко конвертировать EML файлы в формат MHTML для различных целей, таких как архивирование, совместимость, офлайн-просмотр и т. д. Загрузите сообщение электронной почты, используя [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2), затем используйте класс [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) в качестве параметра для метода [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), чтобы указать формат выходного файла при сохранении сообщения в отдельный файл:

```cs
// Инициализировать и загрузить существующий EML файл, указав формат сообщения
var message = MailMessage.Load("myMessage.eml");
var mhtSaveOptions = new MhtSaveOptions();
message.Save("output.mhtml", mhtSaveOptions);
```

Класс [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/) предоставляет различные параметры для настройки выходных файлов MHTML в соответствии с вашими конкретными требованиями:

- Сохранять оригинальное форматирование даты. Вы можете выбрать сохранение оригинального форматирования сообщений электронной почты в процессе конверсии:

  ```cs
  saveOptions.PreserveOriginalDate = true;
  ```

- Установить кодировку выходных данных. Вы можете указать кодировку, которая будет использоваться при записи выходных файлов MHTML:

  ```cs
  saveOptions.OutputEncoding = Encoding.UTF8; 
  ```

- Включить вложения. Это может быть полезно, если вы хотите сохранить вложения при конвертации электронных писем в формат MHTML:

  ```cs
  saveOptions.SaveAttachments = true;
  ```

## **Конвертация EML в MSG**

Независимо от того, нужно ли вам мигрировать данные электронной почты, архивировать сообщения или интегрироваться с Microsoft Outlook, Aspose.Email предоставляет решения для достижения ваших целей. Файлы MSG широко используются Microsoft Outlook. Для конверсии EML в MSG используйте метод [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) для загрузки существующего EML файла, указывая, как он будет загружен с помощью [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class).

Следующий пример кода демонстрирует, как конвертировать файлы EML в формат MSG:

```cs
// Загрузить сообщение электронной почты
using (var message = MailMessage.Load("sourceFile.eml", new EmlLoadOptions())){
// Сохранить как MSG
var msgSaveOptions = new MsgSaveOptions();
message.Save("output.msg", msgSaveOptions);
} 
```

## **Конвертация EML в OFT**

Чтобы конвертировать EML файлы в формат шаблона Outlook (OFT), загрузите существующее сообщение электронной почты с помощью метода [MailMessage.Load](https://reference.aspose.com/email/net/aspose.email/mailmessage/load/#load_2) и сохраните его с [MailMessage.Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3), указав параметры по умолчанию для сохранения сообщения в формате OFT:

```cs
// загрузить EML файл для конверсии
var message = MailMessage.Load("My File.eml"); 
// сохранить EML как OFT 
message.Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Добавление EML в PST**

Чтобы конвертировать EML файлы в формат таблицы личных данных (PST), загрузите сообщение с помощью метода [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load_3), создайте выходной файл с помощью [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) и добавьте электронное письмо в созданную папку «Входящие» в файле хранилища с помощью [AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/): 

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

## **Добавление EML в OST**

Разработчики могут легко конвертировать EML файлы в формат таблицы оффлайн-данных Outlook (OST), что позволяет интегрироваться с Microsoft Outlook. Следующий пример кода демонстрирует, как добавить сообщение EML в OST файл:

```cs
using (var ost = PersonalStorage.FromFile("storage.ost"))
{
    // Загрузить EML файл
    var msg = MapiMessage.Load("message.eml", new EmlLoadOptions());

    // Добавить сообщение EML в OST файл
    var folderInfo = ost.RootFolder.GetSubFolder("Inbox");
    folderInfo.AddMessage(msg);
}
```
Параметр [EmlLoadOptions](https://reference.aspose.com/email/net/aspose.email/emlloadoptions/#emlloadoptions-class) определяет дополнительные параметры для загрузки EML файлов, такие как сохранение встроенных форматов сообщений, удаление подписей и многое другое. 


## **Конвертация EML в VCF**

Aspose.Email для .NET предлагает функциональность для конвертации EML файлов в формат vCard (VCF), позволяя разработчикам извлекать контактную информацию из электронных писем. Для этой цели библиотека предлагает метод [GetAlternateViewContent](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class), позволяющий разработчикам получать альтернативные представления внутри электронных писем и извлекать содержимое VCF, встроенное в EML файлы для дальнейшего использования:


```cs
// Загрузить EML файл
var eml = MailMessage.Load("message.eml");
// Найти альтернативный вид с MediaType "text/vcard" (VCF)
var vcfView = eml.GetAlternateViewContent("text/vcard");
// Если альтернативный вид VCF найден, сохраните его в файл
if (vcfView != null)
{
    File.WriteAllText("contact.vcf", vcfView);
}
```