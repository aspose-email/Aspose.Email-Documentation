---
title: "Работа с назначениями"
url: /ru/java/working-with-appointments/
weight: 20
type: docs
---

## **Загрузите и сохраните встречу в формате ICS**

The [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) класс в Aspose.Email для Java можно использовать для загрузки встречи в формате ICS, а также для создания новой встречи и сохранения ее на диске в формате ICS. В этой статье мы сначала создаем встречу и сохраняем ее на диске в формате ICS, а затем загружаем ее.

### **Загрузить встречу в формате ICS**

Чтобы загрузить встречу в формате ICS, необходимо выполнить следующие шаги:

1. Создайте экземпляр [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) class.
1. Позвоните [Load()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#load-java.io.InputStream-) метод, указав путь к файлу ICS.
1. Прочтите любой объект недвижимости, чтобы получить любую информацию о встрече (файл ICS).

В следующих фрагментах кода показано, как загрузить встречу в формате ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-LoadAppointment.java" >}}

### **Назначьте встречу и сохраните ее на диске в формате ICS**

Чтобы создать встречу и сохранить ее в формате ICS, необходимо выполнить следующие шаги.

1. Создайте экземпляр [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) класс и инициализируйте его с помощью этого конструктора.
1. Передайте следующие аргументы в приведенном выше конструкторе
   1. Attendees
   1. Description
   1. Дата окончания
   1. Location
   1. Organizer
   1. Дата начала
   1. Summary
   1. Дата создания
   1. Дата последнего изменения 
1. Позвоните [Save()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#save-java.io.OutputStream-) метод и укажите имя и формат файла в аргументах.

Встречу можно открыть в Microsoft Outlook или любой программе, которая может загрузить файл ICS. Если файл открыт в Microsoft Outlook, встреча автоматически добавляется в календарь Outlook.

В следующих фрагментах кода показано, как создать и сохранить встречу на диске в формате ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-CreateAppointment.java" >}}

## **Сохранение встреч в формате MSG**

Aspose.Email позволяет сохранять встречи непосредственно в файлах.msg. Для настройки процесса сохранения встреч доступны следующие общедоступные классы:

- [AppointmentMsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentmsgsaveoptions/) класс с дополнительными опциями для сохранения встреч в формате msg.
- [AppointmentIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmenticssaveoptions/) класс с дополнительными опциями для сохранения встречи в формате ics. Он был добавлен для замены устаревших ICSSaveOptions.

В приведенном ниже примере кода показано, как загрузить встречу из файла, а затем сохранить ее в двух разных форматах: .ics и .msg.

```java
Appointment appointment = Appointment.load("fileName");
appointment.save("fileName.ics", new AppointmentIcsSaveOptions());
appointment.save("fileName.msg", new AppointmentMsgSaveOptions());
```

## **Назначьте встречу с помощью HTML-контента**

Обычно заголовок X-ALT-DESC используется в формате iCalendar (RFC 5545). Это расширенное свойство, которое предоставляет альтернативное удобочитаемое описание элемента или события календаря. Этот заголовок часто используется для представления описания события в виде обычного текста или HTML, что может быть полезно для совместимости со старыми календарными программами или для предоставления упрощенной версии описания. В случаях, когда основное описание не поддерживается или неправильно отображается в календарном приложении получателя, в качестве альтернативного описания события используется заголовок X-ALT-DESC. Это позволяет отправителю использовать описание события в разных вариантах, что обеспечивает лучшую совместимость и доступность различных программ и платформ для календаря. Чтобы назначить встречу с HTML-содержимым, задайте поле [HtmlDescription](https://reference.aspose.com/email/java/com.aspose.email/appointment/#setHtmlDescription-java.lang.String-) свойство «истина». Попробуйте следующий пример кода, в котором показано, как создать и определить объект встречи с определенными деталями и настройками, включая дату, время, место, организатора, участников и отформатированное описание:

```java
Date startDate = new Date();
Appointment appointment = new Appointment("Bygget 83",
        startDate, // start date
        addHours(startDate, 1), // end date
        new MailAddress("TintinStrom@from.com", "Tintin Strom"), // organizer
        MailAddressCollection.to_MailAddressCollection(
                new MailAddress("AinaMartensson@to.com", "Aina Martensson"))); // attendee
appointment.setHtmlDescription("<html>\n"
        + "     <style type=\"\"text/css\"\">\n"
        + "      .text {\n"
        + "             font-family:'Comic Sans MS';\n"
        + "             font-size:16px;\n"
        + "            }\n"
        + "     </style>\n"
        + "    <body>\n"
        + "     <p class=\"\"text\"\">Hi, I'm happy to invite you to our party.</p>\n"
        + "    </body>\n"
        + "    </html>");
```

## **Создайте черновик запроса на встречу**

Чтобы сохранить встречу в черновом режиме, [Method](https://reference.aspose.com/email/java/com.aspose.email/appointment/#getMethodType--) собственность [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) класс должен быть установлен на **Publish**. В следующем примере кода показано использование этого свойства в качестве примера.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-CreateADraftAppointmentRequest.java" >}}

### **Создание проекта встречи на основе текста**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-DraftAppointmentCreationFromText.java" >}}

## **Добавление и удаление вложений из элементов календаря**

Aspose.Email предоставляет коллекцию вложений, которую можно использовать для добавления и извлечения вложений, связанных с элементами календаря. В этой статье показано, как:

1. Создавайте и добавляйте вложения в [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) объект класса.
1. Извлеките информацию о вложениях во время встречи.
1. Извлеките вложения из записи на прием.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-AddAndRetrieveAttachmentFromCalendarItems-.java" >}}

## **Форматирование встреч**

В приведенных ниже примерах программирования показано, как использовать [AppointmentFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentformattingoptions/) класс для форматирования текста и HTML.

#### **Пример программирования — форматирование текста**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-TextFormatting.java" >}}

#### **Пример программирования — форматирование HTML**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-HtmlFormatting.java" >}}

## **Чтение нескольких событий из файла ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ReadMultipleEventsfromICSFile-ReadMultipleEventsfromICSFile.java" >}}

## **Запись нескольких событий из файла ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-WriteMultipleEventsToICS.java" >}}

## **Установите статус участников для участников встречи**

Aspose.Email for .NET API позволяет задавать статус участников встречи при составлении ответного сообщения. Это добавляет свойство PARTSTAT в файл ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees.java" >}}

## **Настройка идентификатора продукта для iCalendar**

Aspose.Email для Java API позволяет получить или установить идентификатор продукта, создавшего объект iCalendar.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-ICSSaveOptions.cs" >}}

## **Как обойти проверку адреса при попытке загрузить встречи**

Aspose.Email для Java API позволяет обойти ошибку проверки электронной почты, установив [IgnoreSmtpAddressCheck](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#getIgnoreSmtpAddressCheck--) опция на [AppointmentLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#setIgnoreSmtpAddressCheck(boolean)) объект и передача его в вызов load.

~~~Java
AppointmentLoadOptions lo = new AppointmentLoadOptions();
lo.setIgnoreSmtpAddressCheck(true);
Appointment appointment = Appointment.load("app.ics", lo);
~~~