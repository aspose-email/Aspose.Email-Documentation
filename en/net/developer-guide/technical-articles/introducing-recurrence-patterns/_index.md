---
title: Introducing Recurrence Patterns
type: docs
weight: 60
url: /net/introducing-recurrence-patterns/
---


You can think of a *recurrence pattern* as a way to describe a particular schedule. It contains just enough information to build a list of occurrences (dates and times) according to a given schedule. A recurrence pattern may contain recurrence rules that describe cycles that combine to form the overall pattern. In general, the more complex a recurrence pattern is, the more recurrence rules it will contain. Recurrence patterns can include *exceptions* (not to be confused with exceptions that represent errors that occur during application execution). Exceptions add or remove occurrence dates to the original pattern. Exceptions can be specified as explicit occurrences or as a pattern themselves. Examples of recurrence patterns with exceptions:

- Every 2nd Friday, except from June through August.
- The 1st of every month, except for January, when it should be on the 2nd.

Recurrence patterns are most often periodic, but they don’t have to be. A recurrence pattern can be completely described just as a set of predefined occurrence dates and times. The iCalendar RFC defines *components*, such as such as VEVENT or VTODO that represent events or tasks. The components can have properties such as start date time, description, location, attendees and recurrence. A recurrence pattern, therefore, normally exists as a property of a recurring task or an event. Recurrence pattern properties defined by iCalendar are:

- DTSTART - the start date and time of the pattern (also represents the first occurrence if not excluded explicitly).
- RRULE - specifies a repeating rule for a recurrence set.
- RDATE - defines a list of date and times to include in a recurrence set.
- EXRULE - specifies a repeating rule for exceptions from a recurrence set.
- EXDATE - defines a list of date and time exceptions from a recurrence set.

Only DTSTART is required and there must be only one DTSTART. All other properties are optional and can be specified more than once Aspose.iCalendar takes a string in iCalendar format and reads the recurrence pattern into a [RecurrencePattern](https://apireference.aspose.com/email/net/aspose.email.calendar.recurrences/recurrencepattern) object. The string can be a complete description of an iCalendar component (for example, a complete VEVENT) or it can be just a fragment that contains only the recurrence pattern. Once the recurrence pattern is loaded into a RecurrencePattern object, you can:

- Examine and modify the pattern programmatically via methods and properties provided by Aspose.iCalendar
- Generate occurrence dates/times in a specified date range.
- Save the pattern in iCalendar format.

The following code snippet shows you RRULE part contains the recurrence rule.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-RecurrencePattern-RecurrencePattern.cs" >}}



Look at the [sample recurrence patterns](#sample-patterns) for illustrations on how to create recurrence patterns.
## **About Aspose.iCalendar Object Model**
The Aspose.iCalendar namespace contains all the classes provided by the Aspose.iCalendar component RecurrencePattern and RecurrenceRule are the central classes of Aspose.iCalendar, and provide concrete implementations of the corresponding RFC 2445 elements.

The RecurrencePattern class represents the whole recurrence pattern. You can create a new recurrence pattern from scratch using the default constructor or load an existing pattern in iCalendar format using the static FromiCalendar method. The RecurrenceRule class represents the RRULE or EXRULE part of a recurrence pattern. RecurrenceRule exposes a number of properties that directly map to their counterparts in the iCalendar standard. For example, ByMonth maps to BYMONTH in iCalendar and so on. By examining or setting values of the RecurrenceRule properties you can analyze or modify a recurrence rule. For more information and code samples, see RecurrencePattern and RecurrenceRule in the API Reference.
## **Sample Patterns**
This section includes the following topics:

- The Last Day of The Month.
- The Last Workday of Every Month.
- The Last Monday of The Year.
- Friday of the First ISO 8601 Week of the Year.
- First Friday of the Year.
### **The Last Day of The Month**
This samples [recurrence pattern](/email/net/introducing-recurrence-patterns/) specifies the last day of the month, every month.

RRULE:FREQ=MONTHLY;BYMONTHDAY=-1

Similarly, if you want an occurrence on a day before the last day of the month, use BYMONTHDAY=-2. If you specify BYMONTHDAY=31 then according to the iCalendar standard, there will be no occurrence generated in the months that have fewer than 31 day.
### **The Last Workday of Every Month**
This samples [recurrence pattern](/email/net/introducing-recurrence-patterns/) specifies the last workday of the month, every month. Workdays are defined as the days on which you work. In Europe, for example, workdays are normally Monday to Friday.

RRULE:FREQ=MONTHLY;BYDAY=MO,TU,WE,TH,FR;BYSETPOS=-1

The above rule specifies all workdays of a month and selects the last of them. The net result is a last workday in a month.
### **The Last Monday of The Year**
This sample [recurrence pattern](/email/net/introducing-recurrence-patterns/) specifies an event that occurs on the last Monday of the year.

RRULE:FREQ=YEARLY;BYDAY=-1MO
### **Friday of the First ISO 8601 Week of the Year**
This sample [recurrence pattern](/email/net/introducing-recurrence-patterns/) specifies the Friday of the first week of the year. In the ISO 8601 specification, the first week of the year, is the first week of the year is one with at least four days. When a year starts on a Saturday, for example, week 1 is the week immediately following, starting Monday, January 3.

FREQ=YEARLY;BYWEEKNO=1;BYDAY=FR
### **First Friday of the Year**
This sample [recurrence pattern](/email/net/introducing-recurrence-patterns/) specifies an event that occurs on the 1st Friday of the year.

FREQ=YEARLY;BYDAY=1FR

In 1999, for example, the 1st Friday of the year is 1999/01/01, while the Friday of the 1st ISO 8601 week is 1999/01/08.
