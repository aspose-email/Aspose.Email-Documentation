---
title: "Создание и установка содержимого электронных писем"
url: /ru/java/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---

## **Создать новое сообщение электронной почты**

Aspose.Email для Java позволяет разработчикам создавать MIME (расширения интернет-почты общего назначения) сообщения с нуля. Основной класс для этой цели в API Aspose.Email для Java — это класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
В этой теме объясняются шаги, необходимые для создания электронных писем в форматах файлов EML, MSG и MTH с использованием Aspose.Email для Java.

Чтобы создать сообщение электронной почты с нуля:

1. Создайте экземпляр класса MailMessage.
2. Установите тему сообщения с помощью метода [setSubject()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setSubject-java.lang.String-) .
3. Установите тело сообщения с помощью метода [setHtmlBody()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) .
4. Установите отправителя электронной почты с помощью метода [setFrom()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setFrom-com.aspose.email.MailAddress-) .
5. Установите получателя в поле **Кому** с помощью метода [getTo().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) .
6. Установите получателя в поле **Копия** с помощью метода [getCC().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) .
7. Вызовите метод [Save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.io.OutputStream-) , чтобы сохранить файл сообщения на диск в форматах MSG, EML и MHT.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-CreateNewEmail-.java" >}}

## **Указание нескольких получателей**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) представляет собой сообщение электронной почты. Экземпляры класса MailMessage используются для формирования электронных писем, которые передаются на SMTP-сервер с помощью класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) . В этой теме демонстрируется, как указать более один адрес электронной почты. Адреса электронной почты можно указывать с помощью класса MailMessage. Адреса электронной почты, используемые в классе MailMessage:

- **Кому** - адреса получателей могут быть указаны в поле «Кому». Получатели в поле «Кому» являются основной аудиторией сообщения. Может быть более одного адреса получателя.
- **Копия** - Копия обозначает "углеродную копию" или "вежливую копию" и позволяет вам добавлять электронных получателей, которые должны видеть электронное письмо, но не обязательно ожидается, что они предпримут какие-либо действия в ответ на него. Например, менеджеры или члены вашей команды, которые должны быть в курсе обсуждения. С помощью Aspose.Email адреса CC могут быть указаны в вашем коде. Таким образом, автоматизированные электронные письма или все письма на конкретный адрес могут быть скопированы соответствующему персоналу.
- **Скрытая копия** - Скритая копия позволяет отправить электронное письмо получателю, который скрыт от других получателей. В то время как CC отображается в информации о письме, которую видят основные получатели, Bcc не отображается. Это предназначено для скрытого уведомления.

Чтобы указать несколько адресов электронной почты в сообщении электронной почты, выполните следующие шаги:

1. Создайте экземпляр класса MailMessage.
2. Укажите отправителя и несколько адресов «Кому», «Копия» и «Скрытая копия», используя экземпляр MailMessage.
3. Создайте экземпляр класса SmtpClient и отправьте электронное письмо, используя метод Send.

Пример кода ниже показывает, как можно указать несколько адресов «Кому», «Копия» и «Скрытая копия».

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyRecipientAddresses-SpecifyRecipientAddresses.java" >}}

## **Изменение адресов электронной почты на дружелюбные имена**

Программные примеры ниже демонстрируют, как изменить адреса электронной почты на дружелюбные имена в сообщении электронной почты. Дружелюбное имя — это имя, которое более удобно для восприятия, чем адрес электронной почты, например, Джон Смит вместо js346@domain.com. При отправке электронного письма мы можем ассоциировать дружелюбное имя с адресом электронной почты в конструкторе класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .

Чтобы изменить адреса электронной почты на дружелюбные имена в сообщении электронной почты, выполните следующие шаги:

- Создайте экземпляр класса MailMessage и укажите адреса электронной почты в полях **Кому** и **От** вместе с дружелюбными именами.
- Укажите адреса электронной почты CC и Bcc вместе с дружелюбными именами, вызвав конструктор класса MailMessage в экземпляре MailMessage.
- Создайте экземпляр класса SmtpClient и отправьте электронное письмо, используя метод Send.

Следующий фрагмент кода показывает, как отобразить имена для адресов электронной почты.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ChangeEmailAddress-ChangeEmailAddress.java" >}}

