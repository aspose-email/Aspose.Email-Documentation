---
title: Working with Calendar Items on Exchange Server
ArticleTitle: Working with Calendar Items on Exchange Server
type: docs
weight: 50
url: /java/working-with-calendar-items-on-exchange-server/
---


## **Sending Meeting Requests**
This article shows how to send a meeting request to multiple recipients using Exchange Web Services and Aspose.Email.

1. Create a meeting request using the Appointment class and set the location, time and attendees.
1. Create an instance of the MailMessage class and set the appointment using the MailMessage.addAlternateView() method.
1. Connect to the Exchange Server and send the meeting request using the send(MailMessage) method.

The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class can be used to connect to an Exchange Servers with Exchange Web Services (EWS) support. For this to work, the server has to be Exchange Server 2007 or later. The following code snippet shows you how to use EWS to send the meeting requests.



~~~Java
try {
    // Create instance of IEWSClient class by giving credentials
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

    Calendar c = Calendar.getInstance();
    c.add(Calendar.HOUR_OF_DAY, 1);
    Date startTime = c.getTime();
    c.add(Calendar.MINUTE, 90);
    Date endTime = c.getTime();

    // Create the meeting request
    Appointment app = new Appointment("meeting request", startTime, endTime, MailAddress.to_MailAddress("administrator@test.com"),
            MailAddressCollection.to_MailAddressCollection("bob@test.com"));
    app.setSummary("meeting request summary");
    app.setDescription("description");

    c = Calendar.getInstance();
    c.add(Calendar.DATE, 5);
    RecurrencePattern pattern = new DailyRecurrencePattern(c.getTime());
    app.setRecurrence(pattern);

    // Create the message and set the meeting request
    MailMessage msg = new MailMessage();
    msg.setFrom(MailAddress.to_MailAddress("administrator@test.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("bob@test.com"));
    msg.isBodyHtml(true);
    msg.setHtmlBody("<h3>HTML Heading</h3><p>Email Message detail</p>");
    msg.setSubject("meeting request");
    msg.addAlternateView(app.requestApointment(0));

    // send the appointment
    client.send(msg);
    System.out.println("Appointment request sent");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Working with Calendar Items using EWS**
Aspose.Email provides the capability to add, update and cancel appointments using Exchange Web Service (EWS) client. The IEWSClients [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)), and [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) methods allow manipulating calendar items using EWS. This article provides a detailed code sample of working with Calendar items. The following code sample shows how to:

1. Create an appointment.
1. Update an appointment.
1. Delete/Cancel an appointment.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "your.username", "your.Password");
Calendar c = Calendar.getInstance();
c.set(Calendar.MINUTE, 0);
c.set(Calendar.SECOND, 0);
c.set(Calendar.MILLISECOND, 0);
Date startTime = c.getTime();
c.add(Calendar.HOUR_OF_DAY, 1);
Date endTime = c.getTime();
String timeZone = "America/New_York";

Appointment app = new Appointment("Room 112", startTime, endTime, MailAddress.to_MailAddress("organizeraspose-email.test3@domain.com"),
        MailAddressCollection.to_MailAddressCollection("attendee@gmail.com"));
app.setTimeZone(timeZone);
app.setSummary("NETWORKNET-34136" + UUID.randomUUID().toString());
app.setDescription("NETWORKNET-34136 Exchange 2007/EWS: Provide support for Add/Update/Delete calendar items");

String uid = client.createAppointment(app);
Appointment fetchedAppointment1 = client.fetchAppointment(uid);
app.setLocation("Room 115");
app.setSummary("New summary for " + app.getSummary());
app.setDescription("New Description");
client.updateAppointment(app);

Appointment[] appointments1 = client.listAppointments();
System.out.println("Total Appointments: " + appointments1.length);
Appointment fetchedAppointment2 = client.fetchAppointment(uid);
System.out.println("Summary: " + fetchedAppointment2.getSummary());
System.out.println("Location: " + fetchedAppointment2.getLocation());
System.out.println("Description: " + fetchedAppointment2.getDescription());
client.cancelAppointment(app);
Appointment[] appointments2 = client.listAppointments();
System.out.println("Total Appointments: " + appointments2.length);
~~~

### **Return the Recurring Calendar Items Within the Specified Date Range**

Aspose.Email EWSClient supports the return of the recurring calendar items within the range specified by StartDate and EndDate. The [AppointmentQueryBuilder.setCalendarView(Date startDate, Date endDate, int maxEntriesReturned)](https://reference.aspose.com/email/java/com.aspose.email/appointmentquerybuilder/#setCalendarView-java.util.Date-java.util.Date-int-) method, if the CalendarView is specified, returns a list of single calendar items and occurrences of recurring calendar items within the range specified by StartDate and EndDate. The *maxEntriesReturned* parameter describes the maximum number of results. (Value <= 0 for all results).

```java
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getAppointment().setCalendarView(startDate, endDate, -1);

Appointment[] appointments = client.listAppointments(builder.getQuery());
```
## **Listing Appointments with Paging Support**
The ListAppointments method exposed by the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) API retrieves the complete list of appointments from the Exchange server. This may take time if there are a large number of appointments on the Exchange Server. The API provides overloaded methods of [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listAppointments\(\)) method that gives paging support to the operation. This can be used in different combinations with the querying feature as well. The following overloaded methods are available to list appointments from Exchange Server with Paging support.

- AppointmentCollection IEWSClient.listAppointments(int itemsPerPage).
- AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage).
- AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage).
- AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage).
- AppointmentCollection IEWSClient.listAppointments(int itemsPerPage, int itemOffset).
- AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage, int itemOffset).
- AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage, int itemOffset).
- AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage, int itemOffset).

