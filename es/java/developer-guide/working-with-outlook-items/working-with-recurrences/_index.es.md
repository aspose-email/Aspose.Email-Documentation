---
title: "Trabajando con recurrencias"
url: /es/java/trabajando-con-recurrencias/
weight: 140
type: docs
---


## **Trabajando con recurrencias diarias**

Aspose.Email soporta la creación de recurrencias diarias utilizando [MapiCalendarDailyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendardailyrecurrencepattern/). Se pueden usar tres tipos diferentes de finales de recurrencia en el calendario Mapi, incluyendo *EndAfterNOccurrences*, *EndAfterDate* y *NeverEnd*. Esta sección demuestra la creación de diferentes patrones de recurrencia diaria.

### **Recurrencias diarias: Tipo de recurrencia EndAfterNOccurrence**

En este tipo de recurrencia, se debe fijar el número de recurrencias junto con otra información de la siguiente manera:

1. Establecer fecha de inicio, final y de vencimiento.
1. Crear un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Crear el objeto de recurrencia diaria configurando las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* y *OccurenceCount*.
1. Establecer la propiedad **MapiTask.setRecurrence** a este objeto de recurrencia diaria.
1. Guardar este mensaje en disco.

El siguiente fragmento de código muestra cómo crear una tarea con el tipo de fin de recurrencia como *EndAfterNOccurrence*.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 8, 1);
 
MapiTask task = new MapiTask("Esta es una tarea de prueba", "Cuerpo de ejemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Establecer la recurrencia diaria
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

La siguiente función puede ser utilizada para calcular el número de eventos entre las dos fechas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Estableciendo el valor del conteo de ocurrencias**

El siguiente fragmento de código muestra cómo establecer el valor del conteo de ocurrencias.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia diaria
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
record.setOccurrenceCount(5);
task.setRecurrence(record);
~~~

### **Recurrencias diarias: Tipo de recurrencia EndAfterDate**

La opción "Finaliza en" en la tarea Mapi se logra configurando la propiedad *OccurrenceCount* calculada por la función **getOccurrenceCount()**. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE.

#### **Recurrencias diarias: Estableciendo el valor de cada día**

El siguiente fragmento de código muestra cómo establecer el valor del periodo a 1 y el valor de INTERVALO a 1 en la cadena RRULE también.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia diaria
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=1"));
record.setEndDate(endByDate);
~~~

El valor de cada día puede establecerse en cualquier valor apropiado como se muestra en el siguiente ejemplo:

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia diaria
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(2);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=2"));
~~~

### **Recurrencias diarias: Tipo de recurrencia NeverEnd**

El tipo de fin puede establecerse utilizando *MapiCalendarRecurrenceEndType.NeverEnd*. El periodo o INTERVALO puede establecerse en el valor requerido, digamos 1 en el siguiente ejemplo.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia diaria
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Trabajando con recurrencias semanales**

Aspose.Email proporciona ricas características para la creación de recurrencias semanales utilizando [MapiCalendarWeeklyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarweeklyrecurrencepattern/). Se pueden usar tres tipos diferentes de finales de recurrencia en el calendario Mapi, incluyendo *EndAfterNOccurrences*, *EndAfterDate* y *NeverEnd*. Esta sección demuestra la creación de diferentes patrones de recurrencia semanal.

### **Recurrencias semanales: Tipo de recurrencia EndAfterNOccurrences**

En este tipo de recurrencia, se debe fijar el número de recurrencias junto con otra información de la siguiente manera:

1. Establecer fecha de inicio, final y de vencimiento.
1. Crear un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Crear el objeto de recurrencia semanal configurando las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* y *OccurenceCount*.
1. Establecer la propiedad **MapiTask.setRecurrence** a este objeto de recurrencia semanal.
1. Guardar este mensaje en disco.

El siguiente fragmento de código muestra cómo crear una tarea con el tipo de fin de recurrencia como *EndAfterNOccurrence*.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 9, 1);

