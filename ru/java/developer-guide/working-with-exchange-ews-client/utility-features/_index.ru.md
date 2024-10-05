---
title: "Утилитарные функции"
url: /ru/java/utility-features/
weight: 120
type: docs
---

## **Отправка сообщения с вариантами голосования**
Microsoft Outlook позволяет пользователям создавать опрос при составлении нового сообщения. Это делается путем включения вариантов голосования, таких как Да, Нет, Может быть и т.д. Класс FollowUpOptions, предлагаемый Aspose.Email, предоставляет свойство VotingButtons, которое можно использовать для установки или получения значений вариантов голосования. Эта статья предоставляет детальный пример создания MapiMessage с вариантами голосования для создания опроса, а затем отправки сообщения с помощью клиента Exchange Web Service (EWS).
### **Создание и отправка сообщения с вариантами голосования**
Следующий фрагмент кода показывает, как создать новое сообщение и затем отправить его с вариантами голосования.

~~~Java
String address = "firstname.lastname@aspose.com";

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Установите кнопки вариантов голосования
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Да;Нет;Может быть;Совершенно верно!");

client.send(message, options);
~~~
### **Образцы методов, использованных в примерах**
Следующий фрагмент кода показывает, как использовать методы, использованные в приведенном выше примере.

~~~Java
private static MailMessage createTestMessage(String address) {
    MailMessage eml = new MailMessage(address, address, "Помеченное сообщение",
            "Сделайте его приятным и коротким, но описательным. Описание может появиться на страницах результатов поиска...");

    return eml;
}
~~~
## **Создание RE и FW сообщений из MSG файлов**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) позволяет разработчикам создавать RE (Ответ/Ответить всем) и FW (Переслать) сообщения из исходного сообщения. Исходное сообщение определяется выбором конкретного [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) из [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection), полученной с помощью IEWSClient.listMessages(). Другим аргументом является фактическое [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage), которое должно быть отправлено как сообщение RE или FW. Следующий фрагмент кода показывает, как создать образец учетной записи, который используется для отправки сообщения, а затем демонстрируются функции Ответа и Пересылки по отношению к этому образцу сообщения. Для выполнения этой задачи:

1. Инициализируйте объект IEWSClient, предоставив действительные учетные данные.
1. Отправьте несколько образцовых сообщений.
1. Вызовите функции IEWSClient.reply(), IEWSClient.replyAll() и IEWSClient.forward(), чтобы отправить сообщения.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

