---
title: "Работа с сообщениями от сервера"
url: /ru/java/working-with-messages-from-server/
weight: 50
type: docs
---


## **Получение информации о почтовом ящике**

Мы можем получить информацию о почтовом ящике, такую как количество сообщений и размер почтового ящика, с помощью методов [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) и [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

- Метод [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) возвращает размер почтового ящика в байтах.
- Метод [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) возвращает объект типа [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/).

Также можно получить количество сообщений с помощью свойства [MessageCount](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getMessageCount--) и размер с помощью свойства [OccupiedSize](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getOccupiedSize--) класса [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/). Следующий пример кода демонстрирует, как получить информацию о почтовом ящике. Он показывает, как:

1. Создать [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Подключиться к серверу POP3.
1. Получить размер почтового ящика.
1. Получить информацию о почтовом ящике.
1. Получить количество сообщений в почтовом ящике.
1. Получить занятый размер.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
// Укажите хост, имя пользователя, пароль, порт и параметры безопасности для вашего клиента
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

// Получить размер почтового ящика, получить информацию о почтовом ящике, количество сообщений в почтовом ящике
long nSize = client.getMailboxSize();
System.out.println("Размер почтового ящика составляет " + nSize + " байт.");
Pop3MailboxInfo info = client.getMailboxInfo();
int nMessageCount = info.getMessageCount();
System.out.println("Количество сообщений в почтовом ящике составляет " + nMessageCount);
long nOccupiedSize = info.getOccupiedSize();
System.out.println("Занятый размер составляет " + nOccupiedSize);
~~~

## **Получение количества электронных писем в почтовом ящике**

Следующий фрагмент кода показывает, как подсчитать электронные сообщения в почтовом ящике.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
Pop3Client client = new Pop3Client("pop3.server.com", "username", "password");
try {
    client.setSecurityOptions(SecurityOptions.Auto);
    int i = client.getMessageCount();
    System.out.println("Количество сообщений: " + i);
} catch (Pop3Exception ex) {
    System.out.println("Ошибка:" + ex.toString());
}
~~~

Aspose.Email позволяет разработчикам работать с электронными письмами различными способами. Например, они могут получать информацию заголовка перед тем, как решить, следует ли загружать электронную почту. Или они могут получать электронные письма с сервера и сохранять их без обработки (быстрее) или после обработки (медленнее). Эта статья показывает, как извлекать и преобразовывать электронные письма.

## **Получение информации заголовков электронной почты**

Заголовки электронной почты могут предоставить нам информацию о сообщении электронной почты, которую мы можем использовать, чтобы решить, нужно ли извлекать все сообщение электронной почты или нет. Обычно информация заголовка содержит отправителя, тему, дату получения и так далее. (Заголовки электронной почты подробно описаны в [Настройка заголовков электронной почты](/email/java/creating-and-setting-contents-of-emails/#set-email-headers). Эта тема касается в основном отправки электронной почты с помощью SMTP, но информация о содержании заголовка электронной почты остается действительной для электронных писем POP3). Следующие примеры показывают, как извлекать заголовки электронной почты с сервера POP3 по номеру последовательности сообщения.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр класса Pop3Client
Pop3Client client = new Pop3Client();

// Укажите хост, имя пользователя, пароль, порт и параметры безопасности для вашего клиента
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    HeaderCollection headers = client.getMessageHeaders(1);
    for (int i = 0; i < headers.size(); i++) {
        // Отобразить ключ и значение в коллекции заголовка
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

## **Извлечение сообщений электронной почты**

Класс [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) предоставляет возможность извлекать сообщения электронной почты с сервера POP3 и обрабатывать их в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) с помощью компонентов [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) содержит несколько свойств и методов для манипулирования содержимым электронной почты. Используя метод [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/), вы можете получить экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) непосредственно с сервера POP3. Следующий фрагмент кода показывает, как извлечь полное сообщение электронной почты с сервера POP3.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр класса Pop3Client
Pop3Client client = new Pop3Client();

// Укажите хост, имя пользователя, пароль, порт и параметры безопасности для вашего клиента
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    int messageCount = client.getMessageCount();
    // Создайте экземпляр класса MailMessage и извлеките сообщение
    MailMessage message;
    for (int i = 1; i <= messageCount; i++) {
        message = client.fetchMessage(i);
        System.out.println("От:" + message.getFrom());
        System.out.println("Тема:" + message.getSubject());
        System.out.println(message.getHtmlBody());
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Извлечение сводной информации о сообщениях по уникальному идентификатору**

Клиент POP3 API может извлекать сводную информацию о сообщениях с сервера, используя уникальный идентификатор сообщения. Это обеспечивает быстрый доступ к краткой информации о сообщении без предварительного извлечения полного сообщения с сервера. Следующий фрагмент кода показывает, как извлечь сводную информацию о сообщении.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
String uniqueId = "уникальный идентификатор сообщения с сервера";
Pop3Client client = new Pop3Client("host.domain.com", 456, "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
Pop3MessageInfo messageInfo = client.getMessageInfo(uniqueId);

if (messageInfo != null) {
    System.out.println(messageInfo.getSubject());
    System.out.println(messageInfo.getDate());
}
~~~

## **Список сообщений с многосоединением**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) предоставляет свойство [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setUseMultiConnection-int-), которое можно использовать для создания нескольких соединений для тяжелых операций. Вы также можете установить количество соединений, используемых в режиме многосоединения, с помощью [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setConnectionsQuantity-int-). Следующий фрагмент кода демонстрирует использование режима многосоединения для перечисления сообщений и сравнивает его производительность с режимом одного соединения.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр класса Pop3Client
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

System.out.println("multiConnectionModeTimeSpan: " + multiConnectionModeTimeSpan);
System.out.println("singleConnectionModeTimeSpan: " + singleConnectionModeTimeSpan);
double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Соотношение производительности: " + performanceRelation);
~~~

{{% alert color="primary" %}} 

Пожалуйста, обратите внимание, что использование режима многосоединения не гарантирует увеличение производительности.

{{% /alert %}} 

## **Извлечение сообщений с сервера и сохранение на диск**

### **Сохранение сообщения на диск без обработки**

Если вы хотите загрузить электронные сообщения с сервера POP3 без их обработки, используйте функцию [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage\(java.lang.String,%20java.io.OutputStream\)) класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). Функция [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) не обрабатывает сообщение электронной почты, поэтому она быстрее, чем функция [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-). Следующий фрагмент кода показывает, как сохранить сообщение по его номеру последовательности, в данном случае номер 1. Метод [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) сохраняет сообщение в оригинальном формате EML без обработки его.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "pop3/";
String dstEmail = dataDir + "InsertHeaders.eml";

// Создайте экземпляр класса Pop3Client
Pop3Client client = new Pop3Client();

// Укажите хост, имя пользователя, пароль, порт и параметры безопасности для вашего клиента
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Сохранить сообщение на диск по номеру последовательности
    client.saveMessage(1, dstEmail);
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
System.out.println("Извлеченные электронные сообщения с использованием POP3 ");
~~~

### **Обработка сообщения перед сохранением**

Следующий фрагмент кода использует метод [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) для извлечения сообщения с сервера POP3 по его номеру последовательности, а затем сохраняет сообщение на диск, используя тему в качестве имени файла.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "pop3/";

// Создайте экземпляр класса Pop3Client
Pop3Client client = new Pop3Client();

// Укажите хост, имя пользователя и пароль, порт и параметры безопасности для вашего клиента
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Извлечь сообщение по его номеру последовательности и сохранить сообщение, используя его тему в качестве имени файла
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

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) предоставляет метод [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) который принимает итерируемую последовательность номеров или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Следующий фрагмент кода демонстрирует использование метода [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) для извлечения сообщений по номерам последовательности и уникальным идентификаторам.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр класса Pop3Client
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

Pop3MessageInfoCollection messageInfoCol = pop3Client.listMessages();
System.out.println("Количество сообщений ListMessages: " + messageInfoCol.size());

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

Класс [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/), описанный в [Подключение к серверу POP3](/email/java/connect-to-pop3-server/#connecting-to-pop3-server), предоставляет метод [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) который получает все сообщения из почтового ящика. Чтобы получить только сообщения, соответствующие некоторому условию, используйте перегруженный метод [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) который принимает [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) в качестве аргумента. Класс [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) предоставляет различные свойства для указания условий запроса, например, дата, тема, отправитель, получатель и так далее. Класс [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) используется для построения выражения поиска. Сначала устанавливаются все условия и ограничения, а затем [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) заполняется запросом, разработанным с помощью [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/). Объект класса [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) используется [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) для извлечения отфильтрованной информации с сервера. Эта статья показывает, как фильтровать электронные сообщения из почтового ящика. Первый пример иллюстрирует, как фильтровать сообщения по дате и теме. Мы также покажем, как фильтровать по другим критериям и как строить более сложные запросы. Также показано применение фильтра по дате и времени для извлечения конкретных электронных писем из почтового ящика. Кроме того, также показано, как применять фильтрацию с учетом регистра.

### **Фильтрация сообщений из почтового ящика**

Чтобы отфильтровать сообщения из почтового ящика:

1. [Подключитесь и войдите на сервер POP3](/email/java/connect-to-pop3-server#connecting-to-pop3-server).
1. Создайте экземпляр [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) и установите необходимые свойства.
1. Вызовите метод [Pop3Client.listMessages(MailQuery query)](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages-com.aspose.email.MailQuery-) и передайте [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) в параметры, чтобы получить только отфильтрованные сообщения.

Следующий фрагмент кода показывает, как подключиться к почтовому ящику POP3 и получить сообщения, которые пришли сегодня и содержат слово "рассылка" в теме.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Подключитесь и войдите в POP3
String host = "host";
int port = 110;
String username = "user@host.com";
String password = "password";
Pop3Client client = new Pop3Client(host, port, username, password);

// Установите условия, Тема содержит "Рассылка", Электронные письма, которые пришли сегодня
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Рассылка");
builder.getInternalDate().on(new Date());
// Постройте запрос и получите список сообщений
MailQuery query = builder.getQuery();
Pop3MessageInfoCollection messages = client.listMessages(query);
System.out.println("Pop3: " + messages.size() + " сообщение(й) найдено.");
~~~

### **Получение сообщений, соответствующих определенным критериям**

[Примеры кода выше](/email/java/working-with-messages-from-server/#filtering-messages-from-mailbox) фильтруют сообщения на основе темы электронной почты и даты. Мы можем также использовать другие свойства для установки других поддерживаемых условий. Ниже приведены несколько примеров установки условий с использованием [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

Следующие фрагменты кода показывают, как фильтровать электронные письма по другим критериям:

- Найти электронные письма, доставленные сегодня.
- Найти электронные письма, полученные в диапазоне.
- Найти электронные письма от конкретного отправителя.
- Найти электронные письма, отправленные с конкретного домена.
- Найти электронные письма, отправленные конкретному получателю.
  
#### **Дата сегодня**

Следующий фрагмент кода показывает, как найти электронные письма, доставленные сегодня.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Электронные письма, которые пришли сегодня
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~

#### **Диапазон дат**

Следующий фрагмент кода показывает, как найти электронные письма, полученные в диапазоне.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Электронные письма, которые пришли за последние 7 дней
Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Конкретный отправитель**

Следующий фрагмент кода показывает, как найти электронные письма от конкретного отправителя.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Получить электронные письма от конкретного отправителя
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

#### **Конкретный домен**

Следующий фрагмент кода показывает, как найти электронные письма, отправленные с конкретного домена.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Получить электронные письма от конкретного домена
builder.getFrom().contains("SpecificHost.com");
~~~

#### **Конкретный получатель**

Следующий фрагмент кода показывает, как найти электронные письма, отправленные конкретному получателю.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Получить электронные письма, отправленные конкретному получателю
builder.getTo().contains("recipient");
~~~

### **Построение сложных запросов**

Если различные свойства [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) устанавливаются в отдельных инструкциях, тогда все условия будут соответствовать. Например, если мы хотим получить сообщения в диапазоне дат и от конкретного хоста, нам нужно написать три инструкции.

#### **Комбинирование запросов с AND**

Следующий фрагмент кода показывает, как комбинировать запросы с AND.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Электронные письма от конкретного хоста, получаем все электронные письма, пришедшие до сегодня, и все электронные письма, пришедшие с 7 дней назад
builder.getFrom().contains("SpecificHost.com");

Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Комбинирование запросов с OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) предоставляет метод [or](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) который принимает два экземпляра [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) в качестве параметров. Он получает сообщения, которые соответствуют любому из двух указанных условий. Следующий фрагмент кода показывает, как фильтровать сообщения, которые содержат "тест" в теме или "noreply@host.com" в качестве отправителя. Следующий фрагмент кода показывает, как комбинировать запросы с OR.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Установите условие OR
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

#### **Применение фильтров с учетом регистра**

API также предоставляет возможность фильтровать электронные письма из почтового ящика на основе критерия с учетом регистра. Следующие методы предоставляют возможность искать электронные письма, указывая флаг с учетом регистра.

- Метод StringComparisonField.contains(String value, boolean ignoreCase)
- Метод StringComparisonField.equals(String value, boolean ignoreCase)
- Метод StringComparisonField.notContains(String boolean, bool ignoreCase)
- Метод StringComparisonField.notEquals(String boolean, bool ignoreCase)

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// IgnoreCase равно true
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
Pop3MessageInfoCollection messageInfoCol1 = client.listMessages(query1);
~~~