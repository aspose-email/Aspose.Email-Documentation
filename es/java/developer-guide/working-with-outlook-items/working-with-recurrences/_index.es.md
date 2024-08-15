---
title: "Trabajando con recurrencias"
url: /es/java/working-with-recurrences/
weight: 140
type: docs
---


## **Trabajando con las recurrencias diarias**

Aspose.Email admite la creación de recurrencias diarias utilizando [MapiCalendarDailyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendardailyrecurrencepattern/). Se pueden utilizar tres tipos diferentes de finales de recurrencia del calendario Mapi, que incluyen *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. Esta sección muestra la creación de diferentes patrones de recurrencia diaria.

### **Recurrencias diarias: tipo de recurrencia EndAfterNoccurrence**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Cree el objeto de recurrencia diaria configurando las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** propiedad de este objeto de recurrencia diaria.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código se muestra cómo crear una tarea con un tipo de final recurrente como *EndAfterNOccurrence*.

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

La siguiente función se puede utilizar para calcular el número de eventos entre las dos fechas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Configuración del valor del recuento de ocurrencias**

El siguiente fragmento de código muestra cómo establecer el valor del recuento de ocurrencias.

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

### **Recurrencias diarias: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra configurando el *OccurrenceCount* propiedad calculada por el **getOccurrenceCount()** función. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE.

#### **Recurrencias diarias: establecer el valor diario**

En el siguiente fragmento de código, también se muestra cómo establecer el valor del período en 1 y el valor INTERVAL en 1 en la cadena RRULE.

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

El valor de cada día se puede establecer en cualquier valor apropiado, como se muestra en el siguiente ejemplo:

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(2);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=2"));
~~~

### **Recurrencias diarias: tipo de recurrencia sin fin**

El tipo de extremo se puede configurar mediante *MapiCalendarRecurrenceEndType.NeverEnd*. El período o el INTERVALO se pueden establecer en el valor requerido, por ejemplo, 1 en el siguiente ejemplo.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Trabajando con recurrencias semanales**

Aspose.Email proporciona funciones completas para la creación de recurrencias semanales utilizando [MapiCalendarWeeklyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarweeklyrecurrencepattern/). Se pueden utilizar tres tipos diferentes de finales de recurrencia del calendario Mapi, que incluyen *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. Esta sección muestra la creación de diferentes patrones de recurrencia semanal.

### **Recurrencias semanales: tipo de recurrencia EndAfterNoccurrences**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Cree el objeto de periodicidad semanal estableciendo las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** propiedad de este objeto de periodicidad semanal.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código se muestra cómo crear una tarea con un tipo de final recurrente como *EndAfterNOccurrence*.

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

La siguiente función se puede utilizar para calcular el número de eventos entre las dos fechas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Selección de varios días en una semana**

En el siguiente fragmento de código, se muestra cómo seleccionar varios días de la semana.

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

#### **Selección de varios días en una semana y configuración de intervalos**

El siguiente fragmento de código muestra cómo seleccionar varios días de una semana y establecer intervalos.

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

### **Recurrencias semanales: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra configurando el *OccurrenceCount* propiedad calculada por el **getOccurrenceCount()** función. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE.

#### **Recurrencias semanales: establecer el valor diario**

En el siguiente fragmento de código, también se muestra cómo establecer el valor del período en 1 y el valor INTERVAL en 1 en la cadena RRULE.

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

El valor de cada día se puede establecer en cualquier valor apropiado y se pueden seleccionar varios días como se muestra en el siguiente ejemplo:

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

### **Recurrencias semanales: tipo de recurrencia sin fin**

El tipo de extremo se puede configurar mediante *MapiCalendarRecurrenceEndType.NeverEnd*. El período o el INTERVALO se pueden establecer en el valor requerido, por ejemplo, 1 en el siguiente ejemplo.



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

## **Trabajando con recurrencias mensuales**

