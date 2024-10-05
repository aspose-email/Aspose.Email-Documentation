---
title: Работа с почтовыми ящиками Exchange и сообщениями - Чтение электронной почты с сервера Exchange на Java
linktitle: Работа с почтовыми ящиками Exchange и сообщениями
type: docs
weight: 20
url: /java/working-with-exchange-mailbox-and-messages/
keywords: java чтение электронной почты с сервера exchange
---


## **Получение информации о почтовом ящике с помощью EWS**
Класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) имеет члены, которые могут быть использованы для получения информации о почтовом ящике с сервера Exchange, вызывая метод [IEWSClient.getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getMailboxInfo\(\)). Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo). Получите информацию о почтовом ящике из таких свойств, как [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getInboxUri\(\)) и [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#setDraftsUri\(java.lang.String\)). Эта статья показывает, как получить доступ к информации о почтовом ящике с помощью веб-служб Exchange.

Если вы хотите подключиться к серверу Exchange, используя веб-службы Exchange (EWS), используйте класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient). Этот класс использует EWS для подключения и управления элементами на сервере Exchange. Следующий фрагмент кода на Java показывает, как получить информацию о почтовом ящике с помощью веб-служб обмена.



~~~Java
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получить размер почтового ящика, информацию о почтовом ящике Exchange, URI почтового ящика и URI папки "Входящие"
System.out.println("Размер почтового ящика: " + client.getMailboxSize() + " байт");
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
System.out.println("URI почтового ящика: " + mailboxInfo.getMailboxUri());
System.out.println("URI папки 'Входящие': " + mailboxInfo.getInboxUri());
System.out.println("URI отправленных элементов: " + mailboxInfo.getSentItemsUri());
System.out.println("URI папки 'Черновики': " + mailboxInfo.getDraftsUri());
~~~
## **Отправка электронных сообщений**
Вы можете отправлять электронные сообщения с помощью сервера Exchange с помощью инструментов из [Aspose.Email.Exchange](#working-with-exchange-mailbox-and-messages). Метод IEWSClient.Send() принимает экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) в качестве параметра и отправляет электронное сообщение. Эта статья объясняет, как отправлять электронные сообщения с помощью веб-служб Exchange.

Aspose.Email предоставляет класс IEWSClient для подключения к Microsoft Exchange Server с использованием веб-служб Exchange. Следующий фрагмент кода показывает, как использовать EWS для отправки электронных писем с помощью сервера Microsoft Exchange. Следующий фрагмент кода на Java показывает, как отправлять электронные сообщения с использованием EWS.



~~~Java
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Создать экземпляр типа MailMessage
MailMessage msg = new MailMessage();
msg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("recipient@ domain.com "));
msg.setSubject("Отправка сообщения с сервера Exchange");
msg.setHtmlBody("<h3>отправка сообщения с сервера Exchange</h3>");

// Отправить сообщение
client.send(msg);
~~~

## **Получение класса сообщения**

Метод [getMessageClass()](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/#getMessageClass--) класса [ExchangeMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/) получает строку, представляющую класс для сообщения. Пример кода ниже показывает, как получить класс сообщения:

```java
try (IEWSClient client = EWSClient.getEWSClient(uri, credentials))
{
    ExchangeMessageInfoCollection messageInfoCollection = client.listMessagesFromPublicFolder(publicFolder);

    for (ExchangeMessageInfo messageInfo : messageInfoCollection)
    {
        System.out.println("Класс сообщения: " + messageInfo.getMessageClass());
    }
}
```
## **Чтение электронных писем из почтового ящика другого пользователя**
Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, и у некоторых пользователей есть несколько электронных почтовых учетных записей на одном и том же сервере Exchange. В обоих случаях пользователи могут получить доступ к почтовым ящикам других пользователей, используя Aspose.Email для Java. Этот API предоставляет механизм для доступа к папкам и электронным письмам из других почтовых ящиков с помощью класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Эта функция может быть достигнута с помощью перегруженного метода [getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#getMailboxInfo\(\)), предоставляя адрес электронной почты пользователя в качестве параметра.

Следующий фрагмент кода показывает, как читать электронные письма с помощью класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



~~~Java
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получить информацию о почтовом ящике Exchange другой учетной записи
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo("otherUser@domain.com");
~~~
## **Список сообщений**
Список электронных сообщений в почтовом ящике Exchange можно получить, вызвав метод [IEWSClient.listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)). Получите основную информацию о сообщениях, такую как тема, от, к и идентификатор сообщения, используя метод [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)).
### **Простой список сообщений**
Чтобы перечислить сообщения в почтовом ящике Exchange:

