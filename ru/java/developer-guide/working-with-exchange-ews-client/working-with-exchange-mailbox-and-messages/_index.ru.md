---
title: "Работа с почтовым ящиком и сообщениями Exchange — чтение электронной почты с сервера Exchange на Java"
url: /ru/java/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Работа с почтовым ящиком и сообщениями Exchange"
keywords: "java читает электронную почту с сервера Exchange"
---


## **Получение данных почтового ящика с помощью EWS**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс содержит элементы, которые можно использовать для получения информации о почтовом ящике с сервера Exchange путем вызова [IEWSClient.getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getMailboxInfo\(\)) метод. Он возвращает экземпляр типа [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo). Получайте информацию о почтовом ящике из таких объектов, как [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getInboxUri\(\)) and [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#setDraftsUri\(java.lang.String\)). В этой статье показано, как получить доступ к данным почтового ящика с помощью веб-служб Exchange.

Если вы хотите подключиться к серверу Exchange с помощью веб-служб Exchange (EWS), используйте [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) класс. В этом классе используется EWS для подключения к элементам на сервере Exchange и управления ими. В следующем фрагменте кода Java показано, как получать информацию о почтовом ящике с помощью веб-служб Exchange.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get mailbox size, exchange mailbox info, Mailbox and Inbox folder URI
System.out.println("Mailbox size: " + client.getMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
System.out.println("Inbox folder URI: " + mailboxInfo.getInboxUri());
System.out.println("Sent Items URI: " + mailboxInfo.getSentItemsUri());
System.out.println("Drafts folder URI: " + mailboxInfo.getDraftsUri());
~~~
## **Отправка сообщений электронной почты**
Вы можете отправлять сообщения электронной почты с помощью Exchange Server с помощью инструментов в [Aspose.Email.Exchange](#working-with-exchange-mailbox-and-messages). Метод IewSclient.send () принимает [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) экземпляр в качестве параметра и отправляет электронное письмо. В этой статье объясняется, как отправлять сообщения электронной почты с помощью веб-служб Exchange.

Aspose.Email предоставляет класс IEWSClient для подключения к серверу Microsoft Exchange с помощью веб-служб Exchange. В следующем фрагменте кода показано, как использовать EWS для отправки электронных писем с помощью Microsoft Exchange Server. В следующем фрагменте кода Java показано, как отправлять сообщения электронной почты с помощью EWS.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create instance of type MailMessage
MailMessage msg = new MailMessage();
msg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("recipient@ domain.com "));
msg.setSubject("Sending message from exchange server");
msg.setHtmlBody("<h3>sending message from exchange server</h3>");

// Send the message
client.send(msg);
~~~

## **Получение класса сообщений**

The [getMessageClass()](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/#getMessageClass--) метод [ExchangeMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/) class получает строку, представляющую класс сообщения. В приведенном ниже примере кода показано, как получить класс сообщения:

```java
try (IEWSClient client = EWSClient.getEWSClient(uri, credentials))
{
    ExchangeMessageInfoCollection messageInfoCollection = client.listMessagesFromPublicFolder(publicFolder);

    for (ExchangeMessageInfo messageInfo : messageInfoCollection)
    {
        System.out.println("Message Class: " + messageInfo.getMessageClass());
    }
}
```
## **Чтение писем из почтового ящика другого пользователя**
Некоторые учетные записи на серверах Exchange имеют право доступа к нескольким почтовым ящикам, а некоторые пользователи имеют несколько учетных записей электронной почты на одном сервере Exchange. В обоих случаях пользователи могут получить доступ к почтовым ящикам других пользователей с помощью Aspose.Email для Java. Этот API предоставляет механизм доступа к папкам и электронным письмам из других почтовых ящиков с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) класс. Эта функциональность может быть достигнута с помощью перегруженных [getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#getMailboxInfo\(\)) метод и указание адреса электронной почты пользователя в качестве параметра.

В следующем фрагменте кода показано, как читать электронные письма с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo("otherUser@domain.com");
~~~
## **Список сообщений**
Список сообщений электронной почты в почтовом ящике Exchange можно получить, позвонив в [IEWSClient.listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) метод. Получите базовую информацию о сообщениях, такую как тема, от кого и идентификатор сообщения, используя [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) method.
### **Простой список сообщений**
Чтобы вывести список сообщений в почтовом ящике Exchange, выполните следующие действия:

1. Создайте экземпляр [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class.
1. Вызовите метод listMessages и создайте коллекцию сообщений.
1. Просмотрите коллекцию и отобразите информацию о сообщениях.

В следующем фрагменте кода Java показано, как подключиться к серверу Exchange с помощью EWS, и перечислены сообщения из папки «Входящие».



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject: " + msgInfo.getSubject());
    System.out.println("From: " + msgInfo.getFrom().toString());
    System.out.println("To: " + msgInfo.getTo().toString());
    System.out.println("Message ID: " + msgInfo.getMessageId());
    System.out.println("Unique URI: " + msgInfo.getUniqueUri());
}
~~~
### **Список сообщений из разных папок**
[Вышеуказанные фрагменты кода](#simple-messages-listing), перечислите все сообщения в папке «Входящие». Также можно получить список сообщений из других папок. [IEWSClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) метод принимает URI папки в качестве параметра. Если URI папки действителен, вы можете получить список сообщений из этой папки. Используйте свойство iewSclient.getMailboxInfo () .getXXXFolderUri, чтобы получить URI различных папок. В остальном код аналогичен получению списка сообщений. В следующем фрагменте кода показано, как размещать сообщения из разных папок с помощью EWS.


~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get folder URI
String strFolderURI = "";
strFolderURI = client.getMailboxInfo().getInboxUri();
strFolderURI = client.getMailboxInfo().getDeletedItemsUri();
strFolderURI = client.getMailboxInfo().getDraftsUri();
strFolderURI = client.getMailboxInfo().getSentItemsUri();

// Get list of messages from the specified folder
ExchangeMessageInfoCollection msgCollection = client.listMessages(strFolderURI);
~~~
### **Список сообщений с поддержкой пейджинга**
В следующем фрагменте кода Java показано, как получить список сообщений с поддержкой разбиения на страницы.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
try {
    try {
        // Create some test messages to be added to server for retrieval later
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157_1 - " + UUID.randomUUID().toString(),
                    "EMAILNET-35157 Move paging parameters to separate class");
            client.appendMessage(client.getMailboxInfo().getInboxUri(), message);
        }
        // Verfiy that the messages have been added to the server
        ExchangeMessageInfoCollection totalMessageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RETREIVING THE MESSAGES USING PAGING SUPPORT ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
        // Total Pages Count
        System.out.println(pageInfo.getTotalCount());

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage, pageInfo.getPageOffset() + 1);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // foreach to while statements conversion
        for (ExchangeMessagePageInfo pageCol : pages) {
            retrievedItems += pageCol.getItems().size();
        }
        // Verify total message count using paging
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
В этой статье показано, как получать сообщения из почтового ящика Exchange Server и сохранять их на диск в форматах EML и MSG:

- Сохранить как EML на диске.
- Сохранить в потоке памяти.
- Сохранить как MSG.
### **Сохранение сообщений в EML**
Чтобы получать сообщения и сохранять их в формате EML, выполните следующие действия:

1. Создайте экземпляр класса IewsClient.
1. Укажите URI почтового ящика, имя пользователя, пароль и домен.
1. Вызовите метод IEWSClient.listMessages (), чтобы получить экземпляр коллекции ExchangeMessagesInfoCollection.
1. Просмотрите коллекцию ExchangeMessagesInfoCollection, чтобы получить уникальный URI для каждого сообщения.
1. Вызовите метод IEWSClient.saveMessage () и передайте уникальный URI в качестве параметра.
1. Укажите в методе saveMessage () путь к тому месту, куда вы хотите сохранить файл.

В следующем фрагменте кода показано, как использовать EWS для подключения к серверу Exchange и сохранения сообщений в виде файлов EML.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now save the message in disk
    client.saveMessage(strMessageURI, dataDir + msgInfo.getMessageId() + "out.eml");
}
~~~
### **Сохранение сообщений в потоке памяти**
Вместо сохранения файлов EML на диск можно сохранить их в потоке памяти. Это удобно, если вы хотите сохранить поток в каком-либо месте хранения, например в базе данных. Как только поток будет сохранен в базе данных, вы можете перезагрузить файл EML в [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) класс. В следующем фрагменте кода показано, как сохранять сообщения из почтового ящика Exchange Server в поток памяти с помощью EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now save the message in memory stream
    ByteArrayOutputStream stream = new ByteArrayOutputStream();
    client.saveMessage(strMessageURI, stream);
}
~~~
### **Сохранение сообщений в формате MSG**
The [IEWSClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#saveMessage\(java.lang.String,%20java.lang.String\)) метод может напрямую сохранить сообщение в формате EML. Чтобы сохранить сообщения в формате MSG, сначала вызовите [IEWSClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchMessage\(java.lang.String\)) метод, который возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) класс. Затем позвоните [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.lang.String\)) метод сохранения сообщения в MSG. В следующем фрагменте кода показано, как получать сообщения из почтового ящика Exchange Server и сохранять их в формате MSG с помощью EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

int count = 0;
// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now get the message details using FetchMessage() and Save message as Msg
    MailMessage message = client.fetchMessage(strMessageURI);
    message.save(dataDir + (count++) + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~
## **Получение сведений о сообщениях Exchange из URI сообщения**
Сообщение электронной почты представлено уникальным идентификатором, URI, и является неотъемлемой частью [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) объект. В случае, если доступен только URI сообщения, тогда [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) объект также можно получить, используя эту доступную информацию. Версия, предназначенная для перегрузки [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.Iterable\)) принимает список идентификаторов для использования [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection). В следующем фрагменте кода показано, как получить [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) из URI сообщения.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<String> ids = new ArrayList<String>();
List<MailMessage> messages = new ArrayList<MailMessage>();

for (int i = 0; i < 5; i++) {
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + UUID.randomUUID().toString(),
            "EMAILNET-35033 Messages saved from Sent Items folder doesn't contain 'To' field");
    messages.add(message);
    String uri = client.appendMessage(message);
    ids.add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(ids);

for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) messageInfoCol) {
    // Do something ...
    System.out.println(messageInfo.getUniqueUri());
}
~~~
## **Получение сообщений из почтового ящика сервера Exchange**
При перечислении сообщений на сервере Exchange использовалось [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) метод получения списка сообщений из почтового ящика Exchange Server. [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) метод получает основную информацию о сообщениях, например тему, идентификатор сообщения, от и до. Чтобы получить полную информацию о сообщении, Aspose.Email.Exchange предоставляет метод IEWSclient.fetchMessage (). Этот метод принимает URI сообщения в качестве параметра и возвращает экземпляр [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) класс. [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) Затем класс предоставляет сведения о сообщении, такие как текст, заголовки и вложения. Узнайте больше о [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) API или узнайте, как управлять электронной почтой с помощью [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) класс. Чтобы получить сообщения из почтового ящика сервера Exchange, выполните следующие действия:

