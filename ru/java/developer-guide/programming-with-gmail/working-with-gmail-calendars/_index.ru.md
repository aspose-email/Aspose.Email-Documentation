---
title: "Работа с календарями Gmail"
url: /ru/java/working-with-gmail-calendars/
weight: 20
type: docs
---


## **Добавление, редактирование и удаление календаря**
Aspose.Email позволяет приложениям управлять календарями Gmail с помощью [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) который предоставляет такие функции, как добавление, удаление и обновление календарей Gmail. Этот клиентский класс возвращает список объектов типа ExtendedCalendar, содержащих информацию об элементах календаря Gmail. [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) класс предоставляет следующие функции для календарей:

- [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\))
  Чтобы вставить новый календарь
- [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\))

Получите список всех календарей клиента

- [deleteCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteCalendar\(java.lang.String\))
  Его можно использовать для удаления календаря
- [fetchCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchCalendar\(java.lang.String\))
  Его можно использовать для получения определенного календаря клиента
- [updateCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateCalendar\(com.aspose.email.Calendar\))
  Эта функция используется для вставки измененного календаря клиента

Чтобы получить доступ к календарям, GoogleTestUser инициализируется с использованием учетных данных учетной записи gmail. GoogleOAuthHelper используется для получения токена доступа для пользователя, который в дальнейшем используется для инициализации [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient).
### **Вставка, загрузка и обновление**
Для вставки календаря инициализируйте [Calendar](https://apireference.aspose.com/email/java/com.aspose.email/Calendar) введите объект и вставьте его, используя [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) function. [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) возвращает идентификатор только что вставленного календаря. Этот идентификатор можно использовать для загрузки календаря с сервера. В следующем фрагменте кода показано, как вставлять, извлекать и обновлять календарь.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Insert, get and update calendar
    Calendar calendar = new Calendar("Summary", "Description", "Location", "America/Los_Angeles");

    // Insert calendar and Retrieve same calendar using id
    String id = client.createCalendar(calendar);
    Calendar cal = client.fetchCalendar(id);

    // Change information in the fetched calendar and Update calendar
    cal.setDescription("New Description");
    cal.setLocation("New Location");
    client.updateCalendar(cal);
}
~~~
### **Удалить определенный календарь**
Чтобы удалить определенный календарь, нам нужно получить список всех календарей клиента, а затем удалить его при необходимости. [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\)) возвращает список [ExtendedCalendar](https://apireference.aspose.com/email/java/com.aspose.email/ExtendedCalendar) который содержит календари Gmail. В следующем фрагменте кода показано, как удалить определенный календарь.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Access and delete calendar with summary starting from "Calendar summary"
    String summary = "Calendar summary";

    // Get calendars list
    ExtendedCalendar[] lst = client.listCalendars();

    for (ExtendedCalendar extCal : lst) {
        // Delete selected calendars
        if (extCal.getSummary().startsWith(summary))
            client.deleteCalendar(extCal.getId());
    }
}
~~~
## **Работа с контролем доступа к календарю**
Aspose.Email обеспечивает полный контроль доступа к элементам календаря. [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\)) функция раскрывается [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) который возвращает список [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule). Информация об отдельных правилах может быть извлечена, изменена и сохранена в календаре клиента. [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) содержит следующие функции для управления правилами контроля доступа.

- [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\))
  Эта функция предоставляет список [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule)
