---
title: "Trabajando con Calendarios de Gmail"
url: /es/java/working-with-gmail-calendars/
weight: 20
type: docs
---


## **Agregar, Editar y Eliminar un Calendario**
Aspose.Email permite a las aplicaciones gestionar los calendarios de Gmail usando [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), que proporciona características como agregar, eliminar y actualizar calendarios de Gmail. Esta clase de cliente devuelve una lista de objetos del tipo ExtendedCalendar que contienen información sobre los elementos del calendario de Gmail. La clase [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) expone las siguientes funciones para los calendarios:

- [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\))
  Para insertar un nuevo calendario
- [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\))

Obtener la lista de todos los calendarios de un cliente

- [deleteCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteCalendar\(java.lang.String\))
  Se puede usar para eliminar un calendario
- [fetchCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchCalendar\(java.lang.String\))
  Se puede usar para obtener un calendario particular de un cliente
- [updateCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateCalendar\(com.aspose.email.Calendar\))
  Esta función se utiliza para insertar de nuevo un calendario modificado de un cliente

Para acceder a los calendarios, GoogleTestUser se inicializa utilizando las credenciales de la cuenta de gmail. GoogleOAuthHelper se usa para obtener el token de acceso para el usuario, el cual se utiliza posteriormente para inicializar [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient).
### **Insertar, Obtener y Actualizar**
Para insertar un calendario, inicializa un objeto del tipo [Calendar](https://apireference.aspose.com/email/java/com.aspose.email/Calendar) e insértalo utilizando la función [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)). [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) devuelve el id del calendario recién insertado. Este id se puede usar para obtener el calendario del servidor. El siguiente fragmento de código te muestra cómo insertar, obtener y actualizar un calendario.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Insertar, obtener y actualizar calendario
    Calendar calendar = new Calendar("Resumen", "Descripción", "Ubicación", "America/Los_Angeles");

    // Insertar calendario y recuperar el mismo calendario usando el id
    String id = client.createCalendar(calendar);
    Calendar cal = client.fetchCalendar(id);

    // Cambiar información en el calendario obtenido y actualizar el calendario
    cal.setDescription("Nueva Descripción");
    cal.setLocation("Nueva Ubicación");
    client.updateCalendar(cal);
}
~~~
### **Eliminar un Calendario Particular**
Para eliminar un calendario particular, necesitamos obtener la lista de todos los calendarios de un cliente y luego eliminar según sea necesario. [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\)) devuelve la lista de [ExtendedCalendar](https://apireference.aspose.com/email/java/com.aspose.email/ExtendedCalendar) que contiene los calendarios de Gmail. El siguiente fragmento de código te muestra cómo eliminar un calendario particular.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Acceder y eliminar calendario con resumen comenzando desde "Resumen del calendario"
    String summary = "Resumen del calendario";

    // Obtener lista de calendarios
    ExtendedCalendar[] lst = client.listCalendars();

    for (ExtendedCalendar extCal : lst) {
        // Eliminar calendarios seleccionados
        if (extCal.getSummary().startsWith(summary))
            client.deleteCalendar(extCal.getId());
    }
}
~~~
## **Trabajando con el Control de Acceso del Calendario**
Aspose.Email proporciona control total sobre el control de acceso a los elementos del calendario. La función [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\)) es expuesta por [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), que devuelve una lista de [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule). La información de cada regla puede ser recuperada, modificada y guardada de nuevo para el calendario de un cliente. [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) contiene las siguientes funciones para gestionar las reglas de control de acceso.

- [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\))
  Esta función proporciona una lista de [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule)
