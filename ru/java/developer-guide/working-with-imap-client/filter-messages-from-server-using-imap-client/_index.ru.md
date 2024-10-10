---
title: "Фильтрация сообщений с сервера с использованием IMAP-клиента"
url: /ru/java/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---


Класс [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет метод [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) для получения всех сообщений из почтового ящика. Чтобы получить только сообщения, соответствующие некоторому условию, используйте перегруженный метод [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) с параметром [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/). Класс [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) предоставляет различные свойства для задействования условий, например, дата, тема, отправитель, получатель и так далее. В первом примере показано, как отфильтровать сообщения по дате и теме. Мы также показываем, как фильтровать по другим критериям и как строить более сложные запросы. API также предоставляет возможность применять условия поиска с учетом регистра для точного фильтрации. API также позволяет указывать кодировку строки поиска для фильтрации сообщений из почтового ящика.

## **Фильтрация сообщений из почтового ящика**

1. [Подключение и вход на IMAP-сервер](/email/java/connecting-to-imap-server#connecting-with-imap-server)
1. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) и задайте свойства
1. Вызовите метод [ImapClient.listMessages(MailQuery query)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages-com.aspose.email.MailQuery-) и передайте [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) с параметрами, чтобы получить только отфильтрованные сообщения.

Следующий фрагмент кода показывает, как подключиться к IMAP-ящику и получить сообщения, которые пришли сегодня и имеют слово "newsletter" в теме.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Подключение и вход на IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");
// Установите условия, тема содержит "Newsletter", письма, которые пришли сегодня
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Построить запрос и получить список сообщений
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
System.out.println("Imap: " + messages.size() + " message(s) found.");
// Отключение от IMAP
client.dispose();
~~~

## **Получение сообщений, соответствующих конкретным критериям**

[Примеры кода выше](#filtering-messages-from-mailbox) фильтруют сообщения на основе темы и даты электронной почты. Мы также можем использовать другие свойства для установки других поддерживаемых условий. Вот некоторые примеры установки условий с использованием [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/). Следующие фрагменты кода показывают, как отфильтровать электронные письма по:

1. Дате сегодня.
1. Диапазону дат.
1. От конкретного отправителя.
1. От конкретного домена.
1. Для конкретного получателя.

### **Дата сегодня**

Следующий фрагмент кода показывает, как отфильтровать электронные письма по дате сегодня.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Письма, которые пришли сегодня
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~
### **Диапазон дат**
Следующий фрагмент кода показывает, как отфильтровать электронные письма по диапазону дат.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Письма, которые пришли за последние 7 дней
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Конкретный отправитель**

Следующий фрагмент кода показывает, как отфильтровать электронные письма от конкретного отправителя.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Получить письма от конкретного отправителя
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

### **Конкретный домен**

Следующий фрагмент кода показывает, как отфильтровать электронные письма от конкретного домена.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Получить письма от конкретного домена
builder.getFrom().contains("SpecificHost.com");
~~~

### **Конкретный получатель**

Следующий фрагмент кода показывает, как отфильтровать электронные письма для конкретного получателя.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Получить письма, отправленные конкретному получателю
builder.getTo().contains("recipient");
~~~

## **Строительство сложных запросов**

Если различные свойства [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) устанавливаются в отдельных выражениях, то все условия будут соответствовать этому. Например, если мы хотим получить сообщения в пределах диапазона дат и от конкретного хоста, нам нужно написать три выражения.

### **Комбинирование запросов с AND**

Следующий фрагмент кода показывает, как комбинировать запросы с AND.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Письма от конкретного хоста, получить все письма, которые пришли до сегодня и все письма, которые пришли за последние 7 дней
builder.getFrom().contains("SpecificHost.com");

Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Комбинирование запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) предоставляет метод [or()](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) , который принимает два экземпляра [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) в качестве параметров. Он получает сообщения, которые соответствуют любому из двух указанных условий. Следующий фрагмент кода показывает, как фильтровать сообщения, которые либо имеют "test" в теме, либо "noreply@host.com" в качестве отправителя. Следующий фрагмент кода показывает, как комбинировать запросы с OR.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Укажите условие OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

## **Фильтрация по InternalDate**

Сообщения могут быть извлечены с сервера на основе InternalDate, однако иногда сервер не возвращает все сообщения, как видно во входящих. Причиной этого могут быть настройки часового пояса сервера, так как он может не быть UTC для всех серверов, таких как [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose отправляет команды, такие как 008 SEARCH ON 4-May-2014 в соответствии с [IMAP протоколом](https://datatracker.ietf.org/doc/html/rfc1730), однако результат может отличаться из-за настроек часового пояса сервера. Новый член добавлен в [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) как [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) , что дополнительно помогает фильтровать сообщения. Следующий фрагмент кода показывает использование [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) для фильтрации сообщений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Подключение и вход на IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");

// Установите условия, тема содержит "Newsletter", письма, которые пришли сегодня
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());

// Построить запрос и получить список сообщений
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
for (ImapMessageInfo info : messages) {
    System.out.println("Internal Date: " + info.getInternalDate());
}

// Отключение от IMAP
client.dispose();
~~~

### **Фильтрация электронной почты с учетом регистра**

Следующий фрагмент кода показывает, как использовать фильтрацию электронной почты с учетом регистра.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Установите условия, тема содержит "Newsletter", письма, которые пришли сегодня
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~

### **Указать кодировку для построения запроса**

Конструктор API [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) может быть использован для указания кодировки для строки поиска. Это также можно установить с помощью [DefaultEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#getDefaultEncoding--) свойства MailQueryBuilder. Следующий фрагмент кода показывает, как указать кодировку для построения запроса.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Установите условия
ImapQueryBuilder builder = new ImapQueryBuilder(Charset.forName("utf-8"));
builder.getSubject().contains("ğüşıöç", true);
MailQuery query = builder.getQuery();
~~~

### **Фильтрация сообщений с поддержкой постраничного отображения**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет возможность поиска сообщений из почтового ящика и их отображения с поддержкой постраничного отображения. Следующий фрагмент кода показывает, как фильтровать сообщения с поддержкой постраничного отображения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
/// <summary>
/// Этот пример показывает, как искать сообщения, используя ImapClient API с поддержкой постраничного отображения
/// Введен в Aspose.Email для .NET 6.4.0
/// </summary>
final ImapClient client = new ImapClient("host.domain.com", 84, "username", "password");
try {
    try {
        // Добавить некоторые тестовые сообщения
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), "111111111111111");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }
        String body = "2222222222222";
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), body);
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        client.selectFolder("Inbox");
        ImapQueryBuilder iqb = new ImapQueryBuilder();
        iqb.getBody().contains(body);
        MailQuery query = iqb.getQuery();

        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages(query);
        System.out.println(totalMessageInfoCol.size());

        //////////////////////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();

        PageSettings ps = new PageSettings();
        ps.setFolderName(ImapFolderInfo.IN_BOX);
        PageInfo pi = new PageInfo(itemsPerPage);
        ImapPageInfo pageInfo = client.listMessagesByPage(query, pi, ps);

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(query, pageInfo.getNextPage(), ps);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // преобразование foreach в while
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Фильтрация сообщений с пользовательским флагом**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();

queryBuilder.hasFlags(ImapMessageFlags.keyword("custom1"));

queryBuilder.hasNoFlags(ImapMessageFlags.keyword("custom2"));
~~~

## **Фильтрация сообщений с использованием пользовательского поиска**

Например, стандарт RFC 3501 не позволяет искать сообщения на основе наличия вложений в них. Но **Gmail** предоставляет [IMAP-расширения](https://developers.google.com/gmail/imap/imap-extensions), которые позволяют выполнять такой поиск. Aspose.Email предоставляет метод [customSearch](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/#customSearch-java.lang.String-) класса [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) для создания соответствующего запроса. 

Пример кода ниже показывает, как получить список электронных сообщений с сервера, имеющих вложения, используя протокол IMAP и пользовательский критерий поиска:

```java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.customSearch("X-GM-RAW \"has:attachment\"");
MailQuery query = builder.getQuery();
messageInfoCol = client.listMessages(query);
```