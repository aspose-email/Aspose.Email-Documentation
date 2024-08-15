---
title: "Отправка и пересылка сообщений - отправка сообщений электронной почты Outlook с помощью программы Java"
url: /ru/java/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Отправка и пересылка сообщений"
---


The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс позволяет приложениям отправлять электронную почту с использованием простого протокола передачи почты (SMTP).

- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class — единственная крупная запись, которую разработчики используют для отправки почтовых сообщений.
- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс также предоставляет другие распространенные методы доставки электронной почты, включая запись сообщений электронной почты в файловую систему, очередь сообщений и т. д.
- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс полностью поддерживает эти две модели программирования:
  - [Synchronous](#sending-emails-synchronously)
  - [Asynchronous](#sending-emails-asynchronously)
- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс также поддерживает [отправка сообщений в формате TNEF](#sending-message-as-tnef)

Чтобы отправить сообщение электронной почты и заблокировать его в ожидании передачи на SMTP-сервер, используйте один из синхронных методов отправки. Чтобы основной поток программы продолжал выполняться во время передачи сообщения электронной почты, используйте [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) method.

## **Синхронная отправка электронных писем**

Сообщение электронной почты можно отправить синхронно с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) метод. Он отправляет указанное сообщение электронной почты через SMTP-сервер для доставки. Отправитель, получатели, тема и тело сообщения указываются с помощью объектов String. Чтобы отправить сообщение электронной почты синхронно, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс и задайте его свойства.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и укажите хост, порт, имя пользователя и пароль.
1. Отправьте сообщение, используя [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) метод и передайте [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.

В следующем фрагменте кода Java показано, как синхронно отправлять электронные письма Outlook.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Declare msg as MailMessage instance
MailMessage msg = new MailMessage();

// Создайте экземпляр SmtpClient class
SmtpClient client = new SmtpClient();

// Specify your mailing host server, Username, Password, Port # and Security option
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);

try {
    // Client.Send will send this message
    client.send(msg);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Асинхронная отправка электронных писем**

Иногда вы можете захотеть отправить почту асинхронно. Например, если вы отправляете большое количество почты через приложение, синхронный подход может не сработать. В таком сценарии вы можете использовать [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) метод [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс отправляет сообщение электронной почты на SMTP-сервер для доставки. Этот метод не блокирует вызывающий поток и позволяет вызывающей стороне передать объект методу, вызываемому после завершения операции. Чтобы отправить сообщение электронной почты Outlook в асинхронном режиме на Java, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс и используйте его различные свойства.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и укажите хост, порт, имя пользователя и пароль.
1. Создайте определенный пользователем экземпляр, который будет передан методу и вызван после завершения асинхронной операции.
1. Отправьте сообщение, используя [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) метод [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и сдайте экзамен [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр и определенный пользователем экземпляр в нем, а также функция обратного вызова, которая будет вызываться после завершения операции.

Чтобы получить уведомление об отправке электронного письма или отмене операции, функция обратного вызова была передана [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) метод вызывается. После вызова [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) метод: нет необходимости ждать полной отправки сообщения электронной почты. Мы можем вызвать другой метод [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) в то же время. Когда электронное письмо было отправлено с использованием [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) метод, фрагмент кода печатает сообщение («Сообщение отправлено»). В следующей программе Java или фрагменте кода показано, как отправлять электронные письма в асинхронном режиме.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

public static void run() {
    sendMail();
}

static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient();
    client.setHost("mail.server.com");
    // Specify your mail Username, Password, Port # and security option
    client.setUsername("username");
    client.setPassword("password");
    client.setPort(587);
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    return client;
}

static void sendMail() {
    try {

        // Declare msg as MailMessage instance
        MailMessage msg = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Test subject", "Test body");
        SmtpClient client = getSmtpClient();
        Object state = new Object();
        IAsyncResult ar = client.beginSend(msg, callback, state);
        // If the user canceled the send, and mail hasn't been sent yet,
        client.cancelAsyncOperation(ar);

        msg.dispose();
        System.out.println("Goodbye.");
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

static AsyncCallback callback = new AsyncCallback() {
    public void invoke(IAsyncResult ar) {
        IAsyncResultExt task = null;
        if (ar instanceof IAsyncResult)
            task = (IAsyncResultExt) ar;

        if (task != null && task.isCanceled()) {
            System.out.println("Send canceled.");
        }

        if (task != null && task.getErrorInfo() != null) {
            System.out.println(task.getErrorInfo());
        } else {
            System.out.println("Message Sent.");
        }
    }
};
~~~

## **Отправка сохраненных сообщений с диска**

Файлы EML (файлы электронной почты Outlook Express) содержат заголовок электронного письма, текст сообщения и все вложения. Aspose.Email позволяет разработчикам работать с файлами EML по-разному. В этой статье показано, как загружать файлы EML с диска и отправлять их по электронной почте с помощью SMTP. Вы можете загружать файлы.eml с диска или в потоковом режиме на [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс и отправьте сообщение электронной почты, используя [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс. [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class является основным классом для создания новых сообщений электронной почты, загрузки файлов сообщений электронной почты с диска или потока и сохранения сообщений. В следующем фрагменте кода Java показано, как отправлять сохраненные сообщения с диска.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Load an EML file in MailMessage class
MailMessage message = MailMessage.load(dataDir + "test.eml");

// Send this message using SmtpClient
SmtpClient client = new SmtpClient("host", "username", "password");

try {
    client.send(message);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Отправка электронного письма в виде обычного текста**

В приведенных ниже примерах программирования показано, как отправить текстовое сообщение по электронной почте. [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) имущество, собственность [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class, используется для указания текстового содержимого тела сообщения. Чтобы отправить сообщение электронной почты в виде обычного текста, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Укажите адреса электронной почты отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
- Укажите [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) содержимое, используемое для текстового сообщения.
- Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и отправьте электронное письмо.

В следующем фрагменте кода показано, как отправить электронное письмо в виде обычного текста.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр MailMessage class
MailMessage message = new MailMessage();

// Set From field, To field and Plain text body
message.setFrom(MailAddress.to_MailAddress("sender@sender.com"));
message.getTo().add("receiver@receiver.com");
message.setBody("This is Plain Text Body");

// Создайте экземпляр SmtpClient class
SmtpClient client = new SmtpClient();

// And Specify your mailing host server, Username, Password and Port
client.setHost("smtp.server.com");
client.setUsername("Username");
client.setPassword("Password");
client.setPort(25);

try {
    // Client.Send will send this message
    client.send(message);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Отправка электронной почты с текстом HTML**

В приведенных ниже примерах программирования показано, как отправить простое HTML-сообщение по электронной почте. [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), собственность [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class, используется для указания HTML-содержимого тела сообщения. Чтобы отправить простое электронное письмо в формате HTML, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Укажите адрес электронной почты отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
- Укажите [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) content.
- Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и отправьте электронное письмо, используя [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) method.

Для целей этой статьи HTML-содержимое электронного письма является элементарным: <html><body>Это тело HTML</body></html> Большинство писем в формате HTML будут более сложными. В следующем фрагменте программы Java показано, как отправить электронное письмо с текстом HTML.

~~~Java
public static void run() {
    // Declare msg as MailMessage instance
    MailMessage msg = new MailMessage();

    // Use MailMessage properties like specify sender, recipient, message and HtmlBody
    msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("asposetest123@gmail.com"));
    msg.setSubject("Test subject");
    msg.setHtmlBody("<html><body>Это тело HTML</body></html>");
    SmtpClient client = getSmtpClient();
    try {
        // Client will send this message
        client.send(msg);
        System.out.println("Message sent");
    } catch (Exception ex) {
        System.err.println(ex);
    }

    System.out.println("Email sent with HTML body.");
}

private static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.setSecurityOptions(SecurityOptions.Auto);
    return client;
}
~~~

## **Отправка электронной почты с альтернативным текстом**

В приведенных ниже примерах программирования показано, как отправить простое HTML-сообщение электронной почты с альтернативным содержимым. Используйте [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) класс для указания копий сообщения электронной почты в разных форматах. Например, если вы отправляете сообщение в формате HTML, вы также можете захотеть предоставить текстовую версию для получателей, использующих программы чтения электронной почты, которые не могут отображать содержимое HTML. Или, если вы отправляете информационный бюллетень, вы можете предоставить копию текста в виде обычного текста тем получателям, которые решили получить текстовую версию. Чтобы отправить электронное письмо с альтернативным текстом, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Укажите адреса электронной почты отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Создайте экземпляр [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) class.

Это создает альтернативное представление сообщения электронной почты с использованием содержимого, указанного в строке.

1. Добавьте экземпляр [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) от класса до [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) object.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и отправьте электронное письмо, используя [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) method.

В следующем фрагменте кода показано, как отправить электронное письмо с альтернативным текстом.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Declare message as MailMessage instance
MailMessage message = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //String
AlternateView alternate = AlternateView.createAlternateViewFromString("Alternate Text");

// Adding alternate text
message.getAlternateViews().addItem(alternate);
~~~

## **Отправка массовых писем**

Массовая отправка электронных писем означает отправку пакета писем одним сообщением. Мы можем отправить пакет электронных писем, используя [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) перегрузка метода, который принимает [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class:

1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class.
1. Укажите [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) свойства класса.
1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Укажите отправителя, получателя, тему письма и сообщение в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Повторите два вышеуказанных шага еще раз, если вы хотите отправить электронное письмо другому человеку.
1. Создайте экземпляр [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class.
1. Добавьте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс в объекте [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class.
1. Теперь отправьте электронное письмо, используя [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) метод путем передачи экземпляра [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) класс в нем.

В следующем фрагменте кода показано, как отправлять массовые электронные письма.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create SmtpClient as client and specify server, port, user name and password
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Create instances of MailMessage class and Specify To, From, Subject and Message
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Subject1", "message1, how are you?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Subject2", "message2, how are you?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Subject3", "message3, how are you?");

// Создайте экземпляр MailMessageCollection class
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.addItem(message1);
manyMsg.addItem(message2);
manyMsg.addItem(message3);

// Use client.BulkSend function to complete the bulk send task
try {
    // Send Message using BulkSend method
    client.send(manyMsg);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~
## **Получите информацию об отправленных массовых сообщениях**

При массовой отправке сообщений вы можете получить информацию о количестве успешно отправленных сообщений и список этих сообщений. [SucceededSending](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setSucceededSending-com.aspose.ms.System.EventHandler-com.aspose.email.MailMessageEventArgs--) событие используется для этой цели.

В приведенном ниже примере кода показано, как получить информацию о количестве успешно отправленных сообщений:

```java
try (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto)) {
    final AtomicInteger messageCount = new AtomicInteger(0);

    client.setSucceededSending(new EventHandler<MailMessageEventArgs>() {
        public void invoke(Object sender, MailMessageEventArgs eventArgs) {
            System.out.println("The message " + eventArgs.getMessage().getSubject() + " was successfully sent.");
            messageCount.incrementAndGet();
        }
    });

    client.send(messages);

    System.out.println(messageCount + " messages were successfully sent.");
}
```


## **Отправка электронных писем с помощью мультиподключения**

[SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) обеспечивает [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseMultiConnection-int-) свойство, которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете настроить количество подключений, которое будет использоваться в режиме нескольких подключений, используя [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setConnectionsQuantity-int-). Следующий фрагмент кода демонстрирует использование режима нескольких подключений для отправки нескольких сообщений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient smtpClient = new SmtpClient();
smtpClient.setHost("<HOST>");
smtpClient.setUsername("<USERNAME>");
smtpClient.setPassword("<PASSWORD>");
smtpClient.setPort(587);
smtpClient.setSupportedEncryption(EncryptionProtocols.Tls);
smtpClient.setSecurityOptions(SecurityOptions.SSLExplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Test Message - " + UUID.randomUUID().toString(),
            "SMTP Send Messages with MultiConnection");
    messages.add(message);
}

smtpClient.setConnectionsQuantity(5);
smtpClient.setUseMultiConnection(MultiConnectionMode.Enable);
smtpClient.send(messages);
~~~

{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Отправка сообщения в формате TNEF**

Письма в формате TNEF имеют специальное форматирование, которое может быть потеряно при отправке с использованием стандартного API. Aspose.Email предоставляет возможность отправлять электронные письма в формате TNEF, тем самым сохраняя формат. [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [UseTnef](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseTnef\(boolean\)) свойство можно настроить для отправки электронного письма в формате TNEF. В следующем фрагменте кода показано, как отправить сообщение в формате TNEF.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

String emlFileName = dataDir + "Message.eml"; // A TNEF Email

// Load from eml
MailMessage eml1 = MailMessage.load(emlFileName, new EmlLoadOptions());
eml1.setFrom(MailAddress.to_MailAddress("somename@gmail.com"));
eml1.getTo().clear();
eml1.getTo().addItem(new MailAddress("first.last@test.com"));
eml1.setSubject("With PreserveTnef flag during loading");
eml1.setDate(new Date());
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setUseTnef(true); // Use this flag to send as TNEF
client.send(eml1);
~~~

## **Отправка приглашений на собрание**

Microsoft Outlook предлагает функции календаря, а также управление электронной почтой. Когда пользователь открывает электронное письмо с приглашением на мероприятие, Outlook предлагает ему принять или отклонить приглашение. Aspose.Email позволяет разработчикам добавлять функции календаря в ваши электронные письма.

### **Отправка запросов по электронной почте**

Чтобы отправить приглашения на собрание по электронной почте, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Укажите адреса отправителя и получателя, используя экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Инициализируйте экземпляр [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) класс и передайте его значения.
- Укажите краткое описание и описание в поле [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/) instance.
- Добавьте [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/)) к [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр и передайте его [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) instance.

|**Запрос на собрание iCalendar отправлен по электронной почте**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
В следующем фрагменте кода показано, как отправлять запросы по электронной почте.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр MailMessage class
MailMessage msg = new MailMessage();

// Set the sender, recipient, who will receive the meeting request. Basically, the recipient is the same as the meeting attendees
msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com"));

// Create Appointment instance
Calendar cal = Calendar.getInstance();
cal.set(2015, Calendar.JULY, 17, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2015, Calendar.JULY, 17, 14, 0, 0);
Date endDate = cal.getTime();
Appointment app = new Appointment("Room 112", startDate, endDate, msg.getFrom(), msg.getTo());
app.setSummary("Release Meetting");
app.setDescription("Discuss for the next release");

// Add appointment to the message and Создайте экземпляр SmtpClient class
msg.addAlternateView(app.requestApointment());
SmtpClient client = getSmtpClient();

try {
    // Client.Send will send this message
    client.send(msg);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

### **iCalendar поддерживает IBM Lotus Notes**

Функция календаря Aspose.Email основана на стандарте iCalendar, стандарте обмена календарными данными (справочник по синтаксису RFC 2445 или RFC2445). Таким образом, он поддерживает не только Microsoft Outlook, но и IBM Lotus Notes. Чтобы отправить приглашение на собрание в Lotus Notes, выполните те же действия, что и выше.

## **Пересылка электронной почты с помощью SMTP-клиента**

### **Пересылка электронной почты с помощью SMTP-клиента**

Пересылка электронной почты — обычная практика в повседневной цифровой коммуникации. Полученное электронное письмо можно переслать определенным получателям, не передавая его первоначальным отправителям. API Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) предоставляет возможность переслать электронное письмо определенным получателям. Это [Forward](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#forward-java.lang.String-com.aspose.email.MailAddressCollection-com.aspose.email.MailMessage-) метод можно использовать для пересылки полученного или сохраненного электронного письма нужным получателям, как показано в этой статье. В следующем фрагменте кода показано, как переслать электронное письмо с помощью SMTP-клиента.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр SmtpClient class
SmtpClient client = new SmtpClient();

// Specify your mailing host server, Username, Password, Port and SecurityOptions
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
MailMessage message = MailMessage.load(dataDir + "Message.eml");
client.forward("Recipient1@domain.com", "Recipient2@domain.com", message);
~~~

### **Пересылка электронной почты без использования MailMessage**

API также поддерживает пересылку сообщений EML без предварительной загрузки в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Это полезно в тех случаях, когда ресурсы системной памяти ограничены.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

String host = "mail.server.com";
String username = "username";
String password = "password";
int smtpPort = 587;
String sender = "Sender@domain.com";
MailAddressCollection recipients = new MailAddressCollection();
recipients.add("recepient1@domain.com, recepient2@domain.com");

try (SmtpClient client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto)) {
    String fileName = "test.eml";
    try (FileInputStream fs = new FileInputStream(new File(dataDir + fileName))) {
        client.forward(sender, recipients, fs);
    }
}
~~~

## **Выполнение слияния писем**

Объединение писем позволяет создавать и отправлять пакеты похожих сообщений электронной почты. Суть писем одна и та же, но их содержимое можно персонализировать. Как правило, контактные данные получателя (имя, отчество, компания и т. д.) используются для персонализации письма.

|**Иллюстрация того, как работает слияние писем:**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email позволяет разработчикам настраивать слияния писем, включающие данные из различных источников данных.

Чтобы выполнить слияние писем с помощью Aspose.Email, выполните следующие шаги:

1. Создайте функцию с подписью имени
1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Укажите отправителя, получателя, тему и текст.
1. Создайте подпись в конце письма.
1. Создайте экземпляр [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) класс и сдайте его [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Сделайте подпись в [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) instance.
1. Создайте экземпляр [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) class.
1. Добавьте столбцы **Receipt**, **FirstName** and **LastName** в качестве источников данных в [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) class.
1. Создайте экземпляр [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) class.
1. Укажите адрес получения, имя и фамилию в поле [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) object.
1. Создайте экземпляр [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class
1. Укажите [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/)  and [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) экземпляры в [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) instance.
1. Создайте экземпляр [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс и укажите сервер, порт, имя пользователя и пароль.
1. Отправляйте электронные письма с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) method.

В приведенном ниже примере #FirstName # означает [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) столбец, значение которого задается пользователем. В следующем фрагменте кода показано, как выполнить Mail Merge.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dstEmail = dataDir + "EmbeddedImage.msg";

    // Create a new MailMessage instance
    MailMessage msg = new MailMessage();

    // Add subject and from address
    msg.setSubject("Hello, #FirstName#");
    msg.setFrom(MailAddress.to_MailAddress("sender@sender.com"));

    // Add email address to send email also Add mesage field to HTML body
    msg.getTo().add("your.email@gmail.com");
    String htmlBody = "Your message here/r/n" + "Thank you for your interest in <STRONG>Aspose.Email</STRONG>.";

    // Use GetSignment as the template routine, which will provide the same signature
    htmlBody += "<br><br>Have fun with it.<br><br>#GetSignature()#";

    msg.setHtmlBody(htmlBody);

    // Create a new TemplateEngine with the MSG message, Register GetSignature routine. It will be used in MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.registerRoutine("GetSignature", new TemplateRoutine() {
        public Object invoke(Object[] args) {
            return getSignature(args);
        }
    });

    // Создайте экземпляр DataTable and Fill a DataTable as data source
    DataTable dt = new DataTable();
    dt.getColumns().add("Receipt");
    dt.getColumns().add("FirstName");
    dt.getColumns().add("LastName");

    DataRow dr;
    dr = dt.newRow();
    dr.set("Receipt", "Nancy&lt;Nancy@somedomain.com&gt;");
    dr.set("FirstName", "Nancy");
    dr.set("LastName", "Doe");
    dt.getRows().add(dr);
    dr = dt.newRow();
    dr.set("Receipt", "Andrew&lt;Andrew@somedomain.com&gt;");
    dr.set("FirstName", "Andrew");
    dr.set("LastName", "Doe");
    dt.getRows().add(dr);
    dr = dt.newRow();
    dr.set("Receipt", "Janet&lt;Janet@somedomain.com&gt;");
    dr.set("FirstName", "Janet");
    dr.set("LastName", "Doe");
    dt.getRows().add(dr);

    MailMessageCollection messages;
    try {
        // Create messages from the message and datasource.
        messages = engine.instantiate(dt);

        // Создайте экземпляр SmtpClient and specify server, port, username and password
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.setSecurityOptions(SecurityOptions.Auto);

        // Send messages in bulk
        client.send(messages);
    } catch (MailException ex) {
        System.err.println(ex);
    }

    catch (SmtpException ex) {
        System.err.println(ex);
    }

    System.out.println("Message sent after performing mail merge.");
}

// Template routine to provide signature
static Object getSignature(Object[] args) {
    return "Aspose.Email Team<br>Aspose Ltd.<br>" + new Date().toString();
}
~~~

## **Выполнение слияния писем по строкам**

Пользователь также может объединить отдельные строки данных, чтобы получить полную и подготовленную [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) объект. [TemplateEngine.merge](https://reference.aspose.com/email/java/com.aspose.email/templateengine/#merge-com.aspose.email.DataRow-) метод можно использовать для объединения писем по строкам.

~~~Java
// Create message from the data in current row.
MailMessage message = engine.merge(currentRow);
~~~
