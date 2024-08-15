---
title: "Работа с календарями Gmail"
url: /ru/net/working-with-gmail-calendars/
weight: 20
type: docs
---


## **Добавление, редактирование и удаление календаря**

Aspose.Email позволяет приложениям управлять календарями Gmail с помощью [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) который предоставляет такие функции, как добавление, удаление и обновление календарей Gmail. Этот клиентский класс возвращает список объектов типа ExtendedCalendar, содержащих информацию об элементах календаря Gmail. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) класс предоставляет следующие функции для календарей:

- [CreateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar)
  Его можно использовать для вставки нового календаря
- [ListCalendars](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/)
  Его можно использовать для получения списка всех календарей клиента
- [DeleteCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecalendar/)
  Его можно использовать для удаления календаря
- [FetchCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchcalendar/)
  Его можно использовать для получения определенного календаря клиента
- [UpdateCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updatecalendar/)
  Эта функция используется для обратной вставки измененного календаря клиента.

Чтобы получить доступ к календарям, GoogleTestUser инициализируется с использованием учетных данных учетной записи gmail. GoogleOAuthHelper используется для получения токена доступа для пользователя, который в дальнейшем используется для инициализации IGMailClient.

### **Вставка, загрузка и обновление**

Для вставки календаря инициализируйте объект типа Calendar и вставьте его с помощью [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) function. [CreateCalendar()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createcalendar/#createcalendar) возвращает идентификатор только что вставленного календаря. Этот идентификатор можно использовать для загрузки календаря с сервера. В следующем фрагменте кода показано, как вставлять, извлекать и обновлять календарь.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-InsertFetchAndUpdateCalendar-InsertFetchAndUpdateCalendar.cs" >}}

### **Удалить определенный календарь**

Чтобы удалить определенный календарь, нам нужно получить список всех календарей клиента, а затем удалить его при необходимости. [ListCalendars()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listcalendars/#listcalendars) возвращает список [ExtendedCalendar](https://reference.aspose.com/email/net/aspose.email.clients.google/extendedcalendar/) который содержит календари Gmail. В следующем фрагменте кода показано, как удалить определенный календарь.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteParticularCalendar-DeleteParticularCalendar.cs" >}}

## **Работа с контролем доступа к календарю**

Aspose.Email обеспечивает полный контроль над доступом к элементам календаря. [ListAccessRules()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/) функция раскрывается [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) который возвращает список [AccessControlRule](https://reference.aspose.com/email/net/aspose.email.clients.google/accesscontrolrule/). Информация об отдельных правилах может быть извлечена, изменена и сохранена в календаре клиента. [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) содержит следующие функции для управления правилами управления доступом.

- [ListAccessRules](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listaccessrules/)
  Эта функция предоставляет список AccessControlRule
- [CreateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createaccessrule/)
  Эта функция создает новое правило доступа к календарю.
- [UpdateAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateaccessrule/)
  Эта функция используется для обновления правила доступа.
- [FetchAccessRule](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchaccessrule/)
  Его можно использовать для получения определенного правила доступа к календарю клиента.
- [DeleteAccessRule](https://search.aspose.com/q/deleteaccessrule.html)
  Эта функция используется для удаления правила доступа.

В следующем фрагменте кода показано, как использовать функции для управления правилами доступа:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-ManageAccessRule-ManageAccessRule.cs" >}}

## **Работа с настройками клиента и информацией о цвете**

Aspose.Email поддерживает доступ к настройкам клиента с помощью [IGmailClient.GetSettings()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getsettings/#igmailclientgetsettings-method). Он возвращает список настроек, как указано ниже:

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

Аналогичным образом, информацию о цвете для клиентов также можно получить с помощью [IGmailClient.GetColors()](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/getcolors/#igmailclientgetcolors-method). Этот информационный объект цвета возвращает список цветов переднего плана, цветов фона, а также дату и время обновления.

### **Доступ к настройкам клиента**

В следующем фрагменте кода показано, как эти функции можно использовать для доступа к настройкам клиента:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessClientSettings-AccessClientSettings.cs" >}}

### **Доступ к информации о цвете**

В следующем фрагменте кода показано, как эти функции можно использовать для доступа к цветовым настройкам клиента.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessColorInfo-AccessColorInfo.cs" >}}

## **Работа с назначениями**

Aspose.Email предоставляет функции для работы с встречами в календарях Google. Ниже приведен список задач, которые можно выполнять на встречах в календаре Google:

1. Добавьте встречи.
1. Получите список встреч.
1. Запишитесь на определенную встречу.
1. Обновите встречу.
1. Перенесите встречу из одного календаря в другой.
1. Удалить встречу.

[IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) предоставляет такие функции, как [CreateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/createappointment/#igmailclientcreateappointment-method), [FetchAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/fetchappointment/#igmailclientfetchappointment-method), [UpdateAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/updateappointment/#igmailclientupdateappointment-method), [ListAppointments](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/listappointments/#igmailclientlistappointments-method), [MoveAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/moveappointment/#moveappointment) and [DeleteAppointment](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deleteappointment/#igmailclientdeleteappointment-method).

### **Добавление встречи**

В следующем примере кода показана возможность добавления встречи в календарь. Для этого выполните следующие действия:

1. Создайте и вставьте календарь.
1. Извлеките список встреч из нового календаря.
1. Назначьте встречу.
1. Укажите встречу.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AddingAnAppointment-AddingAnAppointment.cs" >}}

### **Загрузка и обновление записи**

Здесь извлечение и обновление календаря демонстрируется следующим образом:

1. Запишитесь на определенную встречу.
1. Измените встречу.
1. Обновите встречу в календаре.

Предполагается, что календарь с идентификатором «CalendarID» и уникальным идентификатором встречи «AppointmentUniqueID» уже извлечены. В следующем фрагменте кода показано, как восстановить и обновить запись о встрече.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-RetrieveUpdateAppointment-RetrieveUpdateAppointment.cs" >}}

### **Переместить и удалить встречу**

Встречу можно перенести, указав исходный календарь, календарь назначения и уникальный идентификатор встречи в исходном календаре. В следующем фрагменте кода показано, как перенести и удалить встречу.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-MoveAndDeleteAppointment-MoveAndDeleteAppointment.cs" >}}
