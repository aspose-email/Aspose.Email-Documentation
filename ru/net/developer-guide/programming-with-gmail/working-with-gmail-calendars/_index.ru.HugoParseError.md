---
title: Работа с календарями Gmail
type: docs
weight: 20
url: /net/working-with-gmail-calendars/
---


## **Добавление, редактирование и удаление календаря**

Aspose.Email позволяет приложениям управлять календарями Gmail с помощью [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/), который предоставляет такие функции, как добавление, удаление и обновление календарей Gmail. Этот класс клиента возвращает список объектов типа ExtendedCalendar, которые содержат информацию о элементах календаря Gmail. Класс [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) предоставляет следующие функции для работы с календарями:

- [CreateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) 
  Его можно использовать для добавления нового календаря
- [ListCalendars](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/)
  Его можно использовать для получения списка всех календарей клиента
- [DeleteCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecalendar/)
  Его можно использовать для удаления календаря
- [FetchCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchcalendar/)
  Его можно использовать для получения конкретного календаря клиента
- [UpdateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updatecalendar/)
  Эта функция используется для повторного добавления измененного календаря клиента

Для доступа к календарям GoogleTestUser инициализируется с использованием учетных данных gmail. GoogleOAuthHelper используется для получения токена доступа для пользователя, который затем используется для инициализации IGmailClient.

### **Вставка, получение и обновление**

Для добавления календаря инициализируйте объект типа Calendar и вставьте его с помощью функции [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar). [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) возвращает id новосозданного календаря. Этот id можно использовать для получения календаря с сервера. Следующий фрагмент кода показывает, как вставить, получить и обновить календарь.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-InsertFetchAndUpdateCalendar-InsertFetchAndUpdateCalendar.cs" >}}

### **Удаление конкретного календаря**

Для удаления конкретного календаря необходимо получить список всех календарей клиента, а затем удалить по мере необходимости. [ListCalendars()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/#listcalendars) возвращает список [ExtendedCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/extendedcalendar/), который содержит календари Gmail. Следующий фрагмент кода показывает, как удалить конкретный календарь.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteParticularCalendar-DeleteParticularCalendar.cs" >}}

## **Работа с управлением доступом к календарю**

Aspose.Email обеспечивает полный контроль над доступом к элементам календаря. Функция [ListAccessRules()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/) доступна через [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/), которая возвращает список [AccessControlRule](https://reference.aspose.com/email/net/aspose.email.clients.google/accesscontrolrule/). Индивидуальная информация о правилах может быть извлечена, изменена и сохранена обратно для календаря клиента. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) содержит следующие функции для управления правилами доступа.

- [ListAccessRules](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/)
  Эта функция предоставляет список AccessControlRule
- [CreateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createaccessrule/)
  Эта функция создает новое правило доступа для календаря.
- [UpdateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateaccessrule/)
  Эта функция используется для обновления правила доступа.
- [FetchAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchaccessrule/)
  Его можно использовать для получения конкретного правила доступа для календаря клиента
- [DeleteAccessRule](https://search.aspose.com/q/deleteaccessrule.html)
  Эта функция используется для удаления правила доступа.

Следующий фрагмент кода показывает, как использовать функции для управления правилами доступа:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-ManageAccessRule-ManageAccessRule.cs" >}}

## **Работа с настройками клиента и цветовой информацией**

Aspose.Email поддерживает доступ к настройкам клиента с помощью [IGmailClient.GetSettings()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getsettings/#igmailclientgetsettings-method). Он возвращает список настроек, указанных ниже:

1. dateFieldOrder
1. displayAllTimezones
1. hideInvitations
1. format24HourTime
1. defaultCalendarMode
1. defaultEventLength
1. locale
1. remindOnRespondedEventsOnly
1. alternateCalendar
1. userLocation
1. hideWeekends
1. showDeclinedEvents
1. weekStart
1. weather
1. customCalendarMode
1. timezoneLabel
1. timezone
1. useKeyboardShortcuts
1. country

Аналогично, цветовая информация для клиентов также может быть извлечена с помощью [IGmailClient.GetColors()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getcolors/#igmailclientgetcolors-method). Этот объект цветовой информации возвращает список цветов переднего плана, цветов фона и даты и времени обновления.

### **Доступ к настройкам клиента**

Следующий фрагмент кода показывает, как можно использовать функции для доступа к настройкам клиента:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessClientSettings-AccessClientSettings.cs" >}}

### **Доступ к цветовой информации**

Следующий фрагмент кода показывает, как можно использовать функции для доступа к настройкам цвета клиента.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessColorInfo-AccessColorInfo.cs" >}}

## **Работа с встречами**

Aspose.Email предоставляет функции для работы с встречами в календарях Google. Следующий список задач, которые можно выполнить с встречами в календаре Google:

1. Добавить встречи.
1. Получить список встреч.
1. Получить конкретную встречу.
1. Обновить встречу.
1. Переместить встречу из одного календаря в другой.
1. Удалить встречу.

[IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) предоставляет функции, такие как [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createappointment/#igmailclientcreateappointment-method), [FetchAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchappointment/#igmailclientfetchappointment-method), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateappointment/#igmailclientupdateappointment-method), [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listappointments/#igmailclientlistappointments-method), [MoveAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/moveappointment/#moveappointment) и [DeleteAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deleteappointment/#igmailclientdeleteappointment-method).

### **Добавление встречи**

Следующий пример кода демонстрирует функцию добавления встречи в календарь. Для этого выполните следующие шаги:

1. Создайте и вставьте календарь.
1. Получите список встреч из нового календаря.
1. Создайте встречу.
1. Вставьте встречу.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AddingAnAppointment-AddingAnAppointment.cs" >}}

### **Получение и обновление встречи**

Здесь демонстрируется получение и обновление календаря следующим образом:

1. Извлеките конкретную встречу.
1. Измените встречу.
1. Обновите встречу в календаре.

Предполагается, что календарь с id "calendarId" и уникальный идентификатор встречи "AppointmentUniqueId" уже извлечены. Следующий фрагмент кода показывает, как получить и обновить встречу.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-RetrieveUpdateAppointment-RetrieveUpdateAppointment.cs" >}}

### **Перемещение и удаление встречи**

Встречу можно переместить, указав исходный календарь, целевой календарь и уникальный идентификатор встречи в исходном календаре. Следующий фрагмент кода показывает, как переместить и удалить встречу.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-MoveAndDeleteAppointment-MoveAndDeleteAppointment.cs" >}}