try {
    MailMessage message = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Реализовать возможность создания RE и FW сообщений из исходного MSG файла");

    client.send(message);

    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
    if (messageInfoCol.size() == 1)
        System.out.println("1 сообщение в Входящих");
    else
        System.out.println("Ошибка! Нет сообщения в Входящих");

    MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Реализовать возможность создания RE и FW сообщений из исходного MSG файла");

    client.send(message1);
    messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());

    if (messageInfoCol.size() == 2)
        System.out.println("2 сообщения в Входящих");
    else
        System.out.println("Ошибка! Нет новых сообщений в Входящих");

    MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Реализовать возможность создания RE и FW сообщений из исходного MSG файла");
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Тестовое вложение 1", "Имя вложения 1"));
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Тестовое вложение 2", "Имя вложения 2"));

    // Ответ, Ответить всем и переслать сообщение
    client.reply(message2, messageInfoCol.get_Item(0));
    client.replyAll(message2, messageInfoCol.get_Item(0));
    client.forward(message2, messageInfoCol.get_Item(0));
} catch (java.lang.RuntimeException ex) {
    System.out.println("Ошибка в программе" + ex.getMessage());
}
~~~
## **Поддержка OAuth для EWS с Office 365**
Aspose.Email API предоставляет поддержку для Exchange Web Service (EWS) с Office 365. Интерфейс API [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) предоставляет перегруженный метод, который принимает [OAuthNetworkCredential](https://apireference.aspose.com/email/java/com.aspose.email/OAuthNetworkCredential) в качестве входных данных для доступа к учетной записи Exchange через OAuth. Пользователь должен предоставить параметры Authority, Client Id, Client App Uri и Resource, чтобы это работало. Следующий фрагмент кода показывает поддержку OAuth для EWS с Office 365.

~~~Java
// токен провайдер
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
## **Поддержка ведения журналов в клиентах Exchange**
Aspose.Email API предоставляет возможность вести журнал для клиента Exchange Web Service.
### **Ведение журнала для клиента EWS**

~~~Java
client.setLogFileName("logs/ews");
// ИЛИ
EWSClient.setCommonLogFileName("logs/ews");
~~~
## **Добавление заголовков в запросы EWS**
Aspose.Email API позволяет добавлять заголовки к запросам Exchange. Это можно использовать для добавления заголовков к запросам EWS для различных целей. Одним из таких примеров может быть добавление заголовка X-AnchorMailbox, который используется для управления проблемами ограничения на сервере Exchange. Метод addHeader интерфейса IEWSClient используется для добавления заголовков к запросам EWS, как показано в следующем фрагменте кода.

~~~Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com/ews/Exchange.asmx", "username", "password", "");
try {
    client.addHeader("X-AnchorMailbox", "username@domain.com");
    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
} finally {
    client.dispose();
}
~~~

## **Возврат ID запроса клиента в заголовке**

Заголовок ```return-client-request-id``` отправляется в запросе и используется сервером для определения, следует ли вернуть заголовок ```client-request-id```, указанный клиентом, в ответе сервера. В этой операции используются следующие методы:

- [getReturnClientRequestId()](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#getReturnClientRequestId--) 
- [setReturnClientRequestId(boolean value)](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#setReturnClientRequestId-boolean-) - Получить или установить флаг, указывающий, требуется ли клиенту, чтобы сервер вернул ID запроса.

```java
try (IEWSClient client = createEWSClient())
{
    // Клиент создаст случайный ID и передаст его на сервер.
    // Сервер должен включить этот ID в заголовок request-id всех ответов.
    client.setReturnClientRequestId(true);
    
    client.setLogFileName("ews.log");
    client.getMailboxInfo();
}
```

## **Работа с унифицированными сообщениями**
Aspose.Email может извлекать информацию о унифицированных сообщениях из Exchange Server 2010. В настоящее время поддерживается унифицированная связь, такая как получение конфигурационной информации, инициирование исходящего звонка, извлечение информации о звонках по ID и отключение телефонного звонка по ID. Следующий пример кода показывает, как извлечь информацию о конфигурации унифицированной связи с Microsoft Exchange Server 2010.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);
UnifiedMessagingConfiguration umConf = client.getUMConfiguration();
~~~
## **Получение почтовых подсказок**
Microsoft Exchange Server добавил несколько новых функций в Exchange Server 2010 и 2013. Одна из них позволяет пользователям получать почтовые подсказки при составлении электронного сообщения. Эти подсказки очень полезны, так как предоставляют информацию перед отправкой электронной почты. Например, если адрес электронной почты неверен в списке получателей, отображается подсказка, которая информирует вас о недопустимости адреса электронной почты. Почтовые подсказки также позволяют вам видеть ответы "вне офиса" до отправки электронной почты: сервер Exchange (2010 и 2013) отправляет почтовую подсказку, когда электронная почта составляется, если один или несколько получателей установили ответы "вне офиса". Для всех функций, показанных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1. Следующий фрагмент кода показывает, как использовать класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient), который использует Exchange Web Services, доступные в Microsoft Exchange Server 2007 и более поздних версиях.

~~~Java
// Создайте экземпляр класса EWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
System.out.println("Подключено к серверу Exchange...");
// Укажите параметры почтовых подсказок
MailAddressCollection addrColl = new MailAddressCollection();
addrColl.addMailAddress(new MailAddress("test.exchange@ex2010.local", true));
addrColl.addMailAddress(new MailAddress("invalid.recipient@ex2010.local", true));
GetMailTipsOptions options = new GetMailTipsOptions(MailAddress.to_MailAddress("administrator@ex2010.local"), addrColl, MailTipsType.All);

// Получить почтовые подсказки
MailTips[] tips = client.getMailTips(options);

// Отобразить информацию о каждой почтовой подсказке
for (MailTips tip : tips) {
    // Отобразить сообщение "вне офиса", если оно присутствует
    if (tip.getOutOfOffice() != null) {
        System.out.println("Вне офиса: " + tip.getOutOfOffice().getReplyBody().getMessage());
    }

    // Отобразить недопустимый адрес электронной почты среди получателей, если он присутствует
    if (tip.getInvalidRecipient() == true) {
        System.out.println("Адрес получателя недействителен: " + tip.getRecipientAddress());
    }
}
~~~
## **Имитация в Exchange**
Имитация в Exchange позволяет кому-то имитировать другую учетную запись и выполнять задачи и операции, используя разрешения имитируемой учетной записи вместо собственных. Тогда как делегирование позволяет пользователям действовать от имени других пользователей, Имитация позволяет им действовать как другие пользователи. Aspose.Email поддерживает имитацию Exchange. Класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) предоставляет методы ImpersonateUser и ResetImpersonation для упрощения этой функции.

