---
title: "Отправка и пересылка сообщений - Отправка сообщений электронной почты Outlook с использованием Java-программы"
url: /ru/java/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Отправка и пересылка сообщений"
---

Класс [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) позволяет приложениям отправлять электронные письма с использованием протокола передачи почты Simple Mail Transfer Protocol (SMTP).

- Класс [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) является единственной основной точкой входа, которую используют разработчики для отправки почтовых сообщений.
- Класс [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) также предоставляет другие общие методы доставки электронной почты, включая запись почтовых сообщений в файловую систему, очередь сообщений и т. д.
- Класс [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) полностью поддерживает две модели программирования:
  - [Синхронная](#sending-emails-synchronously)
  - [Асинхронная](#sending-emails-asynchronously)
- Класс [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) также поддерживает [отправку сообщений в виде TNEF](#sending-message-as-tnef)

Чтобы отправить сообщение электронной почты и блокировать выполнение, ожидая, пока письмо будет передано на SMTP-сервер, используйте один из синхронных методов Send. Чтобы позволить основному потоку вашей программы продолжать выполнение во время передачи электронной почты, используйте метод [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-).

## **Отправка электронной почты синхронно**

Электронное сообщение можно отправить синхронно, используя метод [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Он отправляет указанное электронное сообщение через SMTP-сервер для доставки. Отправитель сообщения, получатели, тема и текст сообщения указываются с помощью объектов String. Чтобы отправить сообщение электронной почты синхронно, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и установите его свойства.
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и укажите хост, порт, имя пользователя и пароль.
1. Отправьте сообщение, используя метод [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и передайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

Следующий фрагмент кода на Java показывает, как отправлять электронные письма Outlook синхронно.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Declare msg as MailMessage instance
MailMessage msg = new MailMessage();

// Create an instance of SmtpClient class
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
    System.out.println("Сообщение отправлено");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Отправка электронной почты асинхронно**

Иногда вы можете захотеть отправить почту асинхронно. Например, если вы отправляете много писем через ваше приложение, синхронный подход может не сработать. В таком случае вы можете использовать [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). Метод [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) отправляет сообщение электронной почты на SMTP-сервер для доставки. Этот метод не блокирует вызывающий поток и позволяет вызывающему передать объект методу, который вызывается по завершении операции. Чтобы отправить сообщение Outlook асинхронно на Java, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и используйте его различные свойства.
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и укажите хост, порт, имя пользователя и пароль.
1. Создайте пользовательский экземпляр, который будет передан методу и вызван, когда асинхронная операция завершится.
1. Отправьте сообщение, используя метод [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и передайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и пользовательский экземпляр вместе с функцией обратного вызова, которая будет вызвана, когда операция завершится.

Чтобы получить уведомление, когда электронная почта была отправлена или операция была отменена, вызывается функция обратного вызова, переданная методу [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). После вызова метода [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) не обязательно ждать полной отправки сообщения электронной почты. Мы можем одновременно вызывать другой метод [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). Когда электронная почта была отправлена с помощью метода [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-), фрагмент кода выводит сообщение ("Сообщение отправлено"). Следующая программа на Java или фрагмент кода показывает, как отправить электронные письма асинхронно.

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
        MailMessage msg = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Тестовая тема", "Тестовое тело");
        SmtpClient client = getSmtpClient();
        Object state = new Object();
        IAsyncResult ar = client.beginSend(msg, callback, state);
        // If the user canceled the send, and mail hasn't been sent yet,
        client.cancelAsyncOperation(ar);

        msg.dispose();
        System.out.println("До свидания.");
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
            System.out.println("Отправка отменена.");
        }

        if (task != null && task.getErrorInfo() != null) {
            System.out.println(task.getErrorInfo());
        } else {
            System.out.println("Сообщение отправлено.");
        }
    }
};
~~~

## **Отправка сохраненных сообщений с диска**

Файлы EML (файлы электронной почты Outlook Express) содержат заголовок электронного письма, текст сообщения и любые вложения. Aspose.Email позволяет разработчикам работать с файлами EML различными способами. Эта статья показывает, как загрузить файлы EML с диска и отправить их как электронные письма с помощью SMTP. Вы можете загрузить файлы .eml с диска или потока в класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и отправить сообщение с использованием класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) является основным классом для создания новых электронных писем, загрузки файлов сообщений с диска или потока и сохранения сообщений. Следующий фрагмент кода на Java показывает, как отправить сохраненные сообщения с диска.

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

## **Отправка электронного письма в текстовом формате**

Программные примеры ниже показывают, как отправить сообщение электронной почты в текстовом формате. Свойство [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) используется для указания текстового содержимого тела сообщения. Чтобы отправить электронное письмо в текстовом формате, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Укажите адреса электронной почты отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Укажите содержимое [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) для текстового сообщения.
- Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и отправьте электронную почту.

Следующий фрагмент кода показывает, как отправить электронное письмо в текстовом формате.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create an instance of the MailMessage class
MailMessage message = new MailMessage();

// Set From field, To field and Plain text body
message.setFrom(MailAddress.to_MailAddress("sender@sender.com"));
message.getTo().add("receiver@receiver.com");
message.setBody("Это текстовое тело");

// Create an instance of the SmtpClient class
SmtpClient client = new SmtpClient();

// And Specify your mailing host server, Username, Password and Port
client.setHost("smtp.server.com");
client.setUsername("Username");
client.setPassword("Password");
client.setPort(25);

try {
    // Client.Send will send this message
    client.send(message);
    System.out.println("Сообщение отправлено");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Отправка электронного письма с HTML-телом**

Программные примеры ниже показывают, как вы можете отправить простое HTML-сообщение электронной почты. Свойство [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), являющееся свойством класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), используется для указания HTML-содержимого тела сообщения. Чтобы отправить простое HTML-сообщение, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Укажите адреса электронной почты отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Укажите содержимое [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--).
- Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и отправьте электронную почту, используя метод [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) метода.

Для целей этой статьи HTML-содержимое электронного письма является примитивным: <html><body>Это HTML тело</body></html> Большинство HTML-сообщений электронной почты будет более сложным. Следующий фрагмент программы на Java показывает, как отправить электронное письмо с HTML-телом.

~~~Java
public static void run() {
    // Declare msg as MailMessage instance
    MailMessage msg = new MailMessage();

    // Use MailMessage properties like specify sender, recipient, message and HtmlBody
    msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("asposetest123@gmail.com"));
    msg.setSubject("Тестовая тема");
    msg.setHtmlBody("<html><body>Это HTML тело</body></html>");
    SmtpClient client = getSmtpClient();
    try {
        // Client will send this message
        client.send(msg);
        System.out.println("Сообщение отправлено");
    } catch (Exception ex) {
        System.err.println(ex);
    }

    System.out.println("Электронное письмо отправлено с HTML телом.");
}

private static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.setSecurityOptions(SecurityOptions.Auto);
    return client;
}
~~~

