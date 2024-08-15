---
title: "Функции утилиты"
url: /ru/java/utility-features/
weight: 120
type: docs
---


## **Отправка сообщения с опцией голосования**
Microsoft Outlook позволяет пользователям создавать опрос при создании нового сообщения. Для этого можно включить такие варианты голосования, как «Да», «Нет», «Возможно» и т. д. Класс FollowupOptions, предлагаемый Aspose.Email, предоставляет свойство VotingButtons, которое можно использовать для установки или получения значений параметров голосования. В этой статье приведен подробный пример создания MapiMessage с опциями голосования для создания опроса и последующей отправки сообщения с помощью клиента Exchange Web Service (EWS).
### **Создание и отправка сообщения с опциями голосования**
В следующем фрагменте кода показано, как создать новое сообщение, а затем отправить его с опциями голосования.



~~~Java
String address = "firstname.lastname@aspose.com";

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Set FollowUpOptions Buttons
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Yes;No;Maybe;Exactly!");

client.send(message, options);
~~~
### **Примерные методы, используемые в примерах**
В следующем фрагменте кода показано, как использовать методы, использованные в приведенном выше примере.



~~~Java
private static MailMessage createTestMessage(String address) {
    MailMessage eml = new MailMessage(address, address, "Flagged message",
            "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...");

    return eml;
}
~~~
## **Создание сообщений RE и FW из файлов MSG**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) позволяет разработчикам создавать сообщения RE (ответить/ответить всем) и FW (переслать) из исходного сообщения. Исходное сообщение идентифицируется путем выбора определенного [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) from [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) получено с помощью IEWSclient.listMessages (). Другой аргумент является фактическим [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) для отправки в виде сообщения RE или FW. В следующем фрагменте кода показано, как создать образец учетной записи, который используется для отправки сообщения, а затем на примере этого примера сообщения демонстрируются функции «Ответить» и «Переслать». Для выполнения этой задачи выполните следующие действия:

1. Инициализируйте объект IEWSClient, указав действительные учетные данные.
1. Отправьте несколько образцов сообщений.
1. Вызовите функции IEWSclient.reply (), IEWSclient.replyAll () и IEWSclient.forward () для отправки сообщений.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