1. Создайте экземпляр типа IEWSClient.
1. Укажите имя сервера, имя пользователя, пароль и домен.
1. Позвоните в ListMessages, чтобы получить коллекцию сведений о сообщениях Exchange.
1. Просмотрите коллекцию ExchangeMessageInfoCollection, чтобы получить значения ExchangeMessageInfo.uniqueURI.
1. Вызовите IEWSClient.fetchMessage () и передайте в качестве параметра URL-адрес ExchangeMessageInfo.uniqueURI.

В следующем фрагменте кода показано, как вы подключаетесь к почтовому ящику Exchange Server и получаете все сообщения с помощью EWS.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now get the message details using FetchMessage()
    MailMessage msg = client.fetchMessage(strMessageURI);

    for (Attachment att : (Iterable<Attachment>) msg.getAttachments()) {
        System.out.println("Attachment Name: " + att.getName());
    }
}
~~~

### **Использование метода fetchItem для получения сообщения**

{{% alert color="primary" %}}

Обратите внимание, [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) метод возвращает сообщение без вложений. Для получения сообщений с вложениями используйте [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)) метод, описанный в разделе ниже.

{{% /alert %}}

The [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\))  метод более предпочтителен, если вы хотите получить [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) и работайте со свойствами MAPI. Вы также можете использовать этот метод для загрузки любого элемента Outlook, например контакта, встречи, задачи и т. д.