## **Отправка электронного письма с альтернативным текстом**

Программные примеры ниже показывают, как отправить простое HTML-сообщение электронной почты с альтернативным содержимым. Используйте класс [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) для указания копий сообщения электронной почты в разных форматах. Например, если вы отправляете сообщение в HTML-формате, вы также можете предоставить текстовую версию для получателей, которые используют почтовые чтения, которые не могут отображать HTML-содержимое. Или, если вы отправляете информационный бюллетень, вы можете предоставить текстовую копию текста для тех получателей, которые выбрали получение текстовой версии. Чтобы отправить электронное письмо с альтернативным текстом, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Укажите адреса электронной почты отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Создайте экземпляр класса [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/).

Это создает альтернативный вид для электронного сообщения с использованием содержимого, указанного в строке.

1. Добавьте экземпляр класса [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) в объект [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и отправьте электронное письмо с использованием метода [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) метода.

Следующий фрагмент кода показывает, как отправить электронное письмо с альтернативным текстом.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Declare message as MailMessage instance
MailMessage message = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //String
AlternateView alternate = AlternateView.createAlternateViewFromString("Альтернативный текст");

// Adding alternate text
message.getAlternateViews().addItem(alternate);
~~~

## **Отправка массовых электронных писем**

Отправка электронной почты массово означает отправку партии электронных писем в одном сообщении. Мы можем отправить пакет электронной почты, используя метод перегрузки [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/), который принимает класс [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/):

1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).
1. Укажите свойства класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).
1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Укажите отправителя, получателя, тему письма и сообщение в экземпляре класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Повторите два предыдущих шага, если хотите отправить письмо другому человеку.
1. Создайте экземпляр класса [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Добавьте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) в объект класса [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Теперь отправьте свою электронную почту, используя метод [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/), передавая экземпляр класса [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) в него.

Следующий фрагмент кода показывает, как отправить массовые электронные письма.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create SmtpClient as client and specify server, port, user name and password
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Create instances of MailMessage class and Specify To, From, Subject and Message
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Тема1", "Сообщение1, как дела?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Тема2", "Сообщение2, как дела?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Тема3", "Сообщение3, как дела?");

// Create an instance of MailMessageCollection class
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.addItem(message1);
manyMsg.addItem(message2);
manyMsg.addItem(message3);

// Use client.BulkSend function to complete the bulk send task
try {
    // Send Message using BulkSend method
    client.send(manyMsg);
    System.out.println("Сообщение отправлено");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Получение информации о массовых отправленных сообщениях**

Когда вы отправляете сообщения массово, вы можете получить информацию о количестве успешно отправленных сообщений и списке этих сообщений. Для этого используется событие [SucceededSending](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setSucceededSending-com.aspose.ms.System.EventHandler-com.aspose.email.MailMessageEventArgs--).

Ниже приведен образец кода, который показывает, как получить информацию о количестве успешно отправленных сообщений:

```java
try (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto)) {
    final AtomicInteger messageCount = new AtomicInteger(0);

    client.setSucceededSending(new EventHandler<MailMessageEventArgs>() {
        public void invoke(Object sender, MailMessageEventArgs eventArgs) {
            System.out.println("Сообщение " + eventArgs.getMessage().getSubject() + " было успешно отправлено.");
            messageCount.incrementAndGet();
        }
    });

    client.send(messages);

    System.out.println(messageCount + " сообщения были успешно отправлены.");
}
```

## **Отправка писем с многоподключением**

[SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) предоставляет свойство [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseMultiConnection-int-), которое можно использовать для создания нескольких подключения для тяжелых операций. Вы также можете установить количество соединений, которые будут использоваться в режиме многоподключения, с помощью [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setConnectionsQuantity-int-). Следующий фрагмент кода демонстрирует использование режима многоподключения для отправки нескольких сообщений.

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
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Тестовое сообщение - " + UUID.randomUUID().toString(),
            "Отправка сообщений SMTP с многоподключением");
    messages.add(message);
}

