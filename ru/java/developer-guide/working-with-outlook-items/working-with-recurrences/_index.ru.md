---
title: "Работа с повторами"
url: /ru/java/working-with-recurrences/
weight: 140
type: docs
---


## **Работа с ежедневными повторами**

Aspose.Email поддерживает создание ежедневных повторов с использованием [MapiCalendarDailyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendardailyrecurrencepattern/). Можно использовать три различных типа окончания повторов в Mapi календаре: *EndAfterNOccurrences*, *EndAfterDate* и *NeverEnd*. Этот раздел демонстрирует создание различных шаблонов ежедневных повторов.

### **Ежедневные повторы: тип повторов EndAfterNOccurrence**

В этом типе повтора количество повторов устанавливается вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и дату исполнения.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Установите состояние задачи на *NotAssigned*.
1. Создайте объект ежедневного повтора, установив свойства, такие как *PatternType*, *Period*, *WeekStartDay*, *EndType* и *OccurenceCount*.
1. Установите свойство **MapiTask.setRecurrence** на этот объект ежедневного повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора *EndAfterNOccurrence*.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 8, 1);
 
MapiTask task = new MapiTask("Это тестовая задача", "Пример текста", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Установите ежедневный повтор
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

Следующая функция может быть использована для подсчета количества событий между двумя датами:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Установка значения количества повторов**

Следующий фрагмент кода показывает, как установить значение количества повторов.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите ежедневный повтор
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
record.setOccurrenceCount(5);
task.setRecurrence(record);
~~~

### **Ежедневные повторы: тип повторов EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства *OccurrenceCount*, которое рассчитывается с помощью функции **getOccurrenceCount()**. Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Ежедневные повторы: установка значения Every Day**

Следующий фрагмент кода показывает, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите ежедневный повтор
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=1"));
record.setEndDate(endByDate);
~~~

Значение Every Day может быть установлено на любое подходящее значение, как показано в следующем примере:

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите ежедневный повтор
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(2);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=2"));
~~~

### **Ежедневные повторы: тип повторов NeverEnd**

Тип окончания может быть установлен с использованием *MapiCalendarRecurrenceEndType.NeverEnd*. Период или INTERVAL могут быть установлены на требуемое значение, скажем, 1 в следующем примере.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите ежедневный повтор
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Работа с еженедельными повторами**

Aspose.Email предоставляет широкий спектр возможностей для создания еженедельных повторов с использованием [MapiCalendarWeeklyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarweeklyrecurrencepattern/). Можно использовать три различных типа окончания повторов в Mapi календаре: *EndAfterNOccurrences*, *EndAfterDate* и *NeverEnd*. Этот раздел демонстрирует создание различных шаблонов еженедельных повторов.

### **Еженедельные повторы: тип повторов EndAfterNOccurrences**

В этом типе повтора количество повторов устанавливается вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и дату исполнения.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Установите состояние задачи на *NotAssigned*.
1. Создайте объект еженедельного повтора, установив свойства, такие как *PatternType*, *Period*, *WeekStartDay*, *EndType* и *OccurenceCount*.
1. Установите свойство **MapiTask.setRecurrence** на этот объект еженедельного повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора *EndAfterNOccurrence*.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 9, 1);

