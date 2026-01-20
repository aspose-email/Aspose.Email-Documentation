---
title: Manage Calendar & Meeting Requests with Exchange Web Services (EWS)
ArticleTitle: Manage Calendar & Meeting Requests with Exchange Web Services (EWS)
type: docs
weight: 50
url: /cpp/manage-calendar-items-on-exchange-server/
description: Learn how to create, send, update, list, and manage meeting requests and calendar items in Exchange Web Services (EWS) using Aspose.Email for C++.
---


This article explains how to work with meeting requests and calendar items using Aspose.Email for C++ and Exchange Web Services (EWS). You will learn how to:

- Send meeting requests to one or multiple recipients
- Create, update, and cancel appointments
- List calendar items with paging support
- Add events to secondary calendars
- Share calendars with users
- Retrieve extended properties from calendar items

All scenarios include C++ code examples using [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).


## **Send a Meeting Request via EWS**

You can create and send a meeting request by building an [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) object and attaching it to a [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) before sending it through [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

The following code sample demonstrates how to create and send a recurring meeting request via Exchange Web Services:

1. Create an [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) and set the location, time, attendees.
2. Add recurrence if needed.
3. Create an email message using the [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
4. Attach the meeting request via [AddAlternateView()](https://docs.aspose.com/email/cppfilter-messages-from-exchange-mailbox/).
5. Connect to the Exchange Server and send the message using the [IEWSClient->Send(MailMessage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cpp" >}}


## **Create, Update, and Cancel Appointments**


Aspose.Email provides dedicated [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) methods to manage calendar items:

- `CreateAppointment()`
- `UpdateAppointment()`
- `CancelAppointment()`
- `FetchAppointment()`

The following code sample demonstrates how to manage calendar operations on an Exchange Server using Aspose.Email for C++. It shows the full lifecycle of creating, retrieving, updating, and canceling appointments through Exchange Web Services, including setting timezone information, listing all appointments, and verifying changes by fetching and displaying appointment details before and after modifications.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cpp" >}}


## **List Appointments with Paging Support**


When a mailbox contains many appointments, paging helps retrieve items efficiently. For this purpose, Aspose.Email provides multiple overloads of the [ListAppointmentsByPage()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method including querying feature combinations.

The following code sample demonstrates how to create multiple calendar appointments with sequential time slots, then implement pagination to list all appointments by retrieving them in smaller, manageable pages rather than loading the entire collection at once, which is useful for handling large numbers of calendar items.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cpp" >}}


## **Add Events to a Secondary Calendar Folder**

You can create custom calendar folders and manage appointments inside them. The following code sample demonstrates how to create and manage a secondary calendar folder in Exchange Server and perform appointment operations within it. This includes checking for an existing custom calendar folder, creating a new calendar folder if it doesn't exist, then performing full CRUD operations (create, read, update, delete) on appointments within both the custom calendar folder and the default calendar folder, including setting a current calendar context for simplified API calls.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cpp" >}}


## **Share Calendar Invitation**

Microsoft Exchange server provides the capability to share calendars by sending calendar invitations to other users, registered on the same Exchange server. Aspose.Email API provides the same capability by allowing to share the calendar using the EWS API.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cpp" >}}

## **Retrieve Extended Properties from Calendar Items**

Aspose.Email allows you to fetch custom MAPI properties from calendar items using property descriptors.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cpp" >}}
