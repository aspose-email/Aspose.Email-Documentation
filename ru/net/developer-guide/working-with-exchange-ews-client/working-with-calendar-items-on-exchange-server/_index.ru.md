---
title: "Работа с элементами календаря на сервере Exchange"
url: /ru/net/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---


## **Отправка приглашений на собрание**

В этой статье показано, как отправить приглашение на собрание нескольким получателям с помощью веб-служб Exchange и Aspose.Email.

1. Создайте приглашение на собрание, используя [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) класс и определите место, время и участников.
1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс и назначьте встречу, используя [MailMessage.AddAlternateView()](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/#addalternateview) method.
1. Подключитесь к серверу Exchange и отправьте приглашение на собрание, используя [Send(MailMessage)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/#send) method.

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс можно использовать для подключения к серверу Exchange с поддержкой веб-служб Exchange (EWS). Чтобы это работало, необходимо использовать сервер Exchange Server 2007 или более поздней версии. В следующем фрагменте кода показано, как использовать EWS для отправки приглашений на собрание.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cs" >}}

## **Работа с элементами календаря с помощью EWS**

Aspose.Email предоставляет возможность добавлять, обновлять и отменять встречи с помощью клиента Exchange Web Service (EWS). Клиент IEWS [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/), и [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) методы позволяют манипулировать элементами календаря с помощью EWS. В этой статье представлен подробный пример кода работы с элементами календаря. В следующем примере кода показано, как:

1. Назначьте встречу.
1. Обновите встречу.
1. Удалить/отменить встречу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cs" >}}

## **Составление списков встреч с помощью пейджинговой поддержки**

Метод listAppointments, представленный [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) API получает полный список встреч с сервера Exchange. Если на сервере Exchange много встреч, это может занять некоторое время. API предоставляет перегруженные методы [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listappointments/#listappointments/) метод, обеспечивающий пейджинговую поддержку операции. Его также можно использовать в различных комбинациях с функцией запросов. Доступны следующие перегруженные методы для списка встреч с Exchange Server с поддержкой пейджинга.

- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

В следующем фрагменте кода показано, как составить список встреч с поддержкой пейджинга.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cs" >}}

## **Добавление события в папку дополнительного календаря на сервере Exchange**

API Aspose.Email позволяет создать дополнительную папку календаря на сервере Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Затем встречи можно добавлять, обновлять или отменять из дополнительного календаря, используя [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) and [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) методы. Следующие методы и свойства API используются в приведенных ниже примерах кода для демонстрации функциональности этой функции. Обратите внимание, что эта функция поддерживается Aspose.Email для версии .NET 6.5.0 и выше.

- Method `IEWSClient.CancelAppointment(Appointment, String)`.
- Method `IEWSClient.CancelAppointment(String, String)`.
- Method `IEWSClient.CreateAppointment(Appointment, String)`.
- Method `IEWSClient.CreateFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Method `IEWSClient.FetchAppointment(String, String)`.
- Method `IEWSClient.UpdateAppointment(Appointment, String)`.
- Property `IEWSClient.CurrentCalendarFolderUri`.

В следующем фрагменте кода показано, как добавить событие во дополнительную папку календаря на сервере Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cs" >}}

## **Приглашение поделиться календарем**

Сервер Microsoft Exchange предоставляет возможность совместного использования календарей, отправляя приглашения в календарь другим пользователям, зарегистрированным на том же сервере Exchange. API Aspose.Email предоставляет ту же возможность, позволяя делиться календарем с помощью API EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cs" >}}

## **Получение информации о дополнительных атрибутах из элементов календаря**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cs" >}}

## **Возврат повторяющихся элементов календаря в указанный диапазон дат**

[EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) поддерживает возврат повторяющихся элементов календаря в диапазоне, указанном в параметрах StartDate и EndDate. [AppointmentQueryBuilder.SetCalendarView](https://reference.aspose.com/email/net/aspose.email.clients.exchange/appointmentquerybuilder/setcalendarview/) метод используется для определения определенного диапазона дат и ограничения количества возвращенных встреч для получения соответствующей информации. Задав следующие параметры, вы можете получить встречи, соответствующие указанным критериям.

- StartDate: дата начала просмотра календаря. Встречи, начинающиеся с этой даты, будут включены в результат запроса.

- EndDate: дата окончания просмотра календаря. Встречи, закончившиеся до или в эту дату, будут включены в результат запроса.

- MaxEntriesReturned: максимальное количество встреч, возвращаемых в результате запроса. Значение -1 означает, что нет определенного ограничения.

```cs
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.Appointment.SetCalendarView(DateTime.Now, DateTime.Now.AddMonths(1), -1);

Appointment[] appointments = client.ListAppointments(builder.GetQuery());
```
