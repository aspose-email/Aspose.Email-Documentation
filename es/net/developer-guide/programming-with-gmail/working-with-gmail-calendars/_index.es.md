---
title: "Trabajando con Calendarios de Gmail"
url: /es/net/working-with-gmail-calendars/
weight: 20
type: docs
---


## **Agregar, Editar y Eliminar un Calendario**

Aspose.Email permite a las aplicaciones gestionar los calendarios de Gmail utilizando [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) que proporciona características como agregar, eliminar y actualizar calendarios de Gmail. Esta clase cliente retorna una lista de objetos de tipo ExtendedCalendar que contienen información sobre los elementos del calendario de Gmail. La clase [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) expone las siguientes funciones para calendarios:

- [CreateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) 
  Se puede usar para insertar un nuevo calendario.
- [ListCalendars](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/)
  Se puede usar para obtener la lista de todos los calendarios de un cliente.
- [DeleteCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecalendar/)
  Se puede usar para eliminar un calendario.
- [FetchCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchcalendar/)
  Se puede usar para obtener un calendario particular de un cliente.
- [UpdateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updatecalendar/)
  Esta función se usa para reintegrar un calendario modificado de un cliente.

Para acceder a los calendarios, GoogleTestUser se inicializa utilizando las credenciales de la cuenta de Gmail. GoogleOAuthHelper se usa para obtener el token de acceso para el usuario que se utiliza posteriormente para inicializar IGmailClient.

### **Insertar, Obtener y Actualizar**

Para insertar un calendario, inicialice un objeto de tipo Calendar e insértelo utilizando la función [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar). [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) devuelve el Id del calendario recién insertado. Este Id se puede usar para obtener el calendario del servidor. El siguiente fragmento de código muestra cómo insertar, obtener y actualizar un calendario.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-InsertFetchAndUpdateCalendar-InsertFetchAndUpdateCalendar.cs" >}}

### **Eliminar un calendario particular**

Para eliminar un calendario particular, necesitamos obtener la lista de todos los calendarios de un cliente y luego eliminar según sea necesario. [ListCalendars()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/#listcalendars) devuelve la lista de [ExtendedCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/extendedcalendar/) que contiene calendarios de Gmail. El siguiente fragmento de código muestra cómo eliminar un calendario particular.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteParticularCalendar-DeleteParticularCalendar.cs" >}}

## **Trabajando con Control de Acceso al Calendario**

Aspose.Email proporciona control total sobre el acceso a los elementos del calendario. La función [ListAccessRules()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/) es expuesta por [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) que devuelve la lista de [AccessControlRule](https://reference.aspose.com/email/net/aspose.email.clients.google/accesscontrolrule/). La información de cada regla puede ser recuperada, modificada y guardada nuevamente para el calendario de un cliente. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) contiene las siguientes funciones para gestionar las reglas de control de acceso.

- [ListAccessRules](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/)
  Esta función proporciona la lista de AccessControlRule.
- [CreateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createaccessrule/)
  Esta función crea una nueva regla de acceso para un calendario.
- [UpdateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateaccessrule/)
  Esta función se usa para actualizar una regla de acceso.
- [FetchAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchaccessrule/)
  Se puede usar para obtener una regla de acceso particular para el calendario de un cliente.
- [DeleteAccessRule](https://search.aspose.com/q/deleteaccessrule.html)
  Esta función se usa para eliminar una regla de acceso.

El siguiente fragmento de código muestra cómo usar las funciones para gestionar las reglas de acceso:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-ManageAccessRule-ManageAccessRule.cs" >}}

## **Trabajando con Configuraciones del Cliente y Información de Color**

Aspose.Email admite el acceso a la configuración del Cliente mediante [IGmailClient.GetSettings()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getsettings/#igmailclientgetsettings-method). Devuelve la lista de configuraciones como se indica a continuación:

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

De manera similar, la información de color para los clientes también se puede recuperar utilizando [IGmailClient.GetColors()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getcolors/#igmailclientgetcolors-method). Este objeto de información de color devuelve la lista de colores de primer plano, colores de fondo y fecha y hora de actualización.

### **Acceder a la configuración del cliente**

El siguiente fragmento de código muestra cómo se pueden usar las funciones para acceder a la configuración del cliente:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessClientSettings-AccessClientSettings.cs" >}}

### **Acceder a la información de color**

El siguiente fragmento de código muestra cómo se pueden usar las funciones para acceder a la configuración de color del cliente.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessColorInfo-AccessColorInfo.cs" >}}

## **Trabajando con Citas**

Aspose.Email proporciona características para trabajar con Citas en calendarios de Google. A continuación se presenta la lista de tareas que se pueden realizar en citas en el calendario de Google:

1. Agregar citas.
1. Recuperar la lista de citas.
1. Recuperar una cita particular.
1. Actualizar una cita.
1. Mover una cita de un calendario a otro.
1. Eliminar una cita.

[IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) proporciona funciones como [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createappointment/#igmailclientcreateappointment-method), [FetchAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchappointment/#igmailclientfetchappointment-method), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateappointment/#igmailclientupdateappointment-method), [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listappointments/#igmailclientlistappointments-method), [MoveAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/moveappointment/#moveappointment) y [DeleteAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deleteappointment/#igmailclientdeleteappointment-method).

### **Agregando una cita**

El siguiente ejemplo de código demuestra la característica de agregar una cita en un calendario. Para lograr esto, siga los pasos:

1. Crear e insertar un calendario.
1. Recuperar la lista de citas de un nuevo calendario.
1. Crear una cita.
1. Insertar una cita.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AddingAnAppointment-AddingAnAppointment.cs" >}}

### **Recuperar y actualizar una cita**

Aquí se demuestra la recuperación y actualización del calendario de la siguiente manera:

1. Recuperar una cita particular.
1. Modificar la cita.
1. Actualizar la cita en el calendario.

Se asume que un calendario con el Id "calendarId" y el Id único de la cita "AppointmentUniqueId" ya están extraídos. El siguiente fragmento de código muestra cómo recuperar y actualizar una cita.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-RetrieveUpdateAppointment-RetrieveUpdateAppointment.cs" >}}

### **Mover y Eliminar una cita**

La cita se puede mover proporcionando el calendario de origen, el calendario de destino y el Id único de una cita en el calendario de origen. El siguiente fragmento de código muestra cómo mover y eliminar una cita.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-MoveAndDeleteAppointment-MoveAndDeleteAppointment.cs" >}}