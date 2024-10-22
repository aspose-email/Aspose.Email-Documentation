---
title: "Trabalhando com Recorrências"
url: /pt/java/trabalhando-com-recorrencias/
weight: 140
type: docs
---


## **Trabalhando Com Recorrências Diárias**

Aspose.Email suporta a criação de recorrências diárias usando [MapiCalendarDailyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendardailyrecurrencepattern/). Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo *EndAfterNOccurrences*, *EndAfterDate* e *NeverEnd*. Esta seção demonstra a criação de diferentes padrões de recorrência diária.

### **Recorrências Diárias: Tipo de Recorrência EndAfterNOccurrence**

Neste tipo de recorrência, o número de recorrências deve ser definido juntamente com outras informações da seguinte forma:

1. Defina a data de início, término e vencimento.
1. Crie um [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Defina o estado da tarefa como *NotAssigned*.
1. Crie o objeto de recorrência diária definindo as propriedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* e *OccurenceCount*.
1. Defina a propriedade **MapiTask.setRecurrence** para este objeto de recorrência diária.
1. Salve esta mensagem no disco.

O seguinte snippet de código mostra como criar uma tarefa com o tipo de término de recorrência como *EndAfterNOccurrence*.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 8, 1);
 
MapiTask task = new MapiTask("Esta é uma tarefa de teste", "Corpo de Exemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Defina a recorrência diária
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

A seguinte função pode ser usada para calcular o número de eventos entre as duas datas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Definindo o Valor do Contador de Ocorrências**

O seguinte snippet de código mostra como definir o valor do contador de ocorrências.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência diária
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
record.setOccurrenceCount(5);
task.setRecurrence(record);
~~~

### **Recorrências Diárias: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade *OccurrenceCount* calculada pela função **getOccurrenceCount()**. Esta função leva a data de início, a data de término e a string RRULE.

#### **Recorrências Diárias: Definindo o Valor de Todo Dia**

O seguinte snippet de código mostra como definir o valor do período como 1 e o valor do INTERVALO como 1 na string RRULE também.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência diária
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=1"));
record.setEndDate(endByDate);
~~~

O valor de Todo Dia pode ser definido como qualquer valor apropriado, conforme mostrado no seguinte exemplo:

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência diária
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(2);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=2"));
~~~

### **Recorrências Diárias: Tipo de Recorrência NeverEnd**

O tipo de término pode ser definido usando *MapiCalendarRecurrenceEndType.NeverEnd*. O período ou INTERVALO pode ser definido como o valor necessário, digamos 1 no seguinte exemplo.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência diária
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Trabalhando Com Recorrências Semanais**

Aspose.Email oferece ricos recursos para criação de recorrências semanais usando [MapiCalendarWeeklyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarweeklyrecurrencepattern/). Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo *EndAfterNOccurrences*, *EndAfterDate* e *NeverEnd*. Esta seção demonstra a criação de diferentes padrões de recorrência semanal.

### **Recorrências Semanais: Tipo de Recorrência EndAfterNOccurrences**

Neste tipo de recorrência, o número de recorrências deve ser definido juntamente com outras informações da seguinte forma:

1. Defina a data de início, término e vencimento.
1. Crie um [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Defina o estado da tarefa como *NotAssigned*.
1. Crie o objeto de recorrência semanal definindo as propriedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* e *OccurenceCount*.
1. Defina a propriedade **MapiTask.setRecurrence** para este objeto de recorrência semanal.
1. Salve esta mensagem no disco.

O seguinte snippet de código mostra como criar uma tarefa com o tipo de término de recorrência como *EndAfterNOccurrence*.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date dueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 9, 1);

MapiTask task = new MapiTask("Esta é uma tarefa de teste", "Corpo de Exemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Defina a recorrência semanal
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

A função a seguir pode ser usada para calcular o número de eventos entre as duas datas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Selecionando Múltiplos Dias em Uma Semana**

O seguinte snippet de código mostra como selecionar múltiplos dias em uma semana.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência semanal
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();

rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO"));
~~~

#### **Selecionando Múltiplos Dias em Uma Semana e Definindo Intervalos**

O seguinte snippet de código mostra como selecionar múltiplos dias em uma semana e definir intervalos.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência semanal
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(2);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Recorrências Semanais: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade *OccurrenceCount* calculada pela função **getOccurrenceCount()**. Esta função leva a data de início, a data de término e a string RRULE.

#### **Recorrências Semanais: Definindo o Valor de Todo Dia**

O seguinte snippet de código mostra como definir o valor do período como 1 e o valor do INTERVALO como 1 na string RRULE também.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência semanal
MapiCalendarWeeklyRecurrencePattern rec = new MapiCalendarWeeklyRecurrencePattern();
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setPatternType(MapiCalendarRecurrencePatternType.Week);
rec.setPeriod(1);
rec.setWeekStartDay(DayOfWeek.Sunday);
rec.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR;INTERVAL=1"));
~~~

O valor de Todo Dia pode ser definido como qualquer valor apropriado e múltiplos dias podem ser selecionados conforme mostrado no seguinte exemplo:

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarWeeklyRecurrencePattern record = new MapiCalendarWeeklyRecurrencePattern();
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setPatternType(MapiCalendarRecurrencePatternType.Week);
record.setPeriod(2);
record.setWeekStartDay(DayOfWeek.Sunday);
record.setEndDate(endByDate);
record.setDayOfWeek(MapiCalendarDayOfWeek.Friday | MapiCalendarDayOfWeek.Monday);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR,MO;INTERVAL=2"));
~~~

### **Recorrências Semanais: Tipo de Recorrência NeverEnd**

O tipo de término pode ser definido usando *MapiCalendarRecurrenceEndType.NeverEnd*. O período ou INTERVALO pode ser definido como o valor necessário, digamos 1 no seguinte exemplo.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência semanal
MapiCalendarWeeklyRecurrencePattern recurrence = new MapiCalendarWeeklyRecurrencePattern();
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Week);
recurrence.setPeriod(1);
recurrence.setWeekStartDay(DayOfWeek.Sunday);
recurrence.setDayOfWeek(MapiCalendarDayOfWeek.Friday);
recurrence.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=WEEKLY;BYDAY=FR"));
~~~

## **Trabalhando Com Recorrências Mensais**

Aspose.Email suporta a criação de recorrências mensais usando [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo *EndAfterNOccurrences*, *EndAfterDate* e *NeverEnd*. Esta seção demonstra a criação de diferentes padrões de recorrência mensal.

### **Recorrências Mensais: Tipo de Recorrência EndAfterNOccurrences**

Neste tipo de recorrência, o número de recorrências deve ser definido juntamente com outras informações da seguinte forma:

1. Defina a data de início, término e vencimento.
1. Crie um [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Defina o estado da tarefa como *NotAssigned*.
1. Crie o objeto de recorrência mensal definindo as propriedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* e *OccurenceCount*.
1. Defina a propriedade **MapiTask.setRecurrence** para este objeto de recorrência mensal.
1. Salve esta mensagem no disco.

O seguinte snippet de código mostra como criar uma tarefa com o tipo de término de recorrência como *EndAfterNOccurrence*.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-.NET
// O caminho para o diretório de arquivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date DueDate = getDate(2015, 7, 16);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("Esta é uma tarefa de teste", "Corpo de Exemplo", startDate, DueDate);
task.setState(MapiTaskState.NotAssigned);

// Defina a recorrência mensal
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

A seguinte função pode ser usada para calcular o número de eventos entre duas datas:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Definir Número Fixo de Ocorrências**

O seguinte snippet de código mostra como definir um número fixo de ocorrências.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência mensal
MapiCalendarMonthlyRecurrencePattern records = new MapiCalendarMonthlyRecurrencePattern();
records.setDay(15);
records.setPeriod(1);
records.setPatternType(MapiCalendarRecurrencePatternType.Month);
records.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
records.setOccurrenceCount(5);
records.setWeekStartDay(DayOfWeek.Monday);
~~~

### **Recorrências Mensais: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade *OccurrenceCount* calculada pela função **getOccurrenceCount()**. Esta função leva a data de início, a data de término e a string RRULE. O seguinte snippet de código mostra como criar uma recorrência no 15º dia de cada mês entre a data de início e a data de término.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);
Date endByDate = getDate(2015, 12, 31);

MapiTask task = new MapiTask("Esta é uma tarefa de teste", "Corpo de Exemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Defina a recorrência mensal
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

### **Recorrências Mensais: Tipo de Recorrência NeverEnd**

O seguinte snippet de código mostra como o tipo de término pode ser definido usando *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(1);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setWeekStartDay(DayOfWeek.Monday);
~~~

## **Trabalhando Com Recorrências Anuais**

Aspose.Email suporta a criação de recorrências anuais usando [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Definindo a propriedade de período para 12, podemos alcançar o padrão de recorrência anual. Três diferentes tipos de término de recorrência de calendário Mapi podem ser usados, incluindo *EndAfterNOccurrences*, *EndAfterDate* e *NeverEnd*. Esta seção demonstra a criação de diferentes padrões de recorrência anual.

### **Recorrências Anuais: Tipo de Recorrência EndAfterNOccurrences**

Neste tipo de recorrência, o número de recorrências deve ser definido juntamente com outras informações da seguinte forma:

1. Defina a data de início, término e vencimento.
1. Crie um [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Defina o estado da tarefa como *NotAssigned*.
1. Crie o objeto de recorrência mensal definindo as propriedades como *PatternType*, *Period*, *WeekStartDay*, *EndType* e *OccurenceCount*.
1. Defina a propriedade **MapiTask.setRecurrence** para este objeto de recorrência mensal para alcançar a recorrência anual.
1. Salve esta mensagem no disco.

O seguinte snippet de código mostra como criar uma tarefa com o tipo de término de recorrência como *EndAfterNOccurrence*.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
Date startDate = getDate(2015, 7, 1);
Date dueDate = getDate(2015, 7, 1);

MapiTask task = new MapiTask("Esta é uma tarefa de teste", "Corpo de Exemplo", startDate, dueDate);
task.setState(MapiTaskState.NotAssigned);

// Defina a recorrência anual
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.EndAfterNOccurrences);
recurrence.setOccurrenceCount(3);

task.setRecurrence(recurrence);
task.save("Yearly.msg", TaskSaveFormat.Msg);
~~~

### **Recorrências Anuais: Tipo de Recorrência EndAfterDate**

A opção "End By" na Tarefa Mapi é alcançada definindo a propriedade *OccurrenceCount* calculada pela função **getOccurrenceCount()**. Esta função leva a data de início, a data de término e a string RRULE. O seguinte snippet de código mostra como criar uma recorrência no 15º dia de julho entre as datas de início e de término.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência anual
MapiCalendarMonthlyRecurrencePattern rec = new MapiCalendarMonthlyRecurrencePattern();
rec.setDay(15);
rec.setPeriod(12);
rec.setPatternType(MapiCalendarRecurrencePatternType.Month);
rec.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
rec.setEndDate(endByDate);
rec.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=YEARLY;BYMONTHDAY=15;BYMONTH=7;INTERVAL=1"));
~~~

### **Recorrências Anuais: Tipo de Recorrência NeverEnd**

O seguinte snippet de código mostra como o tipo de término pode ser definido usando *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Defina a recorrência anual
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Gerar Recorrência a partir da Regra de Recorrência**

A API Aspose.Email fornece a capacidade de gerar o Padrão de Recorrência a partir da Regra de Recorrência (RRULE). Ela analisa as informações da RRULE de acordo com as especificações iCal RFC 5545 e gera o padrão de recorrência usando o método **MapiCalendarRecurrencePatternFactory.fromString**. O seguinte snippet de código mostra como gerar o padrão de recorrência a partir da regra de recorrência.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = getDate(2015, 7, 16);
Date endDate = getDate(2015, 8, 1);
MapiCalendar app1 = new MapiCalendar("local de teste", "resumo de teste", "descrição de teste", startDate, endDate);

app1.setStartDate(startDate);
app1.setEndDate(endDate);

String pattern = "DTSTART;TZID=Europe/London:20150831T080000\r\nDTEND;TZID=Europe/London:20150831T083000\r\nRRULE:FREQ=DAILY;INTERVAL=1;COUNT=7\r\nEXDATE:20150831T070000Z,20150904T070000Z";
app1.getRecurrence().setRecurrencePattern(MapiCalendarRecurrencePatternFactory.fromString(pattern));
~~~

## **Adicionar Anexos a Eventos de Calendário Recorrentes**

A API Aspose.Email fornece a capacidade de adicionar anexos a eventos de calendário recorrentes.

~~~Java
// Para exemplos completos e arquivos de dados, vá para https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Outlook();

Date startDate = addHours(getDate(2018, 7, 19), 12);
MapiCalendar calendar = new MapiCalendar("local1", "resumo1", "descrição1", startDate, addHours(startDate, 1));

MapiCalendarEventRecurrence recurrence = new MapiCalendarEventRecurrence();
MapiCalendarRecurrencePattern pattern = new MapiCalendarDailyRecurrencePattern();
recurrence.setRecurrencePattern(pattern);
pattern.setPatternType(MapiCalendarRecurrencePatternType.Day);
pattern.setPeriod(1);
pattern.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);

Date exceptionDate = addDays(startDate, 3);
MapiCalendarExceptionInfo exception = new MapiCalendarExceptionInfo();
exception.setLocation("local de exceção");
exception.setSubject("assunto de exceção");
exception.setBody("corpo de exceção");
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
    FolderInfo newFolder = newPst.createPredefinedFolder("Calendário", StandardIpmFolder.Appointments);
    newFolder.addMapiMessageItem(calendar);
}
~~~

## **Definir o Fuso Horário do Evento do Calendário**

A API Aspose.Email fornece a capacidade de definir o fuso horário do calendário:
- informações sobre o fuso horário para a data/hora de início/término
- informações sobre o fuso horário para uma reunião recorrente
- informações sobre o fuso horário que descrevem como converter a data e hora da reunião em uma série recorrente para e a partir do UTC

O seguinte snippet de código mostra como definir informações sobre o fuso horário do calendário:

~~~Java
MapiCalendar event = new MapiCalendar("local", "resumo", "descrição", startDate, endDate);
// fuso horário UTC
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