---
title: "Trabajar con elementos del calendario en Exchange Server"
url: /es/net/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---


## **Envío de convocatorias de reunión**

En este artículo se muestra cómo enviar una convocatoria de reunión a varios destinatarios mediante Exchange Web Services y Aspose.Email.

1. Cree una convocatoria de reunión mediante el [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) clase y establece el lugar, la hora y los asistentes.
1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase y programe la cita usando el [MailMessage.AddAlternateView()](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/#addalternateview) method.
1. Conéctese al servidor Exchange y envíe la convocatoria de reunión mediante [Send(MailMessage)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/#send) method.

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) La clase se puede usar para conectarse a un servidor Exchange compatible con los servicios web de Exchange (EWS). Para que esto funcione, el servidor debe ser Exchange Server 2007 o posterior. El siguiente fragmento de código muestra cómo usar EWS para enviar convocatorias de reunión.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cs" >}}

## **Cómo trabajar con elementos del calendario mediante EWS**

Aspose.Email ofrece la capacidad de agregar, actualizar y cancelar citas mediante el cliente Exchange Web Service (EWS). El cliente IEWS [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/), y [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) los métodos permiten manipular los elementos del calendario mediante EWS. Este artículo proporciona un ejemplo de código detallado sobre cómo trabajar con elementos del calendario. En el siguiente ejemplo de código se muestra cómo:

1. Crea una cita.
1. Actualiza una cita.
1. Eliminar o cancelar una cita.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cs" >}}

## **Listar citas con soporte de paginación**

El método ListAppointments expuesto por [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) La API recupera la lista completa de citas del servidor Exchange. Esto puede llevar tiempo si hay un gran número de citas en el servidor de Exchange. La API proporciona métodos sobrecargados de [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listappointments/#listappointments/) método que brinda soporte de paginación a la operación. También se puede usar en diferentes combinaciones con la función de consulta. Los siguientes métodos sobrecargados están disponibles para enumerar las citas de Exchange Server con soporte de paginación.

- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

En el siguiente fragmento de código, se muestra cómo enumerar las citas con soporte de paginación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cs" >}}

## **Agregar un evento a la carpeta de calendario secundaria en Exchange Server**

La API Aspose.Email le permite crear una carpeta de calendario secundaria en Exchange Server mediante el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). A continuación, se pueden añadir, actualizar o cancelar citas desde el calendario secundario mediante el [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) and [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) métodos. Los siguientes métodos y propiedades de la API se utilizan en los ejemplos de código que aparecen a continuación para mostrar la funcionalidad de esta función. Tenga en cuenta que esta función es compatible con Aspose.Email para .NET 6.5.0 y versiones posteriores.

- Method `IEWSClient.CancelAppointment(Appointment, String)`.
- Method `IEWSClient.CancelAppointment(String, String)`.
- Method `IEWSClient.CreateAppointment(Appointment, String)`.
- Method `IEWSClient.CreateFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Method `IEWSClient.FetchAppointment(String, String)`.
- Method `IEWSClient.UpdateAppointment(Appointment, String)`.
- Property `IEWSClient.CurrentCalendarFolderUri`.

En el siguiente fragmento de código se muestra cómo agregar un evento a la carpeta de calendario secundaria del servidor de Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cs" >}}

## **Invitación de calendario para compartir**

El servidor Microsoft Exchange ofrece la capacidad de compartir calendarios mediante el envío de invitaciones de calendario a otros usuarios registrados en el mismo servidor de Exchange. La API Aspose.Email ofrece la misma capacidad al permitir compartir el calendario mediante la API EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cs" >}}

## **Recuperación de la información de atributos extendidos de los elementos del calendario**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cs" >}}

## **Devolución de los elementos periódicos del calendario dentro del intervalo de fechas especificado**

[EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) admite la devolución de los elementos del calendario periódicos dentro del rango especificado por StartDate y EndDate. [AppointmentQueryBuilder.SetCalendarView](https://reference.aspose.com/email/net/aspose.email.clients.exchange/appointmentquerybuilder/setcalendarview/) El método se utiliza para definir un rango de fechas específico y limitar el número de citas devueltas para recuperar la información relevante. Al establecer los siguientes parámetros, puede recuperar las citas que coincidan con los criterios especificados.

- Fecha de inicio: la fecha de inicio de la vista del calendario. Las citas que comiencen a partir de esta fecha se incluirán en el resultado de la consulta.

- Fecha de finalización: la fecha de finalización de la vista del calendario. Las citas que finalicen antes o en esta fecha se incluirán en el resultado de la consulta.

- maxEntriesReturned: el número máximo de citas que se devolverán en el resultado de la consulta. El valor -1 indica que no hay un límite específico.

```cs
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.Appointment.SetCalendarView(DateTime.Now, DateTime.Now.AddMonths(1), -1);

Appointment[] appointments = client.ListAppointments(builder.GetQuery());
```
