---
title: Filter Appointments from Exchange Server
ArticleTitle: Filter Appointments from Exchange Server
type: docs
weight: 130
url: /cpp/filter-appointments-from-exchange-server/
description: Learn how to filter Exchange appointments by date range or recurrence using IEWSClient and ExchangeQueryBuilder in Aspose.Email for C++.
---

**Aspose.Email for C++** enables developers to filter calendar appointments on Microsoft Exchange using the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) and [ExchangeQueryBuilder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_query_builder/) APIs. You can filter appointments by date range, recurrence state, or other appointment properties to retrieve only the events you need.


## **Filter Appointments by Date Range**

Use [ExchangeQueryBuilder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_query_builder/) to specify start and end time conditions and generate a MailQuery for retrieving matching appointments.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterAppointmentsUsingEWS-FilterAppointmentsByDateUsingEWS.cpp" >}}


## **Filter Recurring or Non-Recurring Appointments**

You can filter appointments based on whether they are recurring events.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterAppointmentsUsingEWS-FilterAppointmentsByRecurrenceUsingEWS.cpp" >}}
