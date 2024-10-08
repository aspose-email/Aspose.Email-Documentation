---
title: "Ограничения и различия в API"
description: "Библиотека парсеров электронной почты C++ имеет некоторые отличия по сравнению с эквивалентной версией .NET. Эта страница содержит информацию обо всех таких функциях, которые недоступны в API."
url: /ru/cpp/limitations-and-api-differences/
weight: 10
type: docs
---

Aspose.Email для C++ имеет некоторые отличия по сравнению с эквивалентной версией .NET API. Эта страница содержит информацию обо всех таких функциях, которые недоступны в API.
## **Ограничения API**
Aspose.Email для C++ имеет следующие ограничения, которые делают его отличным от других API семейства продуктов Aspose.Email. Эти ограничения:

- В данный момент API поддерживает следующие коммуникационные протоколы:
  - SMTP
  - POP3
  - IMAP
- API не поддерживает Exchange (как WebDav, так и EWS)
- Нет поддержки форматов файлов Thunderbird MBox
- Не поддерживается шифрование/дешифрование сообщений
- Поддержка конверсии MapiMessage в MailMessage также отсутствует
- Уведомления о получении и квитанции о прочтении
- Создание писем TNEF из файлов MSG
- Определение типа сообщения также не поддерживается
- Работа с повторениями, включая EndAfterNoccurrences, WeeklyEndAfterNoccurrences, EndAfterNoccurrenceSelectMultipleDaysInweek, MonthlyEndAfterNoccurrences
- Определение сообщения как TNEF
- Обнаружение вложенного сообщения с помощью флага Embedded
- Удаление связанных ресурсов в определенном месте
- Отрисовка календарных событий на основе шаблонов формата
- Удаление дочерних элементов из папок файла PST
- Изменение свойств сообщения в папке PST с использованием ChangeMessages