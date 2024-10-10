---
title: "Создание и установка содержимого электронных писем в .NET"
url: /ru/net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Создание и установка содержимого электронных писем"
---

## **Создание нового электронного сообщения**

Чтобы создать новое электронное сообщение, вы можете использовать класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Класс **MailMessage** также инициализирует свойства создаваемого электронного сообщения, такие как адрес электронной почты отправителя, адреса электронной почты получателей, тему письма и содержимое тела письма в формате HTML.

Рассмотрим следующий код с детальными шагами для создания нового электронного сообщения и установки его свойств.

**Шаги кода:**

1. Создайте новый экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Установите свойство [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) на адрес электронной почты отправителя.
3. Установите свойство [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) на список адресов электронной почты получателей, разделенных запятыми.
4. Установите свойство [Subject](https://reference.aspose.com/email/net/aspose.email/mailmessage/subject/) на тему письма.
5. Установите свойство [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) на содержимое тела письма в HTML.

**Пример кода:**
```cs
// Создайте новый экземпляр класса MailMessage
var message = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "Новое сообщение",
    HtmlBody = @"<!DOCTYPE html>
    <html>
     <head>
      <style>
       h3{font-family:Verdana, sans-serif;color:#000000;background-color:#ffffff;}
       p {font-family:Verdana, sans-serif;font-size:14px;font-style:normal;
         font-weight:normal;color:#000000;background-color:#ffffff;}
      </style>
     </head>
     <body>
       <h3>Новое сообщение</h3>
       <p>Это новое сообщение, созданное с помощью Aspose.Email.</p>
     </body>
    </html>"
};
```

## **Указание нескольких получателей**

Существует три способа указать получателей электронного сообщения: используя поля **To**, **CC** или **BCC**.

- Поле **To** является основным получателем вашего сообщения. Вы можете ввести один или несколько адресов электронной почты в это поле, разделенных запятыми. Поле To является обязательным для каждого электронного сообщения.

- Поле **CC** означает "копия". Оно используется для отправки копии вашего сообщения другим людям, заинтересованным или вовлеченным в тему. Поле CC является необязательным и также может содержать несколько адресов электронной почты. Получатели в поле CC могут видеть, кто еще получил сообщение.

- Поле **BCC** обозначает "слепая копия". Оно похоже на поле CC, но получатели в поле BCC скрыты от других получателей. Поле BCC полезно, когда вы хотите защитить конфиденциальность некоторых получателей или избежать переполнения их почтового ящика ответами. Поле BCC также является необязательным и может иметь несколько адресов электронной почты.

Рассмотрим следующий код с детальными шагами для указания нескольких получателей для электронного сообщения.

**Шаги кода:**

1. Создайте новый экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Установите свойство [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) на адрес электронной почты отправителя.
3. Установите свойство [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) на массив адресов электронной почты основных получателей.
4. Установите свойство [CC](https://reference.aspose.com/email/net/aspose.email/mailmessage/cc/) на массив адресов электронной почты получателей, которые получат копию письма.
5. Установите свойство [Bcc](https://reference.aspose.com/email/net/aspose.email/mailmessage/bcc/) на массив адресов электронной почты получателей, которые получат слепую копию письма.

**Пример кода:**

```cs
var eml = new MailMessage
{
    // Указать адрес From
    From = "sender@sender.com",
    // Указать адреса электронной почты получателей
    To = {"receiver1@receiver.com", "receiver2@receiver.com", "receiver3@receiver.com"},
    // Указать адреса CC
    CC = {"CC1@receiver.com", "CC2@receiver.com"},
    // Указать адреса BCC
    Bcc = {"Bcc1@receiver.com", "Bcc2@receiver.com"}
};
```

## **Добавление отображаемых имен к адресам электронной почты**

Вместе с адресом электронной почты может быть включено **отображаемое имя**, чтобы идентифицировать отправителя или получателя письма. Оно может содержать полное имя человека, прозвище или другой идентификатор.

Когда электронное сообщение отображается в почтовом клиенте или веб-интерфейсе, отображаемое имя обычно показывается рядом с адресом электронной почты, что облегчает пользователю идентификацию, от кого пришло сообщение или кому оно адресовано. Например, адрес электронной почты может быть "johndoe@example.com", но связанное с ним отображаемое имя может быть "John Doe".

Чтобы добавить отображаемые имена к адресам электронной почты в электронном сообщении, рассмотрим следующий код с детальными шагами:

**Шаги кода:**

1. Загрузите электронное сообщение из файла, используя метод [MailMessage.Load]() .
2. Установите отправителя письма, используя свойство [From]() объекта eml, создав новый объект [MailAddress]() с адресом электронной почты и отображаемым именем отправителя.
3. Добавьте получателя к электронной почте, используя свойство [To]() объекта eml, при необходимости добавьте список CC (копия) с помощью свойства [CC](), список BCC (слепая копия) с помощью свойства [Bcc]() и вызовите метод [Add]() с новым объектом [MailAddress](), который содержит адрес электронной почты и отображаемое имя получателя.

**Пример кода:**

```cs
// Загрузите eml из файла
MailMessage eml = MailMessage.Load(Data.Email/"test.eml");

eml.From = new MailAddress("TimothyFairfield@from.com", "Timothy Fairfield");

// Адрес To с отображаемым именем также можно указать так
eml.To.Add(new MailAddress("kyle@to.com", "Kyle Huang"));

// Укажите адреса Cc и Bcc, а также отображаемые имена
eml.CC.Add(new MailAddress("guangzhou@cc.com", "Guangzhou Team"));
eml.Bcc.Add(new MailAddress("ahaq@bcc.com", "Ammad ulHaq "));
```
## **Отображение необязательных участников в заголовке вывода mht**

Следующий пример кода демонстрирует, как использовать функцию *отображения необязательных участников* при сохранении сообщения в формате mhtml:

```cs
MhtSaveOptions options = new MhtSaveOptions()
{
    MhtFormatOptions = MhtFormatOptions.RenderCalendarEvent | MhtFormatOptions.WriteHeader
};

MapiMessage msg = MapiMessage.Load(fileName);
msg.Save(fileName + ".mhtml", options);

// если вам нужно пропустить OptionalAttendees в mhtml-файле, вы можете очистить формат шаблона для OptionalAttendees
options.FormatTemplates[MhtTemplateName.OptionalAttendees] = "";
msg.Save(fileName + "2.mhtml", options);
```

## **Установка тела письма**

В этой статье вы узнаете, как:

- [установить текстовое тело](#Set-Plain-Text-Body)
- [установить HTML-тело](#Setting-HTML-Body)
- [установить альтернативный текст](#Setting-Alternate-Text)
- [указать кодировку тела письма](#Specifying-Mail-Body-Encoding)

### **Установка текстового тела**

Тело письма можно указать с использованием свойства [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

```cs
// Объявите сообщение как экземпляр MailMessage
var eml = new MailMessage
{
    // Укажите HtmlBody
    Body = "Это текстовое тело"
};
```

### **Установка HTML-тела**

Тело письма также можно указать с использованием свойства [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

```cs
// Объявите сообщение как экземпляр MailMessage
var eml = new MailMessage
{
    // Укажите HtmlBody
    HtmlBody = "<html><body>Это HTML тело</body></html>"
};
```

### **Установка альтернативного текста**

Альтернативный вид в файле EML – это дополнительное представление содержимого электронного письма, которое можно использовать для предоставления другого рендеринга электронного сообщения. Например, если вы отправляете сообщение в HTML, вы также можете предоставить версию **в текстовом формате** на случай, если некоторые из получателей используют почтовые клиенты, которые не могут отображать HTML-содержимое. Для этой цели используйте класс [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/). Этот класс имеет два свойства, [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) и [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/), которые используются для разрешения URL-адресов в содержимом электронной почты.

- [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) – это коллекция объектов [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/). При рендеринге URL в содержимом электронной почты сначала сопоставляются с URL в компоненте Content Link каждого объекта [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) в коллекции [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) и разрешаются.
- [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/) используется почтовым читателем для разрешения относительных URL в теле, а также для разрешения относительных URL компонент Content Link в коллекции [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/).

Рассмотрим следующий код с детальными шагами для установки альтернативного текста.

**Шаги кода:**

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Создайте [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/createalternateviewfromstring/) для просмотра электронного сообщения, используя содержимое, указанное в строке.
3. Добавьте альтернативный текст, используя метод [Add](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/) коллекции [MailMessage.AlternateViews](https://reference.aspose.com/email/net/aspose.email/mailmessage/alternateviews/).

**Пример кода:**
```cs
// Объявите сообщение как экземпляр MailMessage
var eml = new MailMessage();

// Создает AlternateView для просмотра электронного сообщения, используя содержимое, указанное в строке
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Альтернативный текст");

// Добавление альтернативного текста
 eml.AlternateViews.Add(alternate);
```

### **Указание кодировки тела письма**

Aspose.Email использует свойство [BodyEncoding](https://reference.aspose.com/email/net/aspose.email/mailmessage/bodyencoding/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) для указания кодировки тела письма. Например:

```cs
eml.BodyEncoding = Encoding.UTF8;
```

## **Установка дополнительных свойств MailMessage**

С помощью Aspose.Email вы можете использовать дополнительные свойства класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) такие как:

- [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) — свойство, устанавливающее **дату и время** электронного письма. По умолчанию дата — это фактическая дата, когда было отправлено сообщение, а время — время, в которое оно было отправлено, как отображает Microsoft Outlook. Тем не менее, фактическое время доставки электронной почты добавляется самим SMTP-сервером в заголовок письма. Например, ниже приведен обычный заголовок письма, где [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) устанавливает поле Date.

   ```cs
   // Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-.NET
   
   // Добавлено SMTP-сервером при доставке писем
   Received: from ip-123.56.99.216.dsl-cust.ca.inter.net ([216.99.56.123]) by Aspose.secureserver.net with MailEnable ESMTP; Thu, 22 Feb 2007 13:58:57 -0700
   
   // Добавлено SMTP-сервером при доставке писем
   Return-Path: <xyz@oikoscucine.it>
   
   // Добавлено SMTP-сервером при доставке писем
   Received: from 195.120.225.20 (HELO mail.oikoscucine.it)
   by aspose.com with esmtp (:1CYY+<LA*- *1WK@)
   id Q8,/O/-.N83@7-9M
   for abc@aspose.com; Thu, 22 Feb 2007 20:58:51 +0300
   From: "XYZ" <xyz@oikoscucine.it>
   To: <abc@aspose.com>
   Subject: Для ABC
   
   // Дата будет установлена в поле Date, Outlook покажет это как
   Date: Thu, 22 Feb 2007 20:58:51 +0300
   Message-ID: <01c756c4$41b554d0$6c822ecf@dishonestyinsufferably>
   MIME-Version: 1.0
   Content-Type: multipart/alternative;
   boundary="----=_NextPart_000_0006_01C7569A.58DF4CD0"
   X-Mailer: Microsoft Office Outlook, Build 11.0.5510
   X-MimeOLE: Produced By Microsoft MimeOLE V6.00.2800.1106
   Thread-Index: Aca6Q:=ES0M(9-=(<.<1.<Q9@QE6CD==
   X-Read: 1
   ```

- [MailPriority](https://reference.aspose.com/email/net/aspose.email/mailpriority/#mailpriority-enumeration) перечисление — указывает приоритеты для отправки электронного сообщения. Он может быть низким, нормальным или высоким. Приоритет влияет на скорость передачи и доставку.
- [MailSensitivity](https://reference.aspose.com/email/net/aspose.email/mailsensitivity/#mailsensitivity-enumeration) перечисление — указывает пять уровней чувствительности.
- [XMailer](https://reference.aspose.com/email/net/aspose.email/mailmessage/xmailer/) — указывает на программное обеспечение, которое создало электронное сообщение.

Следующий фрагмент кода иллюстрирует, как каждое из вышеупомянутых свойств может быть использовано.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Некоторый заголовок", "Некоторый текст тела")
{
    Date = DateTime.Now,
    Priority = MailPriority.High,
    Sensitivity = MailSensitivity.Normal,
    Xmailer = "Aspose.Email"
};
```

## **Запрос на получение подтверждения прочтения**

Чтобы запросить [подтверждение прочтения](https://en.wikipedia.org/wiki/Return_receipt), используйте свойство Aspose.Email [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/mailmessage/deliverynotificationoptions/) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Это свойство содержит значения перечисления [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/deliverynotificationoptions/#deliverynotificationoptions-enumeration).

Рассмотрим следующий **пример кода**:

```cs
// Создайте экземпляр класса MailMessage
var eml = new MailMessage
{
    // Укажите поля From, To, HtmlBody, DeliveryNotificationOptions
    From = "sender@sender.com",
    To = "receiver@receiver.com",
    HtmlBody = "<html><body>Это HTML тело</body></html>",
    DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess
};

eml.Headers.Add("Return-Receipt-To", "sender@sender.com");
eml.Headers.Add("Disposition-Notification-To", "sender@sender.com");

// Создайте экземпляр класса SmtpClient
var client = new SmtpClient
{
    // Укажите ваш хост почтового сервера, имя пользователя, пароль и номер порта
    Host = "smtp.server.com",
    Username = "Username",
    Password = "Password",
    Port = 25
};

try
{
    // Client.Send отправит это сообщение
    client.Send(eml);
    // Отобразить 'Сообщение отправлено', только если сообщение было успешно отправлено
    Console.WriteLine(@"Сообщение отправлено");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

**Примечание**: Запросы на получение подтверждения прочтения могут не всегда выполняться, потому что:

- Почтовый клиент может не реализовывать эту функциональность.
- У конечного пользователя может быть отключена эта функция.
- Конечный пользователь может выбрать, чтобы не отправлять его.

## **Установка заголовков электронного письма**

Заголовки электронных писем представляют собой интернет-стандарт, и RFC определяет поля заголовков, которые включаются в интернет-сообщения. Заголовок email можно указать с помощью класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Общие типы заголовков определены в классе [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/). Это запечатанный класс, работающий как обычное перечисление.

Как правило, заголовок электронного письма содержит следующие поля:

- **To**: Адреса получателей могут быть указаны в поле To. Получатели поля To являются основной аудиторией сообщения. Может быть больше одного адреса получателя.
- **From**: Это поле представляет собой адрес электронной почты отправителя сообщения.
- **Cc**: Позволяет пользователям отправлять сообщение в виде "Carbon Copy" или "Courtesy Copy". То есть, от получателя не ожидается ответ или действие. Обычно надзорный персонал уведомляется с помощью CC.
- **Bcc**: Это означает Blind Carbon Copy, который позволяет отправить электронное письмо получателю, скрытому от других получателей.
- **ReplyTo**: Это поле заголовка предназначено для указания, куда отправитель хочет, чтобы шли ответы.
- **Subject**: Заголовок, заглавие, тема. Часто используется как индикатор потока для сообщений, отвечающих на или комментирующих другие сообщения.
- **Date**: Этот заголовок указывает дату (и время). Обычно это дата, когда сообщение было составлено и отправлено.
- **XMailer**: Информация о клиентском ПО инициатора. Пример: X-Mailer: Aspose.Email. XMailer используется почтовыми клиентами. Разные почтовые клиенты будут иметь разные значения XMailer. Значение XMailer MS Outlook — Microsoft Office Outlook, Build 11.0.5510. Оно игнорируется получателем электронного письма или читателем почты.

Как правило, заголовок электронного письма выглядит примерно так:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: тестовое письмо
Date: 6 Марта 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

Чтобы настроить заголовок электронного письма, следуйте этим **шагам кода**:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Укажите To, From, Cc, Bcc, ReplyTo, Subject, Date и XMailer, используя экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Создайте экземпляр класса [MimeHeader](https://reference.aspose.com/email/net/aspose.email.mime/mimeheader/) и укажите пользовательский заголовок.
- Добавьте пользовательский заголовок к экземпляру [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

Следующий **пример кода** показывает, как установить заголовки электронной почты.

```cs
var eml = new MailMessage
{
    ReplyToList = "reply@reply.com",
    From = "sender@sender.com",
    To = "receiver1@receiver.com",
    CC = "receiver2@receiver.com",
    Bcc = "receiver3@receiver.com",
    Subject = "тестовое письмо",
    Date = new System.DateTime(2006, 3, 6),
    XMailer = "Aspose.Email"
};
```

Вышеуказанный фрагмент кода создает заголовок электронного письма в следующем формате:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: тестовое письмо
Date: 6 Марта 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

### **Вставка заголовка в конкретное место**

Метод [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) класса [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/) вставляет заголовок в конец коллекции. Тем не менее, иногда может быть необходимо вставить заголовок в конкретное место. В таком случае метод [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) не поможет. Чтобы добиться этого, используйте метод [Insert](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/insert/#insert) класса [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/). Если коллекция содержит заголовки с одинаковым именем, этот заголовок будет вставлен перед другими заголовками с таким же именем. Следующий фрагмент кода показывает, как вставить заголовок в конкретное место.

```cs
eml.Headers.Insert("Received", "Value");
```

### **Сохранение всех заголовков в MHTML**

Свойство [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/#mhtsaveoptionssaveallheaders-property) класса [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) определяет необходимость сохранить все заголовки в выходном mhtml или нет. Следующий фрагмент кода показывает, как сохранить все заголовки файла mhtml:

```cs
var eml = MailMessage.Load("message.eml");
var sopt = SaveOptions.DefaultMhtml;
sopt.SaveAllHeaders = true;
eml.Save("message.mhtml", sopt);
```

### **Добавление пользовательских заголовков к электронному письму**

Заголовок электронного письма можно указать с помощью класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Чтобы указать **пользовательский заголовок** в электронном сообщении, рассмотрите следующий образец кода:

```cs
eml.Headers.Add("secret-header", "mystery");
```

Вышеуказанный фрагмент кода создает заголовок электронной почты в следующем формате:

```cs
secret-header: mystery
```

## **Сохранение HTML-файла с полями задачы в заголовке**

Перечисление [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) позволяет вам указать, что поля задач должны быть включены в заголовок сохраняемого HTML-файла. Следующий фрагмент кода показывает, как сохранить поля задач в заголовке при сохранении HTML-файла:

```cs
var msg = MapiMessage.Load("task.msg");
HtmlSaveOptions opt = SaveOptions.DefaultHtml;
opt.HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderTaskFields;
msg.Save("task.html", opt);
```

## **Подписание электронных писем с помощью DKIM**

> **_ПРИМЕЧАНИЕ:_** Эта функция доступна только для версий библиотеки, нацеленных на .NET Framework. Версии, нацеленные на .NET Core, не имеют этой функции.

Aspose.Email позволяет подписывать электронную почту с помощью DKIM (DomainKeys Identified Mail). Это позволяет организации взять на себя ответственность за сообщение, находящееся в транзите ([Дополнительная информация](https://www.dkim.org/)). DKIM добавляет цифровую подпись к заголовкам электронного сообщения, которую могут проверять получатели. Открытый ключ отправителя позволяет получателю подтвердить, что подпись соответствует содержимому сообщения. Метод [DKIMSign](https://reference.aspose.com/email/net/aspose.email/mailmessage/dkimsign/#dkimsign) класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) используется для установки криптографической информации и информации о подписи для подписания сообщения. Следующий фрагмент кода показывает, как подписать электронные письма с помощью DKIM.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Некоторый заголовок", "Некоторый текст тела");

string privateKeyFile = "key2.pem";
RSACryptoServiceProvider rsa = PemReader.GetPrivateKey(privateKeyFile);
DKIMSignatureInfo signInfo = new DKIMSignatureInfo("test", "somedomain.com");

var signedEml = eml.DKIMSign(rsa, signInfo);
```