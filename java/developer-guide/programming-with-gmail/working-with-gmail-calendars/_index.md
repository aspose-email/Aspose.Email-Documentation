---
title: Working with Gmail Calendars
type: docs
weight: 20
url: /java/working-with-gmail-calendars/
---


## **Adding, Editing and Deleting a Calendar**
Aspose.Email allows applications to manage the Gmail calendars using [IGmailClient](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient) which provides feature like adding, deleting and updating Gmail calendars. This client class returns list of ExtendedCalendar type objects which contain information about the Gmail calendar items. [IGmailClient](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient) class exposes following functions for calendars:

- [createCalendar](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\))
  To insert new calendar
- [listCalendars](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\))

Get list of all calendars of a client

- [deleteCalendar](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteCalendar\(java.lang.String\))
  It can be used to delete a calendar
- [fetchCalendar](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchCalendar\(java.lang.String\))
  It can be used to fetch particular calendar of a client
- [updateCalendar](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#updateCalendar\(com.aspose.email.Calendar\))
  This function is used for inserting back a modified calendar of a client

To Access the calendars, GoogleTestUser is initialized using gmail account credentials. GoogleOAuthHelper is used to get the access token for the user which is further used to initialize [IGmailClient](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient).
### **Insert, Fetch and Update**
For inserting a calendar, initialize a [Calendar](https://reference.aspose.com/email/java/com.aspose.email/Calendar) type object and insert it using [createCalendar](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) function. [createCalendar](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) returns the id of the newly inserted calendar. This id can be used to fetch the calendar from the server. The following code snippet shows you how to insert, fetch and update calendar.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Insert, get and update calendar
    Calendar calendar = new Calendar("Summary", "Description", "Location", "America/Los_Angeles");

    // Insert calendar and Retrieve same calendar using id
    String id = client.createCalendar(calendar);
    Calendar cal = client.fetchCalendar(id);

    // Change information in the fetched calendar and Update calendar
    cal.setDescription("New Description");
    cal.setLocation("New Location");
    client.updateCalendar(cal);
}
~~~
### **Delete Particular Calendar**
For deleting a particular calendar, we need to get the list of all the calendars of a client and then delete as required. [listCalendars](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\)) returns the list of [ExtendedCalendar](https://reference.aspose.com/email/java/com.aspose.email/ExtendedCalendar) which contains Gmail calendars. The following code snippet shows you how to delete particular calendar.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Access and delete calendar with summary starting from "Calendar summary"
    String summary = "Calendar summary";

    // Get calendars list
    ExtendedCalendar[] lst = client.listCalendars();

    for (ExtendedCalendar extCal : lst) {
        // Delete selected calendars
        if (extCal.getSummary().startsWith(summary))
            client.deleteCalendar(extCal.getId());
    }
}
~~~
## **Working with Calendar Access Control**
Aspose.Email provides full control over the access control to the calendar items. [listAccessRules](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\)) function is exposed by [IGmailClient](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient) which returns list of [AccessControlRule](https://reference.aspose.com/email/java/com.aspose.email/AccessControlRule). Individual rule information can be retrieved, modified and saved back for the calendar of a client. [IGmailClient](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient) contains following functions for managing the access control rules.

- [listAccessRules](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\))
  This function provides list of [AccessControlRule](https://reference.aspose.com/email/java/com.aspose.email/AccessControlRule)
- [createAccessRule](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#createAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  This function creates a new access rule for a calendar.
- [updateAccessRule](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  This function is used for updating an access rule.
- [fetchAccessRule](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAccessRule\(java.lang.String,%20java.lang.String\))
  It can be used to fetch particular access rule for calendar of a client
- [deleteAccessRule](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAccessRule\(java.lang.String,%20java.lang.String\))
  This function is used for deleting an access rule.

The following code snippet shows you how the functions used for managing the access rules:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Retrieve list of calendars for the current client
    ExtendedCalendar[] calendarList = client.listCalendars();

    // Get first calendar id and retrieve list of AccessControlRule for the first calendar
    String calendarId = calendarList[0].getId();
    AccessControlRule[] roles1 = client.listAccessRules(calendarId);

    // Create a local access control rule and Set rule properties
    AccessControlRule rule = new AccessControlRule();
    rule.setRole(AccessRole.reader);
    rule.setScope(new AclScope(AclScopeType.user, email2));

    // Insert new rule for the calendar. It returns the newly created rule
    AccessControlRule createdRule = client.createAccessRule(calendarId, rule);

    // Get list of rules
    AccessControlRule[] roles2 = client.listAccessRules(calendarId);

    // Current list length should be 1 more than the earlier one
    if (roles1.length + 1 == roles2.length) {
        System.out.println("List lengths are ok");
    } else {
        System.out.println("List lengths are not ok");
        return;
    }

    // Change rule and Update the rule for the selected calendar
    createdRule.setRole(AccessRole.writer);
    AccessControlRule updatedRule = client.updateAccessRule(calendarId, createdRule);

    // Retrieve individaul rule against a calendar
    AccessControlRule fetchedRule = client.fetchAccessRule(calendarId, createdRule.getId());

    // Delete particular rule against a given calendar and Retrieve the all rules list for the same calendar
    client.deleteAccessRule(calendarId, createdRule.getId());
    AccessControlRule[] roles3 = client.listAccessRules(calendarId);

    // Check that current rules list length should be equal to the original list length before adding and deleting the rule
    if (roles1.length == roles3.length) {
        System.out.println("List lengths are same");
    } else {
        System.out.println("List lengths are not equal");
        return;
    }
}
~~~
## **Working with Client Settings and Color Info**
Aspose.Email supports accessing the Client settings by using [IGmailClient.getSettings](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#getSettings\(\)). It returns list of settings as given below:

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

Similarly color info for clients can also be retrieved using [IGmailClient.getColors](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#getColors\(\)). This color info object returns the list of Foreground colors, background colors and update date and time.
### **Access Client Settings**
The following code snippet shows you how the functions used for accessing the client settings:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Retrieve client settings
    Dictionary<String, String> settings = client.getSettings();
    if (settings.size() < 1) {
        System.out.println("No settings are available.");
        return;
    }

    // Traverse the settings list
    for (KeyValuePair<String, String> pair : settings) {
        // Get the setting value and test if settings are ok
        String value = client.getSetting(pair.getKey());
        if (pair.getValue().equals(value)) {
            System.out.println("Key = " + pair.getKey() + ", Value = " + pair.getValue());
        } else {
            System.out.println("Settings could not be retrieved");
        }
    }
}
~~~
### **Access Color Info**
The following code snippet shows you how the functions used for accessing the client color settings.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    ColorsInfo colors = client.getColors();
    Dictionary<String, Colors> palettes = colors.getCalendar();

    // Traverse the settings list
    for (KeyValuePair<String, Colors> pair : palettes) {
        System.out.println("Key = " + pair.getKey() + ", Color = " + pair.getValue());
    }
    System.out.println("Update Date = " + colors.getUpdated());
}
~~~
## **Working with Appointments**
Aspose.Email provides features for working with [Appointments](https://reference.aspose.com/email/java/com.aspose.email/Appointment) in Google calendars. Following is the list of tasks that can be performed on appointments in google calendar:

1. Add Appointments - [createAppointment](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#createAppointment\(java.lang.String,%20com.aspose.email.Appointment\)), [importAppointment](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#importAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Retrieve list off appointments - [listAppointments](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointments\(java.lang.String\))
1. Retrieve particular appointment - [fetchAppointment](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAppointment\(java.lang.String,%20java.lang.String\)), [listAppointmentInstances](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointmentInstances\(java.lang.String,%20java.lang.String\))
1. Update an appointment - [updateAppointment](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Move appointment from one calendar to another - [moveAppointment](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#moveAppointment\(java.lang.String,%20java.lang.String,%20java.lang.String\))
1. Delete appointment - [deleteAppointment](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAppointment\(java.lang.String,%20java.lang.String\))

### **Adding an Appointment**
Following code sample demonstrates the feature of adding an appointment in a calendar. In this sample following steps are followed:

1. Create and insert a calendar.
1. Retrieve list of appointments from a new calendar.
1. Create an appointment.
1. Insert appointment.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Create local calendar
    Calendar calendar1 = new Calendar("Summary", null, null, "Europe/Kiev");

    // Insert calendar and get id of inserted calendar and Get back calendar using an id
    String id = client.createCalendar(calendar1);
    Calendar cal1 = client.fetchCalendar(id);
    String calendarId1 = cal1.getId();

    try {
        // Retrieve list of appointments from the first calendar
        Appointment[] appointments = client.listAppointments(calendarId1);
        if (appointments.length > 0) {
            System.out.println("Wrong number of appointments");
            return;
        }

        // Get current time and Calculate time after an hour from now
        java.util.Calendar c = java.util.Calendar.getInstance();
        Date startDate = c.getTime();
        c.add(java.util.Calendar.HOUR_OF_DAY, 1);
        Date endDate = c.getTime();

        // Initialize a mail address collection and set attendees mail address
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.add("User1.EMail@domain.com");
        attendees.add("User3.EMail@domain.com");

        // Create an appointment with above attendees
        Appointment app1 = new Appointment("Location", startDate, endDate, MailAddress.to_MailAddress(email2), attendees);

        // Set appointment summary, description, start/end time zone
        app1.setSummary("New Summary");
        app1.setDescription("New Description");
        app1.setStartTimeZone("Europe/Kiev");
        app1.setEndTimeZone("Europe/Kiev");

        // Insert appointment in the first calendar inserted above and get back inserted appointment
        Appointment app2 = client.createAppointment(calendarId1, app1);

        // Retrieve appointment using unique id
        Appointment app3 = client.fetchAppointment(calendarId1, app2.getUniqueId());
    } catch (Exception ex) {
        System.err.println(ex);
    }
    
}
~~~
### **Retrieve and Update Appointment**
Here retrieving and updating of calendar is demonstrated as follows:

1. Rerieve particaulr appointment.
1. Modify the appointment.
1. Update the appointment in calendar.

It is assumed that a calendar with id "calendarId" and appointment unique id "AppointmentUniqueId" are already extracted. The following code snippet shows you how to retrieve and update appointment.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String calendarId = client.listCalendars()[0].getId();
    String AppointmentUniqueId = client.listAppointments(calendarId)[0].getUniqueId();

    // Retrieve Appointment
    Appointment app3 = client.fetchAppointment(calendarId, AppointmentUniqueId);
    // Change the appointment information
    app3.setSummary("New Summary");
    app3.setDescription("New Description");
    app3.setLocation("New Location");
    app3.setFlags(AppointmentFlags.AllDayEvent);
    java.util.Calendar c = java.util.Calendar.getInstance();
    c.add(java.util.Calendar.HOUR_OF_DAY, 2);
    app3.setStartDate(c.getTime());
    c.add(java.util.Calendar.HOUR_OF_DAY, 1);
    app3.setEndDate(c.getTime());
    app3.setStartTimeZone("Europe/Kiev");
    app3.setEndTimeZone("Europe/Kiev");
    // Update the appointment and get back updated appointment
    Appointment app4 = client.updateAppointment(calendarId, app3);
}
~~~
### **Move and Delete Appointment**
[Appointment](https://reference.aspose.com/email/java/com.aspose.email/Appointment) can be moved by providing the source calendar, destination calendar and unique id of appointment in the source calendar. The following code snippet shows you how to move and delete appointment.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String SourceCalendarId = client.listCalendars()[0].getId();
    String DestinationCalendarId = client.listCalendars()[1].getId();
    String TargetAppUniqueId = client.listAppointments(SourceCalendarId)[0].getUniqueId();

    // Retrieve the list of appointments in the destination calendar before moving the appointment
    Appointment[] appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Before moving count = " + appointments.length);
    Appointment Movedapp = client.moveAppointment(SourceCalendarId, DestinationCalendarId, TargetAppUniqueId);

    // Retrieve the list of appointments in the destination calendar after moving the appointment
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("After moving count = " + appointments.length);

    // Delete particular appointment from a calendar using unique id
    client.deleteAppointment(DestinationCalendarId, Movedapp.getUniqueId());

    // Retrieve the list of appointments. It should be one less than the earlier appointments in the destination calendar
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("After deleting count = " + appointments.length);
}
~~~
