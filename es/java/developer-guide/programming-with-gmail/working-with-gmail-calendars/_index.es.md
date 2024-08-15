---
title: "Cómo trabajar con los calendarios de Gmail"
url: /es/java/working-with-gmail-calendars/
weight: 20
type: docs
---


## **Añadir, editar y eliminar un calendario**
Aspose.Email permite a las aplicaciones administrar los calendarios de Gmail usando [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) que proporciona funciones como agregar, eliminar y actualizar los calendarios de Gmail. Esta clase de cliente devuelve una lista de objetos de tipo ExtendedCalendar que contienen información sobre los elementos del calendario de Gmail. [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) La clase expone las siguientes funciones para los calendarios:

- [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\))
  Para insertar un calendario nuevo
- [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\))

Obtener la lista de todos los calendarios de un cliente

- [deleteCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteCalendar\(java.lang.String\))
  Se puede usar para eliminar un calendario
- [fetchCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchCalendar\(java.lang.String\))
  Se puede usar para obtener un calendario particular de un cliente
- [updateCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateCalendar\(com.aspose.email.Calendar\))
  Esta función se usa para volver a insertar un calendario modificado de un cliente

Para acceder a los calendarios, GoogleTestUser se inicializa con las credenciales de la cuenta de Gmail. GoogleOAuthHelper se usa para obtener el token de acceso para el usuario, que luego se usa para inicializar [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient).
### **Insertar, recuperar y actualizar**
Para insertar un calendario, inicialice un [Calendar](https://apireference.aspose.com/email/java/com.aspose.email/Calendar) escriba el objeto e insértelo usando [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) function. [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) devuelve el identificador del calendario recién insertado. Este identificador se puede usar para obtener el calendario del servidor. El siguiente fragmento de código muestra cómo insertar, recuperar y actualizar el calendario.



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
### **Eliminar un calendario en particular**
Para eliminar un calendario en particular, necesitamos obtener la lista de todos los calendarios de un cliente y luego eliminarlos según sea necesario. [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\)) devuelve la lista de [ExtendedCalendar](https://apireference.aspose.com/email/java/com.aspose.email/ExtendedCalendar) que contiene los calendarios de Gmail. En el siguiente fragmento de código, se muestra cómo eliminar un calendario determinado.



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
## **Trabajando con el control de acceso al calendario**
Aspose.Email proporciona un control total sobre el control de acceso a los elementos del calendario. [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\)) la función está expuesta por [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) que devuelve la lista de [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule). La información de las reglas individuales se puede recuperar, modificar y guardar para el calendario de un cliente. [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) contiene las siguientes funciones para administrar las reglas de control de acceso.

- [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\))
  Esta función proporciona una lista de [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule)
- [createAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Esta función crea una nueva regla de acceso para un calendario.
- [updateAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Esta función se usa para actualizar una regla de acceso.
- [fetchAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAccessRule\(java.lang.String,%20java.lang.String\))
  Se puede usar para obtener una regla de acceso particular para el calendario de un cliente
- [deleteAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAccessRule\(java.lang.String,%20java.lang.String\))
  Esta función se utiliza para eliminar una regla de acceso.

El siguiente fragmento de código muestra cómo se utilizan las funciones para administrar las reglas de acceso:


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
## **Trabajando con la configuración del cliente y la información de color**
Aspose.Email permite acceder a la configuración del cliente mediante [IGmailClient.getSettings](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getSettings\(\)). Devuelve la lista de ajustes que se indica a continuación:

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

Del mismo modo, la información de color para los clientes también se puede recuperar usando [IGmailClient.getColors](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getColors\(\)). Este objeto de información de color devuelve la lista de colores de primer plano, colores de fondo y la fecha y hora de actualización.
### **Acceder a la configuración del cliente**
El siguiente fragmento de código muestra cómo se utilizan las funciones para acceder a la configuración del cliente:


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
### **Acceder a la información sobre colores**
El siguiente fragmento de código muestra cómo se utilizan las funciones para acceder a la configuración de color del cliente.


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
## **Trabajando con citas**
Aspose.Email proporciona funciones para trabajar con [Appointments](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) en los calendarios de Google. La siguiente es la lista de tareas que se pueden realizar en las citas del calendario de Google:

1. Agregar citas - [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAppointment\(java.lang.String,%20com.aspose.email.Appointment\)), [importAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#importAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Recuperar la lista de citas - [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointments\(java.lang.String\))
1. Recuperar una cita en particular - [fetchAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAppointment\(java.lang.String,%20java.lang.String\)), [listAppointmentInstances](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointmentInstances\(java.lang.String,%20java.lang.String\))
1. Actualizar una cita - [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Mover la cita de un calendario a otro - [moveAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#moveAppointment\(java.lang.String,%20java.lang.String,%20java.lang.String\))
1. Eliminar cita - [deleteAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAppointment\(java.lang.String,%20java.lang.String\))

### **Añadir una cita**
El siguiente ejemplo de código muestra la función de agregar una cita en un calendario. En este ejemplo, se siguen los siguientes pasos:

1. Crea e inserta un calendario.
1. Recupere la lista de citas de un calendario nuevo.
1. Crea una cita.
1. Inserte la cita.


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
### **Recuperar y actualizar la cita**
Aquí se demuestra la recuperación y actualización del calendario de la siguiente manera:

1. Solicite una cita específica.
1. Modifique la cita.
1. Actualiza la cita en el calendario.

Se supone que ya se ha extraído un calendario con el identificador «CalendarID» y el identificador único de cita «AppointmentUniqueID». El siguiente fragmento de código muestra cómo recuperar y actualizar una cita.



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
### **Mover y eliminar cita**
[Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) se puede mover proporcionando el calendario de origen, el calendario de destino y la identificación única de la cita en el calendario de origen. El siguiente fragmento de código muestra cómo mover y eliminar una cita.


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