Для выполнения этой задачи:

1. Инициализируйте ExchangeWebServiceClient для пользователя 1.
1. Инициализируйте ExchangeWebServiceClient для пользователя 2.
1. Добавьте тестовые сообщения в учетные записи.
1. Включите имитацию.
1. Сбросьте имитацию.

Следующий фрагмент кода показывает, как использовать класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) для реализации функции имитации.

~~~Java
// Создайте экземпляры класса EWSClient, указав учетные данные
IEWSClient client1 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser1", "pwd", "domain");
IEWSClient client2 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser2", "pwd", "domain");
{
    String folder = "Черновики";
    try {
        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
            client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj1 = "NETWORKNET_33354 Пользователь User1";
        client1.appendMessage(folder, new MailMessage("User1@exchange.conholdate.local", "To@aspsoe.com", subj1, ""));

        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
            client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj2 = "NETWORKNET_33354 Пользователь User2";
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
## **Функция автоматического обнаружения с использованием EWS**
Aspose.Email API позволяет обнаруживать настройки сервера Exchange с помощью клиента EWS. 

~~~Java
AutodiscoverService svc = new AutodiscoverService();
svc.setCredentials(new NetworkCredential(email, password));

IGenericDictionary</* UserSettingName */Integer, Object> userSettings = svc.getUserSettings(email, UserSettingName.ExternalEwsUrl).getSettings();
String ewsUrl = (String) userSettings.get_Item(UserSettingName.ExternalEwsUrl);
System.out.println("Автоматически обнаруженный EWS Url: " + ewsUrl);
~~~
## **Прерывание операции восстановления PST на сервер Exchange**
Aspose.Email API позволяет восстанавливать файл PST на сервер Exchange. Однако, если операция занимает много времени из-за большого размера файла PST, может потребоваться указать критерий для прерывания операции. Это можно сделать, используя API, как показано в следующем образце кода.

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
        // создайте тестовый pst и добавьте в него несколько тестовых сообщений
        PersonalStorage pst = PersonalStorage.create(new ByteArrayOutputStream(), FileFormatVersion.Unicode);
        FolderInfo folder = pst.getRootFolder().addSubFolder("Моя тестовая папка");
        for (int i = 0; i < 20; i++) {
            MapiMessage message = new MapiMessage("from@gmail.com", "to@gmail.com", "subj", "body");
            folder.addMessage(message);
        }
        RestoreSettings rs = new RestoreSettings();
        rs.setBeforeItemCallback(callback);

        // теперь восстановите PST с помощью обратного вызова
        client.restore(pst, rs);
        System.out.println("Успешно!");
    } catch (AbortRestoreException e) {
        System.out.println("Тайм-аут! " + processedItems.get());
    }
} finally {
    client.dispose();
}
~~~