- [createAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Эта функция создает новое правило доступа к календарю.
- [updateAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Эта функция используется для обновления правила доступа.
- [fetchAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAccessRule\(java.lang.String,%20java.lang.String\))
  Его можно использовать для получения определенного правила доступа к календарю клиента.
- [deleteAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAccessRule\(java.lang.String,%20java.lang.String\))
  Эта функция используется для удаления правила доступа.

В следующем фрагменте кода показано, как используются функции для управления правилами доступа:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Retrieve list of calendars for the current client
    ExtendedCalendar[] calendarList = client.listCalendars();

    // Get first calendar id and retrieve list of AccessControlRule for the first calendar
    String calendarId = calendarList[0].getId();
    AccessControlRule[] roles1 = client.listAccessRules(calendarId);

    // Create a local access control rule and Set rule properties
    AccessControlRule rule = new AccessControlRule();
    rule.setRole(AccessRole.reader);
    rule.setScope(new AclScope(AclScopeType.user, email2));

    // Insert new rule for the calendar. It returns the newly created rule
    AccessControlRule createdRule = client.createAccessRule(calendarId, rule);

    // Get list of rules
    AccessControlRule[] roles2 = client.listAccessRules(calendarId);

    // Current list length should be 1 more than the earlier one
    if (roles1.length + 1 == roles2.length) {
        System.out.println("List lengths are ok");
    } else {
        System.out.println("List lengths are not ok");
        return;
    }

    // Change rule and Update the rule for the selected calendar
    createdRule.setRole(AccessRole.writer);
    AccessControlRule updatedRule = client.updateAccessRule(calendarId, createdRule);

    // Retrieve individaul rule against a calendar
    AccessControlRule fetchedRule = client.fetchAccessRule(calendarId, createdRule.getId());

    // Delete particular rule against a given calendar and Retrieve the all rules list for the same calendar
    client.deleteAccessRule(calendarId, createdRule.getId());
    AccessControlRule[] roles3 = client.listAccessRules(calendarId);

    // Check that current rules list length should be equal to the original list length before adding and deleting the rule
    if (roles1.length == roles3.length) {
        System.out.println("List lengths are same");
    } else {
        System.out.println("List lengths are not equal");
        return;
    }
}
~~~
## **Работа с настройками клиента и информацией о цвете**
Aspose.Email поддерживает доступ к настройкам клиента с помощью [IGmailClient.getSettings](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getSettings\(\)). Он возвращает список настроек, как указано ниже:

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

Аналогичным образом, информацию о цвете для клиентов также можно получить с помощью [IGmailClient.getColors](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getColors\(\)). Этот информационный объект цвета возвращает список цветов переднего плана, цветов фона, а также дату и время обновления.
### **Доступ к настройкам клиента**
В следующем фрагменте кода показано, как используются функции для доступа к настройкам клиента:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Retrieve client settings
    Dictionary<String, String> settings = client.getSettings();
    if (settings.size() < 1) {
        System.out.println("No settings are available.");
        return;
    }

    // Traverse the settings list
    for (KeyValuePair<String, String> pair : settings) {
        // Get the setting value and test if settings are ok
        String value = client.getSetting(pair.getKey());
        if (pair.getValue().equals(value)) {
            System.out.println("Key = " + pair.getKey() + ", Value = " + pair.getValue());
        } else {
            System.out.println("Settings could not be retrieved");
        }
    }
}
~~~
### **Доступ к информации о цвете**
В следующем фрагменте кода показано, как используются функции для доступа к цветовым настройкам клиента.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    ColorsInfo colors = client.getColors();
    Dictionary<String, Colors> palettes = colors.getCalendar();

    // Traverse the settings list
    for (KeyValuePair<String, Colors> pair : palettes) {
        System.out.println("Key = " + pair.getKey() + ", Color = " + pair.getValue());
    }
    System.out.println("Update Date = " + colors.getUpdated());
}
~~~
## **Работа с назначениями**
Aspose.Email предоставляет функции для работы с [Appointments](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) в календарях Google. Ниже приведен список задач, которые можно выполнять на встречах в календаре Google:

