---
title: "Работа с элементами календаря Outlook с помощью библиотеки электронной почты C++"
description: "Используя C++ Email Library API, вы можете создавать и сохранять элементы календаря Outlook в формате MSG, добавлять и извлекать вложения из файлов календаря, а также устанавливать напоминания с встречами, добавляя теги."
url: /ru/cpp/working-with-outlook-calendar-items/
weight: 80
type: docs
linktitle: "Работа с элементами календаря Outlook"
---

## **Работа с MapiCalendar**
Класс MapicaLendar в Aspose.Email предоставляет методы и атрибуты для установки различных свойств элемента календаря. В этой статье представлены примеры кода для:

- Создание и сохранение элементов календаря
- Настройка напоминаний для элементов MapicaLendar
- Добавление/извлечение вложений из календаря
- Получение статуса получателей из приглашений на собрания
- Создание объекта MapicaLendar TimeZone из стандартного часового пояса

### **Создание и сохранение элементов календаря**
В следующем фрагменте кода показано, как создать и сохранить элемент календаря в формате ICS с помощью библиотеки C++ Email Parser Library или API.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cpp" >}}

### **Сохранение элемента календаря в формате MSG**
В следующем фрагменте кода показано, как сохранить элемент календаря в формате MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cpp" >}}

### **Добавление экранного напоминания в календарь**
В следующем фрагменте кода показано, как добавить напоминание о отображении в календарь.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cpp" >}}

### **Добавление звукового напоминания в календарь**
В следующем фрагменте кода показано, как добавить звуковое напоминание в календарь.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cpp" >}}

### **Добавление/извлечение вложений из файлов календаря**
В следующем фрагменте кода показано, как добавлять/извлекать вложения из файлов календаря.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cpp" >}}

### **Статус получателей приглашения на собрание**
В следующем фрагменте кода показано, как определить статус получателей приглашения на собрание.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cpp" >}}

### **Создание часового пояса Mapicalend из стандартного часового пояса**
В следующем фрагменте кода показано, как создать MapicaLendaTimeZone из стандартного часового пояса.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cpp" >}}

## **Настройка напоминания с созданной встречей**
Напоминание можно добавить при создании встречи. Эти сигналы могут срабатывать по разным критериям, например, за n минут до начала расписания и повторяться n раз с интервалом n раз. Для создания этих триггеров можно использовать разные теги в скрипте, прилагаемом к командам BEGIN:VALARM и END:VALARM во время встречи. Существует несколько вариантов, в которых напоминание можно установить во время встречи.

### **Настройка напоминания путем добавления тегов**
В следующем фрагменте кода показано, как настроить напоминание, добавив теги.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cpp" >}}
