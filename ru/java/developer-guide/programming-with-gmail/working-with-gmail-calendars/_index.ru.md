---
title: "Работа с календарями Gmail"
url: /ru/java/working-with-gmail-calendars/
weight: 20
type: docs
---


## **Добавление, редактирование и удаление календаря**
Aspose.Email позволяет приложениям управлять календарями Gmail с использованием [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), который предоставляет такие функции, как добавление, удаление и обновление календарей Gmail. Этот класс клиента возвращает список объектов типа ExtendedCalendar, которые содержат информацию о элементах календаря Gmail. Класс [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) предоставляет следующие функции для работы с календарями:

- [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\))
  Для вставки нового календаря
- [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\))

Получить список всех календарей клиента

- [deleteCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteCalendar\(java.lang.String\))
  Может быть использован для удаления календаря
- [fetchCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchCalendar\(java.lang.String\))
  Может быть использован для получения конкретного календаря клиента
- [updateCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateCalendar\(com.aspose.email.Calendar\))
  Эта функция используется для вставки обратно измененного календаря клиента

Для доступа к календарям GoogleTestUser инициализируется с использованием учетных данных gmail-аккаунта. GoogleOAuthHelper используется для получения токена доступа для пользователя, который далее используется для инициализации [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient).
### **Вставка, получение и обновление**
Для вставки календаря инициализируйте объект типа [Calendar](https://apireference.aspose.com/email/java/com.aspose.email/Calendar) и вставьте его с помощью функции [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)). [createCalendar](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createCalendar\(com.aspose.email.Calendar\)) возвращает идентификатор вновь вставленного календаря. Этот идентификатор может быть использован для получения календаря с сервера. Следующий фрагмент кода демонстрирует, как вставить, получить и обновить календарь.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Вставить, получить и обновить календарь
    Calendar calendar = new Calendar("Summary", "Description", "Location", "America/Los_Angeles");

    // Вставить календарь и получить тот же календарь по идентификатору
    String id = client.createCalendar(calendar);
    Calendar cal = client.fetchCalendar(id);

    // Изменить информацию в полученном календаре и обновить календарь
    cal.setDescription("New Description");
    cal.setLocation("New Location");
    client.updateCalendar(cal);
}
~~~
### **Удаление конкретного календаря**
Чтобы удалить конкретный календарь, нужно получить список всех календарей клиента и затем удалить по мере необходимости. [listCalendars](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listCalendars\(\)) возвращает список [ExtendedCalendar](https://apireference.aspose.com/email/java/com.aspose.email/ExtendedCalendar), который содержит календари Gmail. Следующий фрагмент кода демонстрирует, как удалить конкретный календарь.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Получить доступ и удалить календарь с описанием, начинающимся с "Calendar summary"
    String summary = "Calendar summary";

    // Получить список календарей
    ExtendedCalendar[] lst = client.listCalendars();

    for (ExtendedCalendar extCal : lst) {
        // Удалить выбранные календари
        if (extCal.getSummary().startsWith(summary))
            client.deleteCalendar(extCal.getId());
    }
}
~~~
## **Работа с контролем доступа к календарю**
Aspose.Email предоставляет полный контроль над доступом к элементам календаря. Функция [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\)) предоставляется классом [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), который возвращает список [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule). Информация об отдельных правилах может быть получена, изменена и сохранена для календаря клиента. [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient) содержит следующие функции для управления правилами контроля доступа.

