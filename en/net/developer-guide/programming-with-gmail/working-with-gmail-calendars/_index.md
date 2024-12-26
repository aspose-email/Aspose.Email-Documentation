---
title: Google Calendar Management in .NET Applications 
ArticleTitle: Manage Google Calendars using Gmail Client   
type: docs
weight: 20
url: /net/manage-google-calendars/
---


## **Add, Edit and Delete Gmail Calendars**

Aspose.Email allows applications to manage the Gmail calendars using [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) which provides features like adding, deleting and updating Gmail calendars. This client class returns a list of ExtendedCalendar type objects which contain information about the Gmail calendar items. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) class exposes the following functions for calendars:

- [CreateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) 
  It can be used to insert new calendar
- [ListCalendars](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/)
  It can be used to get the list of all calendars of a client
- [DeleteCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecalendar/)
  It can be used to delete a calendar
- [FetchCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchcalendar/)
  It can be used to fetch particular calendar of a client
- [UpdateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updatecalendar/)
  This function is used to insert back a modified calendar of a client

To Access the calendars, GoogleTestUser is initialized using gmail account credentials. GoogleOAuthHelper is used to get the access token for the user which is further used to initialize IGmailClient.

## **Insert, Fetch and Update Gmail Calendars**

For inserting a calendar, initialize a Calendar type object and insert it using [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) function. [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) returns the id of the newly inserted calendar. This id can be used to fetch the calendar from the server. The following code snippet shows you how to insert, fetch and update calendar.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-InsertFetchAndUpdateCalendar-InsertFetchAndUpdateCalendar.cs" >}}

## **Delete Specific Google Calendars**

