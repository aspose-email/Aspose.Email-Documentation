---
title: "Работа с календарными элементами на Exchange Server"
url: /ru/java/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---


## **Отправка запросов на встречу**
Эта статья показывает, как отправить запрос на встречу нескольким получателям, используя Exchange Web Services и Aspose.Email.

1. Создайте запрос на встречу, используя класс Appointment, и укажите местоположение, время и участников.
1. Создайте экземпляр класса MailMessage и установите встречу с помощью метода MailMessage.addAlternateView().
1. Подключитесь к Exchange Server и отправьте запрос на встречу, используя метод send(MailMessage).

Класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) может использоваться для подключения к Exchange Server с поддержкой Exchange Web Services (EWS). Для этого сервер должен быть Exchange Server 2007 или новее. В следующем кодовом фрагменте показано, как использовать EWS для отправки запросов на встречу.

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
## **Работа с календарными элементами с использованием EWS**
Aspose.Email предоставляет возможность добавлять, обновлять и отменять встречи с помощью клиента Exchange Web Service (EWS). Методы IEWSClients [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)), и [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) позволяют управлять календарными элементами с использованием EWS. Эта статья предоставляет подробный пример кода для работы с календарными элементами. В следующем кодовом примере показано, как:

1. Создать встречу.
1. Обновить встречу.
1. Удалить/Отменить встречу.

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

### **Возврат повторяющихся календарных элементов в заданном диапазоне дат**

Aspose.Email EWSClient поддерживает возврат повторяющихся календарных элементов в диапазоне, заданном StartDate и EndDate. Метод [AppointmentQueryBuilder.setCalendarView(Date startDate, Date endDate, int maxEntriesReturned)](https://reference.aspose.com/email/java/com.aspose.email/appointmentquerybuilder/#setCalendarView-java.util.Date-java.util.Date-int-) возвращает список одиночных календарных элементов и появлений повторяющихся календарных элементов в диапазоне, заданном StartDate и EndDate, если CalendarView указан. Параметр *maxEntriesReturned* описывает максимальное количество результатов. (Значение <= 0 для всех результатов).

```java
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getAppointment().setCalendarView(startDate, endDate, -1);

Appointment[] appointments = client.listAppointments(builder.getQuery());
```
## **Список встреч с поддержкой пагинации**
Метод ListAppointments, предоставленный API [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient), извлекает полный список встреч с сервера Exchange. Это может занять время, если на сервере Exchange имеется большое количество встреч. API предоставляет перегруженные методы [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listAppointments\(\)) метода, который предоставляет поддержку пагинации для операции. Это может быть использовано в различных комбинациях с функцией агрегации. Следующие перегруженные методы доступны для перечисления встреч с сервера Exchange с поддержкой пагинации.

- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

Следующий кодовый фрагмент показывает, как перечислить встречи с поддержкой пагинации.

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
## **Добавление события во вторичную календарную папку на Exchange Server**
API Aspose.Email позволяет создать вторичную календарную папку на Exchange Server с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Встречи могут быть добавлены, обновлены или отменены из вторичного календаря с использованием методов [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)) и [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)). В следующем кодовом примере показаны методы и свойства API, используемые для демонстрации функциональности этой функции. Обратите внимание, что эта функция поддерживается Aspose.Email для Java начиная с версии 6.5.0.

- Метод `IEWSClient.cancelAppointment(Appointment, String)`.
- Метод `IEWSClient.cancelAppointment(String, String)`.
- Метод `IEWSClient.createAppointment(Appointment, String)`.
- Метод `IEWSClient.createFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Метод `IEWSClient.fetchAppointment(String, String)`.
- Метод `IEWSClient.updateAppointment(Appointment, String)`.
- Свойство `IEWSClient.CurrentCalendarFolderUri`.

Следующий кодовый фрагмент показывает, как добавить событие во вторичную календарную папку на сервере Exchange.

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
## **Обмен приглашением на календарь**
Сервер Microsoft Exchange предоставляет возможность обмениваться календарями, отправляя приглашения на календарь другим пользователям, зарегистрированным на том же сервере Exchange. API Aspose.Email предоставляет такую же возможность, позволяя делиться календарем с использованием API EWS.

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
## **Получение информации о расширенных атрибутах из элементов календаря**
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