- [listAccessRules](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAccessRules\(java.lang.String\))
  Эта функция предоставляет список [AccessControlRule](https://apireference.aspose.com/email/java/com.aspose.email/AccessControlRule)
- [createAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Эта функция создает новое правило доступа для календаря.
- [updateAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAccessRule\(java.lang.String,%20com.aspose.email.AccessControlRule\))
  Эта функция используется для обновления правила доступа.
- [fetchAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAccessRule\(java.lang.String,%20java.lang.String\))
  Может быть использована для получения конкретного правила доступа для календаря клиента
- [deleteAccessRule](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAccessRule\(java.lang.String,%20java.lang.String\))
  Эта функция используется для удаления правила доступа.

Следующий фрагмент кода демонстрирует, как использовать функции для управления правилами доступа:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Получить список календарей для текущего клиента
    ExtendedCalendar[] calendarList = client.listCalendars();

    // Получить идентификатор первого календаря и извлечь список AccessControlRule для первого календаря
    String calendarId = calendarList[0].getId();
    AccessControlRule[] roles1 = client.listAccessRules(calendarId);

    // Создать локальное правило контроля доступа и установить свойства правила
    AccessControlRule rule = new AccessControlRule();
    rule.setRole(AccessRole.reader);
    rule.setScope(new AclScope(AclScopeType.user, email2));

    // Вставить новое правило для календаря. Оно возвращает вновь созданное правило
    AccessControlRule createdRule = client.createAccessRule(calendarId, rule);

    // Получить список правил
    AccessControlRule[] roles2 = client.listAccessRules(calendarId);

    // Длина текущего списка должна быть на 1 больше, чем раньше
    if (roles1.length + 1 == roles2.length) {
        System.out.println("Длины списков в порядке");
    } else {
        System.out.println("Длины списков не в порядке");
        return;
    }

    // Изменить правило и обновить правило для выбранного календаря
    createdRule.setRole(AccessRole.writer);
    AccessControlRule updatedRule = client.updateAccessRule(calendarId, createdRule);

    // Извлечь отдельное правило для календаря
    AccessControlRule fetchedRule = client.fetchAccessRule(calendarId, createdRule.getId());

    // Удалить конкретное правило для данного календаря и извлечь весь список правил для того же календаря
    client.deleteAccessRule(calendarId, createdRule.getId());
    AccessControlRule[] roles3 = client.listAccessRules(calendarId);

    // Проверить, что длина текущего списка правил должна быть равна длине исходного списка до добавления и удаления правила
    if (roles1.length == roles3.length) {
        System.out.println("Длины списков равны");
    } else {
        System.out.println("Длины списков не равны");
        return;
    }
}
~~~
## **Работа с настройками клиента и информацией о цветах**
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

Аналогично информация о цветах для клиентов также может быть получена с использованием [IGmailClient.getColors](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#getColors\(\)). Этот объект информации о цветах возвращает список основных цветов, фоновых цветов и даты и времени обновления.
### **Доступ к настройкам клиента**
Следующий фрагмент кода демонстрирует, как использовать функции для доступа к настройкам клиента:


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Получить настройки клиента
    Dictionary<String, String> settings = client.getSettings();
    if (settings.size() < 1) {
        System.out.println("Нет доступных настроек.");
        return;
    }

    // Пройтись по списку настроек
    for (KeyValuePair<String, String> pair : settings) {
        // Получить значение настройки и проверить, все ли в порядке
        String value = client.getSetting(pair.getKey());
        if (pair.getValue().equals(value)) {
            System.out.println("Ключ = " + pair.getKey() + ", Значение = " + pair.getValue());
        } else {
            System.out.println("Настройки не удалось извлечь");
        }
    }
}
~~~
### **Доступ к информации о цветах**
Следующий фрагмент кода демонстрирует, как использовать функции для доступа к настройкам цветов клиента.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    ColorsInfo colors = client.getColors();
    Dictionary<String, Colors> palettes = colors.getCalendar();

    // Пройтись по списку настроек
    for (KeyValuePair<String, Colors> pair : palettes) {
        System.out.println("Ключ = " + pair.getKey() + ", Цвет = " + pair.getValue());
    }
    System.out.println("Дата обновления = " + colors.getUpdated());
}
~~~
## **Работа с встречами**
Aspose.Email предоставляет функции для работы с [Appointments](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) в календарях Google. Вот список задач, которые можно выполнить с встречами в календаре Google:

