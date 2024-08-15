---
title: "Работа с сообщениями с сервера"
url: /ru/java/working-with-messages-from-server/
weight: 50
type: docs
---


## **Получение данных почтового ящика**

Мы можем получить информацию о почтовом ящике, такую как количество сообщений и размер почтового ящика, используя [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) and [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) методы [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.

- The [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) метод возвращает размер почтового ящика в байтах.
- The [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) метод возвращает объект типа [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/).

Также можно получить количество сообщений, используя [MessageCount](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getMessageCount--) свойство и размер с использованием [OccupiedSize](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getOccupiedSize--) собственность [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/) класс. В следующем примере кода показано, как получить информацию о почтовом ящике. В нем показано, как:

1. Создайте [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Подключитесь к серверу POP3.
1. Узнайте размер почтового ящика.
1. Получите информацию о почтовом ящике.
1. Получите количество сообщений в почтовом ящике.
1. Найдите занятый размер.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

// Get the size of the mailbox, Get mailbox info, number of messages in the mailbox
long nSize = client.getMailboxSize();
System.out.println("Mailbox size is " + nSize + " bytes.");
Pop3MailboxInfo info = client.getMailboxInfo();
int nMessageCount = info.getMessageCount();
System.out.println("Number of messages in mailbox are " + nMessageCount);
long nOccupiedSize = info.getOccupiedSize();
System.out.println("Occupied size is " + nOccupiedSize);
~~~

## **Определение количества сообщений электронной почты в почтовом ящике**

В следующем фрагменте кода показано, как подсчитать количество сообщений электронной почты в почтовом ящике.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
Pop3Client client = new Pop3Client("pop3.server.com", "username", "password");
try {
    client.setSecurityOptions(SecurityOptions.Auto);
    int i = client.getMessageCount();
    System.out.println("Message count: " + i);
} catch (Pop3Exception ex) {
    System.out.println("Error:" + ex.toString());
}
~~~

Aspose.Email позволяет разработчикам работать с электронной почтой разными способами. Например, они могут получить информацию из заголовка, прежде чем принимать решение о загрузке электронного письма. Или они могут извлекать электронные письма с сервера и сохранять их без анализа (быстрее) или после анализа (медленнее). В этой статье показано, как извлекать и конвертировать электронные письма.

## **Получение информации о заголовках электронных писем**

Заголовки электронной почты могут предоставить нам информацию об электронном сообщении, которую мы можем использовать для принятия решения о том, следует ли получать все сообщение электронной почты. Как правило, информация в заголовке содержит отправителя, тему, дату получения и т. д. (заголовки электронных писем подробно описаны в [Настройка заголовков электронной почты](/email/java/creating-and-setting-contents-of-emails/#set-email-headers). Этот раздел посвящен, в частности, отправке электронного письма по протоколу SMTP, но информация о содержимом заголовка письма остается актуальной для писем по протоколу POP3). В следующих примерах показано, как получать заголовки писем с сервера POP3 по порядковому номеру сообщения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username. password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    HeaderCollection headers = client.getMessageHeaders(1);
    for (int i = 0; i < headers.size(); i++) {
        // Display key and value in the header collection
        System.out.print(headers.getKey(i));
        System.out.print(" : ");
        System.out.println(headers.get(i));
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Получение сообщений электронной почты**

The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) компонент класса предоставляет возможность извлекать сообщения электронной почты с сервера POP3 и преобразовывать их в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр с помощью [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) компоненты. [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс содержит несколько свойств и методов для управления содержимым электронной почты. Используя [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) метод [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) класс, вы можете получить [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр непосредственно с сервера POP3. В следующем фрагменте кода показано, как получить полное сообщение электронной почты с сервера POP3.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    int messageCount = client.getMessageCount();
    // Создайте экземпляр the MailMessage class and Retrieve message
    MailMessage message;
    for (int i = 1; i <= messageCount; i++) {
        message = client.fetchMessage(i);
        System.out.println("From:" + message.getFrom());
        System.out.println("Subject:" + message.getSubject());
        System.out.println(message.getHtmlBody());
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Получение сводной информации о сообщении с использованием уникального идентификатора**

Клиент API POP3 может получать сводную информацию о сообщении с сервера, используя уникальный идентификатор сообщения. Это обеспечивает быстрый доступ к краткой информации о сообщении без предварительного получения полного сообщения с сервера. В следующем фрагменте кода показано, как получить сводную информацию о сообщении.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String uniqueId = "unique id of a message from server";
Pop3Client client = new Pop3Client("host.domain.com", 456, "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
Pop3MessageInfo messageInfo = client.getMessageInfo(uniqueId);

if (messageInfo != null) {
    System.out.println(messageInfo.getSubject());
    System.out.println(messageInfo.getDate());
}
~~~

## **Список сообщений с помощью MultiConnection**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) обеспечивает [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setUseMultiConnection-int-) свойство, которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете настроить количество подключений, которое будет использоваться в режиме нескольких подключений, используя [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setConnectionsQuantity-int-). В следующем фрагменте кода показано использование режима нескольких подключений для перечисления сообщений и сравнивается его производительность с режимом одиночного подключения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр the Pop3Client class
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

pop3Client.setConnectionsQuantity(5);
pop3Client.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol1 = pop3Client.listMessages();
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

pop3Client.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol2 = pop3Client.listMessages();
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

System.out.println("multyConnectionModeTimeSpan: " + multiConnectionModeTimeSpan);
System.out.println("singleConnectionModeTimeSpan: " + singleConnectionModeTimeSpan);
double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Performance Relation: " + performanceRelation);
~~~

{{% alert color="primary" %}}

Обратите внимание, что использование режима нескольких подключений не гарантирует повышения производительности.

{{% /alert %}}

## **Загрузка сообщений с сервера и сохранение на диск**

### **Сохранить сообщение на диск без парсинга**

Если вы хотите загрузить сообщения электронной почты с сервера POP3 без их анализа, используйте [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage\(java.lang.String,%20java.io.OutputStream\)) функция. [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) функция не анализирует сообщение электронной почты, поэтому оно работает быстрее, чем [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) функция. В следующем фрагменте кода показано, как сохранить сообщение по порядковому номеру, в данном случае — по номеру 1. [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) метод сохраняет сообщение в исходном формате EML без его анализа.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "pop3/";
String dstEmail = dataDir + "InsertHeaders.eml";

// Создайте экземпляр the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Save message to disk by message sequence number
    client.saveMessage(1, dstEmail);
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
System.out.println("Retrieved email messages using POP3 ");
~~~

### **Проанализируйте сообщение перед сохранением**

В следующем фрагменте кода используется [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) метод получения сообщения с сервера POP3 по порядковому номеру, а затем сохранения сообщения на диск, используя тему в качестве имени файла.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "pop3/";

// Создайте экземпляр the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username and password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Fetch the message by its sequence number and Save the message using its subject as the file name
    MailMessage msg = client.fetchMessage(1);
    msg.save(dataDir + "first-message_out.eml", SaveOptions.getDefaultEml());
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Групповая выборка сообщений**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) обеспечивает [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) метод, который принимает итерацию последовательных номеров или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Следующий фрагмент кода демонстрирует использование [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) метод получения сообщений по порядковым номерам и уникальному идентификатору.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр the Pop3Client class
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

Pop3MessageInfoCollection messageInfoCol = pop3Client.listMessages();
System.out.println("ListMessages Count: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (Pop3MessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : pop3Client.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : pop3Client.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~

## **Фильтрация сообщений по отправителю, получателю или дате**

The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) класс, описанный в [Подключение к серверу POP3](/email/java/connect-to-pop3-server/#connecting-to-pop3-server), предоставляет [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) метод, который получает все сообщения из почтового ящика. Чтобы получать только сообщения, соответствующие определенному условию, используйте перегруженный [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) метод, который принимает [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) в качестве аргумента. [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) класс предоставляет различные свойства для указания условий запроса, например дату, тему, отправитель, получатель и т. д. [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) класс используется для построения поискового выражения. Сначала задаются все условия и ограничения, а затем [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) заполняется запросом, разработанным [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/). [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) объект класса используется [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) для извлечения отфильтрованной информации с сервера. В этой статье показано, как фильтровать сообщения электронной почты из почтового ящика. В первом примере показано, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и создавать более сложные запросы. Также показано применение фильтра даты и времени для извлечения определенных писем из почтового ящика. Кроме того, в нем также показано, как применять фильтрацию с учетом регистра символов.

### **Фильтрация сообщений из почтового ящика**

Чтобы отфильтровать сообщения из почтового ящика, выполните следующие действия

1. [Подключение к серверу POP3 и вход на него](/email/java/connect-to-pop3-server#connecting-to-pop3-server).
1. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) и задайте нужные свойства.
1. Позвоните [Сообщения POP3Client.List (запрос MailQuery)](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages-com.aspose.email.MailQuery-) метод и передайте [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) в параметрах, чтобы получать только отфильтрованные сообщения.

В следующем фрагменте кода показано, как подключиться к почтовому ящику POP3 и получать сообщения, пришедшие сегодня и содержащие слово «информационный бюллетень» в теме.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to POP3
String host = "host";
int port = 110;
String username = "user@host.com";
String password = "password";
Pop3Client client = new Pop3Client(host, port, username, password);

// Set conditions, Subject contains "Newsletter", Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Build the query and Get list of messages
MailQuery query = builder.getQuery();
Pop3MessageInfoCollection messages = client.listMessages(query);
System.out.println("Pop3: " + messages.size() + " message(s) found.");
~~~

### **Получение сообщений, соответствующих определенным критериям**

[Приведенные выше примеры кода](/email/java/working-with-messages-from-server/#filtering-messages-from-mailbox) фильтрует сообщения по теме и дате письма. Мы также можем использовать другие свойства для установки других поддерживаемых условий. Ниже приведены несколько примеров настройки условий с помощью [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

Приведенные ниже фрагменты кода показывают, как фильтровать электронные письма по другим критериям:

- Найдите электронные письма, доставленные сегодня.
- Найдите электронные письма, полученные в пределах диапазона.
- Найдите электронные письма от определенного отправителя.
- Найдите электронные письма, отправленные с определенного домена.
- Найдите электронные письма, отправленные определенному получателю.
 
#### **Сегодняшняя дата**

В следующем фрагменте кода показано, как найти электронные письма, доставленные сегодня.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~

#### **Диапазон дат**

В следующем фрагменте кода показано, как найти электронные письма, полученные в пределах диапазона.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived in last 7 days
Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Конкретный отправитель**

В следующем фрагменте кода показано, как найти электронные письма от определенного отправителя.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

#### **Конкретный домен**

В следующем фрагменте кода показано, как найти электронные письма, отправленные с определенного домена.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~

#### **Конкретный получатель**

В следующем фрагменте кода показано, как найти электронные письма, отправленные определенному получателю.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~

### **Создание сложных запросов**

Если отличается [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) свойства задаются в отдельных выражениях, тогда все условия будут выполнены. Например, если мы хотим получать сообщения за определенный диапазон дат и от определенного хоста, нам нужно написать три выражения.

#### **Объединение запросов с AND**

В следующем фрагменте кода показано, как комбинировать запросы с AND.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");

Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Объединение запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) обеспечивает [or](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) метод, который требует двух [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) экземпляры в качестве параметров. Он получает сообщения, соответствующие любому из двух указанных условий. В следующем фрагменте кода показано, как фильтровать сообщения, в теме которых указано слово «test» или «noreply@host.com» в качестве отправителя. В следующем фрагменте кода показано, как комбинировать запросы с OR.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

#### **Применение фильтров, чувствительных к регистру**

API также предоставляет возможность фильтровать электронные письма из почтового ящика на основе критериев, учитывающих регистр символов. Следующие методы позволяют искать электронные письма, указывая флажок, учитывающий регистр букв.

- Метод StringComparisonField.contains (строковое значение, логическое значение IgnoreCase)
- Метод StringComparisonField.equals (строковое значение, логическое значение IgnoreCase)
- Метод StringComparisonField.notContains (строка булева, логическое значение игнорирует регистр)
- Метод StringComparisonField.noEquals (строка логическое значение, логическое значение IgnoreCase)

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// IgnoreCase is True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
Pop3MessageInfoCollection messageInfoCol1 = client.listMessages(query1);
~~~