1. Создайте экземпляр класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
1. Вызовите метод listMessages и создайте коллекцию сообщений.
1. Пройдите по коллекции и отобразите информацию о сообщении.

Следующий фрагмент кода на Java показывает, как подключиться к серверу обмена, используя EWS, и перечислить сообщения из папки "Входящие".



~~~Java
// Создать экземпляр класса ExchangeWebServiceClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Вызвать метод ListMessages для списка информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Пройтись по коллекции, чтобы отобразить основную информацию
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Тема: " + msgInfo.getSubject());
    System.out.println("От: " + msgInfo.getFrom().toString());
    System.out.println("К: " + msgInfo.getTo().toString());
    System.out.println("Идентификатор сообщения: " + msgInfo.getMessageId());
    System.out.println("Уникальный URI: " + msgInfo.getUniqueUri());
}
~~~
### **Список сообщений из различных папок**
[В приведенных выше фрагментах кода](#simple-messages-listing) перечислены все сообщения в папке "Входящие". Также возможен список сообщений из других папок. Метод [IEWSClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) принимает URI папки в качестве параметра. При условии, что URI папки действителен, вы можете получить список сообщений из этой папки. Используйте свойство IEWSClient.getMailboxInfo().getXXXFolderUri, чтобы получить URI различных папок. Остальная часть кода такая же, как при получении списка сообщений. Следующий фрагмент кода показывает, как перечислить сообщения из различных папок с помощью EWS.


~~~Java
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Получить URI папки
String strFolderURI = "";
strFolderURI = client.getMailboxInfo().getInboxUri();
strFolderURI = client.getMailboxInfo().getDeletedItemsUri();
strFolderURI = client.getMailboxInfo().getDraftsUri();
strFolderURI = client.getMailboxInfo().getSentItemsUri();

// Получить список сообщений из указанной папки
ExchangeMessageInfoCollection msgCollection = client.listMessages(strFolderURI);
~~~
### **Список сообщений с поддержкой постраничной навигации**
Следующий фрагмент кода на Java показывает, как получить список сообщений с поддержкой постраничной навигации.

~~~Java
// Для получения полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
try {
    try {
        // Создать несколько тестовых сообщений, которые будут добавлены на сервер для последующего извлечения
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157_1 - " + UUID.randomUUID().toString(),
                    "EMAILNET-35157 Переместить параметры постраничной навигации в отдельный класс");
            client.appendMessage(client.getMailboxInfo().getInboxUri(), message);
        }
        // Убедитесь, что сообщения были добавлены на сервер
        ExchangeMessageInfoCollection totalMessageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
        System.out.println(totalMessageInfoCol.size());

        ////////////////// ПОЛУЧЕНИЕ СООБЩЕНИЙ С ИСПОЛЬЗОВАНИЕМ ПОДДЕРЖКИ ПОСТРИЧНОЙ НАВИГАЦИИ ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
        // Общее количество страниц
        System.out.println(pageInfo.getTotalCount());

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage, pageInfo.getPageOffset() + 1);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // преобразование цикла foreach в while
        for (ExchangeMessagePageInfo pageCol : pages) {
            retrievedItems += pageCol.getItems().size();
        }
        // Проверьте общее количество сообщений с использованием постраничной навигации
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    client.dispose();
}
~~~
### **Получение информации о типе сообщения из ExchangeMessageInfo**


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.listMessages(client.getMailboxInfo().getDeletedItemsUri());
System.out.println(list.get_Item(0).getMessageInfoType()); // MessageInfoType
~~~
## **Сохранение сообщений**
Эта статья показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их на диск в форматах EML и MSG:

- Сохранить как EML на диск.
- Сохранить в поток памяти.
- Сохранить как MSG.
### **Сохранение сообщений в EML**
Чтобы получить сообщения и сохранить их в формате EML:

1. Создайте экземпляр класса IEWSClient.
2. Укажите mailboxUri, имя пользователя, пароль и домен.
3. Вызовите метод IEWSClient.listMessages() для получения экземпляра коллекции ExchangeMessagesInfoCollection.
4. Пройдите через коллекцию ExchangeMessagesInfoCollection, чтобы получить уникальный URI для каждого сообщения.
5. Вызовите метод IEWSClient.saveMessage() и передайте уникальный URI в качестве параметра.
6. Укажите методу saveMessage() путь, по которому вы хотите сохранить файл.

Следующий фрагмент кода показывает, как использовать EWS для подключения к серверу Exchange и сохранения сообщений в виде файлов EML.



~~~Java
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызвать метод ListMessages для списка информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Пройтись по коллекции, чтобы получить URI сообщения
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Теперь сохраните сообщение на диск
    client.saveMessage(strMessageURI, dataDir + msgInfo.getMessageId() + "out.eml");
}
~~~
### **Сохранение сообщений в поток памяти**
Вместо сохранения файлов EML на диск можно сохранить их в поток памяти. Это полезно, когда вы хотите сохранить поток в каком-то месте хранения, например, в базе данных. После того, как поток был сохранен в базе данных, вы можете загрузить файл EML обратно в класс [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Следующий фрагмент кода показывает, как сохранить сообщения из почтового ящика сервера Exchange в поток памяти, используя EWS.



~~~Java
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызвать метод ListMessages для списка информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Пройтись по коллекции, чтобы получить URI сообщения
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Теперь сохраните сообщение в поток памяти
    ByteArrayOutputStream stream = new ByteArrayOutputStream();
    client.saveMessage(strMessageURI, stream);
}
~~~
### **Сохранение сообщений в формате MSG**
Метод [IEWSClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#saveMessage\(java.lang.String,%20java.lang.String\)) может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите метод [IEWSClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchMessage\(java.lang.String\)), который возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Затем вызовите метод [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.lang.String\)), чтобы сохранить сообщение в MSG. Следующий фрагмент кода показывает, как получить сообщения из почтового ящика сервера Exchange и сохранить их в формате MSG, используя EWS.



~~~Java
// Создать экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызвать метод ListMessages для списка информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

int count = 0;
// Пройтись по коллекции, чтобы получить URI сообщения
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Теперь получите детали сообщения с помощью FetchMessage() и сохраните сообщение как Msg
    MailMessage message = client.fetchMessage(strMessageURI);
    message.save(dataDir + (count++) + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~
## **Получение ExchangeMessageInfo из URI сообщения**
Электронное сообщение представляется своим уникальным идентификатором, URI, и является неотъемлемой частью объекта [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). В случае, если доступен только URI сообщения, объект [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) также может быть получен с использованием этой доступной информации. Перегруженная версия метода [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.Iterable\)) принимает список идентификаторов для использования с [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection). Следующий фрагмент кода показывает, как получить [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) из URI сообщения.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<String> ids = new ArrayList<String>();
List<MailMessage> messages = new ArrayList<MailMessage>();

for (int i = 0; i < 5; i++) {
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + UUID.randomUUID().toString(),
            "EMAILNET-35033 Сообщения, сохраненные из папки 'Отправленные', не содержат поле 'Кому'");
    messages.add(message);
    String uri = client.appendMessage(message);
    ids.add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(ids);

for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) messageInfoCol) {
    // Сделать что-то ...
    System.out.println(messageInfo.getUniqueUri());
}
~~~
## **Получение сообщений из почтового ящика сервера Exchange**
Метод [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) используется для получения списка сообщений из почтового ящика сервера Exchange. Метод [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) получает основную информацию о сообщениях, например, тему, идентификатор сообщения, от и до. Чтобы получить полные детали сообщения, Aspose.Email.Exchange предоставляет метод IEWSClient.fetchMessage(). Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Класс [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) затем предоставляет детали сообщения, такие как тело, заголовки и вложения. Узнайте больше о API [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) или узнайте, как управлять электронной почтой с помощью класса [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Чтобы получить сообщения из почтового ящика сервера Exchange:

1. Создайте экземпляр типа IEWSClient.
2. Укажите имя сервера, имя пользователя, пароль и домен.
3. Вызовите listMessages, чтобы получить ExchangeMessageInfoCollection.
4. Пройдите по коллекции ExchangeMessageInfoCollection, чтобы получить значения ExchangeMessageInfo.UniqueURI.
5. Вызовите метод IEWSClient.fetchMessage() и передайте ExchangeMessageInfo.UniqueURI в качестве параметра.

Следующий фрагмент кода показывает, как подключиться к почтовому ящику сервера Exchange и получить все сообщения, используя EWS.



~~~Java
// Создать экземпляр класса ExchangeWebServiceClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызвать метод ListMessages для списка информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Пройтись по коллекции, чтобы получить URI сообщения
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Теперь получите детали сообщения с помощью FetchMessage()
    MailMessage msg = client.fetchMessage(strMessageURI);

    for (Attachment att : (Iterable<Attachment>) msg.getAttachments()) {
        System.out.println("Имя вложения: " + att.getName());
    }
}
~~~