- [createAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Esta función crea una nueva regla de acceso para un calendario.
- [updateAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Esta función se utiliza para actualizar una regla de acceso.
- [fetchAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAccessRule\(java.lang.String,%20java.lang.String\))
  Se puede usar para obtener una regla de acceso particular para el calendario de un cliente
- [deleteAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAccessRule\(java.lang.String,%20java.lang.String\))
  Esta función se usa para eliminar una regla de acceso.

El siguiente fragmento de código te muestra cómo se utilizan las funciones para gestionar las reglas de acceso:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Recuperar lista de calendarios para el cliente actual
    ExtendedCalendar[] calendarList = client.listCalendars();

    // Obtener el id del primer calendario y recuperar la lista de AccessControlRule para el primer calendario
    String calendarId = calendarList[0].getId();
    AccessControlRule[] roles1 = client.listAccessRules(calendarId);

    // Crear una regla de control de acceso local y establecer las propiedades de la regla
    AccessControlRule rule = new AccessControlRule();
    rule.setRole(AccessRole.reader);
    rule.setScope(new AclScope(AclScopeType.user, email2));

    // Insertar nueva regla para el calendario. Devuelve la regla recién creada
    AccessControlRule createdRule = client.createAccessRule(calendarId, rule);

    // Obtener lista de reglas
    AccessControlRule[] roles2 = client.listAccessRules(calendarId);

    // La longitud de la lista actual debería ser 1 más que la anterior
    if (roles1.length + 1 == roles2.length) {
        System.out.println("Las longitudes de las listas son correctas");
    } else {
        System.out.println("Las longitudes de las listas no son correctas");
        return;
    }

    // Cambiar regla y actualizar la regla para el calendario seleccionado
    createdRule.setRole(AccessRole.writer);
    AccessControlRule updatedRule = client.updateAccessRule(calendarId, createdRule);

    // Recuperar regla individual contra un calendario
    AccessControlRule fetchedRule = client.fetchAccessRule(calendarId, createdRule.getId());

    // Eliminar regla particular contra un calendario dado y recuperar la lista de todas las reglas para el mismo calendario
    client.deleteAccessRule(calendarId, createdRule.getId());
    AccessControlRule[] roles3 = client.listAccessRules(calendarId);

    // Verificar que la longitud de la lista actual de reglas debería ser igual a la longitud de la lista original antes de agregar y eliminar la regla
    if (roles1.length == roles3.length) {
        System.out.println("Las longitudes de las listas son las mismas");
    } else {
        System.out.println("Las longitudes de las listas no son iguales");
        return;
    }
}
~~~
## **Trabajando con Configuración del Cliente e Información de Color**
Aspose.Email admite el acceso a la configuración del cliente utilizando [IGmailClient.getSettings](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getSettings\(\)). Devuelve una lista de configuraciones como se indica a continuación:

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

De manera similar, la información de color para los clientes también se puede recuperar utilizando [IGmailClient.getColors](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getColors\(\)). Este objeto de información de color devuelve la lista de colores de primer plano, colores de fondo y fecha y hora de actualización.
### **Acceder a la Configuración del Cliente**
El siguiente fragmento de código te muestra cómo se utilizan las funciones para acceder a la configuración del cliente:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Recuperar configuración del cliente
    Dictionary<String, String> settings = client.getSettings();
    if (settings.size() < 1) {
        System.out.println("No hay configuraciones disponibles.");
        return;
    }

    // Recorrer la lista de configuraciones
    for (KeyValuePair<String, String> pair : settings) {
        // Obtener el valor de la configuración y probar si las configuraciones son correctas
        String value = client.getSetting(pair.getKey());
        if (pair.getValue().equals(value)) {
            System.out.println("Clave = " + pair.getKey() + ", Valor = " + pair.getValue());
        } else {
            System.out.println("No se pudieron recuperar las configuraciones");
        }
    }
}
~~~
### **Acceder a la Información de Color**
El siguiente fragmento de código te muestra cómo se utilizan las funciones para acceder a la configuración de color del cliente.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    ColorsInfo colors = client.getColors();
    Dictionary<String, Colors> palettes = colors.getCalendar();

    // Recorrer la lista de configuraciones
    for (KeyValuePair<String, Colors> pair : palettes) {
        System.out.println("Clave = " + pair.getKey() + ", Color = " + pair.getValue());
    }
    System.out.println("Fecha de Actualización = " + colors.getUpdated());
}
~~~
## **Trabajando con Citas**
Aspose.Email proporciona características para trabajar con [Citas](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) en los calendarios de Google. La siguiente es la lista de tareas que se pueden realizar en citas en el calendario de Google:

