---
title: "Filtrar citas de Exchange Server"
url: /es/java/filter-appointments-from-exchange-server/
weight: 130
type: docs
---


## **Filtrado de citas con EWS**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) proporciona la posibilidad de filtrar las citas del servidor de Exchange mediante el [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Las citas se pueden filtrar en función de:

- Dates
- Recurrences
### **Filtrar citas por fechas**


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
### **Filtrar citas por eventos recurrentes**


~~~Java
builder = new ExchangeQueryBuilder();
builder.getAppointment().isRecurring().equals(false);
query = builder.getQuery();
appointments = client.listAppointments(query);
~~~