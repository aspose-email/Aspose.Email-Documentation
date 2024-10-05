---
title: Работа с назначениями
type: docs
weight: 20
url: /java/working-with-appointments/
---

## **Загрузка и сохранение назначения в формате ICS**

Класс [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) в Aspose.Email для Java может использоваться для загрузки назначения в формате ICS, а также для создания нового назначения и его сохранения на диск в формате ICS. В этой статье мы сначала создадим назначение и сохраним его на диск в формате ICS, а затем загрузим его.

### **Загрузка назначения в формате ICS**

Для загрузки назначения в формате ICS необходимо выполнить следующие шаги:

1. Создать экземпляр класса [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).
1. Вызвать метод [Load()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#load-java.io.InputStream-) с указанием пути к файлу ICS.
1. Прочитать любое свойство, чтобы получить информацию о назначении (файл ICS).

Следующие фрагменты кода показывают, как загрузить назначение в формате ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-LoadAppointment.java" >}}

### **Создание назначения и сохранение на диск в формате ICS**

Для создания назначения и его сохранения в формате ICS необходимо выполнить следующие шаги.

1. Создать экземпляр класса [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) и инициализировать его с помощью этого конструктора.
1. Передать следующие аргументы в указанный выше конструктор
   1. Участники
   1. Описание
   1. Дата окончания
   1. Место
   1. Организатор
   1. Дата начала
   1. Краткое содержание
   1. Дата создания
   1. Дата последнего изменения
1. Вызвать метод [Save()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#save-java.io.OutputStream-) и указать имя файла и формат в аргументах.

Назначение может быть открыто в Microsoft Outlook или любой программе, которая может загрузить файл ICS. Если файл открыт в Microsoft Outlook, он автоматически добавляет назначение в календарь Outlook.

Следующие фрагменты кода показывают, как создать и сохранить назначение на диск в формате ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-CreateAppointment.java" >}}

## **Сохранение назначений в формате MSG**

Aspose.Email позволяет сохранять назначения непосредственно в .msg файлы. Доступны следующие общедоступные классы для настройки процесса сохранения назначений:

- Класс [AppointmentMsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentmsgsaveoptions/) с дополнительными опциями для сохранения назначений в формате msg.
- Класс [AppointmentIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmenticssaveoptions/) с дополнительными опциями для сохранения назначения в формате ics. Он был добавлен для замены устаревшего IcsSaveOptions.

Пример кода ниже показывает, как загрузить назначение из файла, а затем сохранить его в двух различных форматах: .ics и .msg.

```java
Appointment appointment = Appointment.load("fileName");
appointment.save("fileName.ics", new AppointmentIcsSaveOptions());
appointment.save("fileName.msg", new AppointmentMsgSaveOptions());
```

## **Создание назначения с HTML-содержимым**

Распространенной практикой является использование заголовка X-ALT-DESC в формате iCalendar (RFC 5545). Это расширенное свойство, которое предоставляет альтернативное описание календарного элемента или события в формате, удобном для чтения человеком. Этот заголовок часто используется для включения текстового или HTML представления описания события, что может быть полезно для совместимости со старым календарным программным обеспечением или для предоставления упрощенной версии описания. В случаях, когда основное описание не поддерживается или отображается неправильно в календарном приложении получателя, заголовок X-ALT-DESC используется для предоставления альтернативного описания события. Это позволяет отправителю включать различные представления описания события для обеспечения лучшей совместимости и доступности между различными календарными программами и платформами. Чтобы создать назначение с HTML-содержимым, установите свойство [HtmlDescription](https://reference.aspose.com/email/java/com.aspose.email/appointment/#setHtmlDescription-java.lang.String-) в 'true'. Попробуйте следующий пример кода, который демонстрирует, как создать и определить объект назначения с конкретными деталями и настройками, включая дату, время, место, организатора, участников и отформатированное описание:

```java
Date startDate = new Date();
Appointment appointment = new Appointment("Bygget 83",
        startDate, // дата начала
        addHours(startDate, 1), // дата окончания
        new MailAddress("TintinStrom@from.com", "Tintin Strom"), // организатор
        MailAddressCollection.to_MailAddressCollection(
                new MailAddress("AinaMartensson@to.com", "Aina Martensson"))); // участник
appointment.setHtmlDescription("<html>\n"
        + "     <style type=\"\"text/css\"\">\n"
        + "      .text {\n"
        + "             font-family:'Comic Sans MS';\n"
        + "             font-size:16px;\n"
        + "            }\n"
        + "     </style>\n"
        + "    <body>\n"
        + "     <p class=\"\"text\"\">Привет, я рад пригласить вас на нашу вечеринку.</p>\n"
        + "    </body>\n"
        + "    </html>");
```

## **Создание черновика запроса на назначение**

Чтобы сохранить назначение в режиме черновика, свойство [Method](https://reference.aspose.com/email/java/com.aspose.email/appointment/#getMethodType--) класса [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) должно быть установлено на **Publish**. Следующий пример кода демонстрирует использование этого свойства в качестве примера.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-CreateADraftAppointmentRequest.java" >}}

### **Создание черновика назначения из текста**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-DraftAppointmentCreationFromText.java" >}}

## **Добавление и удаление вложений из календарных элементов**

Aspose.Email предоставляет коллекцию вложений, которую можно использовать для добавления и извлечения вложений, связанных с календарными элементами. Эта статья показывает, как:

1. Создать и добавить вложения к объекту класса [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).
1. Извлечь информацию о вложениях из назначения.
1. Извлечь вложения из назначения.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-AddAndRetrieveAttachmentFromCalendarItems-.java" >}}

## **Форматирование назначений**

Ниже приведены примеры программирования, которые демонстрируют, как использовать класс [AppointmentFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentformattingoptions/) для форматирования текста и HTML.

#### **Пример программирования - Форматирование текста**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-TextFormatting.java" >}}

#### **Пример программирования - Форматирование HTML**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-HtmlFormatting.java" >}}

## **Чтение нескольких событий из файла ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ReadMultipleEventsfromICSFile-ReadMultipleEventsfromICSFile.java" >}}

## **Запись нескольких событий из файла ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-WriteMultipleEventsToICS.java" >}}

## **Установка статуса участников назначений**

Aspose.Email для .NET API позволяет установить статус участников назначений при формировании ответа. Это добавляет свойство PARTSTAT в файл ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees.java" >}}

## **Настройка идентификатора продукта для iCalendar**

Aspose.Email для Java API позволяет получить или установить идентификатор продукта, который создал объект iCalendar.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-ICSSaveOptions.cs" >}}

## **Как избежать проверки адреса при попытке загрузить назначения**

Aspose.Email для Java API позволяет обойти ошибку проверки электронной почты, установив опцию [IgnoreSmtpAddressCheck](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#getIgnoreSmtpAddressCheck--) на объекте [AppointmentLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#setIgnoreSmtpAddressCheck(boolean)) и передав его в вызов загрузки.

~~~Java
AppointmentLoadOptions lo = new AppointmentLoadOptions();
lo.setIgnoreSmtpAddressCheck(true);
Appointment appointment = Appointment.load("app.ics", lo);
~~~