smtpClient.setConnectionsQuantity(5);
smtpClient.setUseMultiConnection(MultiConnectionMode.Enable);
smtpClient.send(messages);
~~~

{{% alert color="primary" %}} 

Пожалуйста, обратите внимание, что использование режима многоподключения не гарантирует увеличение производительности.

{{% /alert %}} 

## **Отправка сообщения в виде TNEF**

Электронные письма TNEF имеют специальное форматирование, которое может быть потеряно, если отправить их с использованием стандартного API. Aspose.Email предоставляет возможность отправлять электронные письма в формате TNEF, таким образом сохраняя формат. Свойство класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) [UseTnef](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseTnef\(boolean\)) может быть установлено для отправки сообщения электронной почты как TNEF. Следующий фрагмент кода показывает, как отправить сообщение в виде TNEF.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

String emlFileName = dataDir + "Message.eml"; // TNEF Email

// Load from eml
MailMessage eml1 = MailMessage.load(emlFileName, new EmlLoadOptions());
eml1.setFrom(MailAddress.to_MailAddress("somename@gmail.com"));
eml1.getTo().clear();
eml1.getTo().addItem(new MailAddress("first.last@test.com"));
eml1.setSubject("С флажком PreserveTnef при загрузке");
eml1.setDate(new Date());
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setUseTnef(true); // Используйте этот флажок, чтобы отправить как TNEF
client.send(eml1);
~~~ 

## **Отправка запросов на встречу**

Microsoft Outlook предлагает функции календаря, а также управление электронной почтой. Когда пользователь открывает электронное письмо с приглашением на событие, Outlook предлагает ему принять или отклонить приглашение. Aspose.Email позволяет разработчикам добавлять функции календаря в ваши электронные письма.

### **Отправка запросов по электронной почте**

Чтобы отправить запросы на встречу по электронной почте, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Укажите адреса отправителя и получателя с помощью экземпляра класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Инициализируйте экземпляр класса [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) и передайте его значения.
- Укажите резюме и описание в экземпляре [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/).
- Добавьте [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/) в экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и передайте ему экземпляр [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).

|**Запрос встречи iCalendar, отправленный по электронной почте**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
Следующий фрагмент кода показывает, как отправить запросы по электронной почте.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create an instance of the MailMessage class
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
app.setSummary("Встреча по выпуску");
app.setDescription("Обсуждение следующего выпуска");

// Add appointment to the message and Create an instance of SmtpClient class
msg.addAlternateView(app.requestApointment());
SmtpClient client = getSmtpClient();