try {
    MailMessage message = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");

    client.send(message);

    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
    if (messageInfoCol.size() == 1)
        System.out.println("1 message in Inbox");
    else
        System.out.println("Error! No message in Inbox");

    MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");

    client.send(message1);
    messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());

    if (messageInfoCol.size() == 2)
        System.out.println("2 messages in Inbox");
    else
        System.out.println("Error! No new message in Inbox");

    MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Test attachment 1", "Attachment Name 1"));
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Test attachment 2", "Attachment Name 2"));

    // Reply, Replay All and forward Message
    client.reply(message2, messageInfoCol.get_Item(0));
    client.replyAll(message2, messageInfoCol.get_Item(0));
    client.forward(message2, messageInfoCol.get_Item(0));
} catch (java.lang.RuntimeException ex) {
    System.out.println("Error in program" + ex.getMessage());
}
~~~
## **Поддержка OAuth для EWS в Office 365**
API Aspose.Email обеспечивает поддержку веб-службы Exchange (EWS) в Office 365. Эти API [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) интерфейс предоставляет метод перегрузки, обеспечивающий [OAuthNetworkCredential](https://apireference.aspose.com/email/java/com.aspose.email/OAuthNetworkCredential) в качестве входных данных для доступа к учетной записи Exchange через OAuth. Чтобы это работало, пользователю необходимо указать авторитет, идентификатор клиента, идентификатор клиентского приложения и параметры ресурса. В следующем фрагменте кода показана поддержка OAuth для EWS в Office 365.


~~~Java
// token provider
/*ITokenProvider provider = new ITokenProvider() {

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        return null;
    }
};

NetworkCredential credentials = new OAuthNetworkCredential(provider);*/

// accessToken
NetworkCredential credentials = new OAuthNetworkCredential("accessToken");

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", credentials);
client.listMessages();
~~~
## **Поддержка входа в систему клиентов Exchange**
API Aspose.Email предоставляет возможность предоставлять возможность ведения журнала клиента веб-службы Exchange.
### **Ведение журнала для клиента EWS**


~~~Java
client.setLogFileName("logs/ews");
// OR
EWSClient.setCommonLogFileName("logs/ews");
~~~
## **Добавление заголовков в запросы EWS**
API Aspose.Email позволяет добавлять заголовки в запросы Exchange. Это можно использовать для добавления заголовков в запросы EWS для разных заголовков, которые можно использовать для разных целей. Одним из таких примеров может служить добавление заголовка X-AnchorMailbox, который используется для решения проблем регулирования на сервере Exchange. Метод addHeader в IEWSClient используется для добавления заголовков к запросам EWS, как показано в следующем фрагменте кода.



~~~Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com/ews/Exchange.asmx", "username", "password", "");
try {
    client.addHeader("X-AnchorMailbox", "username@domain.com");
    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
} finally {
    client.dispose();
}
~~~

## **Верните идентификатор запроса клиента в заголовке**

The ```return-client-request-id``` заголовок отправляется в запросе и используется сервером для определения того, ```client-request-id``` заголовок, указанный клиентом, должен быть возвращен в ответе сервера. В этой операции используются следующие методы:

- [getReturnClientRequestId()](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#getReturnClientRequestId--)
- [Задать идентификатор запроса клиента (логическое значение)](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#setReturnClientRequestId-boolean-) - Получите или установите флаг, указывающий, требует ли клиент от сервера возврата идентификатора запроса.

```java
try (IEWSClient client = createEWSClient())
{
    // Client will create random id and pass it to the server.
    // The server should include this id in request-id header of all responses.
    client.setReturnClientRequestId(true);
   
    client.setLogFileName("ews.log");
    client.getMailboxInfo();
}
```

## **Работа с единой системой обмена сообщениями**
Aspose.Email может получать информацию единой системы обмена сообщениями из Exchange Server 2010. В настоящее время поддерживается единая система обмена сообщениями, такая как получение сведений о конфигурации, инициирование исходящего вызова, получение информации о телефонном звонке по идентификатору вызова и отключение телефонного звонка по идентификатору. В следующем примере кода показано, как получить сведения о конфигурации единой системы обмена сообщениями из Microsoft Exchange Server 2010.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);
UnifiedMessagingConfiguration umConf = client.getUMConfiguration();
~~~
## **Советы по получению почты**
Сервер Microsoft Exchange добавил несколько новых функций в Exchange Server 2010 и 2013. Одна из них позволяет пользователям получать советы по электронной почте при составлении сообщения электронной почты. Эти советы очень полезны, поскольку они предоставляют информацию до отправки электронного письма. Например, если адрес электронной почты указан неправильно в списке получателей, отображается подсказка, сообщающая вам, что адрес электронной почты недействителен. С помощью подсказок по почте вы также можете просмотреть ответы, которые вы не получили от офиса, перед отправкой электронного письма: Exchange Server (2010 и 2013) отправляет подсказку по почте при составлении письма, если один или несколько получателей ответили, отсутствующие на рабочем месте. Для всех функций, описанных в этой статье, требуется пакет обновления 1 (SP1) для Microsoft Exchange Server 2010. В следующем фрагменте кода показано, как использовать [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс, использующий веб-службы Exchange, доступные в Microsoft Exchange Server 2007 и более поздних версиях.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
System.out.println("Connected to Exchange server...");
// Provide mail tips options
MailAddressCollection addrColl = new MailAddressCollection();
addrColl.addMailAddress(new MailAddress("test.exchange@ex2010.local", true));
addrColl.addMailAddress(new MailAddress("invalid.recipient@ex2010.local", true));
GetMailTipsOptions options = new GetMailTipsOptions(MailAddress.to_MailAddress("administrator@ex2010.local"), addrColl, MailTipsType.All);

// Get Mail Tips
MailTips[] tips = client.getMailTips(options);

// Display information about each Mail Tip
for (MailTips tip : tips) {
    // Display Out of office message, if present
    if (tip.getOutOfOffice() != null) {
        System.out.println("Out of office: " + tip.getOutOfOffice().getReplyBody().getMessage());
    }

    // Display the invalid email address in recipient, if present
    if (tip.getInvalidRecipient() == true) {
        System.out.println("The recipient address is invalid: " + tip.getRecipientAddress());
    }
}
~~~
## **Выдача себя за биржу**
Выдача себя за другое лицо Exchange позволяет пользователю выдавать себя за другую учетную запись и выполнять задачи и операции, используя разрешения этой учетной записи вместо своих собственных. Если делегирование позволяет пользователям действовать от имени других пользователей, то выдача себя за другое лицо позволяет им действовать как другие пользователи. Aspose.Email поддерживает выдачу себя за другое лицо в Exchange. [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс предоставляет методы ImpersonateUser и resetImpersonation для облегчения этой функции.

Для выполнения этой задачи выполните следующие действия:

1. Инициализируйте клиент ExchangeWebServiceClient для пользователя 1.
1. Инициализируйте клиент ExchangeWebServiceClient для пользователя 2.
1. Добавляйте тестовые сообщения к учетным записям.
1. Включите выдачу себя за другое лицо.
1. Сбросить олицетворение.

В следующем фрагменте кода показано, как использовать [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс для реализации функции Impersonation.



~~~Java
// Create instance's of EWSClient class by giving credentials
IEWSClient client1 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser1", "pwd", "domain");
IEWSClient client2 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser2", "pwd", "domain");
{
    String folder = "Drafts";
    try {
        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
            client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj1 = "NETWORKNET_33354 User User1";
        client1.appendMessage(folder, new MailMessage("User1@exchange.conholdate.local", "To@aspsoe.com", subj1, ""));

        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
            client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj2 = "NETWORKNET_33354 User User2";
        client2.appendMessage(folder, new MailMessage("User2@exchange.conholdate.local", "To@aspose.com", subj2, ""));

        ExchangeMessageInfoCollection messInfoColl = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl.Count);
        // Assert.AreEqual(subj1, messInfoColl[0].Subject);

        client1.impersonateUser(ItemChoice.PrimarySmtpAddress, "User2@exchange.conholdate.local");
        ExchangeMessageInfoCollection messInfoColl1 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl1.Count);
        // Assert.AreEqual(subj2, messInfoColl1[0].Subject);

        client1.resetImpersonation();
        ExchangeMessageInfoCollection messInfoColl2 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl2.Count);
        // Assert.AreEqual(subj1, messInfoColl2[0].Subject);
    } finally {
        try {
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
                client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
                client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        } catch (java.lang.RuntimeException e) {
        }
    }
}
~~~
## **Функция автоматического обнаружения с помощью EWS**
API Aspose.Email позволяет узнать о настройках сервера Exchange с помощью клиента EWS. 


~~~Java
AutodiscoverService svc = new AutodiscoverService();
svc.setCredentials(new NetworkCredential(email, password));

IGenericDictionary</* UserSettingName */Integer, Object> userSettings = svc.getUserSettings(email, UserSettingName.ExternalEwsUrl).getSettings();
String ewsUrl = (String) userSettings.get_Item(UserSettingName.ExternalEwsUrl);
System.out.println("Auto discovered EWS Url: " + ewsUrl);
~~~
## **Прервать операцию восстановления PST на сервере Exchange**
API Aspose.Email позволяет восстановить файл PST на сервере Exchange. Однако если операция занимает много времени из-за большого размера файла PST, возможно, потребуется указать критерий для прерывания операции. Это можно сделать с помощью API, как показано в следующем примере кода.


~~~Java
final IEWSClient client = EWSClient.getEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password");
try {
    final long startTime = System.currentTimeMillis();
    final AtomicInteger processedItems = new AtomicInteger(0);
    final long S15 = 15 * 1000;

    BeforeItemCallback callback = new BeforeItemCallback() {
        public void invoke(ItemCallbackArgs item) {
            if (System.currentTimeMillis() - startTime > S15) {
                throw new AbortRestoreException();
            }

            processedItems.incrementAndGet();
        }
    };

    try {
        // create a test pst and add some test messages to it
        PersonalStorage pst = PersonalStorage.create(new ByteArrayOutputStream(), FileFormatVersion.Unicode);
        FolderInfo folder = pst.getRootFolder().addSubFolder("My test folder");
        for (int i = 0; i < 20; i++) {
            MapiMessage message = new MapiMessage("from@gmail.com", "to@gmail.com", "subj", "body");
            folder.addMessage(message);
        }
        RestoreSettings rs = new RestoreSettings();
        rs.setBeforeItemCallback(callback);

        // now restore the PST with callback
        client.restore(pst, rs);
        System.out.println("Success!");
    } catch (AbortRestoreException e) {
        System.out.println("Timeout! " + processedItems.get());
    }
} finally {
    client.dispose();
}
~~~