1. Добавить встречи - [createAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#createAppointment\(java.lang.String,%20com.aspose.email.Appointment\)), [importAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#importAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Извлечь список встреч - [listAppointments](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointments\(java.lang.String\))
1. Извлечь конкретную встречу - [fetchAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#fetchAppointment\(java.lang.String,%20java.lang.String\)), [listAppointmentInstances](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#listAppointmentInstances\(java.lang.String,%20java.lang.String\))
1. Обновить встречу - [updateAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#updateAppointment\(java.lang.String,%20com.aspose.email.Appointment\))
1. Переместить встречу из одного календаря в другой - [moveAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#moveAppointment\(java.lang.String,%20java.lang.String,%20java.lang.String\))
1. Удалить встречу - [deleteAppointment](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient#deleteAppointment\(java.lang.String,%20java.lang.String\))

### **Добавление встречи**
Следующий образец кода демонстрирует возможность добавления встречи в календарь. В этом примере выполняются следующие шаги:

1. Создать и вставить календарь.
1. Извлечь список встреч из нового календаря.
1. Создать встречу.
1. Вставить встречу.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    // Создать локальный календарь
    Calendar calendar1 = new Calendar("Summary", null, null, "Europe/Kiev");

    // Вставить календарь и получить идентификатор вставленного календаря, а также получить календарь по идентификатору
    String id = client.createCalendar(calendar1);
    Calendar cal1 = client.fetchCalendar(id);
    String calendarId1 = cal1.getId();

    try {
        // Извлечь список встреч из первого календаря
        Appointment[] appointments = client.listAppointments(calendarId1);
        if (appointments.length > 0) {
            System.out.println("Неверное количество встреч");
            return;
        }

        // Получить текущее время и рассчитать время через час от начала
        java.util.Calendar c = java.util.Calendar.getInstance();
        Date startDate = c.getTime();
        c.add(java.util.Calendar.HOUR_OF_DAY, 1);
        Date endDate = c.getTime();

        // Инициализировать коллекцию адресов электронной почты и установить адреса электронной почты участников
        MailAddressCollection attendees = new MailAddressCollection();
        attendees.add("User1.EMail@domain.com");
        attendees.add("User3.EMail@domain.com");

        // Создать встречу с вышеуказанными участниками
        Appointment app1 = new Appointment("Location", startDate, endDate, MailAddress.to_MailAddress(email2), attendees);

        // Установить краткое содержание встречи, описание, временные зоны начала/конца
        app1.setSummary("New Summary");
        app1.setDescription("New Description");
        app1.setStartTimeZone("Europe/Kiev");
        app1.setEndTimeZone("Europe/Kiev");

        // Вставить встречу в первый календарь, вставленный выше, и получить вставленную встречу
        Appointment app2 = client.createAppointment(calendarId1, app1);

        // Извлечь встречу по уникальному идентификатору
        Appointment app3 = client.fetchAppointment(calendarId1, app2.getUniqueId());
    } catch (Exception ex) {
        System.err.println(ex);
    }
    
}
~~~
### **Извлечение и обновление встречи**
Здесь демонстрируется извлечение и обновление календаря следующим образом:

1. Извлечь конкретную встречу.
1. Изменить встречу.
1. Обновить встречу в календаре.

Предполагается, что календарь с идентификатором "calendarId" и уникальный идентификатор встречи "AppointmentUniqueId" уже извлечены. Следующий фрагмент кода демонстрирует, как извлечь и обновить встречу.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String calendarId = client.listCalendars()[0].getId();
    String AppointmentUniqueId = client.listAppointments(calendarId)[0].getUniqueId();

    // Извлечь встречу
    Appointment app3 = client.fetchAppointment(calendarId, AppointmentUniqueId);
    // Изменить информацию о встрече
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
    // Обновить встречу и получить обновленную встречу
    Appointment app4 = client.updateAppointment(calendarId, app3);
}
~~~
### **Перемещение и удаление встречи**
[Appointment](https://apireference.aspose.com/email/java/com.aspose.email/Appointment) может быть перемещена, если указаны исходный календарь, целевой календарь и уникальный идентификатор встречи в исходном календаре. Следующий фрагмент кода демонстрирует, как переместить и удалить встречу.


~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
    String SourceCalendarId = client.listCalendars()[0].getId();
    String DestinationCalendarId = client.listCalendars()[1].getId();
    String TargetAppUniqueId = client.listAppointments(SourceCalendarId)[0].getUniqueId();

    // Извлечь список встреч в целевом календаре перед перемещением встречи
    Appointment[] appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("Перед перемещением количество = " + appointments.length);
    Appointment Movedapp = client.moveAppointment(SourceCalendarId, DestinationCalendarId, TargetAppUniqueId);

    // Извлечь список встреч в целевом календаре после перемещения встречи
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("После перемещения количество = " + appointments.length);

    // Удалить конкретную встречу из календаря, используя уникальный идентификатор
    client.deleteAppointment(DestinationCalendarId, Movedapp.getUniqueId());

    // Извлечь список встреч. Он должен быть на одну меньше, чем количество встреч в целевом календаре ранее
    appointments = client.listAppointments(DestinationCalendarId);
    System.out.println("После удаления количество = " + appointments.length);
}
~~~