MapiTask task = new MapiTask("Это тестовая задача", "Пример текста", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Установите еженедельный повтор
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

Следующая функция может быть использована для подсчета количества событий между двумя датами:

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

Следующий фрагмент кода показывает, как выбрать несколько дней в неделю.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите еженедельный повтор
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();

rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO"));
~~~

#### **Выбор нескольких дней в неделю и установка интервалов**

Следующий фрагмент кода показывает, как выбрать несколько дней в неделю и установить интервалы.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите еженедельный повтор
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(2);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Еженедельные повторы: тип повторов EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства *OccurrenceCount*, которое рассчитывается с помощью функции **getOccurrenceCount()**. Эта функция принимает дату начала, дату окончания и строку RRULE.

#### **Еженедельные повторы: установка значения Every Day**

Следующий фрагмент кода показывает, как установить значение периода на 1 и значение INTERVAL на 1 в строке RRULE.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите еженедельный повтор
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR;INTERVAL=1"));
~~~

Значение Every Day может быть установлено на любое подходящее значение, и можно выбрать несколько дней, как показано в следующем примере:

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarWeeklyRecurrencePattern record = new MapiCalendarWeeklyRecurrencePattern();
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setPatternType(MapiCalendarRecurrencePatternType.Week);
record.setPeriod(2);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndDate(endByDate);
record.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Еженедельные повторы: тип повторов NeverEnd**

Тип окончания может быть установлен с использованием *MapiCalendarRecurrenceEndType.NeverEnd*. Период или INTERVAL могут быть установлены на требуемое значение, скажем, 1 в следующем примере.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите еженедельный повтор
MapiCalendarWeeklyRecurrencePattern recurrence = new MapiCalendarWeeklyRecurrencePattern();
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Week);
recurrence.setPeriod(1);
recurrence.setWeekStartDay(DayOfWeek.Sunday);
recurrence.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
recurrence.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR"));
~~~

## **Работа с ежемесячными повторами**