## **Установить тело письма**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) представляет собой сообщение электронной почты. Экземпляры класса MailMessage используются для формирования электронных писем, которые передаются на SMTP-сервер для доставки с использованием класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) . Тело письма может быть указано с использованием класса MailMessage. Тело электронного письма может быть задано с использованием метода [setHtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) в MailMessage.

Помимо [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), Aspose.Email имеет другой метод, относящийся к телу письма:

- [isBodyHtml](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isBodyHtml--): сообщает пользователю, является ли тело HTML или обычным текстом.

Эта тема показывает, как определить текст HTML тела и установить альтернативный текст.

### **Установка HTML тела**

[HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) используется для указания HTML-содержимого тела сообщения. HtmlBody должен быть заключен между тегами <html> </html> . Следующий фрагмент кода показывает, как установить HTML тело.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetHTMLBody-SetHTMLBody.java" >}}

### **Установка альтернативного текста**

Используйте класс [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) для указания копий сообщения электронной почты в различных форматах. Например, если вы отправляете сообщение в HTML, вы также можете захотеть предоставить версию в обычном тексте на случай, если некоторые получатели используют почтовые клиенты, которые не могут отображать HTML-содержимое. Этот класс имеет два свойства: [LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getLinkedResources--) и [BaseUri](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getBaseUri--) , которые используются для разрешения URL в содержимом электронной почты.

- LinkedResources — это коллекция объектов LinkedResources. При рендеринге URL в содержимом электронной почты сначала сопоставляются с URL в связи с содержимым каждого объекта LinkedResources в коллекции LinkedResources и разрешаются.
- BaseUri используется почтовым клиентом для разрешения относительных URL в теле, а также для разрешения относительных URL связи с содержимым в коллекции LinkedResources.

Следующий фрагмент кода показывает, как установить альтернативный текст.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetAlternateText-SetAlternateText.java" >}}

## **Указание кодировки тела письма**

Тип содержимого определяет формат содержимого электронной почты: набор символов. Например, несколько общих наборов символов, предоставленных в java.nio.Charset, это:

- US-ASCII - семиразрядный ASCII, также известный как ISO646-US, также известный как базовый латинский блок набора символов Unicode
- ISO-8859-1 - ISO латинский алфавит No. 1, также известный как ISO-LATIN-1
- UTF-8 - восьмиразрядный формат преобразования UCS
- UTF-16BE - шестнадцатизначный формат преобразования UCS, порядок байтов big-endian
- UTF-16LE - шестнадцатизначный формат преобразования UCS, порядок байтов little-endian
- UTF-16 - шестнадцатизначный формат преобразования UCS, порядок байтов определяется необязательной меткой порядка байтов

Aspose.Email использует свойство [BodyEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBodyEncoding--) класса MailMessage для указания кодировки тела электронной почты. Чтобы закодировать тело сообщения электронной почты, выполните следующие шаги:

1. Создайте экземпляр класса MailMessage.
1. Укажите отправителя, получателя и HTML тело электронной почты в экземпляре MailMessage.
1. Укажите значение свойства BodyEncoding.
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и отправьте электронное письмо с помощью метода Send.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyMailBodyEncoding-SpecifyMailBodyEncoding.java" >}}

## **Особенности MailMessage**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) представляет содержимое сообщения электронной почты. Экземпляры класса MailMessage используются для формирования сообщения электронной почты, которое передается на SMTP-сервер для доставки с использованием класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) . Эта статья демонстрирует, как использовать утилитарные функции класса MailMessage для управления следующими функциями электронной почты:

