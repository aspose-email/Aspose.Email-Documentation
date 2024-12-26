---
title: Working with Recurrences
ArticleTitle: Working with Recurrences
type: docs
weight: 140
url: /java/working-with-recurrences/
---


## **Working With Daily Recurrences**

Aspose.Email supports the creation of daily recurrences using [MapiCalendarDailyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendardailyrecurrencepattern/). Three different Mapi calendar recurrence end types can be used including *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. This section demonstrates the creation of different daily recurrence patterns.

### **Daily Recurrences: EndAfterNOccurrence Recurrance Type**

In this type of recurrence, number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Set task state to *NotAssigned*.
1. Create the daily recurrence object by setting the properties like *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** property to this daily recurrence object.
1. Save this message on disc.

The following code snippet shows you how to create a task with recurrence end type as *EndAfterNOccurrence*.

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

The following function can be used to calculate the number of events between the two dates:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Setting the Occurrences Count Value**

The following code snippet shows you how to set the occurrences count value.

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

### **Daily Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the *OccurrenceCount* property calculated by the **getOccurrenceCount()** function. This function takes start date , end date and RRULE string.

#### **Daily Recurrences: Setting the Every Day Value**

The following code snippet shows you how to set the period value to 1 and INTERVAL value to 1 in the RRULE string as well.

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

Every Day value can be set to any appropriate value as shown in the following example:

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(2);
record.setEndType(MapiCalendarRecurrenceEndType.EndAfterDate);
record.setOccurrenceCount(getOccurrenceCount(startDate, endByDate, "FREQ=DAILY;INTERVAL=2"));
~~~

### **Daily Recurrences: NeverEnd Recurrance Type**

End type can be set by using *MapiCalendarRecurrenceEndType.NeverEnd*. Period or INTERVAL can be set to required value say 1 in the following example.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Daily recurrence
MapiCalendarDailyRecurrencePattern record = new MapiCalendarDailyRecurrencePattern();

record.setPatternType(MapiCalendarRecurrencePatternType.Day);
record.setPeriod(1);
record.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Working With Weekly Recurrences**

Aspose.Email provides rich features for creation of weekly recurrences using [MapiCalendarWeeklyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarweeklyrecurrencepattern/). Three different Mapi calendar recurrence end types can be used including *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. This section demonstrates the creation of different weekly recurrence patterns.

### **Weekly Recurrences: EndAfterNOccurrences Recurrance Type**

In this type of recurrence, number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Set task state to *NotAssigned*.
1. Create the weekly recurrence object by setting the properties like *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** property to this weekly recurrence object.
1. Save this message on disc.

The following code snippet shows you how to create a task with recurrence end type as *EndAfterNOccurrence*.

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

Following function can be used to calculate the number of events between the two dates:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Selecting Multiple Days in a Week**

The following code snippet shows you how to select multiple days in a week.

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

#### **Selecting Multiple Days in a Week and Setting Intervals**

The following code snippet shows you how to select multiple days in a week and set intervals.

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

### **Weekly Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the *OccurrenceCount* property calculated by the **getOccurrenceCount()** function. This function takes start date, end date and RRULE string.

#### **Weekly Recurrences: Setting the Every Day Value**

The following code snippet shows you how to set the period value to 1 and INTERVAL value to 1 in the RRULE string as well.

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

Every Day value can be set to any appropriate value and multiple days can be selected as shown in the following example:

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

### **Weekly Recurrences: NeverEnd Recurrance Type**

End type can be set by using *MapiCalendarRecurrenceEndType.NeverEnd*. Period or INTERVAL can be set to required value say 1 in the following example.



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

## **Working With Monthly Recurrences**

Aspose.Email supports the creation of monthly recurrences using [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). Three different Mapi calendar recurrence end types can be used including *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. This section demonstrates the creation of different monthly recurrence patterns.

### **Monthly Recurrences: EndAfterNOccurrences Recurrance Type**

