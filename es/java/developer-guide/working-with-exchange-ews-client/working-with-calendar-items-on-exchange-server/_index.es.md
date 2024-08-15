---
title: "Trabajar con elementos del calendario en Exchange Server"
url: /es/java/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---


## **Envío de convocatorias de reunión**
En este artículo se muestra cómo enviar una convocatoria de reunión a varios destinatarios mediante Exchange Web Services y Aspose.Email.

1. Cree una convocatoria de reunión con la clase Appointment y establezca la ubicación, la hora y los asistentes.
1. Crea una instancia de la clase MailMessage y establece la cita con el método MailMessage.addAlternateView ().
1. Conéctese al servidor Exchange y envíe la convocatoria de reunión mediante el método send (MailMessage).

The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) La clase se puede usar para conectarse a un servidor Exchange con soporte para Exchange Web Services (EWS). Para que esto funcione, el servidor debe ser Exchange Server 2007 o posterior. El siguiente fragmento de código muestra cómo usar EWS para enviar las convocatorias de reunión.



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
## **Cómo trabajar con elementos del calendario mediante EWS**
Aspose.Email ofrece la capacidad de agregar, actualizar y cancelar citas mediante el cliente Exchange Web Service (EWS). Los clientes de IEWS [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)), y [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) los métodos permiten manipular los elementos del calendario mediante EWS. Este artículo proporciona un ejemplo de código detallado sobre cómo trabajar con elementos del calendario. En el siguiente ejemplo de código se muestra cómo:

1. Crea una cita.
1. Actualiza una cita.
1. Eliminar o cancelar una cita.



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

### **Devolver los elementos del calendario recurrentes dentro del rango de fechas especificado**

Aspose.Email EWSClient admite la devolución de los elementos periódicos del calendario dentro del rango especificado por StartDate y EndDate. El [AppointmentQueryBuilder.setCalendarView (fecha de inicio, fecha de finalización, int maxEntriesReturned)](https://reference.aspose.com/email/java/com.aspose.email/appointmentquerybuilder/#setCalendarView-java.util.Date-java.util.Date-int-) método, si se especifica CalendarView, devuelve una lista de elementos de calendario individuales y ocurrencias de elementos de calendario recurrentes dentro del rango especificado por StartDate y EndDate. El *maxEntriesReturned* el parámetro describe el número máximo de resultados. (Valor <= 0 para todos los resultados).

```java
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getAppointment().setCalendarView(startDate, endDate, -1);

Appointment[] appointments = client.listAppointments(builder.getQuery());
```
## **Listar citas con soporte de paginación**
El método ListAppointments expuesto por [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) La API recupera la lista completa de citas del servidor Exchange. Esto puede llevar tiempo si hay un gran número de citas en el servidor de Exchange. La API proporciona métodos sobrecargados de [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listAppointments\(\)) método que brinda soporte de paginación a la operación. También se puede usar en diferentes combinaciones con la función de consulta. Los siguientes métodos sobrecargados están disponibles para enumerar las citas de Exchange Server con soporte de paginación.

- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

En el siguiente fragmento de código, se muestra cómo enumerar las citas con soporte de paginación.



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
## **Agregar un evento a la carpeta de calendario secundaria en Exchange Server**
La API Aspose.Email le permite crear una carpeta de calendario secundaria en Exchange Server mediante el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). A continuación, se pueden añadir, actualizar o cancelar citas desde el calendario secundario mediante el [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)) and [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) métodos. Los siguientes métodos y propiedades de la API se utilizan en los ejemplos de código que aparecen a continuación para mostrar la funcionalidad de esta función. Tenga en cuenta que esta función es compatible con Aspose.Email para Java 6.5.0 y versiones posteriores.

- Method `IEWSClient.cancelAppointment(Appointment, String)`.
- Method `IEWSClient.cancelAppointment(String, String)`.
- Method `IEWSClient.createAppointment(Appointment, String)`.
- Method `IEWSClient.createFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Method `IEWSClient.fetchAppointment(String, String)`.
- Method `IEWSClient.updateAppointment(Appointment, String)`.
- Property `IEWSClient.CurrentCalendarFolderUri`.

En el siguiente fragmento de código se muestra cómo agregar un evento a la carpeta de calendario secundaria del servidor de Exchange.



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
## **Invitación de calendario para compartir**
El servidor Microsoft Exchange ofrece la capacidad de compartir calendarios mediante el envío de invitaciones de calendario a otros usuarios registrados en el mismo servidor de Exchange. La API Aspose.Email ofrece la misma capacidad al permitir compartir el calendario mediante la API EWS.



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
## **Recuperación de la información de atributos extendidos de los elementos del calendario**
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