### **Использование метода FetchItem для получения сообщения**

{{% alert color="primary" %}}

Обратите внимание, что метод [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) возвращает сообщение без вложений. Чтобы извлечь сообщения с вложениями, используйте метод [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)), описанный в разделе ниже. 

{{% /alert %}}

Метод [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) более предпочтителен, если вы хотите извлечь [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) и работать с MAPI-свойствами. Вы также можете использовать этот метод для извлечения любого элемента Outlook, например, контакта, встречи, задачи и т.д.

```java
// Создать экземпляр класса ExchangeWebServiceClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызвать метод ListMessages для списка информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Пройтись по коллекции, чтобы получить URI сообщения
for (ExchangeMessageInfo msgInfo : msgCollection)
{
    // Теперь получите сообщение с помощью FetchItem()
    MapiMessage msg = client.fetchItem(msgInfo.getUniqueUri());

    // Если необходимо, вы можете привести MapiMessage к правильному типу элемента, чтобы упростить работу с его свойствами.
    MapiContact contact = (MapiContact) msg.toMapiMessageItem();
}
```

## **Предварительное получение размера сообщения**
Microsoft Outlook InterOp предоставляет функцию извлечения размера сообщения перед фактическим получением полного сообщения с сервера. В случае с API Aspose.Email сводная информация, извлеченная с сервера Exchange, представлена классом [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). Он предоставляет ту же функцию извлечения размера сообщения с помощью свойства Size. Для извлечения размера сообщения используется стандартный вызов метода IEWSClient's listMessages, который извлекает коллекцию [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). Следующий фрагмент кода показывает, как отобразить размер сообщения с использованием класса [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo).



~~~Java
// Создать экземпляр класса ExchangeWebServiceClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Вызвать метод ListMessages для списка информации о сообщениях из папки "Входящие"
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Пройтись по коллекции, чтобы отобразить основную информацию
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Тема: " + msgInfo.getSubject());
    System.out.println("От: " + msgInfo.getFrom().toString());
    System.out.println("К: " + msgInfo.getTo().toString());
    System.out.println("Размер сообщения: " + msgInfo.getSize());
    System.out.println("==================================");
}
~~~
## **Рекурсивное извлечение сообщений**
Метод [listSubFolders()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listSubFolders\(com.aspose.email.ExchangeFolderInfo\)) класса [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) может быть использован для получения сообщений из папок и подпапок из почтового ящика сервера Exchange рекурсивно. Это требует сервера Exchange 2007 или выше, поскольку он использует EWS. Следующий фрагмент кода показывает, как загрузить всю почту (папки и подпапки) с сервера Exchange. Структура папок создается локально, и все сообщения загружаются.



