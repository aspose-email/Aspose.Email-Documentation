---
title: "Filtrar Citas desde el Servidor de Exchange"
url: /es/java/filter-appointments-from-exchange-server/
weight: 130
type: docs
---


## **Filtrando Citas con EWS**
El [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) proporciona la facilidad de filtrar citas desde el servidor de Exchange utilizando el [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Las citas se pueden filtrar en función de:

- Fechas
- Recurrencias
### **Filtrando Citas por Fechas**


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
### **Filtrando Citas por Eventos Recurrentes**


~~~Java
builder = new ExchangeQueryBuilder();
builder.getAppointment().isRecurring().equals(false);
query = builder.getQuery();
appointments = client.listAppointments(query);
~~~