In this type of recurrence, the number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Set task state to *NotAssigned*.
1. Create the monthly recurrence object by setting the properties like *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** property to this monthly recurrence object.
1. Save this message on disc.

The following code snippet shows you how to create a task with recurrence end type as *EndAfterNOccurrence*.

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

The following function can be used to calculate the number of events between two dates:

~~~Java
private static long getOccurrenceCount(Date start, Date endBy, String rrule)
{
    DateFormat formatter = new SimpleDateFormat("yyyyMMdd");
    CalendarRecurrence pattern = new CalendarRecurrence("DTSTART:" + formatter.format(start) + "\r\nRRULE:" + rrule);
    DateCollection dates = pattern.generateOccurrences(start, endBy);
    return dates.size();
}
~~~

#### **Set Fix Number of Occurrences**

The following code snippet shows you how to set a fix number of occurrences.

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

### **Monthly Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the *OccurrenceCount* property calculated by the **getOccurrenceCount()** function. This function takes start date, end date and RRULE string. The following code snippet shows you how to create a recurrence on the 15th of each month between start and end by date.

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

### **Monthly Recurrences: NeverEnd Recurrance Type**

The following code snippet shows you how the end type can be set by using *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(1);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
recurrence.setWeekStartDay(DayOfWeek.Monday);
~~~

## **Working With Yearly Recurrences**

Aspose.Email supports creation of yearly recurrences using [MapiCalendarMonthlyRecurrencePattern](https://reference.aspose.com/email/java/com.aspose.email/mapicalendarmonthlyrecurrencepattern/). By setting the period property to 12, we can achieve the yearly recurrence pattern. Three different Mapi calendar recurrence end types can be used including *EndAfterNOccurrences*, *EndAfterDate* and *NeverEnd*. This section demonstrates the creation of different yearly recurrence patterns.

### **Yearly Recurrences: EndAfterNOccurrences Recurrance Type**

In this type of recurrence, the number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Set task state to *NotAssigned*.
1. Create the monthly recurrence object by setting the properties like *PatternType*, *Period*, *WeekStartDay*, *EndType* and *OccurenceCount*.
1. Set **MapiTask.setRecurrence** property to this monthly recurrence object to achieve the yearly recurrence.
1. Save this message on disc.

The following code snippet shows you how to create a task with recurrence end type as *EndAfterNOccurrence*.

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

### **Yearly Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the *OccurrenceCount* property calculated by the **getOccurrenceCount()** function. This function takes start date, end date and RRULE string. The following code snippet shows you how to create a recurrence on the 15th of each 7th month between start and end by date.

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

### **Yearly Recurrences: NeverEnd Recurrance Type**

The following code snippet shows you how the end type can be set by using *MapiCalendarRecurrenceEndType.NeverEnd*.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set the Yearly recurrence
MapiCalendarMonthlyRecurrencePattern recurrence = new MapiCalendarMonthlyRecurrencePattern();
recurrence.setDay(15);
recurrence.setPeriod(12);
recurrence.setPatternType(MapiCalendarRecurrencePatternType.Month);
recurrence.setEndType(MapiCalendarRecurrenceEndType.NeverEnd);
~~~

## **Generate Recurrence from Recurrence Rule**

Aspose.Email API provides the capability to generate Recurrence Pattern from Recurrence Rule (RRULE). It parses the information from the RRULE as per RFC 5545 iCal specifications and generates the recurrence pattern using the **MapiCalendarRecurrencePatternFactory.fromString** method. The following code snippet shows you how to generate recurrence pattern from the recurrence rule.

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

## **Add Attachment to Recurring Calendar Events**

Aspose.Email API provides the capability to add attachments to recurring calendar events.

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

## **Set Calendar Event Time Zone**

Aspose.Email API provides the capability to set calendar time zone:
- time zone information for start/end date
- time zone information for a recurring meeting
- time zone information that describes how to convert the meeting date and time on a recurring series to and from UTC

The following code snippet shows you how to set calendar time zone information:

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