MapiTask task = new MapiTask("Esta es una tarea de prueba", "Cuerpo de ejemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Establecer la recurrencia semanal
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

La siguiente función puede ser utilizada para calcular el número de eventos entre las dos fechas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Seleccionando múltiples días en una semana**

El siguiente fragmento de código muestra cómo seleccionar múltiples días en una semana.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia semanal
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();

rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO"));
~~~

#### **Seleccionando múltiples días en una semana y estableciendo intervalos**

El siguiente fragmento de código muestra cómo seleccionar múltiples días en una semana y establecer intervalos.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia semanal
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(2);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Recurrencias semanales: Tipo de recurrencia EndAfterDate**

La opción "Finaliza en" en la tarea Mapi se logra configurando la propiedad *OccurrenceCount* calculada por la función **getOccurrenceCount()**. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE.

#### **Recurrencias semanales: Estableciendo el valor de cada día**

El siguiente fragmento de código muestra cómo establecer el valor del periodo a 1 y el valor de INTERVALO a 1 en la cadena RRULE también.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia semanal
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR;INTERVAL=1"));
~~~

El valor de cada día puede establecerse en cualquier valor apropiado y se pueden seleccionar múltiples días como se muestra en el siguiente ejemplo:

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarWeeklyRecurrencePattern record = new MapiCalendarWeeklyRecurrencePattern();
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setPatternType(MapiCalendarRecurrencePatternType.Week);
record.setPeriod(2);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndDate(endByDate);
record.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Recurrencias semanales: Tipo de recurrencia NeverEnd**

El tipo de fin puede establecerse utilizando *MapiCalendarRecurrenceEndType.NeverEnd*. El periodo o INTERVALO puede establecerse en el valor requerido, digamos 1 en el siguiente ejemplo.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia semanal
MapiCalendarWeeklyRecurrencePattern recurrence = new MapiCalendarWeeklyRecurrencePattern();
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Week);
recurrence.setPeriod(1);
recurrence.setWeekStartDay(DayOfWeek.Sunday);
recurrence.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
recurrence.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR"));
~~~

## **Trabajando con recurrencias mensuales**