The following code snippet shows you how to list appointments with paging support.



~~~Java
        IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
        try {
            try {
                Appointment[] appts = client.listAppointments();
                System.out.println(appts.length);

                Calendar c = Calendar.getInstance();
                c.set(Calendar.MINUTE, 0);
                c.set(Calendar.SECOND, 0);
                c.set(Calendar.MILLISECOND, 0);

                int appNumber = 10;
                Map<String, Appointment> appointmentsDict = new HashMap<String, Appointment>();
                for (int i = 0; i < appNumber; i++) {
                    c.set(Calendar.HOUR_OF_DAY, i + 1);
                    Date startTime = c.getTime();
                    c.set(Calendar.HOUR_OF_DAY, i + 2);
                    Date endTime = c.getTime();

                    String timeZone = "America/New_York";
                    Appointment appointment = new Appointment("Room 112", startTime, endTime, MailAddress.to_MailAddress("from@domain.com"),
                            MailAddressCollection.to_MailAddressCollection("to@domain.com"));
                    appointment.setTimeZone(timeZone);
                    appointment.setSummary("NETWORKNET-35157_3 - " + UUID.randomUUID().toString());
                    appointment.setDescription("EMAILNET-35157 Move paging parameters to separate class");
                    String uid = client.createAppointment(appointment);
                    appointmentsDict.put(uid, appointment);
                }
                AppointmentCollection totalAppointmentCol = AppointmentCollection.to_AppointmentCollection(client.listAppointments());

                ///// LISTING APPOINTMENTS WITH PAGING SUPPORT ///////
                int itemsPerPage = 2;
                List<AppointmentPageInfo> pages = new ArrayList<AppointmentPageInfo>();
                AppointmentPageInfo pagedAppointmentCol = client.listAppointmentsByPage(itemsPerPage);
                System.out.println(pagedAppointmentCol.getItems().size());
                pages.add(pagedAppointmentCol);
                while (!pagedAppointmentCol.getLastPage()) {
                    pagedAppointmentCol = client.listAppointmentsByPage(itemsPerPage, pagedAppointmentCol.getPageOffset() + 1);
                    pages.add(pagedAppointmentCol);
                }
                int retrievedItems = 0;
                // foreach to while statements conversion
                for (AppointmentPageInfo folderCol : pages) {
                    retrievedItems += folderCol.getItems().size();
                }
            } finally {
            }
        } finally {
            client.dispose();
        }
~~~
## **Adding Event to Secondary Calendar folder on Exchange Server**
Aspose.Email API lets you create a secondary Calendar folder on Exchange Server using the [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Appointments can then be added, updated or canceled from the secondary calendar using the [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)) and [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) methods. The following API methods and properties are used in the code samples below to show the functionality of this feature. Please note that this feature is supported by Aspose.Email for Java 6.5.0 onwards.

- Method IEWSClient.cancelAppointment(Appointment, String).
- Method IEWSClient.cancelAppointment(String, String).
- Method IEWSClient.createAppointment(Appointment, String).
- Method IEWSClient.createFolder(String, String, ExchangeFolderPermissionCollection, String).
- Method IEWSClient.fetchAppointment(String, String).
- Method IEWSClient.updateAppointment(Appointment, String).
- Property IEWSClient.CurrentCalendarFolderUri.

