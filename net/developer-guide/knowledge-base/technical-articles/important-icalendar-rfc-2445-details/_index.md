---
title: Important iCalendar RFC 2445 Details
type: docs
weight: 70
url: /net/important-icalendar-rfc-2445-details/
---


## **About Aspose.iCalendar Object Model**
The [Aspose.iCalendar](https://reference.aspose.com/email/net/aspose.email.calendar) namespace contains all the classes provided by the Aspose.iCalendar component RecurrencePattern and RecurrenceRule are the central classes of Aspose.iCalendar, and provide concrete implementations of the corresponding RFC 2445 elements. 

The RecurrencePattern class represents the whole recurrence pattern. You can create a new recurrence pattern from scratch using the default constructor or load an existing pattern in iCalendar format using the static FromiCalendar method. The RecurrenceRule class represents the RRULE or EXRULE part of a recurrence pattern. RecurrenceRule exposes a number of properties that directly map to their counterparts in the iCalendar standard. For example, ByMonth maps to BYMONTH in iCalendar and so on. By examining or setting values of the RecurrenceRule properties you can analyze or modify a recurrence rule. For more information and code samples, see RecurrencePattern and RecurrenceRule in the API Reference. 
## **Important iCalendar RFC 2445 Details**
This section includes the following topics: 

- Date and Time Formats.
- DATE.
- DATE-TIME with Local Time.
- DATE-TIME with UTC Time.
- DATE-TIME with Local Time and Time Zone.
- BYWEEKNO Provides ISO 8601 Compliance
### **Date and Time Formats**
Dates, or dates with associated times, can be used in the DTSTART, UNTIL, EXDATE and RDATE elements when specifying a recurrence pattern. iCalendar defines the DATE value type to identify values that contains a calendar date and also defines the DATE-TIME type to identify values that specify a precise calendar date and time of day. DATE-TIME values can be specified in three forms, with:

- Local time.
- UTC time.
- Local time and time zone.
### **DATE**
According to the iCalendar standard, DATE values must follow the yyyyMMdd format. The following example represents July 14, 1997: 19970714 
### **DATE-TIME with Local Time**
The date with local time form is simply a date-time value that does not contain the UTC designator, and doesn't reference a time zone. For example, the following represents Janurary 18, 1998, at 11 PM: DTSTART:19980118T230000. Date-time values of this type are said to be "floating" and are not bound to any time zone in particular. They are used to represent the same hour, minute, and second value regardless of which time zone is currently being observed. 
### **DATE-TIME with UTC Time**
The date with UTC time, or absolute time, is identified by a Latin CAPITAL LETTER Z suffix character, the UTC designator, appended to the time value. For example, the following represents January 19, 1998, at 0700 UTC: DTSTART:19980119T070000Z Please note that Aspose.iCalendar ignores the UTC format Z suffix and treats the time as local time. The RFC2445 standard states that a time portion specified in the UNTIL rule of a recurrence pattern must be in UTC format. This is a very strange statement, and in fact, there are examples in the standard that are calculated incorrectly. Aspose.iCalendar accepts time in any format in the UNTIL rule. 
### **DATE-TIME with Local Time and Time Zone**
To reference the time zone, DATE-TIME is modified with the TZID properyt. For example, the following represents 2 AM in New York on January 19, 1998: DTSTART;TZID=US-Eastern:19980119T020000. Please note that Aspose.iCalendar at the moment ignores the TZID parameter and treats the time as a local time. 
### **BYWEEKNO Provides ISO 8601 Compliance**
Use BYWEEKNO only when conformance with [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) is required. Week numbers as defined by ISO 8601 are very different from week numbers in the normal sense. According to ISO 8601, week number one of the calendar year is the first week of a calendar year that contains at least four days. This rule makes the algorithm specific to applications requiring conformance to ISO 8601 and make it almost inapplicable to other uses. ISO 8601 is supported by some European banking and financial applications. It is also used in television for booking commercials. The BYWEEKNO rule specifies a comma-delimited list of numbers identifying weeks of the year. Valid values are 1 to 53 and 1 to 53. This corresponds to weeks according to week numbering as defined in ISO 8601. BYWEEKNO is only valid for YEARLY rules.
