---
title: "Filtrar Compromissos do Exchange Server"
url: /pt/java/filter-appointments-from-exchange-server/
weight: 130
type: docs
---


## **Filtrando Compromissos com EWS**
O [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) oferece a possibilidade de filtrar compromissos do servidor Exchange usando o [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Os compromissos podem ser filtrados com base em:

- Datas
- Recorrências
### **Filtrando Compromissos por Datas**


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
### **Filtrando Compromissos por Eventos Recorrentes**


~~~Java
builder = new ExchangeQueryBuilder();
builder.getAppointment().isRecurring().equals(false);
query = builder.getQuery();
appointments = client.listAppointments(query);
~~~