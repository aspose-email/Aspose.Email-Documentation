---
title: Working with Recurrences
type: docs
weight: 140
url: /net/working-with-recurrences/
---


## **Working with Daily Recurrences**

Aspose.Email supports creation of daily recurrences using MapiCalendarDailyRecurrencePattern. Three different Mapi calendar recurrence end types can be used including EndAfterNOccurrences, EndAfterDate and NeverEnd. This section demonstrates the creation of different daily recurrence patterns.

### **Daily Recurrences: EndAfterNOccurrence Recurrance Type**

In this type of recurrence, number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a MapiTask.
1. Set task state to NotAssigned.
1. Create the daily recurrence object by setting the properties like PatternType, Period, WeekStartDay, EndType and OccurenceCount.
1. Set MapiTask.Recurrence property to this daily recurrence object.
1. Save this message on disc.

The following code snippet shows you how to create task with recurrence end type as EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrences-EndAfterNoccurrences.cs" >}}

Following function can be used to calculate the number of events between the two dates:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetOccurrenceCount-GetOccurrenceCount.cs" >}}

#### **Setting the Occurrences count value**

The following code snippet shows you how to set the occurrences count value.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyOccurrenceCount-SetDailyOccurrenceCount.cs" >}}

### **Daily Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the OccurrenceCount property calculated by the GetOccurrenceCount() function. This function takes start date , end date and RRULE string.

#### **Daily Recurrences: Setting the Every Day value**

The following code snippet shows you how to set the period value to 1 and INTERVAL value to 1 in the RRULE string as well.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetRecurrenceEveryDay-SetRecurrenceEveryDay.cs" >}}

Every Day value can be set to any appropriate value as shown in the following example:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DailyRecurrences-SetEveryDayValueInterval.cs" >}}

### **Daily Recurrences: NeverEnd Recurrance Type**

End type can be set by using MapiCalendarRecurrenceEndType.NeverEnd. Period or INTERVAL can be set to required value say 1 in the following example.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetDailyNeverEndRecurrence-SetDailyNeverEndRecurrence.cs" >}}

## **Working with Weekly Recurrences**

Aspose.Email provides rich features for creation of weekly recurrences using MapiCalendarWeeklyRecurrencePattern. Three different Mapi calendar recurrence end types can be used including EndAfterNOccurrences, EndAfterDate and NeverEnd. This section demonstrates the creation of different weekly recurrence patterns.

### **Weekly Recurrences: EndAfterNOccurrences Recurrance Type**

In this type of recurrence, number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a MapiTask.
1. Set task state to NotAssigned.
1. Create the weekly recurrence object by setting the properties like PatternType, Period, WeekStartDay, EndType and OccurenceCount.
1. Set MapiTask.Recurrence property to this weekly recurrence object.
1. Save this message on disc.

The following code snippet shows you how to create a task with recurrence end type as EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-WeeklyEndAfterNoccurrences.cs" >}}

Following function can be used to calculate the number of events between the two dates:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-WeeklyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Selecting multiple days in a week**

The following code snippet shows you how to select multiple days in a week.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-EndAfterNoccurrenceSelectMultipleDaysInweek-EndAfterNoccurrenceSelectMultipleDaysInweek.cs" >}}

#### **Selecting multiple days in a week and setting intervals**

The following code snippet shows you how to select multiple days in a week and set intervals.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval-SetWeeklyRecurrenceMultipleDaysInWeekWithInterval.cs" >}}

### **Weekly Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the OccurrenceCount property calculated by the GetOccurrenceCount() function. This function takes start date , end date and RRULE string.

#### **Weekly Recurrences: Setting the Every Day value**

The following code snippet shows you how to set the period value to 1 and INTERVAL value to 1 in the RRULE string as well.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateEveryDayRecurrence.cs" >}}

Every Day value can be set to any appropriate value and multiple days can be selected as shown in the following example:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyEndAfterDateRecurrence-SetWeeklyEndAfterDateMultipleDaysRecurrence.cs" >}}

### **Weekly Recurrences: NeverEnd Recurrance Type**

End type can be set by using MapiCalendarRecurrenceEndType.NeverEnd. Period or INTERVAL can be set to required value say 1 in the following example.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetWeeklyNeverEndRecurrence-SetWeeklyNeverEndRecurrence.cs" >}}

