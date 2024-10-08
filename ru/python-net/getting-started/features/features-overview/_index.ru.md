---
title: "Обзор характеристик"
url: /ru/python-net/features-overview/
weight: 10
type: docs
---


Apose.Email для Python через .NET разделен на несколько отдельных компонентов, каждый из которых имеет свои особенности. Вот список функций для каждого из основных пакетов.
## **Aspose.Email.Mail**
### **Общие функции электронной почты**
- Создавать электронные письма, содержащие обычный текст
- Создавать электронные письма, содержащие HTML
- Создавать альтернативные текстовые тела сообщений для совместимости как с HTML, так и с клиентами электронной почты, не поддерживающими HTML
- Подключаться к любому SMTP-серверу на указанном порту
- Отправлять электронные письма через любой SMTP-сервер
- Подключаться к SMTP-серверу с поддержкой SSL
- Подключаться к SMTP-серверу на основе TLS
### **Функции вложений**
- Добавлять вложения к вашим электронным письмам
- Удалять вложения из ваших электронных писем
- Создавать вложения из путей к файлам
### **Функции встроенных объектов**
- Встраивать объекты (например, изображения, звуки и т. д.) в ваши электронные письма.
- Удалять встроенные объекты из ваших электронных писем.
- Встраивать объекты из путей к файлам.
- Встраивать объекты из потоков.
- Встраивать объекты из массивов байтов.
### **Функции импорта/экспорта**
- Импортировать электронные письма Microsoft Outlook Email Message Format (MSG).
- Импортировать электронные письма Microsoft HTML (MHT)
- Импортировать электронные письма в формате, совместимом с RFC822 (EML)
- Создавать электронные письма из содержимого HTML
- Экспортировать электронные письма в формат Microsoft HTML (MHT)
- Экспортировать электронные письма в формат, совместимый с RFC822 (EML)
- Экспортировать электронные письма из файла Outlook PST в файлы Outlook MSG
### **Функции массовой рассылки**
- Поддерживает отправку электронных писем партиями.
- Встроенная функция многопоточности для отправки массовых электронных писем.
- Поддерживает сохранение массовых сообщений электронной почты в пуле сообщений
### **Календарные функции**
- Добавлять события iCalendar к электронным сообщениям.
- Отменять события iCalendar.
- Отправлять запросы на встречи по электронной почте.
- Отправлять запросы на встречи по электронной почте.
### **Утилиты**
- Настраивать заголовки электронной почты.
- Устанавливать приоритет сообщения, дату и время.
- Поддерживает все наборы символов.
- Запрашивать уведомления о прочтении.
### **Расширенные функции**
- Асинхронные и синхронные модели программирования.
- Поддержка анализа электронной почты в форматах MSG, MHT и EML.
- Поддержка сохранения электронных писем в форматах MSG, MHT и EML.
- Извлечение вложений из файлов Microsoft Outlook Email Message (MSG).
- Чтение сообщений из файлов Outlook PST.
- Поддержка резервного SMTP-соединения.
- Указание количества попыток для SMTP-соединений.
## **Aspose.Email.Mime**
{{% alert %}}
**Попробуйте!**