The following code snippet shows you how to add an event to the secondary calendar folder on the exchange server.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "your.username", "your.Password");
try {
    try {
        // Create an appointmenta that will be added to secondary calendar folder

        Calendar c = Calendar.getInstance();
        c.set(Calendar.MINUTE, 0);
        c.set(Calendar.SECOND, 0);
        c.set(Calendar.MILLISECOND, 0);
        Date startTime = c.getTime();
        c.add(Calendar.HOUR_OF_DAY, 1);
        Date endTime = c.getTime();

        String timeZone = "America/New_York";

        Appointment[] listAppointments;
        Appointment appointment = new Appointment("Room 121", startTime, endTime, MailAddress.to_MailAddress("from@domain.com"),
                MailAddressCollection.to_MailAddressCollection("attendee@domain.com"));
        appointment.setTimeZone(timeZone);
        appointment.setSummary("EMAILNET-35198 - " + UUID.randomUUID().toString());
        appointment.setDescription("EMAILNET-35198 Ability to add event to Secondary Calendar of Office 365");

        // Verify that the new folder has been created
        ExchangeFolderInfoCollection calendarSubFolders = client.listSubFolders(client.getMailboxInfo().getCalendarUri());

        String getfolderName;
        String setFolderName = "New Calendar";
        boolean alreadyExits = false;

        // Verify that the new folder has been created already exits or not

        for (int i = 0; i < calendarSubFolders.size(); i++) {
            getfolderName = calendarSubFolders.get_Item(i).getDisplayName();

            if (getfolderName.equals(setFolderName)) {
                alreadyExits = true;
            }
        }

        if (alreadyExits) {
            System.out.println("Folder Already Exists");
        } else {
            // Create new calendar folder
            client.createFolder(client.getMailboxInfo().getCalendarUri(), setFolderName, null, "IPF.Appointment");

            System.out.println(calendarSubFolders.size());

            // Get the created folder URI
            String newCalendarFolderUri = calendarSubFolders.get_Item(0).getUri();

            // appointment api with calendar folder uri
            // Create
            client.createAppointment(appointment, newCalendarFolderUri);
            appointment.setLocation("Room 122");
            // update
            client.updateAppointment(appointment, newCalendarFolderUri);
            // list
            listAppointments = client.listAppointments(newCalendarFolderUri);

            // list default calendar folder
            listAppointments = client.listAppointments(client.getMailboxInfo().getCalendarUri());

            // Cancel
            client.cancelAppointment(appointment, newCalendarFolderUri);
            listAppointments = client.listAppointments(newCalendarFolderUri);

            // appointment api with context current calendar folder uri
            client.setCurrentCalendarFolderUri(newCalendarFolderUri);
            // Create
            client.createAppointment(appointment);
            appointment.setLocation("Room 122");
            // update
            client.updateAppointment(appointment);
            // list
            listAppointments = client.listAppointments();

            // list default calendar folder
            listAppointments = client.listAppointments(client.getMailboxInfo().getCalendarUri());

            // Cancel
            client.cancelAppointment(appointment);
            listAppointments = client.listAppointments();

        }
    } finally {
    }
} finally {
    client.dispose();
}
~~~
## **Sharing Calendar Invitation**
Microsoft Exchange server provides the capability to share calendars by sending calendar invitations to other users, registered on the same Exchange server. Aspose.Email API provides the same capability by allowing to share the calendar using the EWS API.



~~~Java
final IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
try {
    // delegate calendar access permission
    ExchangeDelegateUser delegateUser = new ExchangeDelegateUser("sharingfrom@domain.com", ExchangeDelegateFolderPermissionLevel.NotSpecified);
    delegateUser.getFolderPermissions().setCalendarFolderPermissionLevel(ExchangeDelegateFolderPermissionLevel.Reviewer);
    client.delegateAccess(delegateUser, "sharingfrom@domain.com");

    // Create invitation
    MapiMessage mapiMessage = client.createCalendarSharingInvitationMessage("sharingfrom@domain.com");
    MailConversionOptions options = new MailConversionOptions();
    options.setConvertAsTnef(true);
    MailMessage mail = mapiMessage.toMailMessage(options);
    client.send(mail);
} finally {
    client.dispose();
}
~~~
## **Retrieving Extended Attributes Information from Calendar Items**
~~~Java
IEWSClient client = EWSClient.getEWSClient("https://exchange.office365.com/Exchange.asmx", "username", "password");

java.util.List<String> uriList = java.util.Arrays.asList(client.listItems(client.getMailboxInfo().getCalendarUri()));

// Define the Extended Attribute Property Descriptor for searching purpose
// In this case, we have a K1 Long named property for Calendar item
UUID uuid = UUID.fromString("00020329-0000-0000-C000-000000000046");
PropertyDescriptor propertyDescriptor = new PidNamePropertyDescriptor("K1", PropertyDataType.Integer32, uuid);

java.util.List<PropertyDescriptor> propertyDescriptors = java.util.Arrays.asList(new PropertyDescriptor[] { propertyDescriptor });
IGenericList<MapiCalendar> mapiCalendarList = client.fetchMapiCalendar(uriList, propertyDescriptors);

for (MapiCalendar cal : mapiCalendarList) {
    for (MapiNamedProperty namedProperty : (Iterable<MapiNamedProperty>) cal.getNamedProperties().getValues()) {
        System.out.println(namedProperty.getNameId() + " = " + namedProperty.getInt32());
    }
}
~~~