- **Дата и время** - через метод [setDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setDate-java.util.Date-) класса MailMessage мы устанавливаем дату и время электронной почты.
- **Приоритет сообщения** - класс [MailPriority](https://reference.aspose.com/email/java/com.aspose.email/mailpriority/) задает уровни приоритета для отправки сообщения электронной почты. Это может быть низким, нормальным или высоким. Приоритет влияет на скорость передачи и доставку.
- **Чувствительность сообщения** - класс [MailSensitivity](https://reference.aspose.com/email/java/com.aspose.email/mailsensitivity/) задает пять уровней чувствительности.
- **Уведомление о доставке** - Уведомления о доставке сообщают отправителям, что электронное письмо, которое они отправили, было доставлено в почтовый ящик получателя.

По умолчанию дата — это фактическая дата, когда сообщение было отправлено, и время — это время, когда оно было отправлено, как отображается в Microsoft Outlook. Однако реальное время доставки электронной почты добавляется самим SMTP-сервером в заголовок письма. Например, ниже приведен общий заголовок письма, где поле Дата было установлено с использованием MailMessage.setDate.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-DateAndTime-DateAndTime.cs" >}}

Ниже приведенный фрагмент кода иллюстрирует, как можно использовать каждую из обсуждаемых выше функций.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-UseMailMessageFeatures-MailMessageFeatures.java" >}}

## **Запрос подтверждения прочтения**

Программные примеры ниже показывают, как вы можете запросить подтверждение прочтения. Перечисление свойства [DeliveryNotificationOptions](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDeliveryNotificationOptions--) класса MailMessage описывает [варианты уведомления о доставке](https://reference.aspose.com/email/java/com.aspose.email/deliverynotificationoptions/) для электронной почты. Чтобы запросить подтверждение прочтения после отправки электронного письма, выполните следующие шаги:

1. Создайте экземпляр класса MailMessage.
1. Укажите отправителя, получателя и HTML тело для электронного письма в экземпляре MailMessage.
1. Укажите DeliveryNotificationOptions в других экземплярах MailMessage.
2. Создайте экземпляр класса SmtpClient и отправьте электронное письмо, используя метод Send.

Запросы на подтверждение прочтения могут не всегда выполняться, потому что:

- Почтовый клиент может не реализовывать эту функцию.
- Конечный пользователь может отключить эту функцию.
- Конечный пользователь может выбрать не отправлять его.

Следующий фрагмент кода показывает, как запросить подтверждение прочтения.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-RequestReadReceipt-RequestReadReceipt.java" >}}

## **Установка заголовков электронной почты**

Заголовки электронной почты представляют собой интернет-стандарт, а RFC определяет поля заголовков, которые включены в интернет-сообщения электронной почты. Заголовок электронной почты можно указать с помощью класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) . Общие типы заголовков определены в классе [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/) . Это запечатанный класс, который работает как обычная перечисляемая переменная.

Обычно заголовок электронной почты содержит следующие поля:

- Кому: адреса получателей могут быть указаны в поле **Кому**. Получатели в поле **Кому** являются основной аудиторией сообщения. Может быть более одного адреса получателя.
- От: Это поле представляет собой адрес электронной почты отправителя сообщения.
- Копия: Позволяет пользователям отправить сообщение как "углеродную копию" или "вежливую копию". То есть от получателя не ожидается, что он ответит или что-то сделает. Обычно с помощью CC уведомляется руководство.
- Скрытая копия: это означает скрытую углеродную копию, относится к практике отправки сообщения нескольким получателям таким образом, что то, что они получают, не содержит полного списка получателей. Это предназначено для скрытого уведомления.
- Ответить: Это поле заголовка предназначено для указания, куда отправитель хочет, чтобы ответы отправлялись.
- Тема: Заголовок, заголовок, предмет. Часто используется как индикатор темы для сообщений, отвечающих на другие сообщения или комментирующих их.
- Дата: Этот заголовок указывает дату (и время). Обычно это дата, когда сообщение было составлено и отправлено.
- XMailer: Информация о программном обеспечении клиента отправителя. Пример: X-Mailer: Aspose.Email. XMailer используется почтовыми клиентами. У разных почтовых клиентов будут разные значения XMailer. Значение XMailer для MS Outlook - Microsoft Office Outlook, Build 11.0.5510. Его игнорирует получатель электронной почты или почтовый читатель.

Обычно заголовок электронной почты выглядит следующим образом:

``` cs

 Ответить-на: reply@reply.com

От: sender@sender.com

Кому: guangzhou@guangzhoo.com

Тема: тестовое письмо

Дата: 6 Мар 2006 8:2:2 +0800

X-Mailer: Aspose.Email

```

Чтобы настроить заголовок электронной почты, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
- Укажите адреса Получателя, Отправителя, Копии, Скрытой копии, Ответить, Тему, Дата и XMailer, используя экземпляр класса MailMessage.
- Создайте экземпляр класса [MimeHeader](https://reference.aspose.com/email/java/com.aspose.email/mimeheader/) и укажите секретный заголовок.
- Добавьте секретный заголовок в экземпляр MailMessage.

В приведенном ниже коде мы настроили заголовок электронной почты.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-SetEmailHeaders.java" >}}

Приведенный выше фрагмент кода создает заголовок электронной почты в следующем формате. Это можно наблюдать, открыв файл MsgHeaders.msg в Microsoft Outlook и затем просмотрев его свойства.

``` cs

 Ответить-на: reply@reply.com

От: sender@sender.com

Кому: receiver1@receiver.com

Копия: receiver2@receiver.com

Скрытая копия: receiver3@receiver.com

Тема: тестовое письмо

Дата: 6 Мар 2006 8:2:2 +0800

X-Mailer: Aspose.Email

секретный-заголовок: mystery

```

### **Вставка заголовка в конкретное место**

Метод [Add](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#add-com.aspose.email.HeaderCollection-) коллекции заголовков добавляет заголовок в конец коллекции. Однако иногда может быть необходимо вставить заголовок в конкретное место. В этом случае метод Add не поможет. Для достижения этой цели используйте метод [Insert](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#insert-java.lang.String-java.lang.String-) коллекции заголовков. Если коллекция содержит заголовки с одинаковым именем, этот заголовок будет вставлен перед другими заголовками с одинаковым именем. Следующий метод Insert и пример кода для использования.

``` java

 Подпись метода

HeaderCollection.insert(String name, String value)

```

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-InsertHeaderAtSpecificLocation.java" >}}

### **Добавление пользовательских заголовков к электронной почте**

Программные примеры ниже демонстрируют, как указать пользовательский заголовок в сообщении электронной почты. Заголовок электронной почты можно указать с помощью класса MailMessage. Чтобы указать пользовательский заголовок в сообщении электронной почты, выполните следующие действия:

1. Создайте экземпляр класса MailMessage.
1. Укажите значения «Кому», «От» и «Тема», используя экземпляр MailMessage.
1. Добавьте секретный заголовок в экземпляр MailMessage.
1. Создайте экземпляр класса SmtpClient и отправьте электронное письмо, используя метод Send.

Следующий фрагмент кода показывает, как добавить пользовательские заголовки к электронной почте.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyCustomHeader-SpecifyCustomHeader.java" >}}

## **Подписание писем с помощью DKIM**

Aspose.Email позволяет подписывать электронные письма с помощью DKIM (идентификация ключей домена). Это позволяет организации взять на себя ответственность за сообщение, находящееся в транзите ([о DKIM](https://www.dkim.org/)). DKIM добавляет цифровую подпись к заголовкам сообщения электронной почты, которую могут подтвердить получатели. Открытый ключ отправителя позволяет получателю проверить, что подпись совпадает с содержимым сообщения. Метод класса MailMessage [dKIMSign](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#dKIMSign-com.aspose.ms.System.Security.Cryptography.RSACryptoServiceProvider-com.aspose.email.DKIMSignatureInfo-) используется для установки криптографической и подписи информации для подписи сообщения. Следующий фрагмент кода показывает, как подписывать электронные письма с помощью DKIM.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SignEmailsWithDKIM-SignEmailsWithDKIM.java" >}}

## **Выполнение объединения почты**

Объединение почты помогает создать и отправить партию аналогичных электронных сообщений. Основное содержание электронных писем остается неизменным, но содержимое может быть персонализировано. Обычно для персонализации электронной почты используются контактные данные получателя (имя, фамилия, компания и т.д.).

|![todo:image_alt_text](https://i.imgur.com/D7WSp90.png)|
| :- |
|**Рисунок: Иллюстрация работы объединения почты**|

Чтобы выполнить объединение почты с Aspose.Email, выполните следующие шаги:

1. Создайте функцию с сигнатурой имени.
1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Укажите отправителя, получателя, тему и тело.
1. Создайте подпись для конца электронного письма.
1. Создайте экземпляр класса [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) и передайте ему экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Получите подпись в экземпляре [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) .
1. Создайте экземпляр класса [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Добавьте столбцы Receipt, FirstName и LastName в качестве источников данных в классе DataTable.
1. Создайте экземпляр класса [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Укажите адрес получения, имя и фамилию в объекте DataRow.
1. Создайте экземпляр класса [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Укажите экземпляры [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) и DataTable в экземпляре [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
2. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и укажите сервер, порт, имя пользователя и пароль.
3. Отправьте электронные письма, используя метод BulkSendAsync класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .

Код ниже отправляет электронное письмо одному человеку от трех других.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-PerformMailMerge-.java" >}}