1. Agregar Citas - [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAppointment\(java.lang.String,%20com.aspose.email.Appointment\)), [importAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#importAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Recuperar lista de citas - [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointments\(java.lang.String\))
1. Recuperar cita particular - [fetchAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAppointment\(java.lang.String,%20java.lang.String\)), [listAppointmentInstances](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointmentInstances\(java.lang.String,%20java.lang.String\))
1. Actualizar una cita - [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Mover cita de un calendario a otro - [moveAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#moveAppointment\(java.lang.String,%20java.lang.String,%20java.lang.String\))
1. Eliminar cita - [deleteAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAppointment\(java.lang.String,%20java.lang.String\))

### **Agregar una Cita**
El siguiente ejemplo de código demuestra la función de agregar una cita en un calendario. En este ejemplo se siguen los siguientes pasos:

1. Crear e insertar un calendario.
1. Recuperar lista de citas de un nuevo calendario.
1. Crear una cita.
1. Insertar la cita.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Crear calendario local
    Calendar calendar1 = new Calendar("Resumen", null, null, "Europe/Kiev");

    // Insertar calendario y obtener id del calendario insertado y recuperar el calendario usando un id
    String id = client.createCalendar(calendar1);
    Calendar cal1 = client.fetchCalendar(id);
    String calendarId1 = cal1.getId();

    try {
        // Recuperar lista de citas del primer calendario
        Appointment[] appointments = client.listAppointments(calendarId1);
        if (appointments.length > 0) {
            System.out.println("Número incorrecto de citas");
            return;
        }

        // Obtener hora actual y calcular la hora después de una hora desde ahora
        java.util.Calendar c = java.util.Calendar.getInstance();
        Date startDate = c.getTime();
        c.add(java.util.Calendar.HOUR_OF_DAY, 1);
        Date endDate = c.getTime();

        // Inicializar una colección de direcciones de correo y establecer las direcciones de correo de los asistentes
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.add("User1.EMail@domain.com");
        attendees.add("User3.EMail@domain.com");

        // Crear una cita con los asistentes anteriores
        Appointment app1 = new Appointment("Ubicación", startDate, endDate, MailAddress.to_MailAddress(email2), attendees);

        // Establecer resumen de la cita, descripción, zona horaria de inicio/final
        app1.setSummary("Nuevo Resumen");
        app1.setDescription("Nueva Descripción");
        app1.setStartTimeZone("Europe/Kiev");
        app1.setEndTimeZone("Europe/Kiev");

        // Insertar cita en el primer calendario insertado arriba y obtener la cita insertada
        Appointment app2 = client.createAppointment(calendarId1, app1);

        // Recuperar cita usando el id único
        Appointment app3 = client.fetchAppointment(calendarId1, app2.getUniqueId());
    } catch (Exception ex) {
        System.err.println(ex);
    }
    
}
~~~
### **Recuperar y Actualizar Cita**
Aquí se demuestra la recuperación y actualización de calendarios de la siguiente manera:

1. Recuperar una cita particular.
1. Modificar la cita.
1. Actualizar la cita en el calendario.

Se asume que un calendario con id "calendarId" y un id único de cita "AppointmentUniqueId" ya han sido extraídos. El siguiente fragmento de código te muestra cómo recuperar y actualizar una cita.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String calendarId = client.listCalendars()[0].getId();
    String AppointmentUniqueId = client.listAppointments(calendarId)[0].getUniqueId();

    // Recuperar Cita
    Appointment app3 = client.fetchAppointment(calendarId, AppointmentUniqueId);
    // Cambiar la información de la cita
    app3.setSummary("Nuevo Resumen");
    app3.setDescription("Nueva Descripción");
    app3.setLocation("Nueva Ubicación");
    app3.setFlags(AppointmentFlags.AllDayEvent);
    java.util.Calendar c = java.util.Calendar.getInstance();
    c.add(java.util.Calendar.HOUR_OF_DAY, 2);
    app3.setStartDate(c.getTime());
    c.add(java.util.Calendar.HOUR_OF_DAY, 1);
    app3.setEndDate(c.getTime());
    app3.setStartTimeZone("Europe/Kiev");
    app3.setEndTimeZone("Europe/Kiev");
    // Actualizar la cita y obtener la cita actualizada
    Appointment app4 = client.updateAppointment(calendarId, app3);
}
~~~
### **Mover y Eliminar Cita**
[Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) se puede mover proporcionando el calendario de origen, el calendario de destino y el id único de la cita en el calendario de origen. El siguiente fragmento de código te muestra cómo mover y eliminar una cita.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String SourceCalendarId = client.listCalendars()[0].getId();
    String DestinationCalendarId = client.listCalendars()[1].getId();
    String TargetAppUniqueId = client.listAppointments(SourceCalendarId)[0].getUniqueId();

    // Recuperar la lista de citas en el calendario de destino antes de mover la cita
    Appointment[] appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Conteo antes de mover = " + appointments.length);
    Appointment Movedapp = client.moveAppointment(SourceCalendarId, DestinationCalendarId, TargetAppUniqueId);

    // Recuperar la lista de citas en el calendario de destino después de mover la cita
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Conteo después de mover = " + appointments.length);

    // Eliminar una cita particular de un calendario usando el id único
    client.deleteAppointment(DestinationCalendarId, Movedapp.getUniqueId());

    // Recuperar la lista de citas. Debe ser una menos que las citas anteriores en el calendario de destino
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Conteo después de eliminar = " + appointments.length);
}
~~~