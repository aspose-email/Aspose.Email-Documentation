---
title: "Создание и настройка содержимого электронных писем в.NET"
url: /ru/net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Создание и настройка содержимого электронных писем"
---

## **Создать новое сообщение электронной почты**

Чтобы создать новое сообщение электронной почты, вы можете использовать [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. **MailMessage** класс также инициализирует свойства созданного сообщения электронной почты, такие как адрес электронной почты отправителя, адреса электронной почты получателей, тема письма и содержимое текста письма в формате HTML.

Рассмотрим следующий код с подробными инструкциями по созданию нового сообщения электронной почты и настройке его свойств.

**Этапы написания кода:**

1. Создайте новый экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Установите [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) свойство к адресу электронной почты отправителя.
3. Установите [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) свойство списка адресов электронной почты получателей, разделенных запятыми.
4. Установите [Subject](https://reference.aspose.com/email/net/aspose.email/mailmessage/subject/) свойство к теме письма.
5. Установите [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) свойство к HTML-содержимому тела письма.

**Пример кода:**
```cs
// Create a new instance of MailMessage class
var message = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "New message",
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
       <h3>New message</h3>
       <p>This is a new message created by Aspose.Email.</p>
     </body>
    </html>"
};
```

## **Указание нескольких получателей**

Есть три способа указать получателей сообщения электронной почты: используя **To**, **CC**, или **BCC** fields.

- **To** поле — основной получатель вашего сообщения. В это поле можно ввести один или несколько адресов электронной почты, разделенных запятыми. Поле «Кому» обязательно для каждого сообщения электронной почты.

- **CC** поле расшифровывается как копия. Оно используется для отправки копии вашего сообщения другим людям, которые заинтересованы или вовлечены в эту тему. Поле CC необязательно и может содержать несколько адресов электронной почты. Получатели в поле CC могут видеть, кто еще получил сообщение.

- **BCC** поле расшифровывается как слепая копия. Оно похоже на поле CC, но получатели в поле BCC скрыты от других получателей. Поле BCC удобно использовать, если вы хотите защитить конфиденциальность некоторых получателей или не загромождать их входящие сообщения ответами. Поле BCC также необязательно и может содержать несколько адресов электронной почты.

Рассмотрим следующий код с подробными инструкциями по указанию нескольких получателей сообщения электронной почты.

**Этапы написания кода:**

1. Создайте новый экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Установите [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) свойство к адресу электронной почты отправителя.
3. Установите [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) свойство массива адресов электронной почты основных получателей.
4. Установите [CC](https://reference.aspose.com/email/net/aspose.email/mailmessage/cc/) свойство массива адресов электронной почты получателей, которые получат копию письма.
5. Установите [Bcc](https://reference.aspose.com/email/net/aspose.email/mailmessage/bcc/) свойство к массиву адресов электронной почты получателей, которые получат слепую копию письма.

**Пример кода:**

```cs
var eml = new MailMessage
{
    // Specify From address
    From = "sender@sender.com",
    //  Specify recipients’ mail addresses
    To = {"receiver1@receiver.com", "receiver2@receiver.com", "receiver3@receiver.com"},
    // Specify CC addresses
    CC = {"CC1@receiver.com", "CC2@receiver.com"},
    // Specify BCC addresses
    Bcc = {"Bcc1@receiver.com", "Bcc2@receiver.com"}
};
```

## **Добавление отображаемых имен к адресам электронной почты**

Наряду с адресом электронной почты **отображаемое имя** может быть включено для идентификации отправителя или получателя электронного письма. Оно может включать полное имя, псевдоним или другой идентификатор человека.

Когда сообщение электронной почты отображается в почтовом клиенте или интерфейсе веб-почты, отображаемое имя обычно отображается рядом с адресом электронной почты, что позволяет пользователю определить, от кого и кому оно адресовано. Например, адрес электронной почты может быть «johndoe@example.com», но отображаемое имя, связанное с ним, может быть «John Doe».

Чтобы добавить отображаемые имена к адресам электронной почты в сообщении электронной почты, рассмотрите следующий код с подробными инструкциями:

**Этапы написания кода:**

1. Загрузите сообщение электронной почты из файла, используя [MailMessage.Load]() method.
2. Задайте отправителя электронного письма с помощью [From]() свойство объекта eml путем создания нового [MailAddress]() объект с адресом электронной почты и отображаемым именем отправителя.
3. Добавьте получателя в электронное письмо, используя [To]() свойство объекта eml, при необходимости добавьте список CC (Carbon Copy), используя [CC]() свойство, список BCC (слепая копия) с использованием [Bcc]() недвижимость и позвоните [Add]() метод с новым [MailAddress]() объект, содержащий адрес электронной почты и отображаемое имя получателя.

**Пример кода:**

```cs
// Load eml from file
MailMessage eml = MailMessage.Load(Data.Email/"test.eml");

eml.From = new MailAddress("TimothyFairfield@from.com", "Timothy Fairfield");

// A To address with a friendly name can also be specified like this
eml.To.Add(new MailAddress("kyle@to.com", "Kyle Huang"));

// Specify Cc and Bcc email address along with a friendly name
eml.CC.Add(new MailAddress("guangzhou@cc.com", "Guangzhou Team"));
eml.Bcc.Add(new MailAddress("ahaq@bcc.com", "Ammad ulHaq "));
```
## **Отображение дополнительных участников в выходных данных заголовка mht**

В приведенном ниже примере кода показано, как использовать *показать дополнительных участников* функция при сохранении сообщения в формате mhtml:


```cs
MhtSaveOptions options = new MhtSaveOptions()
{
    MhtFormatOptions = MhtFormatOptions.RenderCalendarEvent | MhtFormatOptions.WriteHeader
};

MapiMessage msg = MapiMessage.Load(fileName);
msg.Save(fileName + ".mhtml", options);

//if you need to skip OptionalAttendees in mhtml file you can clear format template for OptionalAttendees
options.FormatTemplates[MhtTemplateName.OptionalAttendees] = "";
msg.Save(fileName + "2.mhtml", options);
```


## **Установить тело письма**

В этой статье вы узнаете, как:

- [задать текст в виде обычного текста](#Set-Plain-Text-Body)
- [установить тело HTML](#Setting-HTML-Body)
- [задать альтернативный текст](#Setting-Alternate-Text)
- [укажите кодировку текста письма](#Specifying-Mail-Body-Encoding)

### **Настройка текста в виде обычного текста**

Тело письма можно указать с помощью [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) собственность [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Specify HtmlBody
    Body = "This is a простой текст body"
};
```

### **Настройка тела HTML**

Тело письма также можно указать с помощью [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) собственность [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Specify HtmlBody
    HtmlBody = "<html><body>This is the HTML body</body></html>"
};
```

### **Настройка альтернативного текста**

Альтернативное представление в файле EML — это дополнительное представление содержимого электронной почты, которое можно использовать для обеспечения другого представления сообщения электронной почты. Например, если вы отправляете сообщение в формате HTML, вы также можете указать **простой текст** версия на случай, если некоторые из получателей используют программы чтения электронной почты, которые не могут отображать HTML-содержимое. Для этого используйте [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) класс. У этого класса есть два свойства: [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) and [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/), которые используются для разрешения URL-адресов в содержимом электронного письма.

- [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) представляет собой коллекцию [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) объекты. При рендеринге URL-адреса в содержимом электронного письма сначала сопоставляются с URL-адресами в ссылке на содержимое каждого из них [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) объект в [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) сбор и урегулирование.
- [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/) используется программой чтения почты для разрешения относительных URL-адресов в теле, а также для разрешения относительных URL-адресов ссылок на содержимое в [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) collection.

Рассмотрим следующий код с подробными инструкциями по настройке альтернативного текста.

**Этапы написания кода:**

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Create [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/createalternateviewfromstring/) для просмотра сообщения электронной почты с использованием содержимого, указанного в строке.
3. Добавьте альтернативный текст, используя [Add](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/) метод [MailMessage.AlternateViews](https://reference.aspose.com/email/net/aspose.email/mailmessage/alternateviews/) collection.

**Пример кода:**
```cs
// Declare message as MailMessage instance
var eml = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Alternate Text");

// Adding alternate text
 eml.AlternateViews.Add(alternate);
```

### **Указание кодировки текста письма**

Aspose.Email использует [BodyEncoding](https://reference.aspose.com/email/net/aspose.email/mailmessage/bodyencoding/) собственность [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс для указания кодировки текста письма. Например:

```cs
eml.BodyEncoding = Encoding.UTF8;
```

## **Настройка дополнительных свойств MailMessage**

С Aspose.Email вы можете использовать дополнительные свойства [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс, такой как:

- [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) свойства - наборы **дата и время** электронного письма. По умолчанию дата — это фактическая дата отправки сообщения, а время — время отправки, отображаемое в Microsoft Outlook. Однако реальное время доставки электронной почты добавляется самим SMTP-сервером в заголовке письма. Например, ниже приведен обычный заголовок письма, где [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) задает поле Дата.

   ```cs
   // For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
  
   // Add by SMTP server in delivery emails
   Received: from ip-123.56.99.216.dsl-cust.ca.inter.net ([216.99.56.123]) by Aspose.secureserver.net with MailEnable ESMTP; Thu, 22 Feb 2007 13:58:57 -0700
  
   // Add by SMTP server in delivery emails
   Return-Path: <xyz@oikoscucine.it>
  
   // Add by SMTP server in delivery emails
   Received: from 195.120.225.20 (HELO mail.oikoscucine.it)
   by aspose.com with esmtp (:1CYY+<LA*- *1WK@)
   id Q8,/O/-.N83@7-9M
   for abc@aspose.com; Thu, 22 Feb 2007 20:58:51 +0300
   From: "XYZ" <xyz@oikoscucine.it>
   To: <abc@aspose.com>
   Subject: For ABC
  
   // Date will set the Date field, outlook will show this as
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

- [MailPriority](https://reference.aspose.com/email/net/aspose.email/mailpriority/#mailpriority-enumeration) перечисление — определяет уровни приоритета для отправки сообщения электронной почты. Он может быть низким, нормальным или высоким. Приоритет влияет на скорость передачи и доставку.
- [MailSensitivity](https://reference.aspose.com/email/net/aspose.email/mailsensitivity/#mailsensitivity-enumeration) перечисление — определяет пять уровней чувствительности.
- [XMailer](https://reference.aspose.com/email/net/aspose.email/mailmessage/xmailer/)- указывает программное обеспечение, создавшее сообщение электронной почты.

Приведенный ниже фрагмент кода иллюстрирует, как можно использовать каждое из описанных выше свойств.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Some subject", "Some body text")
{
    Date = DateTime.Now,
    Priority = MailPriority.High,
    Sensitivity = MailSensitivity.Normal,
    Xmailer = "Aspose.Email"
};
```

## **Запрос квитанции о прочтении**

Чтобы запросить [прочитайте квитанцию](https://en.wikipedia.org/wiki/Return_receipt), используйте Aspose.Email [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/mailmessage/deliverynotificationoptions/) собственность [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Это свойство содержит значения [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/deliverynotificationoptions/#deliverynotificationoptions-enumeration) enumeration.

Рассмотрим следующее **пример кода**:

```cs
// Create an Instance of MailMessage class
var eml = new MailMessage
{
    // Specify From, To, HtmlBody, DeliveryNotificationOptions field
    From = "sender@sender.com",
    To = "receiver@receiver.com",
    HtmlBody = "<html><body>This is the Html body</body></html>",
    DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess
};

eml.Headers.Add("Return-Receipt-To", "sender@sender.com");
eml.Headers.Add("Disposition-Notification-To", "sender@sender.com");

// Создайте экземпляр SmtpClient Class
var client = new SmtpClient
{
    // Specify your mailing host server, Username, Password and Port No
    Host = "smtp.server.com",
    Username = "Username",
    Password = "Password",
    Port = 25
};

try
{
    // Client.Send will send this message
    client.Send(eml);
    // Display ‘Message Sent’, only if message sent successfully
    Console.WriteLine(@"Message sent");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

**Note**: Запросы на получение информации о прочтении могут не всегда удовлетворяться по следующим причинам:

- Почтовый клиент может не реализовать эту функциональность.
- У конечного пользователя эта функция может быть отключена.
- Конечный пользователь может отказаться от отправки.


## **Настройка заголовков электронной почты**

Заголовки электронных писем представляют собой стандарт Интернета, а RFC определяет поля заголовков, которые включаются в сообщения электронной почты Интернета. Заголовок электронного письма можно указать с помощью [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Общие типы заголовков определены в поле [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/) класс. Это запечатанный класс, работающий как обычное перечисление.

Обычно заголовок электронного письма содержит следующие поля:

- **To**: Адреса получателей можно указать в поле Кому. Получатели в поле «Кому» являются основной аудиторией сообщения. Адресов получателей может быть несколько.
- **From**: В этом поле указан адрес электронной почты отправителя сообщения.
- **Cc**: Позволяет пользователям отправлять сообщения в виде «точной копии» или «любезной копии». То есть от получателя не ожидается ответа или действий. Как правило, руководящий персонал уведомляется с помощью CC.
- **Bcc**: Оно расшифровывается как Blind Carbon Copy, что позволяет отправлять получателю электронное письмо, скрытое от других получателей.
- **ReplyTo**: Это поле заголовка предназначено для указания того, куда отправитель хочет отправить ответы.
- **Subject**: Заголовок, заголовок, тема. Часто используется в качестве индикатора темы сообщений, отвечающих на другие сообщения или комментирующих их.
- **Date**: В этом заголовке указаны дата (и время). Обычно это дата составления и отправки сообщения.
- **XMailer**: Информация о клиентском программном обеспечении автора. Пример: программа X-Mailer: Aspose.Email. XMailer используется почтовыми клиентами. Разные почтовые клиенты будут иметь разные значения XMailer. Значение XMailer в MS Outlook — Microsoft Office Outlook, сборка 11.0.5510. Получатель электронной почты или программа для чтения электронной почты игнорируют его.

Обычно заголовок электронного письма выглядит следующим образом:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

Чтобы настроить заголовок письма, выполните следующие действия **шаги кода**:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Укажите «Кому», «От», «Cc», «Bcc», «ReplyTo», «Тема», «Дата» и «XMailer», используя экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Создайте экземпляр [MimeHeader](https://reference.aspose.com/email/net/aspose.email.mime/mimeheader/) класс и укажите пользовательский заголовок.
- Добавьте пользовательский заголовок в поле [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

Следующее **фрагмент кода** показывает, как настроить заголовки электронной почты.

```cs
var eml = new MailMessage
{
    ReplyToList = "reply@reply.com",
    From = "sender@sender.com",
    To = "receiver1@receiver.com",
    CC = "receiver2@receiver.com",
    Bcc = "receiver3@receiver.com",
    Subject = "test mail",
    Date = new System.DateTime(2006, 3, 6),
    XMailer = "Aspose.Email"
};
```

Приведенный выше фрагмент кода создает заголовок электронного письма в следующем формате:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

### **Вставьте заголовок в определенном месте**

The [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) метод [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/) класс вставляет заголовок в конце коллекции. Однако иногда может возникнуть необходимость вставить заголовок в определенном месте. В таком случае [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) метод не поможет. Для этого используйте [Insert](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/insert/#insert) метод [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/). Если коллекция содержит заголовки с одинаковыми именами, этот заголовок будет вставлен перед другими заголовками с таким же именем. В следующем фрагменте кода показано, как вставить заголовок в определенное место.

```cs
eml.Headers.Insert("Received", "Value");
```

### **Сохранить все заголовки в MHTML**

The [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/#mhtsaveoptionssaveallheaders-property) собственность [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) класс определяет, нужно ли сохранять все заголовки в выходном файле mhtml или нет. В следующем фрагменте кода показано, как сохранить все заголовки файла mhtml:

```cs
var eml = MailMessage.Load("message.eml");
var sopt = SaveOptions.DefaultMhtml;
sopt.SaveAllHeaders = true;
eml.Save("message.mhtml", sopt);
```

### **Добавление настраиваемых заголовков в электронное письмо**

Заголовок электронного письма можно указать с помощью [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Чтобы указать **настраиваемый заголовок** в сообщении электронной почты рассмотрим следующий пример кода:

```cs
eml.Headers.Add("secret-header", "mystery");
```

Приведенный выше фрагмент кода создает заголовок электронного письма в следующем формате:

```cs
secret-header: mystery
```

## **Сохраните HTML-файл с полями задач в заголовке**

The [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) перечисление позволяет указать, что поля задач должны быть включены в заголовок сохраненного HTML-файла. В следующем фрагменте кода показано, как сохранить поля задачи в заголовке при сохранении html-файла:

```cs
var msg = MapiMessage.Load("task.msg");
HtmlSaveOptions opt = SaveOptions.DefaultHtml;
opt.HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderTaskFields;
msg.Save("task.html", opt);
```

## **Подписывайте электронные письма с помощью DKIM**

> **_NOTE:_** Эта функция доступна только для версий библиотек, ориентированных на платформу.NET Framework. Версии, ориентированные на .NET Core, не имеют этой функции.

Aspose.Email позволяет подписывать электронную почту с помощью DKIM (почта, идентифицированная доменными ключами). Это позволяет организации взять на себя ответственность за передаваемое сообщение ([Дополнительная информация](https://www.dkim.org/)). DKIM добавляет цифровую подпись к заголовкам сообщений электронной почты, которую могут проверить получатели. Открытый ключ отправителя позволяет получателю проверить, соответствует ли подпись содержимому сообщения. [DKIMSign](https://reference.aspose.com/email/net/aspose.email/mailmessage/dkimsign/#dkimsign) метод [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс используется для задания криптографической и сигнатурной информации для подписи сообщения. В следующем фрагменте кода показано, как подписывать электронные письма с помощью DKIM.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Some subject", "Some body text");

string privateKeyFile = "key2.pem";
RSACryptoServiceProvider rsa = PemReader.GetPrivateKey(privateKeyFile);
DKIMSignatureInfo signInfo = new DKIMSignatureInfo("test", "somedomain.com");

var signedEml = eml.DKIMSign(rsa, signInfo);
```