Парсить электронные файлы с помощью бесплатного [**Aspose.Email Parser App**](https://products.aspose.app/email/ru/parser).
{{% /alert %}}
### **Общие функции парсинга**
- Извлечение заголовков сообщений электронной почты и тел сообщений.
- Извлечение имен и значений из заголовков электронной почты.
- Извлечение адресов From, To, Cc и Reply-To.
- Извлечение и сохранение вложений.
- Извлечение и сохранение встроенных объектов, таких как изображения и звуки.
### **Функции импорта/экспорта**
- Импортировать электронные письма в формате Microsoft Outlook Email Message (MSG).
- Импортировать электронные письма в формате Microsoft HTML (MHT).
- Импортировать электронные письма в формате, совместимом с RFC822 (EML).
- Экспортировать электронные письма в формат Microsoft HTML (MHT).
- Экспортировать электронные письма в формат, совместимый с RFC822 (EML).
### **Утилиты**
- Поддерживает несколько заголовков.
- Поддерживает несколько частей.
- Поддерживает все наборы символов.
- Извлечение метаданных, таких как contentType, MimeVersion и XMailer.

{{% alert %}}
**Попробуйте!**

Используйте [**Aspose.Email Metadata App**](https://products.aspose.app/email/ru/metadata), чтобы просмотреть и отредактировать метаданные онлайн, встроенные свойства или настраиваемые свойства сообщения.
{{% /alert %}}
### **Расширенные функции парсинга**
- Загружать и анализировать электронные письма в форматах MSG, MHT и EML.
## **Aspose.Email.Pop3**
### **Общие функции POP3**
- Извлечение полных сообщений или только заголовков.
- Поддерживает базовые команды POP3.
- Список почтовых сообщений.
- Извлечение электронных писем в форматах MIME и обычного текста.
- Получение информации о почтовом ящике.
- Поддерживать соединение POP3 активным.
- Функции управления электронной почтой.
- Удалять выбранные электронные письма на сервере POP3.
- Удалять все электронные письма.
- Отменить удаление на сервере POP3.
- Подключаться к серверу POP3 с поддержкой SSL.
### **Функции безопасности**
- Поддерживает аутентификацию по протоколу Authenticated Post Office Protocol (APOP).
- Поддерживает аутентификацию Clear Text USER/PASS.
- Поддерживает аутентификацию CRAM-MD5 по RFC 2195.
- Поддерживает аутентификацию DIGEST-MD5 по RFC 2831.
- Поддерживает аутентификацию при входе в систему.
- Поддерживает аутентификацию TLS в открытом тексте по RFC 2595.
## **Aspose.Email.Imap**
### **Общие функции**
- Подключаться и взаимодействовать с сервера IMAP.
- Манипулировать сообщениями электронной почты и папками на сервере.
- Подключаться к серверу IMAP с поддержкой SSL.
- Получать уведомления при получении электронной почты, избегая повторных опросов сервера
### **Функции управления сообщениями**
- Извлекать сообщения электронной почты.
- Извлекать заголовки сообщений электронной почты.
- Сохранять сообщения электронной почты на локальной файловой системе.
- Удалять сообщения электронной почты.
- Список сообщений электронной почты в указанной папке.
- Устанавливать флаги (прочитано, удалено и т. д.) для указанных сообщений электронной почты.
### **Функции управления папками**
- Создавать папки электронной почты.
- Удалять папки электронной почты.
- Переименовывать папки электронной почты.
### **Функции безопасности**
- Поддерживает аутентификацию Clear Text USER/PASS.
- Поддерживает аутентификацию CRAM-MD5 по RFC 2195.
- Поддерживает аутентификацию DIGEST-MD5 по RFC 2831.
- Поддерживает аутентификацию при входе в систему.
- Поддерживает аутентификацию TLS в открытом тексте по RFC 2595.
## **Aspose.iCalendar**
- Легко и надежно рассчитывайте даты и время появления даже для самых сложных паттернов повторения.
- Потребляйте и создавайте паттерны повторения в формате iCalendar (RFC 2445).
- Создавайте паттерны повторения программно через интуитивно понятную объектную модель.
- Используйте паттерны повторения на год, месяц, неделю, день, час, минуту и секунду.
- Представляйте паттерны повторения в ваших Windows, веб- или мобильных приложениях.
### **Поддерживаемые протоколы**
- SMTP
- MIME
- POP3
- IMAP
- HTTP
## **Поддержка файлов PST/OST**
- Поддержка файлов Personal и Offline Storage
- Генерация и чтение файлов OST, PST
- Поддержка PST файлов всех типов
- Все типы OST поддерживаются для чтения