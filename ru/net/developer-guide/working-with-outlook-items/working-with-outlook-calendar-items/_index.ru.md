---
title: "Работа с элементами календаря Outlook"
url: /ru/net/working-with-outlook-calendar-items/
weight: 120
type: docs
---


## **Работа с MapiCalendar**

Класс MapicaLendar в Aspose.Email предоставляет методы и атрибуты для установки различных свойств элемента календаря. В этой статье представлены примеры кода для:

- [**Работа с MapiCalendar**](#working-with-mapicalendar)
  - [**Создание и сохранение элементов календаря**](#creating-and-saving-calendar-items)
  - [**Сохранение элемента календаря в формате MSG**](#saving-the-calendar-item-as-msg)
  - [**Добавление экранного напоминания в календарь**](#adding-display-reminder-to-a-calendar)
  - [**Добавление звукового напоминания в календарь**](#adding-audio-reminder-to-a-calendar)
  - [**Добавление/извлечение вложений из файлов календаря**](#addretrieve-attachments-from-calendar-files)
  - [**Статус получателей приглашения на собрание**](#status-of-recipients-from-a-meeting-request)
  - [**Создание часового пояса Mapicalend из стандартного часового пояса**](#create-mapicalendartimezone-from-standard-timezone)
- [**Настройка напоминания с созданной встречей**](#setting-reminder-with-the-created-appointment)
  - [**Настройка напоминания путем добавления тегов**](#setting-a-reminder-by-adding-tags)
- [**Преобразуйте EML встречи в MSG с помощью HTML-текста**](#convert-appointment-eml-to-msg-with-html-body)
 
### **Создание и сохранение элементов календаря**

В следующем фрагменте кода показано, как создать и сохранить элемент календаря в формате ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cs" >}}

### **Сохранение элемента календаря в формате MSG**

В следующем фрагменте кода показано, как сохранить элемент календаря в формате MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cs" >}}

### **Настройка идентификатора продукта при сохранении MapicaLendar в ICS**

The [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) собственность [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) класс используется для сохранения элемента календаря MAPI в файл iCalendar (ICS) с сохранением исходной информации о дате и времени, а также пользовательского идентификатора продукта. Свойство указывает идентификатор продукта, создавшего объект iCalendar.

В следующем примере кода показано, как работать с данными iCalendar (ICS) в объекте календаря MAPI:

```cs
var icsSaveOptions = new MapiCalendarIcsSaveOptions
{
    KeepOriginalDateTimeStamp = true,
    ProductIdentifier = "Foo Ltd"
};

mapiCalendar.Save("my.ics", icsSaveOptions);
```
### **Получение общего количества событий**

Класс CalendarReader позволяет легко обрабатывать события календаря. Следующие свойства и метод позволяют работать с несколькими событиями:

- **CalendarReader.Count** - Свойство Count класса CalendarReader позволяет получить количество компонентов (событий) Vevent, присутствующих в календаре, что упрощает отслеживание общего количества событий.
- **CalendarReader.IsMultiEvents** - Это свойство определяет, содержит ли календарь несколько событий. Оно предоставляет логическое значение, указывающее, содержит ли календарь более одного события, что помогает идентифицировать календари с одним или несколькими событиями.
- **CalendarReader.Method** - Свойство Method получает тип метода iCalendar, связанный с объектом календаря. Оно возвращает тип метода, например «REQUEST», «PUBLISH» или «CANCEL», что позволяет получить ценную информацию о назначении календаря.
- **CalendarReader.Version** - Получает версию iCalendar.
- **CalendarReader.LoadAsMultiple()** Этот метод позволяет загружать список событий из календаря, содержащего несколько событий. Он возвращает список объектов Appointment, что обеспечивает легкий доступ к каждому событию и его обработку по отдельности.

В следующем примере кода показано, как можно реализовать эти возможности в своем проекте:

```cs
var reader = new CalendarReader(fileName);
Console.WriteLine("Calendar contains " + reader.Count + " events");
Console.WriteLine("The Version of the calendar is " + reader.Version);
Console.WriteLine("The Method of the calendar is " + reader.Method);
Console.WriteLine("Is calendar contains contains multiple events? - " + reader.IsMultiEvents);
List<Appointment> appointments = reader.LoadAsMultiple();
```

### **Добавление экранного напоминания в календарь**

В следующем фрагменте кода показано, как добавить экранное напоминание в календарь.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cs" >}}

### **Добавление звукового напоминания в календарь**

В следующем фрагменте кода показано, как добавить звуковое напоминание в календарь.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cs" >}}

### **Добавление/извлечение вложений из файлов календаря**

В следующем фрагменте кода показано, как добавлять/извлекать вложения из файлов календаря.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cs" >}}

### **Статус получателей приглашения на собрание**

В следующем фрагменте кода показано, как показать статус получателей приглашения на собрание.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cs" >}}

### **Создание часового пояса Mapicalend из стандартного часового пояса**

В следующем фрагменте кода показано, как создать MapicaLendaTimeZone из стандартного часового пояса.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cs" >}}

## **Настройка напоминания с созданной встречей**

Напоминание можно добавить при создании встречи. Эти сигналы могут срабатывать по разным критериям, например, за n минут до начала расписания и повторяться n раз с интервалом n раз. Для создания этих триггеров можно использовать разные теги в скрипте, прилагаемом к командам BEGIN:VALARM и END:VALARM во время встречи. Существует несколько вариантов, в которых напоминание можно установить во время встречи.

### **Настройка напоминания путем добавления тегов**

В следующем фрагменте кода показано, как настроить напоминание, добавляя теги.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cs" >}}

## **Преобразуйте EML встречи в MSG с помощью HTML-текста**

Начиная с версии 19.3, Aspose.Email предоставляет возможность конвертировать EML встречи в MSG, сохраняя при этом текст встречи в формате HTML. Aspose.Email предоставляет [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) свойство, значение которого по умолчанию равно **true.** Когда значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) настроен на **true**, текст записи преобразуется в формат RTF. Чтобы сохранить формат текста встречи в формате HTML, задайте значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) to **false.**

В следующем примере показано использование [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) свойство сохранять формат тела встречи в формате HTML.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-ConvertAppointmentEMLToMSGWithHTMLBody-1.cs" >}}