```java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : msgCollection)
{
    // Now get the message using FetchItem()
    MapiMessage msg = client.fetchItem(msgInfo.getUniqueUri());

    // If necessary, you can cast the MapiMessage to the proper item type to simplify working with its properties.
    MapiContact contact = (MapiContact) msg.toMapiMessageItem();
}
```

## **Размер сообщения перед выборкой**
Microsoft Outlook InterOp предоставляет возможность получения размера сообщения до фактической загрузки всего сообщения с сервера. В случае Aspose.Email API сводная информация, полученная с сервера Exchange, представлена в виде [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) класс. Он предоставляет ту же функцию, что и получение размера сообщения с помощью свойства Size. Чтобы получить размер сообщения, используется стандартный вызов ListMessages IEWSClient, который извлекает коллекцию [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). В следующем фрагменте кода показано, как отображать размер сообщения с помощью [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) class.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject: " + msgInfo.getSubject());
    System.out.println("From: " + msgInfo.getFrom().toString());
    System.out.println("To: " + msgInfo.getTo().toString());
    System.out.println("Message Size: " + msgInfo.getSize());
    System.out.println("==================================");
}
~~~
## **Рекурсивная загрузка сообщений**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient)’s [listSubFolders()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listSubFolders\(com.aspose.email.ExchangeFolderInfo\)) метод можно использовать для рекурсивного получения сообщений из папок и подпапок из почтового ящика Exchange Server. Для этого требуется Exchange Server 2007 или более поздними версиями, поскольку в нем используется EWS. В следующем фрагменте кода показано, как загрузить весь почтовый ящик (папки и подпапки) сервера Exchange. Структура папок создается локально, и все сообщения загружаются.



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

        System.out.println("Downloading all messages from Inbox....");
        // Create instance of IEWSClient class by giving credentials
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Call the recursive method to read messages and get sub-folders
            listMessagesInFolder(client, folderInfo, rootFolder);
        }

        System.out.println("All messages downloaded.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

// Recursive method to get messages from folders and sub-folders
private static void listMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, String rootFolder) {
    // Create the folder in disk (same name as on IMAP server)
    String currentFolder = rootFolder + "\\" + folderInfo.getDisplayName();
    new File(currentFolder).mkdirs();

    // List messages
    ExchangeMessageInfoCollection msgInfoColl = client.listMessages(folderInfo.getUri());
    System.out.println("Listing messages....");
    int i = 0;
    for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
        // Get subject and other properties of the message
        System.out.println("Subject: " + msgInfo.getSubject());

        // Get rid of characters like ? and :, which should not be included in a file name
        String fileName = msgInfo.getSubject().replace("?", " ").replace(":", " ");

        MailMessage msg = client.fetchMessage(msgInfo.getUniqueUri());
        msg.save(dataDir + "\\" + fileName + "-" + i + ".msg");

        i++;
    }
    System.out.println("============================\n");
    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Загрузка сообщений из общедоступных папок**
