---
title: "Cómo trabajar con los calendarios de Gmail"
url: /es/net/working-with-gmail-calendars/
weight: 20
type: docs
---


## **Añadir, editar y eliminar un calendario**

Aspose.Email permite a las aplicaciones administrar los calendarios de Gmail usando [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) que ofrece funciones como añadir, eliminar y actualizar los calendarios de Gmail. Esta clase de cliente devuelve una lista de objetos de tipo ExtendedCalendar que contienen información sobre los elementos del calendario de Gmail. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) La clase expone las siguientes funciones para los calendarios:

- [CreateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar)
  Se puede usar para insertar un nuevo calendario
- [ListCalendars](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/)
  Se puede usar para obtener la lista de todos los calendarios de un cliente
- [DeleteCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecalendar/)
  Se puede usar para eliminar un calendario
- [FetchCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchcalendar/)
  Se puede usar para obtener un calendario particular de un cliente
- [UpdateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updatecalendar/)
  Esta función se usa para volver a insertar un calendario modificado de un cliente

Para acceder a los calendarios, GoogleTestUser se inicializa con las credenciales de la cuenta de Gmail. GoogleOAuthHelper se usa para obtener el token de acceso para el usuario, que luego se usa para inicializar IGmailClient.

### **Insertar, recuperar y actualizar**

Para insertar un calendario, inicialice un objeto de tipo Calendario e insértelo mediante [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) function. [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) devuelve el identificador del calendario recién insertado. Este identificador se puede usar para obtener el calendario del servidor. El siguiente fragmento de código muestra cómo insertar, recuperar y actualizar el calendario.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-InsertFetchAndUpdateCalendar-InsertFetchAndUpdateCalendar.cs" >}}

### **Eliminar un calendario en particular**

Para eliminar un calendario en particular, necesitamos obtener la lista de todos los calendarios de un cliente y luego eliminarlos según sea necesario. [ListCalendars()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/#listcalendars) devuelve la lista de [ExtendedCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/extendedcalendar/) que contiene los calendarios de Gmail. En el siguiente fragmento de código, se muestra cómo eliminar un calendario determinado.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteParticularCalendar-DeleteParticularCalendar.cs" >}}

## **Trabajando con el control de acceso al calendario**

Aspose.Email proporciona un control total sobre el acceso a los elementos del calendario. [ListAccessRules()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/) la función está expuesta por [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) que devuelve la lista de [AccessControlRule](https://reference.aspose.com/email/net/aspose.email.clients.google/accesscontrolrule/). La información de las reglas individuales se puede recuperar, modificar y guardar para el calendario de un cliente. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) contiene las siguientes funciones para administrar las reglas de control de acceso.

- [ListAccessRules](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/)
  Esta función proporciona la lista de AccessControlRule
- [CreateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createaccessrule/)
  Esta función crea una nueva regla de acceso para un calendario.
- [UpdateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateaccessrule/)
  Esta función se usa para actualizar una regla de acceso.
- [FetchAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchaccessrule/)
  Se puede usar para obtener una regla de acceso particular para el calendario de un cliente
- [DeleteAccessRule](https://search.aspose.com/q/deleteaccessrule.html)
  Esta función se utiliza para eliminar una regla de acceso.

El siguiente fragmento de código muestra cómo usar las funciones para administrar las reglas de acceso:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-ManageAccessRule-ManageAccessRule.cs" >}}

## **Trabajando con la configuración del cliente y la información de color**

Aspose.Email permite acceder a la configuración del cliente mediante [IGmailClient.GetSettings()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getsettings/#igmailclientgetsettings-method). Devuelve la lista de ajustes que se indica a continuación:

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

Del mismo modo, la información de color para los clientes también se puede recuperar usando [IGmailClient.GetColors()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getcolors/#igmailclientgetcolors-method). Este objeto de información de color devuelve la lista de colores de primer plano, colores de fondo y la fecha y hora de actualización.

### **Acceder a la configuración del cliente**

El siguiente fragmento de código muestra cómo se pueden usar las funciones para acceder a la configuración del cliente:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessClientSettings-AccessClientSettings.cs" >}}

### **Acceder a la información de color**

El siguiente fragmento de código muestra cómo se pueden usar las funciones para acceder a la configuración de color del cliente.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessColorInfo-AccessColorInfo.cs" >}}

## **Trabajando con citas**

Aspose.Email ofrece funciones para trabajar con citas en los calendarios de Google. La siguiente es la lista de tareas que se pueden realizar en las citas del calendario de Google:

1. Agregar citas.
1. Recupere la lista de citas.
1. Recupera una cita en particular.
1. Actualiza una cita.
1. Mueva la cita de un calendario a otro.
1. Eliminar cita.

[IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) proporciona funciones como [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createappointment/#igmailclientcreateappointment-method), [FetchAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchappointment/#igmailclientfetchappointment-method), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateappointment/#igmailclientupdateappointment-method), [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listappointments/#igmailclientlistappointments-method), [MoveAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/moveappointment/#moveappointment) and [DeleteAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deleteappointment/#igmailclientdeleteappointment-method).

### **Añadir una cita**

El siguiente ejemplo de código muestra la función de agregar una cita en un calendario. Para lograrlo, sigue los pasos:

1. Crea e inserta un calendario.
1. Recupere la lista de citas de un calendario nuevo.
1. Crea una cita.
1. Inserta una cita.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AddingAnAppointment-AddingAnAppointment.cs" >}}

### **Recuperar y actualizar una cita**

Aquí se demuestra la recuperación y actualización del calendario de la siguiente manera:

1. Solicite una cita específica.
1. Modifique la cita.
1. Actualiza la cita en el calendario.

Se supone que ya se ha extraído un calendario con el identificador «CalendarID» y el identificador único de cita «AppointmentUniqueID». El siguiente fragmento de código muestra cómo recuperar y actualizar una cita.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-RetrieveUpdateAppointment-RetrieveUpdateAppointment.cs" >}}

### **Mover y eliminar una cita**

La cita se puede mover proporcionando el calendario de origen, el calendario de destino y el identificador único de una cita en el calendario de origen. En el siguiente fragmento de código, se muestra cómo mover y eliminar una cita.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-MoveAndDeleteAppointment-MoveAndDeleteAppointment.cs" >}}
