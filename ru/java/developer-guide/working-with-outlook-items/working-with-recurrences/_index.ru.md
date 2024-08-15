---
title: "Работа с рецидивами"
url: /ru/java/working-with-recurrences/
weight: 140
type: docs
---


## **Работа с ежедневными рецидивами**

Aspose.Email поддерживает создание ежедневных повторов с помощью [MapiCalendarDailyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendardailyrecurrencepattern/). Можно использовать три разных типа окончания повторения календаря Mapi, в том числе: *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. В этом разделе показано создание различных моделей ежедневных рецидивов.

### **Ежедневные рецидивы: тип рецидива в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Задайте состояние задачи *NotAssigned*.
1. Создайте объект ежедневного повторения, установив такие свойства, как *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** свойство к этому объекту ежедневной повторяемости.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с повторяющимся типом окончания как *EndAfterNOccurrence*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 8, 1);

MapiTask task = new MapiTask("This is test task", "Sample Body", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern rec = new MapiCalendarDailyRecurrencePattern();
rec.setPatternType(MapiCalendarRecurrencePatternType.Day);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY"));

if (rec.getOccurrenceCount() == 0)
{
    rec.setOccurrenceCount(1);
}

task.setRecurrence(rec);
task.save(dataDir + "Daily_out.msg", TaskSaveFormat.Msg);
~~~

Для вычисления количества событий между двумя датами можно использовать следующую функцию:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Настройка значения количества появлений**

В следующем фрагменте кода показано, как установить значение количества вхождений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
record.setOccurrenceCount(5);
task.setRecurrence(record);
~~~

### **Ежедневные повторения: тип рецидива EndAfterDate**

Опция «End By» в задаче Mapi достигается путем установки *OccurrenceCount* свойство, рассчитанное по формуле **getOccurrenceCount()** функция. Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Ежедневные повторения: настройка ежедневного значения**

В следующем фрагменте кода также показано, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=1"));
record.setEndDate(endByDate);
~~~

Для значения «Каждый день» можно задать любое подходящее значение, как показано в следующем примере:

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(2);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=2"));
~~~

### **Ежедневные рецидивы: тип повторения NeverEnd**

Тип конца можно установить с помощью *MapiCalendarRecurrenceEndType.NeverEnd*. В следующем примере для периода или ИНТЕРВАЛА можно задать требуемое значение, например, 1.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Работа с еженедельными рецидивами**

Aspose.Email предоставляет широкие возможности для создания еженедельных рекурсов с использованием [MapiCalendarWeeklyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarweeklyrecurrencepattern/). Можно использовать три разных типа окончания повторения календаря Mapi, в том числе: *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. В этом разделе показано создание различных моделей еженедельного повторения.

### **Еженедельные рецидивы: тип повторения событий в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Задайте состояние задачи *NotAssigned*.
1. Создайте объект еженедельного повторения, установив такие свойства, как *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** свойство этого объекта еженедельного повторения.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с повторяющимся типом окончания как *EndAfterNOccurrence*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 9, 1);

MapiTask task = new MapiTask("This is test task", "Sample Body", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Set the weekly recurrence
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR"));

if (rec.getOccurrenceCount() == 0)
{
    rec.setOccurrenceCount(1);
}

task.setRecurrence(rec);
task.save(dataDir + "Weekly_out.msg", TaskSaveFormat.Msg);
~~~

Для вычисления количества событий между двумя датами можно использовать следующую функцию:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Выбор нескольких дней в неделю**

В следующем фрагменте кода показано, как выбрать несколько дней в неделю.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the weekly recurrence
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();

rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO"));
~~~

#### **Выбор нескольких дней в неделю и настройка интервалов**

В следующем фрагменте кода показано, как выбрать несколько дней в неделю и установить интервалы.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the weekly recurrence
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(2);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Еженедельные повторения: тип повторения EndAfterDate**

Опция «End By» в задаче Mapi достигается путем установки *OccurrenceCount* свойство, рассчитанное по формуле **getOccurrenceCount()** функция. Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Еженедельные повторения: настройка значения за каждый день**

В следующем фрагменте кода также показано, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the weekly recurrence
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR;INTERVAL=1"));
~~~

Для значения «Каждый день» можно задать любое подходящее значение и выбрать несколько дней, как показано в следующем примере:

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarWeeklyRecurrencePattern record = new MapiCalendarWeeklyRecurrencePattern();
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setPatternType(MapiCalendarRecurrencePatternType.Week);
record.setPeriod(2);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndDate(endByDate);
record.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Еженедельные рецидивы: тип повторения NeverEnd**

Тип конца можно установить с помощью *MapiCalendarRecurrenceEndType.NeverEnd*. В следующем примере для периода или ИНТЕРВАЛА можно задать требуемое значение, например, 1.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the weekly recurrence
MapiCalendarWeeklyRecurrencePattern recurrence = new MapiCalendarWeeklyRecurrencePattern();
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Week);
recurrence.setPeriod(1);
recurrence.setWeekStartDay(DayOfWeek.Sunday);
recurrence.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
recurrence.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR"));
~~~