1. Добавить встречи - [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAppointment\(java.lang.String,%20com.aspose.email.Appointment\)), [importAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#importAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Получить список встреч - [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointments\(java.lang.String\))
1. Запишитесь на конкретную встречу - [fetchAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAppointment\(java.lang.String,%20java.lang.String\)), [listAppointmentInstances](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointmentInstances\(java.lang.String,%20java.lang.String\))
1. Обновить запись на прием - [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Перенести встречу из одного календаря в другой - [moveAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#moveAppointment\(java.lang.String,%20java.lang.String,%20java.lang.String\))
1. Удалить встречу - [deleteAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAppointment\(java.lang.String,%20java.lang.String\))

### **Добавление встречи**
Следующий пример кода демонстрирует возможность добавления встречи в календарь. В этом примере выполняются следующие шаги:

1. Создайте и вставьте календарь.
1. Извлеките список встреч из нового календаря.
1. Назначьте встречу.
1. Укажите встречу.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Create local calendar
    Calendar calendar1 = new Calendar("Summary", null, null, "Europe/Kiev");

    // Insert calendar and get id of inserted calendar and Get back calendar using an id
    String id = client.createCalendar(calendar1);
    Calendar cal1 = client.fetchCalendar(id);
    String calendarId1 = cal1.getId();

    try {
        // Retrieve list of appointments from the first calendar
        Appointment[] appointments = client.listAppointments(calendarId1);
        if (appointments.length > 0) {
            System.out.println("Wrong number of appointments");
            return;
        }

        // Get current time and Calculate time after an hour from now
        java.util.Calendar c = java.util.Calendar.getInstance();
        Date startDate = c.getTime();
        c.add(java.util.Calendar.HOUR_OF_DAY, 1);
        Date endDate = c.getTime();

        // Initialize a mail address collection and set attendees mail address
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.add("User1.EMail@domain.com");
        attendees.add("User3.EMail@domain.com");

        // Create an appointment with above attendees
        Appointment app1 = new Appointment("Location", startDate, endDate, MailAddress.to_MailAddress(email2), attendees);

        // Set appointment summary, description, start/end time zone
        app1.setSummary("New Summary");
        app1.setDescription("New Description");
        app1.setStartTimeZone("Europe/Kiev");
        app1.setEndTimeZone("Europe/Kiev");

        // Insert appointment in the first calendar inserted above and get back inserted appointment
        Appointment app2 = client.createAppointment(calendarId1, app1);

        // Retrieve appointment using unique id
        Appointment app3 = client.fetchAppointment(calendarId1, app2.getUniqueId());
    } catch (Exception ex) {
        System.err.println(ex);
    }
   
}
~~~
### **Запросить и обновить запись**
Здесь извлечение и обновление календаря демонстрируется следующим образом:

1. Запишитесь на определенную встречу.
1. Измените встречу.
1. Обновите встречу в календаре.

Предполагается, что календарь с идентификатором «CalendarID» и уникальным идентификатором встречи «AppointmentUniqueID» уже извлечены. В следующем фрагменте кода показано, как восстановить и обновить встречу.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String calendarId = client.listCalendars()[0].getId();
    String AppointmentUniqueId = client.listAppointments(calendarId)[0].getUniqueId();

    // Retrieve Appointment
    Appointment app3 = client.fetchAppointment(calendarId, AppointmentUniqueId);
    // Change the appointment information
    app3.setSummary("New Summary");
    app3.setDescription("New Description");
    app3.setLocation("New Location");
    app3.setFlags(AppointmentFlags.AllDayEvent);
    java.util.Calendar c = java.util.Calendar.getInstance();
    c.add(java.util.Calendar.HOUR_OF_DAY, 2);
    app3.setStartDate(c.getTime());
    c.add(java.util.Calendar.HOUR_OF_DAY, 1);
    app3.setEndDate(c.getTime());
    app3.setStartTimeZone("Europe/Kiev");
    app3.setEndTimeZone("Europe/Kiev");
    // Update the appointment and get back updated appointment
    Appointment app4 = client.updateAppointment(calendarId, app3);
}
~~~
### **Переместить и удалить встречу**
[Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) можно переместить, указав исходный календарь, календарь назначения и уникальный идентификатор встречи в исходном календаре. В следующем фрагменте кода показано, как перемещать и удалять встречу.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String SourceCalendarId = client.listCalendars()[0].getId();
    String DestinationCalendarId = client.listCalendars()[1].getId();
    String TargetAppUniqueId = client.listAppointments(SourceCalendarId)[0].getUniqueId();

    // Retrieve the list of appointments in the destination calendar before moving the appointment
    Appointment[] appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Before moving count = " + appointments.length);
    Appointment Movedapp = client.moveAppointment(SourceCalendarId, DestinationCalendarId, TargetAppUniqueId);

    // Retrieve the list of appointments in the destination calendar after moving the appointment
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("After moving count = " + appointments.length);

    // Delete particular appointment from a calendar using unique id
    client.deleteAppointment(DestinationCalendarId, Movedapp.getUniqueId());

    // Retrieve the list of appointments. It should be one less than the earlier appointments in the destination calendar
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("After deleting count = " + appointments.length);
}
~~~
