---
title: "Фильтрация встреч с сервера Exchange"
url: /ru/java/filter-appointments-from-exchange-server/
weight: 130
type: docs
---


## **Фильтрация встреч с помощью EWS**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) предоставляет возможность фильтровать встречи с сервера Exchange с помощью [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Встречи можно отфильтровать по следующим критериям:

- Dates
- Recurrences
### **Фильтрация встреч по датам**


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
### **Фильтрация встреч по повторяющимся событиям**


~~~Java
builder = new ExchangeQueryBuilder();
builder.getAppointment().isRecurring().equals(false);
query = builder.getQuery();
appointments = client.listAppointments(query);
~~~