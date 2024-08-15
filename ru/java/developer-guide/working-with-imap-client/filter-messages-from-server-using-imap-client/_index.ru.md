---
title: "Фильтрация сообщений с сервера с помощью клиента IMAP"
url: /ru/java/filter-messages-from-server-using-imap-client/
weight: 40
type: docs
---


The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс предоставляет [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) метод, который принимает [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) в качестве аргумента. [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) класс предоставляет различные свойства для указания условий, например дату, тему, отправитель, получатель и т. д. В первом примере показано, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и создавать более сложные запросы. API также предоставляет возможность применять критерии поиска, учитывающие регистр символов, для точного соответствия критериям фильтрации. API также позволяет указать кодировку поисковой строки для фильтрации сообщений из почтового ящика.

## **Фильтрация сообщений из почтового ящика**

1. [Подключитесь к серверу IMAP и войдите на него](/email/java/connecting-to-imap-server#connecting-with-imap-server)
1. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) и задайте свойства
1. Позвоните [Сообщения IMAPClient.listMessages (запрос MailQuery)](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages-com.aspose.email.MailQuery-) метод и передайте [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) с параметрами для получения только отфильтрованных сообщений.

В следующем фрагменте кода показано, как подключиться к почтовому ящику IMAP и получать сообщения, пришедшие сегодня и содержащие слово «информационный бюллетень» в теме.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");
// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Build the query and Get list of messages
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
System.out.println("Imap: " + messages.size() + " message(s) found.");
// Disconnect from IMAP
client.dispose();
~~~

## **Получайте сообщения, соответствующие определенным критериям**

[Приведенные выше примеры кода](#filtering-messages-from-mailbox) фильтруйте сообщения по теме и дате письма. Мы также можем использовать другие свойства для установки других поддерживаемых условий. Ниже приведены несколько примеров настройки условий с помощью [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/). Приведенные ниже фрагменты кода показывают, как фильтровать электронные письма по следующим адресам:

1. Сегодняшняя дата.
1. Диапазон дат.
1. От конкретного отправителя.
1. Из определенного домена.
1. От конкретного получателя.

### **Сегодняшняя дата**

В следующем фрагменте кода показано, как фильтровать электронные письма в Сегодняшняя дата.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~
### **Date Range*
The following code snippet shows you how to filter emails on the date range.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived in last 7 days
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Конкретный отправитель**

В следующем фрагменте кода показано, как фильтровать электронные письма определенного отправителя.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

### **Конкретный домен**

В следующем фрагменте кода показано, как фильтровать электронные письма в определенном домене.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~

### **Конкретный получатель**

В следующем фрагменте кода показано, как фильтровать электронные письма по определенному получателю.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~

## **Создание сложных запросов**

Если отличается [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) свойства задаются в отдельных выражениях, тогда все условия будут выполнены. Например, если мы хотим получать сообщения за определенный диапазон дат и от определенного хоста, нам нужно написать три выражения.

### **Объединение запросов с AND**

В следующем фрагменте кода показано, как комбинировать запросы с AND.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");

Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~

### **Объединение запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) обеспечивает [or()](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) метод, который требует двух [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В следующем фрагменте кода показано, как фильтровать сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

## **Фильтрация по внутренней дате**

Сообщения могут быть извлечены с сервера на основе InternalDate, однако иногда сервер не возвращает все сообщения, видимые в папке «Входящие». Это может быть связано с часовым поясом сервера, поскольку на всех серверах, таких как UTC, может быть не так. [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose отправляет команды типа 008 SEARCH 4 мая 2014 года в соответствии с [протокол IMAP](https://datatracker.ietf.org/doc/html/rfc1730) однако результат может отличаться из-за настроек часового пояса сервера. Новый участник добавлен в [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) as [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) что дополнительно помогает фильтровать сообщения. Следующий фрагмент кода показывает использование [InternalDate](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getInternalDate--) для фильтрации сообщений.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");

// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());

// Build the query and Get list of messages
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
for (ImapMessageInfo info : messages) {
    System.out.println("Internal Date: " + info.getInternalDate());
}

// Disconnect from IMAP
client.dispose();
~~~

### **Фильтрация писем с учетом регистра**

В следующем фрагменте кода показано, как использовать фильтрацию писем с учетом регистра букв.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~

### **Укажите кодировку для конструктора запросов**

API [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) Конструктор можно использовать для указания кодировки строки поиска. Это также можно установить с помощью [DefaultEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#getDefaultEncoding--) свойство конструктора MailQueryBuilder. В следующем фрагменте кода показано, как указать кодировку для конструктора запросов.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set conditions
ImapQueryBuilder builder = new ImapQueryBuilder(Charset.forName("utf-8"));
builder.getSubject().contains("ğüşıöç", true);
MailQuery query = builder.getQuery();
~~~

### **Фильтрация сообщений с поддержкой пейджинга**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет возможность искать сообщения из почтового ящика и составлять их список с поддержкой пейджинга. В следующем фрагменте кода показано, как фильтровать сообщения с поддержкой пейджинга.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
/// <summary>
/// This example shows how to search for messages using ImapClient of the API with paging support
/// Introduced in Aspose.Email for .NET 6.4.0
/// </summary>
final ImapClient client = new ImapClient("host.domain.com", 84, "username", "password");
try {
    try {
        // Append some test messages
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
        // foreach to while statements conversion
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

## **Фильтрация сообщений с помощью настраиваемого флага**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();

queryBuilder.hasFlags(ImapMessageFlags.keyword("custom1"));

queryBuilder.hasNoFlags(ImapMessageFlags.keyword("custom2"));
~~~

## **Фильтрация сообщений с помощью настраиваемого поиска**

Например, стандарт RFC 3501 не разрешает поиск сообщений на основе наличия вложений в сообщениях. Но **Gmail** provides [Расширения IMAP](https://developers.google.com/gmail/imap/imap-extensions) которые позволяют выполнить такой поиск. Aspose.Email предоставляет [customSearch](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/#customSearch-java.lang.String-) метод [ImapQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/imapquerybuilder/) класс для создания соответствующего запроса.

В приведенном ниже примере кода показано, как получить список сообщений электронной почты с вложениями с сервером, используя протокол IMAP и настраиваемый критерий поиска:

```java
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.customSearch("X-GM-RAW \"has:attachment\"");
MailQuery query = builder.getQuery();
messageInfoCol = client.listMessages(query);
```
