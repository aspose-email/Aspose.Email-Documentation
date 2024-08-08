---
title: iCalendar RFC 2445
type: docs
weight: 30
url: /java/icalendar-rfc-2445/
---


{{% alert color="primary" %}} 

The iCalendar RFC 2445 describes a set of interoperable calendaring and scheduling elements that allow group scheduling, personal information management and calendaring applications to exchange information in a common format.

Aspose.Email implements the schedule-related elements of the RFC since these have very wide application. Future versions may implement other RFC 2445 elements, depending on demand.

This articles describes the elements of the RFC that relate to Aspose.Email. We recommend that you consult with the iCalendar standard <http://www.faqs.org/rfcs/rfc2445.html> for the complete picture. 

{{% /alert %}} 
## **Recurrence Patterns in the Real World**
A recurrence pattern describes the rules when the event occurs. A recurrence pattern engine such as Aspose iCalendar is needed to calculate the dates and times of the occurrences for a given recurrence pattern.
We encounter schedules or recurrence patterns in many situations, for example:

- Ten team meetings, every Monday at 10am.
- Process salary payment on the last work day every month.
- Check patient's temperature every day for two weeks.
- Go to the gym on Monday, Wednesday and Friday.
- Run backup every 4 hours on work days.
- Generate sales report on …
- Update website statistics every …
  Almost any event that occurs periodically can be represented as a recurrence pattern. For example, the following code will return an array containing ten occurrences of the previous team meeting example: 

~~~java
CalendarRecurrence recurrencePattern = new CalendarRecurrence("DTSTART:20040301T100000\nRRULE:FREQ=WEEKLY;COUNT=10;BYDAY=MO");
DateCollection expectedDates = recurrencePattern.generateOccurrences();
System.out.println("expectedDates.Count = " + expectedDates.size());
for (int i = 0; i < expectedDates.size(); i++) {
    System.out.println("DateTime = " + sdf.format(expectedDates.getItem(i)));
}
~~~

{{% alert color="primary" %}} 

Recurrence patterns can get quite complex and require a reliable recurrence pattern engine to parse and validate the input and to generate occurrences correctly. 

{{% /alert %}}