Aspose.Email поддерживает создание ежемесячных повторов с использованием [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Можно использовать три различных типа окончания повторов в Mapi календаре: *EndAfterNOccurrences*, *EndAfterDate* и *NeverEnd*. Этот раздел демонстрирует создание различных шаблонов ежемесячных повторов.

### **Ежемесячные повторы: тип повторов EndAfterNOccurrences**

В этом типе повтора количество повторов устанавливается вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и дату исполнения.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Установите состояние задачи на *NotAssigned*.
1. Создайте объект ежемесячного повтора, установив свойства, такие как *PatternType*, *Period*, *WeekStartDay*, *EndType* и *OccurenceCount*.
1. Установите свойство **MapiTask.setRecurrence** на этот объект ежемесячного повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора *EndAfterNOccurrence*.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-.NET
// Путь к директории файлов.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("Это тестовая задача", "Пример текста", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Установите ежемесячный повтор
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

Следующая функция может быть использована для подсчета количества событий между двумя датами:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Установить фиксированное количество повторов**

Следующий фрагмент кода показывает, как установить фиксированное количество повторов.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите ежемесячный повтор
MapiCalendarMonthlyRecurrencePattern records = new MapiCalendarMonthlyRecurrencePattern();
records.setDay(15);
records.setPeriod(1);
records.setPatternType(MapiCalendarRecurrencePatternType.Month);
records.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
records.setOccurrenceCount(5);
records.setWeekStartDay(DayOfWeek.Monday);
~~~

### **Ежемесячные повторы: тип повторов EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства *OccurrenceCount*, которое рассчитывается с помощью функции **getOccurrenceCount()**. Эта функция принимает дату начала, дату окончания и строку RRULE. Следующий фрагмент кода показывает, как создать повтор на 15-е число каждого месяца между датой начала и датой окончания.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("Это тестовая задача", "Пример текста", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Установите ежемесячный повтор
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

### **Ежемесячные повторы: тип повторов NeverEnd**

Следующий фрагмент кода показывает, как тип окончания может быть установлен с использованием *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(1);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setWeekStartDay(DayOfWeek.Monday);
~~~

## **Работа с годовыми повторами**

Aspose.Email поддерживает создание годовыми повторами с использованием [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Установив значение свойства периода на 12, мы можем достичь годового повторного шаблона. Можно использовать три различных типа окончания повторов в Mapi календаре: *EndAfterNOccurrences*, *EndAfterDate* и *NeverEnd*. Этот раздел демонстрирует создание различных шаблонов годовых повторов.

### **Годовые повторы: тип повторов EndAfterNOccurrences**

В этом типе повтора устанавливается количество повторов вместе с другой информацией следующим образом:

1. Установите дату начала, окончания и дату исполнения.
1. Создайте [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Установите состояние задачи на *NotAssigned*.
1. Создайте объект ежемесячного повтора, установив свойства, такие как *PatternType*, *Period*, *WeekStartDay*, *EndType* и *OccurenceCount*.
1. Установите свойство **MapiTask.setRecurrence** на этот объект ежемесячного повтора для достижения годового повтора.
1. Сохраните это сообщение на диске.

Следующий фрагмент кода показывает, как создать задачу с типом окончания повтора *EndAfterNOccurrence*.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);

MapiTask task = new MapiTask("Это тестовая задача", "Пример текста", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Установите годовой повтор
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
recurrence.setOccurrenceCount(3);

task.setRecurrence(recurrence);
task.save("Yearly.msg", TaskSaveFormat.Msg);
~~~

### **Годовые повторы: тип повторов EndAfterDate**

Опция "End By" в Mapi Task достигается путем установки свойства *OccurrenceCount*, которое рассчитывается с помощью функции **getOccurrenceCount()**. Эта функция принимает дату начала, дату окончания и строку RRULE. Следующий фрагмент кода показывает, как создать повтор на 15-е число каждого 7-го месяца между датой начала и датой окончания.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите годовой повтор
MapiCalendarMonthlyRecurrencePattern rec = new MapiCalendarMonthlyRecurrencePattern();
rec.setDay(15);
rec.setPeriod(12);
rec.setPatternType(MapiCalendarRecurrencePatternType.Month);
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=YEARLY;BYMONTHDAY=15;BYMONTH=7;INTERVAL=1"));
~~~

### **Годовые повторы: тип повторов NeverEnd**

Следующий фрагмент кода показывает, как тип окончания может быть установлен с использованием *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Установите годовой повтор
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Генерация повтора из правила повторов**

API Aspose.Email предоставляет возможность генерировать шаблон повтора из правила повтора (RRULE). Он разбирает информацию из RRULE в соответствии с RFC 5545 iCal спецификациями и генерирует шаблон повтора с использованием метода **MapiCalendarRecurrencePatternFactory.fromString**. Следующий фрагмент кода показывает, как сгенерировать шаблон повтора из правила повтора.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date endDate = getDate(2015, 8, 1);
MapiCalendar app1 = new MapiCalendar("тестовое место", "тестовое резюме", "тестовое описание", startDate, endDate);

app1.setStartDate(startDate);
app1.setEndDate(endDate);

String pattern = "DTSTART;TZID=Europe/London:20150831T080000\r\nDTEND;TZID=Europe/London:20150831T083000\r\nRRULE:FREQ=DAILY;INTERVAL=1;COUNT=7\r\nEXDATE:20150831T070000Z,20150904T070000Z";
app1.getRecurrence().setRecurrencePattern(MapiCalendarRecurrencePatternFactory.fromString(pattern));
~~~

## **Добавление вложений к повторяющимся календарным событиям**

API Aspose.Email предоставляет возможность добавлять вложения к повторяющимся календарным событиям.

~~~Java
// Для полноценных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = addHours(getDate(2018, 7, 19), 12);
MapiCalendar calendar = new MapiCalendar("место1", "резюме1", "описание1", startDate, addHours(startDate, 1));

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
    FolderInfo newFolder = newPst.createPredefinedFolder("Календарь", StandardIpmFolder.Appointments);
    newFolder.addMapiMessageItem(calendar);
}
~~~

## **Установка часового пояса для календарного события**

API Aspose.Email предоставляет возможность устанавливать информацию о часовом поясе для календаря:
- информация о часовом поясе для даты начала/окончания
- информация о часовом поясе для повторяющейся встречи
- информация о часовом поясе, описывающая, как конвертировать дату и время встречи в повторяющейся серии в и из UTC

Следующий фрагмент кода показывает, как установить информацию о часовом поясе для календаря:

~~~Java
MapiCalendar event = new MapiCalendar("место", "резюме", "описание", startDate, endDate);
// Часовой пояс UTC
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