Aspose.Email admite la creación de recurrencias mensuales utilizando [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Se pueden utilizar tres tipos diferentes de finales de recurrencia del calendario Mapi, que incluyen *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. En esta sección se muestra la creación de diferentes patrones de recurrencia mensual.

### **Recurrencias mensuales: tipo de recurrencia de EndAfternoCurrences**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Cree el objeto de periodicidad mensual configurando las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** propiedad de este objeto de periodicidad mensual.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código se muestra cómo crear una tarea con un tipo de final recurrente como *EndAfterNOccurrence*.

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

La siguiente función se puede utilizar para calcular el número de eventos entre dos fechas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Establecer el número fijo de ocurrencias**

El siguiente fragmento de código muestra cómo establecer un número fijo de ocurrencias.

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

### **Recurrencias mensuales: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra configurando el *OccurrenceCount* propiedad calculada por el **getOccurrenceCount()** función. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE. El siguiente fragmento de código muestra cómo crear una repetición el día 15 de cada mes entre la fecha de inicio y la fecha de caducidad.

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

### **Recurrencias mensuales: tipo de recurrencia sin fin**

El siguiente fragmento de código muestra cómo se puede configurar el tipo de extremo mediante *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(1);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setWeekStartDay(DayOfWeek.Monday);
~~~

## **Trabajando con recurrencias anuales**

Aspose.Email admite la creación de recurrencias anuales utilizando [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Al establecer la propiedad del período en 12, podemos lograr el patrón de recurrencia anual. Se pueden usar tres tipos diferentes de finales de recurrencia del calendario Mapi, que incluyen *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. Esta sección muestra la creación de diferentes patrones de recurrencia anual.

### **Recurrencias anuales: tipo de recurrencia EndAfterNoccurrences**

En este tipo de recurrencia, el número de recurrencias se establecerá junto con otra información de la siguiente manera:

1. Establezca la fecha de inicio, finalización y vencimiento.
1. Crea un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Cree el objeto de periodicidad mensual configurando las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** propiedad de este objeto de periodicidad mensual para lograr la periodicidad anual.
1. Guarde este mensaje en el disco.

En el siguiente fragmento de código se muestra cómo crear una tarea con un tipo de final recurrente como *EndAfterNOccurrence*.

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

### **Recurrencias anuales: tipo de recurrencia EndAfterDate**

La opción «Finalizar por» de la tarea Mapi se logra configurando el *OccurrenceCount* propiedad calculada por el **getOccurrenceCount()** función. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE. El siguiente fragmento de código muestra cómo crear una repetición el día 15 de cada séptimo mes entre la fecha de inicio y la fecha de caducidad.

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

### **Recurrencias anuales: tipo de recurrencia sin fin**

El siguiente fragmento de código muestra cómo se puede configurar el tipo de extremo mediante *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Yearly recurrence
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Generar repetición a partir de la regla de recurrencia**

La API Aspose.Email brinda la capacidad de generar un patrón de recurrencia a partir de la regla de recurrencia (RRULE). Analiza la información de la RRULE según las especificaciones de iCal según la RFC 5545 y genera el patrón de recurrencia mediante el **MapiCalendarRecurrencePatternFactory.fromString** método. El siguiente fragmento de código muestra cómo generar un patrón de recurrencia a partir de la regla de recurrencia.

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

## **Agregar datos adjuntos a los eventos periódicos del calendario**

La API Aspose.Email ofrece la capacidad de agregar archivos adjuntos a los eventos periódicos del calendario.

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

## **Establecer la zona horaria de los eventos del calendario**

La API Aspose.Email ofrece la capacidad de establecer la zona horaria del calendario:
- información de zona horaria para la fecha de inicio y finalización
- información de zona horaria para una reunión periódica
- información de zona horaria que describe cómo convertir la fecha y la hora de la reunión en una serie periódica a y desde UTC

En el siguiente fragmento de código, se muestra cómo configurar la información de la zona horaria del calendario:

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
