---
title: "Создание и настройка содержимого электронных писем"
url: /ru/java/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---

## **Создать новое сообщение электронной почты**

Aspose.Email для Java позволяет разработчикам создавать сообщения MIME (многоцелевые расширения электронной почты Интернета) с нуля. Основным классом для этой цели в API Aspose.Email для Java является [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс.
В этом разделе описаны шаги, необходимые для создания сообщений электронной почты в форматах файлов EML, MSG и MTH с использованием Aspose.Email для Java.

Чтобы создать сообщение электронной почты с нуля, выполните следующие действия:

1. Создайте экземпляр класса MailMessage.
2. Задайте тему сообщения, используя [setSubject()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setSubject-java.lang.String-) method.
3. Задайте тело сообщения, используя [setHtmlBody()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) method.
4. Настройте отправителя электронной почты, используя [setFrom()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setFrom-com.aspose.email.MailAddress-) method.
5. Укажите получателя в поле **TO** поле, используя [getTo().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) method.
6. Укажите получателя в поле **CC** поле, используя [getCC().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) method.
7. Позвоните [Save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.io.OutputStream-) метод сохранения файла сообщения на диск в форматах MSG, EML и MHT.
 
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-CreateNewEmail-.java" >}}

## **Указание нескольких получателей**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) представляет собой сообщение электронной почты. Экземпляры класса MailMessage используются для создания сообщений электронной почты, которые передаются на SMTP-сервер с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс. В этом разделе показано, как указать несколько адресов электронной почты. Адреса электронной почты можно указать с помощью класса MailMessage. В классе MailMessage используются следующие адреса электронной почты:

- **To** - Адреса получателей можно указать в поле «Кому». Получатели в поле «Кому» являются основной аудиторией сообщений. Адресов получателей может быть несколько
- **Cc** - CC расшифровывается как «точная копия» или «любезная копия» и позволяет добавлять получателей электронной почты, которым необходимо ознакомиться с письмом, но от которых не требуется никаких действий по нему. Например, руководители или члены вашей команды, которым необходимо быть в курсе разговоров. С помощью Aspose.Email в коде можно указать адреса CC. Таким образом, автоматические электронные письма или все электронные письма на определенный адрес могут быть скопированы соответствующему персоналу.
- **Bcc** - Bcc, «слепая копия», позволяет отправлять получателю электронное письмо, скрытое от других получателей. Если в информации по электронной почте, которую видят основные получатели, буква «CC» отображается, то в ней нет. Оно предназначено для скрытых уведомлений. 

Чтобы указать несколько адресов электронной почты в сообщении электронной почты, выполните следующие действия:

1. Создайте экземпляр класса MailMessage.
2. Укажите адрес From и несколько адресов To, Cc и Bcc, используя экземпляр MailMessage.
3. Создайте экземпляр класса SmtpClient и отправьте электронное письмо с помощью метода Send.

В приведенном ниже примере кода показано, как можно указать несколько адресов To, CC и BCC.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyRecipientAddresses-SpecifyRecipientAddresses.java" >}}

## **Изменение адресов электронной почты на понятное имя**

В приведенных ниже примерах программирования показано, как изменить адреса электронной почты на удобные имена в сообщении электронной почты. Дружественное имя — это имя, более удобное для пользователя, чем адрес электронной почты. Например, Джон Смит вместо js346@domain.com. При отправке электронного письма мы можем связать удобное имя с адресом электронной почты в поле [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) конструктор классов.

Чтобы изменить адреса электронной почты на удобные имена в сообщении электронной почты, выполните следующие действия:

- Создайте экземпляр класса MailMessage и укажите адреса электронной почты в поле **To** and **From** поля вместе с понятными именами.
- Укажите адреса электронной почты Cc и Bcc, а также удобные имена, вызвав конструктор класса MailMessage в экземпляре MailMessage.
- Создайте экземпляр класса SmtpClient и отправьте электронное письмо с помощью метода Send.

В следующем фрагменте кода показано, как отображать имена для адресов электронной почты.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ChangeEmailAddress-ChangeEmailAddress.java" >}}

## **Установить тело письма**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс представляет собой сообщение электронной почты. Экземпляры класса MailMessage используются для создания сообщений электронной почты, которые передаются на SMTP-сервер для доставки с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс. Текст письма можно указать с помощью класса MailMessage. Тело электронного письма можно указать с помощью [setHtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) метод в MailMessage.

В дополнение к [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), Aspose.Email имеет другой метод, связанный с телом письма:

- [isBodyHtml](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isBodyHtml--): сообщает пользователю, является ли текст текстом HTML или обычным текстом.

В этом разделе показано, как определить основной текст HTML и задать альтернативный текст.

### **Настройка тела HTML**

[HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) используется для указания HTML-содержимого тела сообщения. HTMLBody должен быть заключен между <html> </html> теги. В следующем фрагменте кода показано, как настроить тело HTML.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetHTMLBody-SetHTMLBody.java" >}}

### **Настройка альтернативного текста**

Используйте [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) класс для указания копий сообщения электронной почты в другом формате. Например, если вы отправляете сообщение в формате HTML, вы также можете захотеть предоставить текстовую версию на случай, если некоторые из получателей используют программы чтения электронной почты, которые не могут отображать содержимое HTML. У этого класса есть два свойства: [LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getLinkedResources--) and [BaseUri](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getBaseUri--), которые используются для разрешения URL-адресов в содержимом электронного письма.

- LinkedResources — это набор объектов LinkedResources. При рендеринге URL-адреса в содержимом электронного письма сначала сопоставляются с URL-адресами в ссылке на содержимое каждого объекта LinkedResources в коллекции LinkedResources, а затем обрабатываются.
- BaseURI используется программой чтения почты для разрешения относительных URL-адресов в тексте, а также для разрешения относительных URL-адресов ссылок на содержимое в коллекции LinkedResources.

В следующем фрагменте кода показано, как задать альтернативный текст.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetAlternateText-SetAlternateText.java" >}}

## **Указание кодировки текста письма**

Тип содержимого определяет формат содержимого электронного письма: набор символов. Например, в java.nio.Charset есть несколько распространенных наборов символов:

- US-ASCII — семибитный ASCII, также известный как ISO646-US, также известный как базовый латинский блок набора символов Unicode
- ISO-8859-1 - латинский алфавит ИСО № 1, также известный как ISO-LATIN-1
- UTF-8 — восьмибитный формат преобразования UCS
- UTF-16BE - шестнадцатибитный формат преобразования UCS, порядок байтов с обратным порядком байтов
- UTF-16LE - шестнадцатибитный формат преобразования UCS, порядок байтов с прямым порядком байтов
- UTF-16 — шестнадцатибитный формат преобразования UCS, порядок байтов определяется дополнительным знаком порядка байтов

Aspose.Email использует [BodyEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBodyEncoding--) свойство класса MailMessage для указания кодировки текста письма. Чтобы закодировать текст сообщения электронной почты, выполните следующие действия:

1. Создайте экземпляр класса MailMessage.
1. Укажите отправителя, получателя и текст письма в формате HTML в экземпляре MailMessage.
1. Укажите значение свойства BodyEncoding.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и отправьте электронное письмо с помощью метода Send.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyMailBodyEncoding-SpecifyMailBodyEncoding.java" >}}

## **Функции почтовых сообщений**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс представляет собой содержимое сообщения электронной почты. Экземпляры класса MailMessage используются для создания сообщения электронной почты, которое передается на SMTP-сервер для доставки с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс. В этой статье показано, как использовать служебные функции класса MailMessage для управления следующими функциями электронной почты:

- **Дата и время** - Через класс MailMessage [setDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setDate-java.util.Date-) метод: мы устанавливаем дату и время электронного письма.
- **Приоритет сообщений** - [MailPriority](https://reference.aspose.com/email/java/com.aspose.email/mailpriority/) класс определяет уровни приоритета для отправки сообщения электронной почты. Он может быть низким, нормальным или высоким. Приоритет влияет на скорость передачи и доставку.
- **Чувствительность сообщений** - [MailSensitivity](https://reference.aspose.com/email/java/com.aspose.email/mailsensitivity/) класс определяет пять уровней чувствительности.
- **Уведомление о доста** - Уведомления о доставке сообщают отправителям, что отправленное ими электронное письмо было доставлено в почтовый ящик получателя.

По умолчанию дата — это фактическая дата отправки сообщения, а время — время отправки, отображаемое в Microsoft Outlook. Однако реальное время доставки электронной почты добавляется самим SMTP-сервером в заголовке письма. Например, ниже приведен обычный заголовок письма, в котором поле Дата задано с помощью MailMessage.setDate.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-DateAndTime-DateAndTime.cs" >}}

Приведенный ниже фрагмент кода иллюстрирует, как можно использовать каждую из описанных выше функций.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-UseMailMessageFeatures-MailMessageFeatures.java" >}}

## **Запрос квитанции о прочтении**

В приведенных ниже примерах программирования показано, как можно запросить квитанцию о прочтении. Класс MailMessage [DeliveryNotificationOptions](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDeliveryNotificationOptions--) Свойство Enumeration описывает [варианты уведомления о доставке](https://reference.aspose.com/email/java/com.aspose.email/deliverynotificationoptions/) для электронного письма. Чтобы запросить квитанцию о прочтении после отправки электронного письма, выполните следующие действия:

1. Создайте экземпляр класса MailMessage.
1. Укажите отправителя, получателя и текст HTML для электронного письма в экземпляре MailMessage.
1. Укажите параметры DeliveryNotificationOptions в других экземплярах MailMessage.
2. Создайте экземпляр класса SmtpClient и отправьте электронное письмо с помощью метода Send.

Запросы на получение квитанции о прочтении могут быть выполнены не всегда по следующим причинам:

- Почтовый клиент может не реализовать эту функциональность.
- У конечного пользователя эта функция может быть отключена.
- Конечный пользователь может отказаться от отправки.

В следующем фрагменте кода показано, как запросить квитанцию о прочтении.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-RequestReadReceipt-RequestReadReceipt.java" >}}

## **Настройка заголовков электронной почты**

Заголовки электронных писем представляют собой стандарт Интернета, а RFC определяет поля заголовков, которые включаются в сообщения электронной почты Интернета. Заголовок электронного письма можно указать с помощью [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс. Общие типы заголовков определены в поле [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/) класс. Это запечатанный класс, который работает как обычное перечисление.

Обычно заголовок электронного письма содержит следующие поля:

- Кому: адреса получателей можно указать в поле **To** поле. **To** получатели поля — основная аудитория сообщения. Адресов получателей может быть несколько.
- От: в этом поле указан адрес электронной почты отправителя сообщения.
- Cc: позволяет пользователям отправлять сообщения в виде «точной копии» или «любезной копии». То есть получатель не должен отвечать или действовать. Как правило, руководящий персонал уведомляется с помощью CC.
- Bcc: расшифровывается как Blind Carbon Copy и означает практику отправки сообщения нескольким получателям таким образом, чтобы полученное сообщение не содержало полного списка получателей. Оно предназначено для скрытого уведомления.
- ReplyTo: это поле заголовка предназначено для указания того, куда отправитель хочет отправить ответы.
- Тема: Заголовок, заголовок, тема. Часто используется в качестве индикатора темы для сообщений, отвечающих на другие сообщения или комментирующих их.
- Дата: в этом заголовке указаны дата (и время). Обычно это дата составления и отправки сообщения.
- XMailer: информация о клиентском программном обеспечении автора. Пример: программа X-Mailer: Aspose.Email. XMailer используется почтовыми клиентами. Разные почтовые клиенты будут иметь разные значения XMailer. Значение XMailer в MS Outlook — Microsoft Office Outlook, сборка 11.0.5510. Получатель электронной почты или программа для чтения электронной почты игнорируют его.

Обычно заголовок электронного письма выглядит следующим образом:

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: guangzhou@guangzhoo.com

Subject: test mail

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

```

Чтобы настроить заголовок электронного письма, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Укажите «Кому», «От», «CC», «Bcc», «ReplyTo», «Тема», «Дата» и «XMailer», используя экземпляр класса MailMessage.
- Создайте экземпляр [MimeHeader](https://reference.aspose.com/email/java/com.aspose.email/mimeheader/) класс и укажите секретный заголовок.
- Добавьте секретный заголовок в экземпляр MailMessage.

В приведенном ниже коде мы настроили заголовок электронного письма.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-SetEmailHeaders.java" >}}

Приведенный выше фрагмент кода создает заголовок электронного письма в следующем формате. Это можно увидеть, открыв файл MsgHeaders.msg в Microsoft Outlook и просмотрев его свойства.

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: receiver1@receiver.com

CC: receiver2@receiver.com

BCC: receiver3@receiver.com

Subject: test mail

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

secret-header: mystery

```

### **Вставить заголовок в определенном месте**

The [Add](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#add-com.aspose.email.HeaderCollection-) метод headersCollection вставляет заголовок в конец коллекции. Однако иногда может потребоваться вставить заголовок в определенном месте. В таком случае метод Add не поможет. Для этого используйте [Insert](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#insert-java.lang.String-java.lang.String-) метод коллекции заголовков. Если коллекция содержит заголовки с одинаковыми именами, этот заголовок будет вставлен перед другими заголовками с таким же именем. Ниже приведена подпись метода Insert и пример кода для использования.

``` java

 Method Signature

HeaderCollection.insert(String name, String value)

```

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-InsertHeaderAtSpecificLocation.java" >}}

### **Добавление настраиваемых заголовков в электронное письмо**

В приведенных ниже примерах программирования показано, как указать пользовательский заголовок в сообщении электронной почты. Заголовок электронного письма можно указать с помощью класса MailMessage. Чтобы указать пользовательский заголовок в сообщении электронной почты, выполните следующие действия:

1. Создайте экземпляр класса MailMessage.
1. Укажите значения «кому», «от» и «тема», используя экземпляр MailMessage.
1. Добавьте секретный заголовок в экземпляр MailMessage.
1. Создайте экземпляр класса SmtpClient и отправьте электронное письмо с помощью метода Send.

В следующем фрагменте кода показано, как добавлять собственные заголовки в электронное письмо.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyCustomHeader-SpecifyCustomHeader.java" >}}

## **Подписывайте электронные письма с помощью DKIM**

Aspose.Email позволяет подписывать электронную почту с помощью DKIM (почта, идентифицированная доменными ключами). Это позволяет организации взять на себя ответственность за передаваемое сообщение ([о DKIM](https://www.dkim.org/)). DKIM добавляет цифровую подпись к заголовкам сообщений электронной почты, которую получатели могут проверить. Открытый ключ отправителя позволяет получателю проверить, соответствует ли подпись содержимому сообщения. Класс MailMessage [dKIMSign](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#dKIMSign-com.aspose.ms.System.Security.Cryptography.RSACryptoServiceProvider-com.aspose.email.DKIMSignatureInfo-) метод используется для задания криптографической и сигнатурной информации для подписи сообщения. В следующем фрагменте кода показано, как подписывать электронные письма с помощью DKIM.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SignEmailsWithDKIM-SignEmailsWithDKIM.java" >}}

## **Выполнение слияния писем**

Объединение писем позволяет создавать и отправлять пакеты похожих сообщений электронной почты. Суть писем одна и та же, но их содержимое можно персонализировать. Как правило, контактные данные получателя (имя, отчество, компания и т. д.) используются для персонализации письма.

|![todo:image_alt_text](https://i.imgur.com/D7WSp90.png)|
|: - |
|**Рис.: Иллюстрация того, как работает слияние писем**|

Чтобы выполнить слияние писем с помощью Aspose.Email, выполните следующие шаги:

1. Создайте функцию с подписью имени
1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Укажите отправителя, получателя, тему и тело.
1. Создайте подпись в конце письма.
1. Создайте экземпляр [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) класс и сдайте его [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Сделайте подпись в [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) instance.
1. Создайте экземпляр [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) class.
1. Добавьте столбцы Receipt, FirstName и LastName в качестве источников данных в классе DataTable
1. Создайте экземпляр [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) class
1. Укажите адрес получения, имя и фамилию в объекте DataRow
1. Создайте экземпляр [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class
1. Укажите [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) и экземпляры DataTable в [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) instance.
2. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и укажите сервер, порт, имя пользователя и пароль
3. Отправляйте электронные письма с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) метод класса BulkSendAsync

Приведенный ниже код отправляет электронное письмо одному человеку из трех других.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-PerformMailMerge-.java" >}}