For deleting a particular calendar, we need to get the list of all the calendars of a client and then delete as required. [ListCalendars()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/#listcalendars) returns the list of [ExtendedCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/extendedcalendar/) which contains Gmail calendars. The following code snippet shows you how to delete particular calendar.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteParticularCalendar-DeleteParticularCalendar.cs" >}}

## **Calendar Access Control**

Aspose.Email provides full control over the access to the calendar items. [ListAccessRules()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/) function is exposed by [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) which returns the list of [AccessControlRule](https://reference.aspose.com/email/net/aspose.email.clients.google/accesscontrolrule/). Individual rule information can be retrieved, modified and saved back for the calendar of a client. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) contains the following functions for managing the access control rules.

- [ListAccessRules](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/)
  This function provides the list of AccessControlRule
- [CreateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createaccessrule/)
  This function creates a new access rule for a calendar.
- [UpdateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateaccessrule/)
  This function is used for updating an access rule.
- [FetchAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchaccessrule/)
  It can be used to fetch particular access rule for calendar of a client
- [DeleteAccessRule](https://search.aspose.com/q/deleteaccessrule.html)
  This function is used for deleting an access rule.

The following code snippet shows you how to use functions for managing the access rules:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-ManageAccessRule-ManageAccessRule.cs" >}}

## **Calendar Client Settings and Color Information**

Aspose.Email supports accessing the Client settings by using [IGmailClient.GetSettings()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getsettings/#igmailclientgetsettings-method). It returns the list of settings as given below:

1. dateFieldOrder
1. displayAllTimezones
1. hideInvitations
1. format24HourTime
1. defaultCalendarMode
1. defaultEventLength
1. locale
1. remindOnRespondedEventsOnly
1. alternateCalendar
1. userLocation
1. hideWeekends
1. showDeclinedEvents
1. weekStart
1. weather
1. customCalendarMode
1. timezoneLabel
1. timezone
1. useKeyboardShortcuts
1. country

Similarly color info for clients can also be retrieved using [IGmailClient.GetColors()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getcolors/#igmailclientgetcolors-method). This color info object returns the list of Foreground colors, background colors and update date and time.

### **Access Client Settings**

The following code snippet shows you how the functions can be used for accessing the client settings:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessClientSettings-AccessClientSettings.cs" >}}

### **Access Color Information**

The following code snippet shows you how the functions can be used for accessing the client color settings.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessColorInfo-AccessColorInfo.cs" >}}

## **Manage Google Calendar Appointments**

Aspose.Email provides features for working with Appointments in Google calendars. The following tasks can be performed on appointments in google calendar:

1. Add Appointments.
1. Retrieve list off appointments.
1. Retrieve particular appointment.
1. Update an appointment.
1. Move appointment from one calendar to another.
1. Delete appointment.

[IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) provides functions like [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createappointment/#igmailclientcreateappointment-method), [FetchAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchappointment/#igmailclientfetchappointment-method), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateappointment/#igmailclientupdateappointment-method), [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listappointments/#igmailclientlistappointments-method), [MoveAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/moveappointment/#moveappointment) and [DeleteAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deleteappointment/#igmailclientdeleteappointment-method).

### **Add Appointments to Google Calendar**

The following code sample demonstrates the feature of adding an appointment in a calendar. To achieve this, follow the steps:

1. Create and insert a calendar.
1. Retrieve the list of appointments from a new calendar.
1. Create an appointment.
1. Insert an appointment.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AddingAnAppointment-AddingAnAppointment.cs" >}}

### **Retrieve and Update Google Calendar Appointments**

Here retrieving and updating of calendar is demonstrated as follows:

1. Rerieve particaulr appointment.
1. Modify the appointment.
1. Update the appointment in calendar.

It is assumed that a calendar with id "calendarId" and appointment unique id "AppointmentUniqueId" are already extracted. The following code snippet shows you how to retrieve and update an appointment.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-RetrieveUpdateAppointment-RetrieveUpdateAppointment.cs" >}}

### **Move and Delete Appointments in Google Calendar**

Appointment can be moved by providing the source calendar, destination calendar and the unique id of an appointment in the source calendar. The following code snippet shows you how to move and delete an appointment.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-MoveAndDeleteAppointment-MoveAndDeleteAppointment.cs" >}}

### **FreeBusy Query for Google Calendar**

Aspose.Email provides querying mechanism to check whether an appointment is due or not as per the criteria. FreebusyQuery class is provided for this purpose which allows to prepare a query for a particular calendar.

This code sample demonstrates the feature of querying a calendar. The following tasks are performed in this sample:

1. Create and insert a calendar
1. Create an appointment
1. Insert appointment
1. Prepare a FreeBusyQuery
1. Get the FreebusyResponse

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Use the GoogleUser and GoogleOAuthHelper classes below to receive an access token
using (IGmailClient client = GmailClient.GetInstance(accessToken, user.Email))
{
    // Initialize calendar item
    Aspose.Email.Clients.Google.Calendar calendar1 = new Aspose.Email.Clients.Google.Calendar("summary - " + Guid.NewGuid().ToString(), null, null, "Europe/Kiev");

    // Insert calendar and get back id of newly inserted calendar and Fetch the same calendar using calendar id
    string id = client.CreateCalendar(calendar1);
    Aspose.Email.Clients.Google.Calendar cal1 = client.FetchCalendar(id);
    string calendarId1 = cal1.Id;
    try
    {
        // Get list of appointments in newly inserted calendar. It should be zero
        Appointment[] appointments = client.ListAppointments(calendarId1);
        if (appointments.Length != 0)
        {
            Console.WriteLine("Wrong number of appointments");
            return;
        }

        // Create a new appointment and Calculate appointment start and finish time
        DateTime startDate = DateTime.Now;
        DateTime endDate = startDate.AddHours(1);

        // Create attendees list for appointment
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.Add("user1@domain.com");
        attendees.Add("user2@domain.com");

        // Create appointment
        Appointment app1 = new Appointment("Location - " + Guid.NewGuid().ToString(), startDate, endDate, "user2@domain.com", attendees);
        app1.Summary = "Summary - " + Guid.NewGuid().ToString();
        app1.Description = "Description - " + Guid.NewGuid().ToString();
        app1.StartTimeZone = "Europe/Kiev";
        app1.EndTimeZone = "Europe/Kiev";

        // Insert the newly created appointment and get back the same in case of successful insertion
        Appointment app2 = client.CreateAppointment(calendarId1, app1);

        // Create Freebusy query by setting min/max timeand time zone
        FreebusyQuery query = new FreebusyQuery();
        query.TimeMin = DateTime.Now.AddDays(-1);
        query.TimeMax = DateTime.Now.AddDays(1);
        query.TimeZone = "Europe/Kiev";

        // Set calendar item to search and Get the reponse of query containing 
        query.Items.Add(cal1.Id);
        FreebusyResponse resp = client.GetFreebusyInfo(query);
        // Delete the appointment
        client.DeleteAppointment(calendarId1, app2.UniqueId);
    }
    finally
    {
        // Delete the calendar
        client.DeleteCalendar(cal1.Id);
    }
}
```
