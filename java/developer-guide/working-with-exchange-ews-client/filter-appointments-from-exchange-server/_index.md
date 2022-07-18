---
title: Filter Appointments from Exchange Server
type: docs
weight: 130
url: /java/filter-appointments-from-exchange-server/
---


## **Filtering Appointments with EWS**
The [IEWSClient](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient) provides the facility to filter appointments from the Exchange server using the [ExchangeQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Appointments can be filtered based on:

- Dates
- Recurrences
### **Filtering Appointments by Dates**


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, username, password, domain);

SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
Date startTime = sdf.parse("15/09/2017 00:00:00");
Date endTime = sdf.parse("10/10/2017 00:00:00");
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getAppointment().getStart().since(startTime);
builder.getAppointment().getEnd().beforeOrEqual(endTime);
MailQuery query = builder.getQuery();
Appointment[] appointments = client.listAppointments(query);
~~~
### **Filtering Appointments by Recurring Events**


~~~Java
builder = new ExchangeQueryBuilder();
builder.getAppointment().isRecurring().equals(false);
query = builder.getQuery();
appointments = client.listAppointments(query);
~~~