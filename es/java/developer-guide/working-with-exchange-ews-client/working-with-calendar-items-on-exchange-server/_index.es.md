---
title: "Trabajando con Elementos del Calendario en Exchange Server"
url: /es/java/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---

## **Enviando Solicitudes de Reunión**
Este artículo muestra cómo enviar una solicitud de reunión a múltiples destinatarios utilizando Exchange Web Services y Aspose.Email.

1. Cree una solicitud de reunión usando la clase Appointment y establezca la ubicación, hora y asistentes.
1. Cree una instancia de la clase MailMessage y establezca la cita utilizando el método MailMessage.addAlternateView().
1. Conéctese al Exchange Server y envíe la solicitud de reunión utilizando el método send(MailMessage).

La clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) se puede usar para conectarse a servidores Exchange con soporte de Exchange Web Services (EWS). Para que esto funcione, el servidor debe ser Exchange Server 2007 o posterior. El siguiente fragmento de código muestra cómo usar EWS para enviar las solicitudes de reunión.

~~~Java
try {
    // Crear instancia de la clase IEWSClient proporcionando credenciales
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

    Calendar c = Calendar.getInstance();
    c.add(Calendar.HOUR_OF_DAY, 1);
    Date startTime = c.getTime();
    c.add(Calendar.MINUTE, 90);
    Date endTime = c.getTime();

    // Crear la solicitud de reunión
    Appointment app = new Appointment("meeting request", startTime, endTime, MailAddress.to_MailAddress("administrator@test.com"),
            MailAddressCollection.to_MailAddressCollection("bob@test.com"));
    app.setSummary("meeting request summary");
    app.setDescription("description");

    c = Calendar.getInstance();
    c.add(Calendar.DATE, 5);
    RecurrencePattern pattern = new DailyRecurrencePattern(c.getTime());
    app.setRecurrence(pattern);

    // Crear el mensaje y establecer la solicitud de reunión
    MailMessage msg = new MailMessage();
    msg.setFrom(MailAddress.to_MailAddress("administrator@test.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("bob@test.com"));
    msg.isBodyHtml(true);
    msg.setHtmlBody("<h3>HTML Heading</h3><p>Email Message detail</p>");
    msg.setSubject("meeting request");
    msg.addAlternateView(app.requestApointment(0));

    // enviar la cita
    client.send(msg);
    System.out.println("Appointment request sent");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Trabajando con Elementos del Calendario usando EWS**
Aspose.Email proporciona la capacidad de agregar, actualizar y cancelar citas utilizando el cliente de Exchange Web Service (EWS). Los métodos [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)), y [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)) permiten manipular elementos del calendario usando EWS. Este artículo proporciona un ejemplo de código detallado sobre cómo trabajar con elementos del calendario. El siguiente ejemplo de código muestra cómo:

1. Crear una cita.
1. Actualizar una cita.
1. Eliminar/C cancelar una cita.

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

### **Devolviendo los Elementos del Calendario Recurrentes Dentro del Rango de Fechas Especificado**

Aspose.Email EWSClient admite la devolución de elementos del calendario recurrentes dentro del rango especificado por StartDate y EndDate. El método [AppointmentQueryBuilder.setCalendarView(Date startDate, Date endDate, int maxEntriesReturned)](https://reference.aspose.com/email/java/com.aspose.email/appointmentquerybuilder/#setCalendarView-java.util.Date-java.util.Date-int-) devuelve una lista de elementos de calendario individuales y ocurrencias de elementos de calendario recurrentes dentro del rango especificado por StartDate y EndDate si se especifica el CalendarView. El parámetro *maxEntriesReturned* describe el número máximo de resultados. (Valor <= 0 para todos los resultados).

```java
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getAppointment().setCalendarView(startDate, endDate, -1);

Appointment[] appointments = client.listAppointments(builder.getQuery());
```
## **Listando Citas con Soporte de Paginación**
El método ListAppointments expuesto por la API [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) recupera la lista completa de citas del servidor Exchange. Esto puede tardar tiempo si hay un gran número de citas en el servidor Exchange. La API proporciona métodos sobrecargados de [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listAppointments\(\)) que dan soporte de paginación a la operación. Esto se puede usar en diferentes combinaciones con la característica de consulta también. Los siguientes métodos sobrecargados están disponibles para listar citas desde el servidor Exchange con soporte de paginación.

- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.listAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.listAppointments(String folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

El siguiente fragmento de código muestra cómo listar citas con soporte de paginación.

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

                ///// LISTANDO CITAS CON SOPORTE DE PAGINACIÓN ///////
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
                // conversión de foreach a while
                for (AppointmentPageInfo folderCol : pages) {
                    retrievedItems += folderCol.getItems().size();
                }
            } finally {
            }
        } finally {
            client.dispose();
        }
~~~ 
## **Agregando Evento a la Carpeta del Calendario Secundario en Exchange Server**
La API de Aspose.Email le permite crear una carpeta de calendario secundaria en el servidor Exchange utilizando el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Las citas se pueden agregar, actualizar o cancelar desde el calendario secundario utilizando los métodos [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createAppointment\(com.aspose.email.Appointment\)), [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateAppointment\(com.aspose.email.Appointment\)) y [cancelAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#cancelAppointment\(com.aspose.email.Appointment\)). Los siguientes métodos y propiedades de la API se utilizan en los ejemplos de código a continuación para mostrar la funcionalidad de esta característica. Tenga en cuenta que esta característica es compatible con Aspose.Email para Java 6.5.0 en adelante.

- Método `IEWSClient.cancelAppointment(Appointment, String)`.
- Método `IEWSClient.cancelAppointment(String, String)`.
- Método `IEWSClient.createAppointment(Appointment, String)`.
- Método `IEWSClient.createFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Método `IEWSClient.fetchAppointment(String, String)`.
- Método `IEWSClient.updateAppointment(Appointment, String)`.
- Propiedad `IEWSClient.CurrentCalendarFolderUri`.

El siguiente fragmento de código muestra cómo agregar un evento a la carpeta de calendario secundaria en el servidor de intercambio.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "your.username", "your.Password");
try {
    try {
        // Crear una cita que se agregará a la carpeta del calendario secundaria

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

        // Verificar que la nueva carpeta se ha creado
        ExchangeFolderInfoCollection calendarSubFolders = client.listSubFolders(client.getMailboxInfo().getCalendarUri());

        String getfolderName;
        String setFolderName = "New Calendar";
        boolean alreadyExits = false;

        // Verificar que la nueva carpeta ya existe

        for (int i = 0; i < calendarSubFolders.size(); i++) {
            getfolderName = calendarSubFolders.get_Item(i).getDisplayName();

            if (getfolderName.equals(setFolderName)) {
                alreadyExits = true;
            }
        }

        if (alreadyExits) {
            System.out.println("La carpeta ya existe");
        } else {
            // Crear nueva carpeta de calendario
            client.createFolder(client.getMailboxInfo().getCalendarUri(), setFolderName, null, "IPF.Appointment");

            System.out.println(calendarSubFolders.size());

            // Obtener la URI de la carpeta creada
            String newCalendarFolderUri = calendarSubFolders.get_Item(0).getUri();

            // API de cita con la URI de la carpeta del calendario
            // Crear
            client.createAppointment(appointment, newCalendarFolderUri);
            appointment.setLocation("Room 122");
            // actualizar
            client.updateAppointment(appointment, newCalendarFolderUri);
            // listar
            listAppointments = client.listAppointments(newCalendarFolderUri);

            // listar carpeta de calendario predeterminada
            listAppointments = client.listAppointments(client.getMailboxInfo().getCalendarUri());

            // Cancelar
            client.cancelAppointment(appointment, newCalendarFolderUri);
            listAppointments = client.listAppointments(newCalendarFolderUri);

            // API de cita con el contexto de la URI actual de la carpeta del calendario
            client.setCurrentCalendarFolderUri(newCalendarFolderUri);
            // Crear
            client.createAppointment(appointment);
            appointment.setLocation("Room 122");
            // actualizar
            client.updateAppointment(appointment);
            // listar
            listAppointments = client.listAppointments();

            // listar carpeta de calendario predeterminada
            listAppointments = client.listAppointments(client.getMailboxInfo().getCalendarUri());

            // Cancelar
            client.cancelAppointment(appointment);
            listAppointments = client.listAppointments();

        }
    } finally {
    }
} finally {
    client.dispose();
}
~~~ 
## **Compartiendo Invitaciones de Calendario**
El servidor Microsoft Exchange proporciona la capacidad de compartir calendarios enviando invitaciones de calendario a otros usuarios, registrados en el mismo servidor Exchange. La API de Aspose.Email proporciona la misma capacidad permitiendo compartir el calendario utilizando la API de EWS.

~~~Java
final IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
try {
    // delegar permiso de acceso al calendario
    ExchangeDelegateUser delegateUser = new ExchangeDelegateUser("sharingfrom@domain.com", ExchangeDelegateFolderPermissionLevel.NotSpecified);
    delegateUser.getFolderPermissions().setCalendarFolderPermissionLevel(ExchangeDelegateFolderPermissionLevel.Reviewer);
    client.delegateAccess(delegateUser, "sharingfrom@domain.com");

    // Crear invitación
    MapiMessage mapiMessage = client.createCalendarSharingInvitationMessage("sharingfrom@domain.com");
    MailConversionOptions options = new MailConversionOptions();
    options.setConvertAsTnef(true);
    MailMessage mail = mapiMessage.toMailMessage(options);
    client.send(mail);
} finally {
    client.dispose();
}
~~~ 
## **Recuperando Información de Atributos Extendidos de Elementos del Calendario**
~~~Java
IEWSClient client = EWSClient.getEWSClient("https://exchange.office365.com/Exchange.asmx", "username", "password");

java.util.List<String> uriList = java.util.Arrays.asList(client.listItems(client.getMailboxInfo().getCalendarUri()));

// Definir el Descriptor de Propiedad de Atributo Extendida para fines de búsqueda
// En este caso, tenemos una propiedad larga llamada K1 para el elemento del calendario
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