try {
    // Client.Send will send this message
    client.send(msg);
    System.out.println("Сообщение отправлено");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~ 

### **Поддержка iCalendar для IBM Lotus Notes**

Функция календаря Aspose.Email основана на стандарте iCalendar, стандарте для обмена данными календаря (RFC 2445 или справочник синтаксиса RFC2445). Таким образом, она поддерживает не только Microsoft Outlook, но и IBM Lotus Notes. Чтобы отправить запрос на встречу в Lotus Notes, выполните те же шаги, что и выше.

## **Пересылка электронной почты с использованием SMTP-клиента**

### **Пересылка электронной почты с помощью SMTP-клиента**

Пересылка электронной почты является обычной практикой в повседневной цифровой коммуникации. Полученное письмо можно переслать определенным получателям, не делясь при этом с оригинальными отправителями. API Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) предоставляет возможность пересылать электронные письма определенным получателям. Его метод [Forward](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#forward-java.lang.String-com.aspose.email.MailAddressCollection-com.aspose.email.MailMessage-) можно использовать для пересылки полученного или сохраненного письма желаемым получателям, как показано в этой статье. Следующий фрагмент кода показывает, как переслать электронное письмо с использованием SMTP-клиента.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create an instance of SmtpClient class
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

API также поддерживает пересылку сообщений EML без предварительной загрузки в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Это полезно в тех случаях, когда существуют ограниченные ресурсы с точки зрения оперативной памяти.

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

## **Выполнение слияния почты**

Слияние почты помогает создавать и отправлять партию похожих сообщений электронной почты. Основная часть электронных писем является одинаковой, но содержание может быть персонализировано. Обычно контактные данные получателя (имя, фамилия, компания и так далее) используются для персонализации электронной почты.

|**Иллюстрация того, как работает слияние почты:**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email позволяет разработчикам настраивать слияние почты, которое включает данные из различных источников данных.

Чтобы выполнить слияние почты с помощью Aspose.Email, выполните следующие шаги:

1. Создайте функцию с подписью имени.
1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Укажите отправителя, получателя, тему и тело.
1. Создайте подпись для конца электронного письма.
1. Создайте экземпляр класса [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) и передайте ему экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Возьмите подпись в экземпляре [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) .
1. Создайте экземпляр класса [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Добавьте столбцы **Receipt**, **FirstName** и **LastName** в качестве источников данных в класс [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Создайте экземпляр класса [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Укажите адрес для получения, имя и фамилию в объекте [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Создайте экземпляр класса [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Укажите экземпляры [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) и [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) в экземпляре [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Создайте экземпляр класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) и укажите сервер, порт, имя пользователя и пароль.
1. Отправьте электронные письма с использованием метода [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .

В приведенном ниже примере #FirstName# указывает на столбец [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/), значение которого установлено пользователем. Следующий фрагмент кода показывает, как выполнить слияние почты.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // Путь к директории файлов.
    String dstEmail = dataDir + "EmbeddedImage.msg";

    // Создайте новый экземпляр MailMessage 
    MailMessage msg = new MailMessage();

    // Добавьте тему и адрес от
    msg.setSubject("Здравствуйте, #FirstName#");
    msg.setFrom(MailAddress.to_MailAddress("sender@sender.com"));

    // Добавьте адрес электронной почты для отправки письма, также добавьте сообщение в поле HTML тела
    msg.getTo().add("your.email@gmail.com");
    String htmlBody = "Ваше сообщение здесь/r/n" + "Спасибо за ваш интерес к <STRONG>Aspose.Email</STRONG>." ;

    // Используйте GetSignment как шаблонную процедуру, которая обеспечит одинаковую подпись
    htmlBody += "<br><br>Получите удовольствие от этого.<br><br>#GetSignature()#";

    msg.setHtmlBody(htmlBody);

    // Создайте новый TemplateEngine с сообщением MSG, зарегистрируйте GetSignature процедуру. Она будет использована в MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.registerRoutine("GetSignature", new TemplateRoutine() {
        public Object invoke(Object[] args) {
            return getSignature(args);
        }
    });

    // Создайте экземпляр DataTable и заполните DataTable как источник данных
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
        // Создайте сообщения на основе сообщения и источника данных.
        messages = engine.instantiate(dt);

        // Создайте экземпляр SmtpClient и укажите сервер, порт, имя пользователя и пароль
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.setSecurityOptions(SecurityOptions.Auto);

        // Отправка сообщений оптом
        client.send(messages);
    } catch (MailException ex) {
        System.err.println(ex);
    }

    catch (SmtpException ex) {
        System.err.println(ex);
    }

    System.out.println("Сообщение отправлено после выполнения слияния почты.");
}

// Шаблонная процедура для предоставления подписи
static Object getSignature(Object[] args) {
    return "Команда Aspose.Email<br>Aspose Ltd.<br>" + new Date().toString();
}
~~~ 

## **Выполнение слияния почты по строкам**

Пользователь также может объединить отдельные строки данных, чтобы получить целый и подготовленный объект [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Метод [TemplateEngine.merge](https://reference.aspose.com/email/java/com.aspose.email/templateengine/#merge-com.aspose.email.DataRow-) можно использовать для выполнения слияния почты по строкам.

~~~Java
// Создать сообщение из данных в текущей строке.
MailMessage message = engine.merge(currentRow);
~~~