## **Работа с ежемесячными рецидивами**

Aspose.Email поддерживает создание ежемесячных рецидивов с использованием [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Можно использовать три разных типа окончания повторения календаря Mapi, в том числе: *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. В этом разделе показано создание различных моделей ежемесячных рецидивов.

### **Ежемесячные рецидивы: тип повторения событий в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Задайте состояние задачи *NotAssigned*.
1. Создайте объект ежемесячного повторения, установив такие свойства, как *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** свойство к этому объекту ежемесячной повторяемости.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с повторяющимся типом окончания как *EndAfterNOccurrence*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date DueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("This is test task", "Sample Body", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Set the Monthly recurrence
MapiCalendarMonthlyRecurrencePattern rec = new MapiCalendarMonthlyRecurrencePattern();
rec.setDay(15);
rec.setPeriod(1);
rec.setPatternType(MapiCalendarRecurrencePatternType.Month);
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=MONTHLY;BYMONTHDAY=15;INTERVAL=1"));
rec.setWeekStartDay(DayOfWeek.Monday);

if (rec.getOccurrenceCount() == 0)
{
    rec.setOccurrenceCount(1);
}

task.setRecurrence(rec);
task.save(dataDir + "Monthly_out.msg", TaskSaveFormat.Msg);
~~~

Для вычисления количества событий между двумя датами можно использовать следующую функцию:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Задать фиксировать количество повторов**

В следующем фрагменте кода показано, как установить исправление количества вхождений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Monthly recurrence
MapiCalendarMonthlyRecurrencePattern records = new MapiCalendarMonthlyRecurrencePattern();
records.setDay(15);
records.setPeriod(1);
records.setPatternType(MapiCalendarRecurrencePatternType.Month);
records.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
records.setOccurrenceCount(5);
records.setWeekStartDay(DayOfWeek.Monday);
~~~

### **Ежемесячные рецидивы: тип повторения EndAfterDate**

Опция «End By» в задаче Mapi достигается путем установки *OccurrenceCount* свойство, рассчитанное по формуле **getOccurrenceCount()** функция. Эта функция принимает дату начала, дату окончания и строку RRULE. В следующем фрагменте кода показано, как создать повтор 15 числа каждого месяца между датой начала и концом.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("This is test task", "Sample Body", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Set the Monthly recurrence
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(1);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
recurrence.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=MONTHLY;BYMONTHDAY=15;INTERVAL=1"));
recurrence.setWeekStartDay(DayOfWeek.Monday);
recurrence.setEndDate(endByDate);

task.setRecurrence(recurrence);
task.save(dataDir + "SetMonthlyEndAfterDateRecurrence_out.msg", TaskSaveFormat.Msg);
~~~

### **Ежемесячные рецидивы: тип повторения NeverEnd**

В следующем фрагменте кода показано, как можно установить конечный тип, используя *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(1);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setWeekStartDay(DayOfWeek.Monday);
~~~

## **Работа с годовыми рецидивами**

Aspose.Email поддерживает создание ежегодных рекурсов с использованием [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Установив для параметра периода значение 12, мы сможем добиться ежегодной повторяемости. Можно использовать три разных типа окончания повторения в календаре Mapi, в том числе *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. В этом разделе показано создание различных моделей ежегодных рецидивов.

### **Годовые рецидивы: тип повторения событий в конце дня**

В этом типе повторения количество рецидивов должно быть установлено вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и срока.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Задайте состояние задачи *NotAssigned*.
1. Создайте объект ежемесячного повторения, установив такие свойства, как *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** имущество к этому объекту ежемесячного повторения для достижения ежегодного повторения.
1. Сохраните это сообщение на диске.

В следующем фрагменте кода показано, как создать задачу с повторяющимся типом окончания как *EndAfterNOccurrence*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);

MapiTask task = new MapiTask("This is test task", "Sample Body", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Set the Yearly recurrence
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
recurrence.setOccurrenceCount(3);

task.setRecurrence(recurrence);
task.save("Yearly.msg", TaskSaveFormat.Msg);
~~~

### **Годовые рецидивы: тип повторения EndAfterDate**

Опция «End By» в задаче Mapi достигается путем установки *OccurrenceCount* свойство, рассчитанное по формуле **getOccurrenceCount()** функция. Эта функция принимает дату начала, дату окончания и строку RRULE. В следующем фрагменте кода показано, как создать повтор 15 числа каждого 7-го месяца между датой начала и концом.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Yearly recurrence
MapiCalendarMonthlyRecurrencePattern rec = new MapiCalendarMonthlyRecurrencePattern();
rec.setDay(15);
rec.setPeriod(12);
rec.setPatternType(MapiCalendarRecurrencePatternType.Month);
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=YEARLY;BYMONTHDAY=15;BYMONTH=7;INTERVAL=1"));
~~~

### **Годовые рецидивы: тип бесконечного повторения**

В следующем фрагменте кода показано, как можно установить конечный тип, используя *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Yearly recurrence
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Создать повторение на основе правила повторения**

Aspose.Email API предоставляет возможность генерировать шаблон повторения на основе правила повторения (RRULE). Он анализирует информацию из RRULE в соответствии со спецификациями RFC 5545 iCal и генерирует шаблон повторения с помощью **MapiCalendarRecurrencePatternFactory.fromString** метод. В следующем фрагменте кода показано, как создать шаблон повторения на основе правила повторения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date endDate = getDate(2015, 8, 1);
MapiCalendar app1 = new MapiCalendar("test location", "test summary", "test description", startDate, endDate);

app1.setStartDate(startDate);
app1.setEndDate(endDate);

String pattern = "DTSTART;TZID=Europe/London:20150831T080000\r\nDTEND;TZID=Europe/London:20150831T083000\r\nRRULE:FREQ=DAILY;INTERVAL=1;COUNT=7\r\nEXDATE:20150831T070000Z,20150904T070000Z";
app1.getRecurrence().setRecurrencePattern(MapiCalendarRecurrencePatternFactory.fromString(pattern));
~~~

## **Добавить вложение к повторяющимся событиям календаря**

Aspose.Email API предоставляет возможность добавлять вложения к повторяющимся событиям календаря.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = addHours(getDate(2018, 7, 19), 12);
MapiCalendar calendar = new MapiCalendar("location1", "summary1", "description1", startDate, addHours(startDate, 1));

MapiCalendarEventRecurrence recurrence = new MapiCalendarEventRecurrence();
MapiCalendarRecurrencePattern pattern = new MapiCalendarDailyRecurrencePattern();
recurrence.setRecurrencePattern(pattern);
pattern.setPatternType(MapiCalendarRecurrencePatternType.Day);
pattern.setPeriod(1);
pattern.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);

Date exceptionDate = addDays(startDate, 3);
MapiCalendarExceptionInfo exception = new MapiCalendarExceptionInfo();
exception.setLocation("exceptionLoc");
exception.setSubject("exceptionSubj");
exception.setBody("exceptionBody");
exception.setOriginalStartDate(exceptionDate);
exception.setStartDateTime(exceptionDate);
exception.setEndDateTime(addHours(exceptionDate, 5));
exception.setAttachments(new MapiAttachmentCollection(calendar));
exception.getAttachments().add("file.txt", "hello, world!".getBytes());

pattern.getExceptions().addItem(exception);
pattern.getModifiedInstanceDates().addItem(exceptionDate);
pattern.getDeletedInstanceDates().addItem(exceptionDate);
calendar.setRecurrence(recurrence);

try (PersonalStorage newPst = PersonalStorage.create(dataDir + "AddAttachmentToMapiExceptionInfo.pst", FileFormatVersion.Unicode))
{
    FolderInfo newFolder = newPst.createPredefinedFolder("Calendar", StandardIpmFolder.Appointments);
    newFolder.addMapiMessageItem(calendar);
}
~~~

## **Настройка часового пояса событий в календаре**

Aspose.Email API предоставляет возможность установить часовой пояс календаря:
- информация о часовом поясе для даты начала/окончания
- информация о часовом поясе для повторяющейся встречи
- информация о часовом поясе, описывающая, как преобразовать дату и время совещания в повторяющейся серии в UTC и обратно

В следующем фрагменте кода показано, как настроить информацию о часовом поясе календаря:

~~~Java
MapiCalendar event = new MapiCalendar("location", "summary", "description", startDate, endDate);
// UTC time zone
MapiCalendarTimeZone utcTimeZone = new MapiCalendarTimeZone("UTC");
event.setStartDateTimeZone(utcTimeZone);
event.setEndDateTimeZone(utcTimeZone);

MapiCalendarDailyRecurrencePattern pattern = new MapiCalendarDailyRecurrencePattern();
pattern.setPeriod(1);
pattern.setStartDate(startDate);
pattern.setEndDate(untilDate);
pattern.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
pattern.setPatternType(MapiCalendarRecurrencePatternType.Day);
pattern.setDayOfWeek(DayOfWeek.Monday);

MapiCalendarEventRecurrence r = new MapiCalendarEventRecurrence();
r.setRecurrencePattern(pattern);
r.setClipStart(startDate);
r.setClipEnd(pattern.getEndDate());
//https://docs.microsoft.com/en-us/office/client-developer/outlook/mapi/pidlidappointmenttimezonedefinitionrecur-canonical-property
r.setAppointmentTimeZoneDefinitionRecur(utcTimeZone); // <---
r.setTimeZoneStruct(utcTimeZone); // <---
event.setRecurrence(r);
~~~