Aspose.Email soporta la creación de recurrencias mensuales utilizando [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Se pueden usar tres tipos diferentes de finales de recurrencia en el calendario Mapi, incluyendo *EndAfterNOccurrences*, *EndAfterDate* y *NeverEnd*. Esta sección demuestra la creación de diferentes patrones de recurrencia mensual.

### **Recurrencias mensuales: Tipo de recurrencia EndAfterNOccurrences**

En este tipo de recurrencia, el número de recurrencias debe fijarse junto con otra información de la siguiente manera:

1. Establecer fecha de inicio, final y de vencimiento.
1. Crear un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Crear el objeto de recurrencia mensual configurando las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* y *OccurenceCount*.
1. Establecer la propiedad **MapiTask.setRecurrence** a este objeto de recurrencia mensual.
1. Guardar este mensaje en disco.

El siguiente fragmento de código muestra cómo crear una tarea con el tipo de fin de recurrencia como *EndAfterNOccurrence*.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
// La ruta al directorio de archivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date DueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("Esta es una tarea de prueba", "Cuerpo de ejemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Establecer la recurrencia mensual
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

La siguiente función puede ser utilizada para calcular el número de eventos entre dos fechas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Establecer número fijo de ocurrencias**

El siguiente fragmento de código muestra cómo establecer un número fijo de ocurrencias.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia mensual
MapiCalendarMonthlyRecurrencePattern records = new MapiCalendarMonthlyRecurrencePattern();
records.setDay(15);
records.setPeriod(1);
records.setPatternType(MapiCalendarRecurrencePatternType.Month);
records.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
records.setOccurrenceCount(5);
records.setWeekStartDay(DayOfWeek.Monday);
~~~

### **Recurrencias mensuales: Tipo de recurrencia EndAfterDate**

La opción "Finaliza en" en la tarea Mapi se logra configurando la propiedad *OccurrenceCount* calculada por la función **getOccurrenceCount()**. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE. El siguiente fragmento de código muestra cómo crear una recurrencia el día 15 de cada mes entre la fecha de inicio y la fecha de fin.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("Esta es una tarea de prueba", "Cuerpo de ejemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Establecer la recurrencia mensual
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

### **Recurrencias mensuales: Tipo de recurrencia NeverEnd**

El siguiente fragmento de código muestra cómo se puede establecer el tipo de fin utilizando *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(1);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setWeekStartDay(DayOfWeek.Monday);
~~~

## **Trabajando con recurrencias anuales**

Aspose.Email soporta la creación de recurrencias anuales utilizando [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Al establecer la propiedad de periodo en 12, podemos lograr el patrón de recurrencia anual. Se pueden utilizar tres tipos diferentes de finales de recurrencia en el calendario Mapi, incluyendo *EndAfterNOccurrences*, *EndAfterDate* y *NeverEnd*. Esta sección demuestra la creación de diferentes patrones de recurrencia anual.

### **Recurrencias anuales: Tipo de recurrencia EndAfterNOccurrences**

En este tipo de recurrencia, se debe fijar el número de recurrencias junto con otra información de la siguiente manera:

1. Establecer fecha de inicio, final y de vencimiento.
1. Crear un [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Establecer el estado de la tarea en *NotAssigned*.
1. Crear el objeto de recurrencia mensual configurando las propiedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* y *OccurenceCount*.
1. Establecer la propiedad **MapiTask.setRecurrence** a este objeto de recurrencia mensual para lograr la recurrencia anual.
1. Guardar este mensaje en disco.

El siguiente fragmento de código muestra cómo crear una tarea con el tipo de fin de recurrencia como *EndAfterNOccurrence*.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);

MapiTask task = new MapiTask("Esta es una tarea de prueba", "Cuerpo de ejemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Establecer la recurrencia anual
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
recurrence.setOccurrenceCount(3);

task.setRecurrence(recurrence);
task.save("Yearly.msg", TaskSaveFormat.Msg);
~~~

### **Recurrencias anuales: Tipo de recurrencia EndAfterDate**

La opción "Finaliza en" en la tarea Mapi se logra configurando la propiedad *OccurrenceCount* calculada por la función **getOccurrenceCount()**. Esta función toma la fecha de inicio, la fecha de finalización y la cadena RRULE. El siguiente fragmento de código muestra cómo crear una recurrencia el día 15 de cada 7mo mes entre la fecha de inicio y la fecha de fin.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia anual
MapiCalendarMonthlyRecurrencePattern rec = new MapiCalendarMonthlyRecurrencePattern();
rec.setDay(15);
rec.setPeriod(12);
rec.setPatternType(MapiCalendarRecurrencePatternType.Month);
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=YEARLY;BYMONTHDAY=15;BYMONTH=7;INTERVAL=1"));
~~~

### **Recurrencias anuales: Tipo de recurrencia NeverEnd**

El siguiente fragmento de código muestra cómo se puede establecer el tipo de fin utilizando *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// Establecer la recurrencia anual
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Generar recurrencia desde la regla de recurrencia**

La API de Aspose.Email proporciona la capacidad de generar un patrón de recurrencia a partir de la regla de recurrencia (RRULE). Analiza la información de la RRULE según las especificaciones iCal RFC 5545 y genera el patrón de recurrencia utilizando el método **MapiCalendarRecurrencePatternFactory.fromString**. El siguiente fragmento de código muestra cómo generar el patrón de recurrencia a partir de la regla de recurrencia.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date endDate = getDate(2015, 8, 1);
MapiCalendar app1 = new MapiCalendar("ubicación de prueba", "resumen de prueba", "descripción de prueba", startDate, endDate);

app1.setStartDate(startDate);
app1.setEndDate(endDate);

String pattern = "DTSTART;TZID=Europe/London:20150831T080000\r\nDTEND;TZID=Europe/London:20150831T083000\r\nRRULE:FREQ=DAILY;INTERVAL=1;COUNT=7\r\nEXDATE:20150831T070000Z,20150904T070000Z";
app1.getRecurrence().setRecurrencePattern(MapiCalendarRecurrencePatternFactory.fromString(pattern));
~~~

## **Agregar adjunto a eventos de calendario recurrentes**

La API de Aspose.Email proporciona la capacidad de agregar adjuntos a eventos de calendario recurrentes.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = addHours(getDate(2018, 7, 19), 12);
MapiCalendar calendar = new MapiCalendar("ubicación1", "resumen1", "descripción1", startDate, addHours(startDate, 1));

MapiCalendarEventRecurrence recurrence = new MapiCalendarEventRecurrence();
MapiCalendarRecurrencePattern pattern = new MapiCalendarDailyRecurrencePattern();
recurrence.setRecurrencePattern(pattern);
pattern.setPatternType(MapiCalendarRecurrencePatternType.Day);
pattern.setPeriod(1);
pattern.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);

Date exceptionDate = addDays(startDate, 3);
MapiCalendarExceptionInfo exception = new MapiCalendarExceptionInfo();
exception.setLocation("ubicación de excepción");
exception.setSubject("asunto de excepción");
exception.setBody("cuerpo de excepción");
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
    FolderInfo newFolder = newPst.createPredefinedFolder("Calendario", StandardIpmFolder.Appointments);
    newFolder.addMapiMessageItem(calendar);
}
~~~ 

## **Establecer la zona horaria del evento del calendario**

La API de Aspose.Email proporciona la capacidad de establecer información de zona horaria del calendario:
- información de zona horaria para la fecha/hora de inicio/final
- información de zona horaria para una reunión recurrente
- información de zona horaria que describe cómo convertir la fecha y hora de la reunión en una serie recurrente de y hacia UTC

El siguiente fragmento de código muestra cómo establecer la información de la zona horaria del calendario:

~~~Java
MapiCalendar event = new MapiCalendar("ubicación", "resumen", "descripción", startDate, endDate);
// zona horaria UTC
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