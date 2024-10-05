---
title: "Работа с элементами календаря Outlook с использованием библиотеки электронной почты C++"
description: "Используя API библиотеки электронной почты C++, вы можете создавать и сохранять элементы календаря Outlook в формате MSG, добавлять и извлекать вложения из файлов календаря, а также устанавливать напоминания о встречах, добавляя теги."
url: /ru/cpp/working-with-outlook-calendar-items/
weight: 80
type: docs
linktitle: "Работа с элементами календаря Outlook"
---

## **Работа с MapiCalendar**
Класс MapiCalendar библиотеки Aspose.Email предоставляет методы и атрибуты для настройки различных свойств элемента календаря. В этой статье приведены примеры кода для:

- Создания и сохранения элементов календаря
- Установки напоминаний для элементов MapiCalendar
- Добавления/извлечения вложений из календаря
- Получения статуса получателей из запросов на встречу
- Создания объекта MapiCalendar TimeZone из стандартного часового пояса

### **Создание и сохранение элементов календаря**
Следующий фрагмент кода показывает, как создать и сохранить элемент календаря в формате ICS с использованием библиотеки или API C++ Email Parser.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cpp" >}}

### **Сохранение элемента календаря в формате MSG**
Следующий фрагмент кода показывает, как сохранить элемент календаря в формате MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cpp" >}}

### **Добавление дисплейного напоминания в календарь**
Следующий фрагмент кода показывает, как добавить дисплейное напоминание в календарь.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cpp" >}}

### **Добавление аудионапоминания в календарь**
Следующий фрагмент кода показывает, как добавить аудионапоминание в календарь.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cpp" >}}

### **Добавление/извлечение вложений из файлов календаря**
Следующий фрагмент кода показывает, как добавлять/извлекать вложения из файлов календаря.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cpp" >}}

### **Статус получателей из запроса на встречу**
Следующий фрагмент кода показывает, как получить статус получателей из запроса на встречу.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cpp" >}}

### **Создание MapiCalendarTimeZone из стандартного часового пояса**
Следующий фрагмент кода показывает, как создать MapiCalendarTimeZone из стандартного часового пояса.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cpp" >}}

## **Установка напоминания с созданной встречей**
Напоминание может быть добавлено при создании встречи. Эти сигнализации могут срабатывать на основе различных критериев, таких как n минут до начала расписания, повторение n раз с интервалами в n. Для создания этих триггеров в сценарии можно использовать различные теги, заключенные между BEGIN:VALARM и END:VALARM внутри встречи. Существует несколько вариантов, при которых напоминание может быть установлено для встречи.

### **Установка напоминания путем добавления тегов**
Следующий фрагмент кода показывает, как установить напоминание, добавляя теги.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cpp" >}}