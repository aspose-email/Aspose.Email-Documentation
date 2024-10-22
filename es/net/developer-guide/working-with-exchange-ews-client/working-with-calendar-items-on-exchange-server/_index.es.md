---
title: "Trabajando con Elementos de Calendario en Exchange Server"
url: /es/net/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---


## **Enviando Solicitudes de Reunión**

Este artículo muestra cómo enviar una solicitud de reunión a múltiples destinatarios usando Exchange Web Services y Aspose.Email.

1. Crea una solicitud de reunión utilizando la clase [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) y establece la ubicación, la hora y los asistentes.
1. Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y establece la cita usando el método [MailMessage.AddAlternateView()](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/#addalternateview).
1. Conéctate al Exchange Server y envía la solicitud de reunión usando el método [Send(MailMessage)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/#send) .

La clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) se puede utilizar para conectarse a un Exchange Server con soporte para Exchange Web Services (EWS). Para que esto funcione, el servidor debe ser Exchange Server 2007 o posterior. El siguiente fragmento de código te muestra cómo utilizar EWS para enviar solicitudes de reunión.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cs" >}}


## **Trabajando con Elementos de Calendario usando EWS**

Aspose.Email proporciona la capacidad de agregar, actualizar y cancelar citas utilizando el cliente de Exchange Web Service (EWS). Los métodos IEWSClient [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/), y [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) permiten manipular elementos de calendario usando EWS. Este artículo proporciona un ejemplo de código detallado sobre cómo trabajar con elementos de calendario. El siguiente ejemplo de código muestra cómo:

1. Crear una cita.
1. Actualizar una cita.
1. Eliminar/Cancela una cita.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cs" >}}


## **Listando Citas con Soporte de Paginación**

El método ListAppointments expuesto por la API [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) recupera la lista completa de citas del servidor Exchange. Esto puede tomar tiempo si hay un gran número de citas en el Exchange Server. La API proporciona métodos sobrecargados del método [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listappointments/#listappointments/) que otorgan soporte de paginación a la operación. Esto se puede usar en diferentes combinaciones con la característica de consulta también. Los siguientes métodos sobrecargados están disponibles para listar citas desde el Exchange Server con soporte de paginación.

- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

El siguiente fragmento de código te muestra cómo listar citas con soporte de paginación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cs" >}}


## **Agregando Evento a la Carpeta de Calendario Secundario en Exchange Server**

La API Aspose.Email te permite crear una carpeta de Calendario secundaria en Exchange Server usando el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Las citas pueden ser agregadas, actualizadas o canceladas desde el calendario secundario usando los métodos [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) y [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/). Los siguientes métodos y propiedades de la API se utilizan en los ejemplos de código a continuación para mostrar la funcionalidad de esta característica. Ten en cuenta que esta característica es compatible con Aspose.Email para .NET 6.5.0 en adelante.

- Método `IEWSClient.CancelAppointment(Appointment, String)`.
- Método `IEWSClient.CancelAppointment(String, String)`.
- Método `IEWSClient.CreateAppointment(Appointment, String)`.
- Método `IEWSClient.CreateFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Método `IEWSClient.FetchAppointment(String, String)`.
- Método `IEWSClient.UpdateAppointment(Appointment, String)`.
- Propiedad `IEWSClient.CurrentCalendarFolderUri`.

El siguiente fragmento de código te muestra cómo agregar un evento a la carpeta de calendario secundaria en el servidor de intercambio.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cs" >}}


## **Compartiendo Invitación de Calendario**

El servidor Microsoft Exchange proporciona la capacidad de compartir calendarios enviando invitaciones de calendario a otros usuarios, registrados en el mismo servidor de Exchange. La API Aspose.Email proporciona la misma capacidad permitiendo compartir el calendario mediante la API EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cs" >}}


## **Recuperando Información de Atributos Extendidos de Elementos de Calendario**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cs" >}}


## **Devolviendo los Elementos de Calendario Recurrentes Dentro del Rango de Fechas Especificado**

[EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) admite el retorno de los elementos de calendario recurrentes dentro del rango especificado por StartDate y EndDate. El método [AppointmentQueryBuilder.SetCalendarView](https://reference.aspose.com/email/net/aspose.email.clients.exchange/appointmentquerybuilder/setcalendarview/) se utiliza para definir un rango de fechas específico y limitar el número de citas devueltas para recuperar información relevante. Al establecer los siguientes parámetros, puedes recuperar las citas que coinciden con los criterios especificados.

- startDate: La fecha de inicio de la vista del calendario. Las citas que comienzan a partir de esta fecha se incluirán en el resultado de la consulta.

- endDate: La fecha de finalización de la vista del calendario. Las citas que terminan antes o en esta fecha se incluirán en el resultado de la consulta.

- maxEntriesReturned: El número máximo de citas que se devolverán en el resultado de la consulta. El valor de -1 indica que no hay un límite específico.

```cs
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.Appointment.SetCalendarView(DateTime.Now, DateTime.Now.AddMonths(1), -1);

Appointment[] appointments = client.ListAppointments(builder.GetQuery());
```