Microsoft Exchange Server позволяет пользователям создавать общедоступные папки и публиковать в них сообщения. Чтобы сделать это через приложение, используйте Aspose.Email [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс для подключения к серверу Exchange и чтения и загрузки сообщений и сообщений из общедоступных папок. В следующем фрагменте кода показано, как читать все общедоступные папки и подпапки, а также перечислять и загружать все сообщения, обнаруженные в этих папках. Этот пример работает только с Microsoft Exchange Server 2007 или выше, поскольку только они поддерживают EWS.



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
        System.out.println("Name: " + publicFolder.getDisplayName());
        System.out.println("Subfolders count: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Folder Name: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Call this method recursively for any subfolders
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Перемещение сообщений**
Вы можете перемещать сообщения электронной почты из одной папки в другую с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class [move](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#moveItem\(java.lang.String,%20java.lang.String\)) метод. Он принимает следующие параметры:

- Уникальный URI сообщения, которое нужно переместить.
- Уникальный URI целевой папки.
### **Перемещение сообщений между папками**
В следующем фрагменте кода показано, как переместить сообщение в почтовом ящике из папки «Входящие» в папку «Обработано». В этом примере приложение:

1. Читает сообщения из папки «Входящие».
1. Обрабатывает некоторые сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Перемещает сообщения, удовлетворяющие заданному условию, в обработанную папку.

~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// List all messages from Inbox folder
System.out.println("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Move message to "Processed" folder, after processing certain messages based on some criteria
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("process this message")) {
        client.moveItem(mailboxInfo.getDeletedItemsUri(), msgInfo.getUniqueUri()); // EWS
        System.out.println("Message moved...." + msgInfo.getSubject());
    } else {
        // Do something else
    }
}
~~~
## **Удаление сообщений**
Вы можете удалить сообщения электронной почты из папки с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) метод. В качестве параметра он принимает уникальный URI сообщения.

В следующем фрагменте кода показано, как удалить сообщение из папки «Входящие». Для целей данного примера используется следующий код:

1. Читает сообщения из папки «Входящие».
1. Обрабатывайте сообщения на основе некоторых критериев (в этом примере мы находим ключевое слово в теме сообщения).
1. Удаляет сообщение.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// List all messages from Inbox folder
System.out.println("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Delete message based on some criteria
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("delete") == true) {
        client.deleteItem(msgInfo.getUniqueUri(), DeletionOptions.getDeletePermanently()); // EWS
        System.out.println("Message deleted...." + msgInfo.getSubject());
    } else {
        // Do something else
    }
}
~~~
## **Копирование сообщений**
Aspose.Email API позволяет копировать сообщение из одной папки в другую, используя [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)) метод. Перегруженная версия этого метода возвращает уникальный URI скопированного сообщения, как показано в этой статье.
### **Копирование сообщения в другую папку**
В следующем фрагменте кода показано, как скопировать сообщение в другую папку.



~~~Java
try {
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
