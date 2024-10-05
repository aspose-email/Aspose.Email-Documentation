---
title: Фильтрация встреч с Exchange Server
type: docs
weight: 130
url: /java/filter-appointments-from-exchange-server/
---


## **Фильтрация встреч с помощью EWS**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) предоставляет возможность фильтровать встречи с Exchange сервера с использованием [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Встречи могут быть отфильтрованы по следующим критериям:

- Даты
- Повторяющиеся события
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