## **Working with Monthly Recurrences**

Aspose.Email supports creation of monthly recurrences using MapiCalendarMonthlyRecurrencePattern. Three different Mapi calendar recurrence end types can be used including EndAfterNOccurrences, EndAfterDate and NeverEnd. This section demonstrates the creation of different monthly recurrence patterns.

### **Monthly Recurrences: EndAfterNOccurrences Recurrance Type**

In this type of recurrence, number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a MapiTask.
1. Set task state to NotAssigned.
1. Create the monthly recurrence object by setting the properties like PatternType, Period, WeekStartDay, EndType and OccurenceCount.
1. Set MapiTask.Recurrence property to this monthly recurrence object.
1. Save this message on disc.

The following code snippet shows you how to create a task with recurrence end type as EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-MonthlyEndAfterNoccurrences.cs" >}}

Following function can be used to calculate the number of events between the two dates:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-EventsBetweenTheTwoDates.cs" >}}

#### **Set fix number of occurrences**

The following code snippet shows you how to set fix number of occurrences.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MonthlyEndAfterNoccurrences-SetFixNumberOfOccurrences.cs" >}}

### **Monthly Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the OccurrenceCount property calculated by the GetOccurrenceCount() function. This function takes start date , end date and RRULE string. The following code snippet shows you how to create a recurrence on 15th of each month between start and end by date.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyEndAfterDateRecurrence-SetMonthlyEndAfterDateRecurrence.cs" >}}

### **Monthly Recurrences: NeverEnd Recurrance Type**

The following code snippet shows you how to set the end type using MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetMonthlyNeverEndRecurrence-SetMonthlyNeverEndRecurrence.cs" >}}

## **Working with Yearly Recurrences**

Aspose.Email supports creation of yearly recurrences using MapiCalendarMonthlyRecurrencePattern. By setting the period property to 12, we can achieve the yearly recurrence pattern. Three different Mapi calendar recurrence end types can be used including EndAfterNOccurrences, EndAfterDate and NeverEnd. This section demonstrates the creation of different yearly recurrence patterns.

### **Yearly Recurrences: EndAfterNOccurrences Recurrance Type**

In this type of recurrence, number of recurrences is to be set along with other information as follows:

1. Set start, end and due date.
1. Create a MapiTask.
1. Set task state to NotAssigned.
1. Create the monthly recurrence object by setting the properties like PatternType, Period, WeekStartDay, EndType and OccurenceCount.
1. Set MapiTask.Recurrence property to this monthly recurrence object to achieve the yearly recurrence.
1. Save this message on disc.

The following code snippet shows you how to create a task with recurrence end type as EndAfterNOccurrence.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyRecurrences-EndAfterNOccurrences.cs" >}}

### **Yearly Recurrences: EndAfterDate Recurrance Type**

"End By" option in the Mapi Task is achieved by setting the OccurrenceCount property calculated by the GetOccurrenceCount() function. This function takes start date, end date and RRULE string. The following code snippet shows you how to create a recurrence on 15th of each 7th month between start and end by date.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-YearlyEndAfterDate-YearlyEndAfterDate.cs" >}}

### **Yearly Recurrences: NeverEnd Recurrance Type**

The following code snippet shows you how to set the end type using MapiCalendarRecurrenceEndType.NeverEnd.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-SetYearlyNeverEndRecurrence-SetYearlyNeverEndRecurrence.cs" >}}

## **Generate Recurrence from Recurrence Rule**

Aspose.Email API provides the capability to generate Recurrence Pattern from Recurrence Rule (RRULE). It parses the information from the RRULE as per RFC 5545 iCal specifications and generates the recurrence pattern using the MapiCalendarRecurrencePatternFactory.FromString method. The following code snippet shows you how to generate recurrence pattern from recurrence rule.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GenerateRecurrenceFromRecurrenceRule-GenerateRecurrenceFromRecurrenceRule.cs" >}}

## **Add an Attachment to Recurring Calendar Events**

Aspose.Email API provides the capability to add attachments to recurring calendar events.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-AddAttachmentToMapiExceptionInfo-AddAttachmentToMapiExceptionInfo.cs" >}}
