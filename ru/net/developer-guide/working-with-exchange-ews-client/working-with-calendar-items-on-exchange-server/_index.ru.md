---
title: "Работа с элементами календаря на Exchange Server"
url: /ru/net/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---


## **Отправка запросов на встречу**

В этой статье показано, как отправить запрос на встречу нескольким получателям с помощью Exchange Web Services и Aspose.Email.

1. Создайте запрос на встречу, используя класс [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/), и укажите местоположение, время и участников.
1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и установите встречу с помощью метода [MailMessage.AddAlternateView()](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/#addalternateview).
1. Подключитесь к Exchange Server и отправьте запрос на встречу, используя метод [Send(MailMessage)](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/#send).

Класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) можно использовать для подключения к Exchange Server с поддержкой Exchange Web Services (EWS). Для этого сервер должен быть Exchange Server 2007 или более поздней версии. Следующий фрагмент кода показывает, как использовать EWS для отправки запросов на встречу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cs" >}}

## **Работа с элементами календаря с использованием EWS**

Aspose.Email предоставляет возможность добавлять, обновлять и отменять встречи с помощью клиента Exchange Web Service (EWS). Методы IEWSClient [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) и [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/) позволяют управлять элементами календаря с использованием EWS. В этой статье приведен подробный пример кода для работы с элементами календаря. Следующий пример кода показывает, как:

1. Создать встречу.
1. Обновить встречу.
1. Удалить/Отменить встречу.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cs" >}}

## **Список встреч с поддержкой пагинации**

Метод ListAppointments, предоставляемый API [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/), извлекает полный список встреч с Exchange сервера. Это может занять время, если на Exchange Server имеется большое количество встреч. API предоставляет перегруженные методы метода [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listappointments/#listappointments/), которые обеспечивают поддержку пагинации для данной операции. Это можно использовать в различных комбинациях с функцией запросов. Следующие перегруженные методы доступны для перечисления встреч с Exchange Server с поддержкой пагинации.

- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage)`.
- `AppointmentCollection IEWSClient.ListAppointments(int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(MailQuery query, int itemsPerPage, int itemOffset)`.
- `AppointmentCollection IEWSClient.ListAppointments(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`.

Следующий фрагмент кода показывает, как перечислить встречи с поддержкой пагинации.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cs" >}}

## **Добавление события во вторичный календарь на Exchange Server**

API Aspose.Email позволяет вам создать вторичный каталог календаря на Exchange Server с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Встречи можно добавлять, обновлять или отменять из вторичного календаря с использованием методов [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createappointment/#createappointment/), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateappointment/#updateappointment/) и [CancelAppointment](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/cancelappointment/#cancelappointment/). В следующих примерах кода используются методы и свойства API, чтобы продемонстрировать функциональность этой функции. Обратите внимание, что эта функция поддерживается в Aspose.Email для .NET начиная с версии 6.5.0.

- Метод `IEWSClient.CancelAppointment(Appointment, String)`.
- Метод `IEWSClient.CancelAppointment(String, String)`.
- Метод `IEWSClient.CreateAppointment(Appointment, String)`.
- Метод `IEWSClient.CreateFolder(String, String, ExchangeFolderPermissionCollection, String)`.
- Метод `IEWSClient.FetchAppointment(String, String)`.
- Метод `IEWSClient.UpdateAppointment(Appointment, String)`.
- Свойство `IEWSClient.CurrentCalendarFolderUri`.

Следующий фрагмент кода показывает, как добавить событие во вторичный календарь на Exchange Server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cs" >}}

## **Обмен приглашениями на календарь**

Сервер Microsoft Exchange предоставляет возможность делиться календарями, отправляя приглашения на календарь другим пользователям, зарегистрированным на том же сервере Exchange. API Aspose.Email предоставляет ту же возможность, позволяя делиться календарем с использованием API EWS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cs" >}}

## **Получение информации о расширенных атрибутах из элементов календаря**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cs" >}}

## **Возврат повторяющихся элементов календаря в заданном диапазоне дат**

[EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) поддерживает возврат повторяющихся элементов календаря в диапазоне, заданном параметрами StartDate и EndDate. Метод [AppointmentQueryBuilder.SetCalendarView](https://reference.aspose.com/email/net/aspose.email.clients.exchange/appointmentquerybuilder/setcalendarview/) используется для определения конкретного диапазона дат и ограничения количества возвращаемых встреч для получения соответствующей информации. Установив следующие параметры, вы можете получить встречи, соответствующие указанным критериям.

- startDate: Дата начала календарного представления. Встречи, начинающиеся с этой даты, будут включены в результат запроса.

- endDate: Дата окончания календарного представления. Встречи, заканчивающиеся до этой даты или в этот день, будут включены в результат запроса.

- maxEntriesReturned: Максимальное количество встреч, которые будут возвращены в результате запроса. Значение -1 указывает на то, что нет конкретного ограничения.

```cs
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.Appointment.SetCalendarView(DateTime.Now, DateTime.Now.AddMonths(1), -1);

Appointment[] appointments = client.ListAppointments(builder.GetQuery());
```