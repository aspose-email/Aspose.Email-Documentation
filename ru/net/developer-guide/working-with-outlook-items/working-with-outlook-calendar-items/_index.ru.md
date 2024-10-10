---
title: "Работа с элементами календаря Outlook"
url: /ru/net/working-with-outlook-calendar-items/
weight: 120
type: docs
---


## **Работа с MapiCalendar**

Класс MapiCalendar библиотеки Aspose.Email предоставляет методы и атрибуты для установки различных свойств элемента календаря. В этой статье приведены примеры кода для:

- [**Работа с MapiCalendar**](#working-with-mapicalendar)
  - [**Создание и сохранение элементов календаря**](#creating-and-saving-calendar-items)
  - [**Сохранение элемента календаря в формате MSG**](#saving-the-calendar-item-as-msg)
  - [**Добавление визуального напоминания в календарь**](#adding-display-reminder-to-a-calendar)
  - [**Добавление аудионапоминания в календарь**](#adding-audio-reminder-to-a-calendar)
  - [**Добавление/получение вложений из файлов календаря**](#addretrieve-attachments-from-calendar-files)
  - [**Статус получателей из запроса на встречу**](#status-of-recipients-from-a-meeting-request)
  - [**Создание MapiCalendarTimeZone из стандартного часового пояса**](#create-mapicalendartimezone-from-standard-timezone)
- [**Настройка напоминания с созданным событием**](#setting-reminder-with-the-created-appointment)
  - [**Настройка напоминания с помощью добавления тегов**](#setting-a-reminder-by-adding-tags)
- [**Преобразование EML события в MSG с HTML телом**](#convert-appointment-eml-to-msg-with-html-body)
  
### **Создание и сохранение элементов календаря**

Следующий фрагмент кода показывает, как создать и сохранить элемент календаря в формате ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cs" >}}

### **Сохранение элемента календаря в формате MSG**

Следующий фрагмент кода показывает, как сохранить элемент календаря в формате MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cs" >}}

### **Настройка идентификатора продукта при сохранении MapiCalendar в ICS**

Свойство [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) класса [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) используется для сохранения элемента MAPI календаря в файле iCalendar (ICS), сохраняя оригинальную информацию о дате и времени, а также пользовательский идентификатор продукта. Свойство указывает идентификатор продукта, который создал объект iCalendar.

Следующий пример кода показывает, как работать с данными iCalendar (ICS) в объекте MAPI календаря:

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

- **CalendarReader.Count** - Свойство Count класса CalendarReader позволяет получить количество компонентов Vevent (событий), присутствующих в календаре, что упрощает отслеживание общего числа событий.
- **CalendarReader.IsMultiEvents** - Это свойство определяет, содержит ли календарь несколько событий. Оно возвращает булево значение, указывающее, содержит ли календарь более одного события, что помогает выявить календари с одиночными или множественными событиями.
- **CalendarReader.Method** - Свойство Method получает тип метода iCalendar, связанный с объектом календаря. Оно возвращает тип метода, такой как “REQUEST,” “PUBLISH,” или “CANCEL,” предоставляя ценную информацию о назначении календаря.
- **CalendarReader.Version** - Получает версию iCalendar.
- **CalendarReader.LoadAsMultiple()** Этот метод позволяет загрузить список событий из календаря, содержащего несколько событий. Он возвращает список объектов Appointment, что позволяет легко получать доступ и обрабатывать каждое событие индивидуально.

Следующий пример кода демонстрирует, как вы можете реализовать эти возможности в вашем проекте:

```cs
var reader = new CalendarReader(fileName);
Console.WriteLine("Календарь содержит " + reader.Count + " событий");
Console.WriteLine("Версия календаря " + reader.Version);
Console.WriteLine("Метод календаря " + reader.Method);
Console.WriteLine("Содержит ли календарь несколько событий? - " + reader.IsMultiEvents);
List<Appointment> appointments = reader.LoadAsMultiple();
```

### **Добавление визуального напоминания в календарь**

Следующий фрагмент кода показывает, как добавить визуальное напоминание в календарь.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cs" >}}

### **Добавление аудионапоминания в календарь**

Следующий фрагмент кода показывает, как добавить аудионапоминание в календарь.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cs" >}}

### **Добавление/получение вложений из файлов календаря**

Следующий фрагмент кода показывает, как добавить/получить вложения из файлов календаря.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cs" >}}

### **Статус получателей из запроса на встречу**

Следующий фрагмент кода показывает, как отобразить статус получателей из запроса на встречу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cs" >}}

### **Создание MapiCalendarTimeZone из стандартного часового пояса**

Следующий фрагмент кода показывает, как создать MapiCalendarTimeZone из стандартного часового пояса.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cs" >}}

## **Настройка напоминания с созданным событием**

Напоминание может быть добавлено при создании события. Эти будильники могут срабатывать по разным критериям, например за n минут до начала расписания, повторять n раз с интервалами в n. Различные теги могут использоваться для создания этих триггеров в скрипте, заключенном между BEGIN:VALARM и END:VALARM внутри события. Существует множество вариантов настройки напоминания на событие.

### **Настройка напоминания с помощью добавления тегов**

Следующий фрагмент кода показывает, как установить напоминание, добавив теги.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cs" >}}

## **Преобразование EML события в MSG с HTML телом**

Начиная с версии 19.3, Aspose.Email предоставляет возможность преобразовать EML события в MSG, сохраняя HTML тело события. Aspose.Email предоставляет свойство [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/), которое имеет значение по умолчанию **true.** Когда значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) установлено в **true**, тело события преобразуется в формат RTF. Чтобы сохранить формат тела события в формате HTML, установите значение [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) в **false.**

Следующий пример демонстрирует использование [MapiConversionOptions.ForcedRtfBodyForAppointment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/forcedrtfbodyforappointment/) для сохранения формата тела события в формате HTML.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-ConvertAppointmentEMLToMSGWithHTMLBody-1.cs" >}}