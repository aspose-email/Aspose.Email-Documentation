---
title: Working with Calendar Items on Exchange Server
type: docs
weight: 50
url: /cpp/working-with-calendar-items-on-exchange-server/
---

## **Sending Meeting Requests**
This article shows how to send a meeting request to multiple recipients using Exchange Web Services and Aspose.Email.

1. Create a meeting request using the [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) class and set the location, time and attendees.
1. Create an instance of the [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) class and set the appointment using the [MailMessage->AddAlternateView()](https://docs.aspose.com/email/cppfilter-messages-from-exchange-mailbox/) method.
1. Connect to the Exchange Server and send the meeting request using the [IEWSClient->Send(MailMessage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method.

The [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) class can be used to connect to an Exchange Servers with Exchange Web Services (EWS) support. For this to work, the server has to be Exchange Server 2007 or later. The following code snippet shows you how to use EWS to send the meeting requests.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cpp" >}}
## **Working with Calendar Items using EWS**
Aspose.Email provides the capability to add, update and cancel appointments using Exchange Web Service (EWS) client. The [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), and [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) methods allow manipulating calendar items using EWS. This article provides a detailed code sample of working with Calendar items. The following code sample shows how to:

1. Create an appointment.
1. Update an appointment.
1. Delete/Cancel an appointment.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cpp" >}}
## **Listing Appointments with Paging Support**
The [ListAppointments](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method exposed by the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) API retrieves the complete list of appointments from the Exchange server. This may take time if there are a large number of appointments on the Exchange Server. The API provides overloaded methods of [ListAppointmentsByPage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method that gives paging support to the operation. This can be used in different combinations with the querying feature as well. The following overloaded methods are available to list appointments from Exchange Server with Paging support.

- [IEWSClient.ListAppointmentsByPage(int itemsPerPage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [IEWSClient.ListAppointmentsByPage(int itemsPerPage, int itemOffset)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage, int itemOffset)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage, int itemOffset)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

The following code snippet shows you how to list appointments with paging support.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cpp" >}}
## **Adding Event to Secondary Calendar folder on Exchange Server**
Aspose.Email API lets you create a secondary Calendar folder on Exchange Server using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Appointments can then be added, updated or canceled from the secondary calendar using the [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), and [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) methods. 

The following code snippet shows you how to add an event to a secondary calendar folder on the exchange server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cpp" >}}
## **Sharing Calendar Invitation**
Microsoft Exchange server provides the capability to share calendars by sending calendar invitations to other users, registered on the same Exchange server. Aspose.Email API provides the same capability by allowing to share the calendar using the EWS API.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cpp" >}}
## **Retrieving Extended Attributes Information from Calendar Items**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cpp" >}}