~~~Java
public static void run() {
    try {
        downloadAllMessages();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void downloadAllMessages() {
    try {
        String rootFolder = domain + "-" + username;
        new File(rootFolder).mkdirs();
        String inboxFolder = rootFolder + "\\Inbox";
        new File(inboxFolder).mkdirs();

        System.out.println("Загрузка всех сообщений из папки 'Входящие'....");
        // Создать экземпляр класса IEWSClient, указав учетные данные
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI почтового ящика: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Перечислить все папки с сервера Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Вызвать рекурсивный метод для чтения сообщений и получения подпапок
            listMessagesInFolder(client, folderInfo, rootFolder);
        }

        System.out.println("Все сообщения загружены.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

// Рекурсивный метод для получения сообщений из папок и подпапок
private static void listMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, String rootFolder) {
    // Создать папку на диске (с тем же именем, что и на IMAP-сервере)
    String currentFolder = rootFolder + "\\" + folderInfo.getDisplayName();
    new File(currentFolder).mkdirs();

    // Перечислить сообщения
    ExchangeMessageInfoCollection msgInfoColl = client.listMessages(folderInfo.getUri());
    System.out.println("Перечисление сообщений....");
    int i = 0;
    for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
        // Получить тему и другие свойства сообщения
        System.out.println("Тема: " + msgInfo.getSubject());

        // Избавиться от символов, таких как ? и :, которые не должны быть включены в имя файла
        String fileName = msgInfo.getSubject().replace("?", " ").replace(":", " ");

        MailMessage msg = client.fetchMessage(msgInfo.getUniqueUri());
        msg.save(dataDir + "\\" + fileName + "-" + i + ".msg");

        i++;
    }
    System.out.println("============================\n");
    try {
        // Если у этой папки есть подпапки, вызовите этот метод рекурсивно, чтобы получить сообщения
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Загрузка сообщений из общих папок**
Microsoft Exchange Server позволяет пользователям создавать общие папки и размещать в них сообщения. Чтобы сделать это через ваше приложение, используйте класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) Aspose.Email для подключения к серверу Exchange и чтения и загрузки сообщений и постов из общих папок. Следующий фрагмент кода показывает, как прочитать все общие папки и подпапки и перечислить и загрузить любые сообщения, найденные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, так как только они поддерживают EWS.



~~~Java
public static void run() {
    try {
        readPublicFolders();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void readPublicFolders() {
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.listPublicFolders();
    for (ExchangeFolderInfo publicFolder : (Iterable<ExchangeFolderInfo>) folders) {
        System.out.println("Имя: " + publicFolder.getDisplayName());
        System.out.println("Количество подпапок: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Имя папки: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Вызовите этот метод рекурсивно для любых подпапок
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Перемещение сообщений**
Вы можете перемещать электронные сообщения из одной папки в другую с помощью класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) и метода [move](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#moveItem\(java.lang.String,%20java.lang.String\)). Он принимает параметры:

- Уникальный URI сообщения, которое необходимо переместить.
- Уникальный URI папки назначения.
### **Перемещение сообщений между папками**
Следующий фрагмент кода показывает, как переместить сообщение в почтовом ящике из папки "Входящие" в папку под названием "Обработано". В этом примере приложение:

1. Читает сообщения из папки "Входящие".
2. Обрабатывает некоторые сообщения на основе некоторых критериев (в этом примере мы ищем ключевое слово в теме сообщения).
3. Перемещает сообщения, которые соответствуют заданному условию, в папку "Обработано".

~~~Java
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// Перечислить все сообщения из папки "Входящие"
System.out.println("Перечисление всех сообщений из папки 'Входящие'....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Переместить сообщение в папку "Обработано" после обработки определенных сообщений на основе некоторых критериев
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("обработать это сообщение")) {
        client.moveItem(mailboxInfo.getDeletedItemsUri(), msgInfo.getUniqueUri()); // EWS
        System.out.println("Сообщение перемещено...." + msgInfo.getSubject());
    } else {
        // Сделать что-то другое
    }
}
~~~
## **Удаление сообщений**
Вы можете удалять электронные сообщения из папки с помощью метода [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) класса [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Он принимает уникальный URI сообщения в качестве параметра.

Следующий фрагмент кода показывает, как удалить сообщение из папки "Входящие". Для этой примера код:

1. Читает сообщения из папки "Входящие".
2. Обрабатывает сообщения на основе некоторых критериев (в этом примере мы ищем ключевое слово в теме сообщения).
3. Удаляет сообщение.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// Перечислить все сообщения из папки "Входящие"
System.out.println("Перечисление всех сообщений из папки 'Входящие'....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Удалить сообщение на основе некоторых критериев
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("удалить") == true) {
        client.deleteItem(msgInfo.getUniqueUri(), DeletionOptions.getDeletePermanently()); // EWS
        System.out.println("Сообщение удалено...." + msgInfo.getSubject());
    } else {
        // Сделать что-то другое
    }
}
~~~
## **Копирование сообщений**
API Aspose.Email позволяет копировать сообщение из одной папки в другую с помощью метода [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)). Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.
### **Копирование сообщения в другую папку**
Следующий фрагмент кода показывает, как скопировать сообщение в другую папку.



~~~Java
try {
    // Создать экземпляр класса EWSClient, указав учетные данные
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Копирование сообщения и получение ссылки на новый скопированный элемент");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~