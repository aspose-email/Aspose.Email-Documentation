---
title: Working with Calendar Items on Exchange Server
type: docs
weight: 50
url: /net/working-with-calendar-items-on-exchange-server/
---


## **Sending Meeting Requests**

This article shows how to send a meeting request to multiple recipients using Exchange Web Services and Aspose.Email.

1. Create a meeting request using the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) class and set the location, time and attendees.
1. Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class and set the appointment using the [MailMessage.AddAlternateView()](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/#addalternateview) method.
1. Connect to the Exchange Server and send the meeting request using the [Send(MailMessage)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/#send) method.

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class can be used to connect to an Exchange Server with Exchange Web Services (EWS) support. For this to work, the server has to be Exchange Server 2007 or later. The following code snippet shows you how to use EWS to send meeting requests.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cs" >}}

## **Working with Calendar Items using EWS**

Aspose.Email provides the capability to add, update and cancel appointments using Exchange Web Service (EWS) client. The IEWSClient [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/), and [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) methods allow manipulating calendar items using EWS. This article provides a detailed code sample of working with Calendar items. The following code sample shows how to:

1. Create an appointment.
1. Update an appointment.
1. Delete/Cancel an appointment.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cs" >}}

## **Listing Appointments with Paging Support**

The ListAppointments method exposed by the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) API retrieves the complete list of appointments from the Exchange server. This may take time if there is a large number of appointments on the Exchange Server. The API provides overloaded methods of [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listappointments/#listappointments/) method that gives paging support to the operation. This can be used in different combinations with the querying feature as well. The following overloaded methods are available to list appointments from Exchange Server with Paging support.

- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

The following code snippet shows you how to list appointments with paging support.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cs" >}}

## **Adding Event to Secondary Calendar folder on Exchange Server**

Aspose.Email API lets you create a secondary Calendar folder on Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Appointments can then be added, updated or canceled from the secondary calendar using the [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) and [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) methods. The following API methods and properties are used in the code samples below to show the functionality of this feature. Please note that this feature is supported by Aspose.Email for .NET 6.5.0 onwards.

- Method `IEWSClient.CancelAppointment(Appointment, String)`.
- Method `IEWSClient.CancelAppointment(String, String)`.
- Method `IEWSClient.CreateAppointment(Appointment, String)`.
- Method `IEWSClient.CreateFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Method `IEWSClient.FetchAppointment(String, String)`.
- Method `IEWSClient.UpdateAppointment(Appointment, String)`.
- Property `IEWSClient.CurrentCalendarFolderUri`.

The following code snippet shows you how to add an event to the secondary calendar folder on the exchange server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cs" >}}

## **Sharing Calendar Invitation**

Microsoft Exchange server provides the capability to share calendars by sending calendar invitations to other users, registered on the same Exchange server. Aspose.Email API provides the same capability by allowing to share the calendar using the EWS API.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cs" >}}

## **Retrieving Extended Attributes Information from Calendar Items**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cs" >}}

## **Returning the Recurring Calendar Items Within the Specified Date Range**

[EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) supports the return of the recurring calendar items within the range specified by StartDate and EndDate. [AppointmentQueryBuilder.SetCalendarView](https://reference.aspose.com/email/net/aspose.email.clients.exchange/appointmentquerybuilder/setcalendarview/) method is used to define a specific date range and limit the number of returned appointments to retrieve relevant information. By setting the following parameters you can retrieve the appointments matching the specified criteria.

- startDate: The start date of the calendar view. Appointments starting from this date will be included in the query result.

- endDate: The end date of the calendar view. Appointments ending before or on this date will be included in the query result.

- maxEntriesReturned: The maximum number of appointments to be returned in the query result. The value of -1 indicates that there is no specific limit.

```cs
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.Appointment.SetCalendarView(DateTime.Now, DateTime.Now.AddMonths(1), -1);

Appointment[] appointments = client.ListAppointments(builder.GetQuery());
```
