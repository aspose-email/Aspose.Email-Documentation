---
title: "Работа с элементами календаря на сервере Exchange"
url: /ru/java/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---


## **Отправка приглашений на собрание**
В этой статье показано, как отправить приглашение на собрание нескольким получателям с помощью веб-служб Exchange и Aspose.Email.

1. Создайте приглашение на собрание с помощью класса «Встреча» и задайте место, время и участников.
1. Создайте экземпляр класса MailMessage и назначьте встречу с помощью метода MailMessage.addAlternateView ().
1. Подключитесь к серверу Exchange и отправьте приглашение на собрание с помощью метода send (MailMessage).

The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс можно использовать для подключения к серверам Exchange с поддержкой веб-служб Exchange (EWS). Чтобы это работало, необходимо использовать сервер Exchange Server 2007 или более поздней версии. В следующем фрагменте кода показано, как использовать EWS для отправки приглашений на собрания.



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
## **Работа с элементами календаря с помощью EWS**
Aspose.Email предоставляет возможность добавлять, обновлять и отменять встречи с помощью клиента Exchange Web Service (EWS). Клиенты IEWS [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)), и [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) методы позволяют манипулировать элементами календаря с помощью EWS. В этой статье представлен подробный пример кода работы с элементами календаря. В следующем примере кода показано, как:

1. Назначьте встречу.
1. Обновите встречу.
1. Удалить/отменить встречу.



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

### **Возвращайте повторяющиеся элементы календаря в указанный диапазон дат**

Aspose.Email Ewsclient поддерживает возврат повторяющихся элементов календаря в диапазоне, указанном в параметрах StartDate и EndDate. [AppointmentQueryBuilder.setCalendarView (дата начала, дата, дата окончания, максимальное количество возвращенных записей)](https://reference.aspose.com/email/java/com.aspose.email/appointmentquerybuilder/#setCalendarView-java.util.Date-java.util.Date-int-) метод, если указан CalendarView, возвращает список отдельных элементов календаря и повторяющихся календарных элементов в диапазоне, указанном в параметрах StartDate и EndDate. *maxEntriesReturned* параметр описывает максимальное количество результатов. (Значение <= 0 для всех результатов).

```java
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getAppointment().setCalendarView(startDate, endDate, -1);

Appointment[] appointments = client.listAppointments(builder.getQuery());
```
## **Составление списков встреч с помощью пейджинговой поддержки**
Метод listAppointments, представленный [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) API получает полный список встреч с сервера Exchange. Если на сервере Exchange много встреч, это может занять некоторое время. API предоставляет перегруженные методы [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listAppointments\(\)) метод, обеспечивающий пейджинговую поддержку операции. Его также можно использовать в различных комбинациях с функцией запросов. Доступны следующие перегруженные методы для списка встреч с Exchange Server с поддержкой пейджинга.

- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

В следующем фрагменте кода показано, как составить список встреч с поддержкой пейджинга.



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
## **Добавление события в папку дополнительного календаря на сервере Exchange**
API Aspose.Email позволяет создать дополнительную папку календаря на сервере Exchange с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Затем встречи можно добавлять, обновлять или отменять из дополнительного календаря, используя [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)) and [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) методы. Следующие методы и свойства API используются в приведенных ниже примерах кода для демонстрации функциональности этой функции. Обратите внимание, что эта функция поддерживается Aspose.Email для Java 6.5.0 и выше.

- Method `IEWSClient.cancelAppointment(Appointment, String)`.
- Method `IEWSClient.cancelAppointment(String, String)`.
- Method `IEWSClient.createAppointment(Appointment, String)`.
- Method `IEWSClient.createFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Method `IEWSClient.fetchAppointment(String, String)`.
- Method `IEWSClient.updateAppointment(Appointment, String)`.
- Property `IEWSClient.CurrentCalendarFolderUri`.

В следующем фрагменте кода показано, как добавить событие во дополнительную папку календаря на сервере Exchange.



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
## **Приглашение поделиться календарем**
Сервер Microsoft Exchange предоставляет возможность совместного использования календарей, отправляя приглашения в календарь другим пользователям, зарегистрированным на том же сервере Exchange. API Aspose.Email предоставляет ту же возможность, позволяя делиться календарем с помощью API EWS.



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
## **Получение информации о дополнительных атрибутах из элементов календаря**
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
