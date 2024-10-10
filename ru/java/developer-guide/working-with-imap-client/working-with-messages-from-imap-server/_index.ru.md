---
title: "Работа с сообщениями с IMAP-сервера"
url: /ru/java/working-with-messages-from-imap-server/
weight: 20
type: docs
---

## **Получение идентификаторов MIME-сообщений с сервера**

[ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) предоставляет MIME [MessageId](https://reference.aspose.com/email/java/com.aspose.email/messageinfobase/#getMessageId--) для идентификации сообщения без извлечения полного сообщения. Следующий фрагмент кода показывает, как получить список MIME messageId.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");

try {
    ImapMessageInfoCollection messageInfoCol = client.listMessages("Inbox");
    for (ImapMessageInfo info : messageInfoCol) {
        // Отобразить MIME Message ID
        System.out.println("Message Id = " + info.getMessageId());
    }
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Получение сообщений с сервера**

Aspose.Email предоставляет перегруженный вариант [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) для извлечения указанного количества сообщений на основе запроса. Следующий фрагмент кода показывает, как получить список сообщений.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте imapclient с хостом, пользователем и паролем
ImapClient client = new ImapClient("localhost", "user", "password");

// Выберите папку "Входящие" и получите коллекцию информации о сообщениях
ImapQueryBuilder builder = new ImapQueryBuilder();
MailQuery query = builder
        .or(builder.or(builder.or(builder.or(builder.getSubject().contains(" (1) "), builder.getSubject().contains(" (2) ")), builder.getSubject().contains(" (3) ")),
                builder.getSubject().contains(" (4) ")), builder.getSubject().contains(" (5) "));
ImapMessageInfoCollection messageInfoCol4 = client.listMessages(query, 4);
System.out.println((messageInfoCol4.size() == 4) ? "Успех" : "Неудача");
~~~

## **Получение сообщений с сервера рекурсивно**

Протокол IMAP поддерживает рекурсивное получение сообщений из почтовой папки. Это помогает получить сообщения из подкаталогов папки. Следующий фрагмент кода показывает, как получить сообщения рекурсивно.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте imapclient с хостом, пользователем и паролем
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");
client.selectFolder("InBox");
ImapMessageInfoCollection msgsColl = client.listMessages(true);
System.out.println("Всего сообщений: " + msgsColl.size());
~~~

## **Получение сообщений с MultiConnection**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет свойство [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setUseMultiConnection-int-), которое может быть использовано для создания нескольких соединений для тяжелых операций. Вы также можете установить количество соединений, которые будут использоваться в режиме многосоединения, с помощью [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setConnectionsQuantity-int-). Следующий фрагмент кода демонстрирует использование режима многосоединения для получения сообщений и сравнивает его производительность с режимом одного соединения.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

imapClient.selectFolder("Inbox");
imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol1 = imapClient.listMessages(true);
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

imapClient.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol2 = imapClient.listMessages(true);
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Отношение производительности: " + performanceRelation);
~~~
{{% alert color="primary" %}} 

Пожалуйста, обратите внимание, что использование режима многосоединения не гарантирует увеличение производительности.

{{% /alert %}} 

## **Получение сообщений в порядке убывания**

Aspose.Email предоставляет метод [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-), который позволяет выводить сообщения с поддержкой постраничного отображения. Некоторые перегрузки метода [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) принимают [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) в качестве параметра. [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) предоставляет свойство [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) которое, когда установлено в **false**, возвращает электронные письма в порядке убывания.

Следующий пример кода демонстрирует использование свойства [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) класса [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) для изменения порядка электронных писем.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

PageSettings pageSettings = new PageSettings();
pageSettings.setAscendingSorting(false);
ImapPageInfo pageInfo = imapClient.listMessagesByPage(5, pageSettings);
ImapMessageInfoCollection messages = pageInfo.getItems();

for (ImapMessageInfo message : messages) {
    System.out.println(message.getSubject() + " -> " + message.getDate().toString());
}
~~~

## **Получение сообщений с сервера и сохранение на диск**

Класс [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) может извлекать сообщения с IMAP-сервера и сохранять сообщения в формате EML на локальном диске. Для сохранения сообщений на диск необходимы следующие шаги:

1. Создайте экземпляр класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
2. Укажите имя хоста, порт, имя пользователя и пароль в [конструкторе](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#ImapClient\(java.lang.String,%20int,%20java.lang.String,%20java.lang.String\)) класса ImapClient.
3. Выберите папку, используя метод [selectFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#selectFolder-com.aspose.email.IConnection-java.lang.String-).
4. Вызовите метод [listMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) для получения объекта [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/).
5. Переберите коллекцию [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/), вызовите метод [saveMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#saveMessage-com.aspose.email.IConnection-int-java.io.OutputStream-) и предоставьте путь и имя файла для вывода.

Следующий фрагмент кода показывает, как извлечь электронные письма с сервера и сохранить их.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Выберите папку "Входящие" и получите коллекцию информации о сообщениях
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Скачайте каждое сообщение
for (int i = 0; i < list.size(); i++) {
    // Сохраните файл EML локально
    client.saveMessage(list.get_Item(i).getUniqueId(), dataDir + list.get_Item(i).getUniqueId() + ".eml");
}
~~~

## **Сохранение сообщений в формате MSG**

[В приведенном выше примере](#fetch-messages-from-server-and-save-to-disc) сообщения сохраняются в формате EML. Чтобы сохранить электронные письма в формате MSG, необходимо вызвать метод [ImapClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessage-com.aspose.email.IConnection-int-). Он возвращает сообщение в экземпляре класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Затем можно вызвать метод [MailMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) для сохранения сообщения в формате MSG. Следующий фрагмент кода показывает, как сохранить сообщения в формате MSG.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "data/";

// Создайте imapclient с хостом, пользователем и паролем
ImapClient client = new ImapClient("localhost", "user", "password");

// Выберите папку "Входящие" и получите коллекцию информации о сообщениях
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Скачайте каждое сообщение
for (int i = 0; i < list.size(); i++) {
    // Сохраните сообщение в формате MSG
    MailMessage message = client.fetchMessage(list.get_Item(i).getUniqueId());
    message.save(dataDir + list.get_Item(i).getUniqueId() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~

## **Групповая загрузка сообщений**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет метод [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--), который принимает итератор последовательных номеров или уникальных идентификаторов и возвращает список [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Следующий фрагмент кода демонстрирует использование метода [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) для получения сообщений по последовательным номерам и уникальным идентификаторам.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
System.out.println("Количество ListMessages: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (ImapMessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : imapClient.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : imapClient.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~

## **Потоковая обработка электронной почты/Организация писем в беседы**

Aspose.Email позволяет группировать все пересылки, ответы и ответы всем, относящимся к одной беседе, вместе в иерархическом порядке. В основном, протокол IMAP может поддерживать возможность THREAD, определенную в RFC-5256. Кроме того, существует еще одно расширение IMAP, предоставляемое Gmail и описываемое как X-GM-EXT-1.

Следующие функции потоковой обработки электронной почты доступны для использования:

- Метод [getMessageThreads](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getMessageThreads-com.aspose.email.BaseSearchConditions-) - получает потоки сообщений по [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
- boolean [getGmExt1Supported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getGmExt1Supported--) - получает информацию о том, поддерживается ли расширение Gmail X-GM-EXT-1.
- boolean [getThreadSupported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadSupported--) - получает информацию о том, поддерживается ли расширение THREAD.
- String[] [getThreadAlgorithms](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadAlgorithms--) - получает поддерживаемые алгоритмы THREAD.

Следующие примеры кода показывают использование этих функций для получения потоков электронной почты из Gmail:

```java
  ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password", SecurityOptions.SSLImplicit);

try {

    client.selectFolder(ImapFolderInfo.IN_BOX);

   // получаем список сообщений, которые мы сгруппируем по беседе

   ImapMessageInfoCollection messages = client.listMessages();

   // убедитесь, что IMAP-сервер поддерживает расширение X-GM-EXT-1

   if (client.getGmExt1Supported()) {

       // получаем уникальный conversationId для нашего примера

       Set<String> conversationIds = new HashSet<String>();

       for (ImapMessageInfo messageInfo : messages) {

           if (messageInfo.getConversationId() != null)

                conversationIds.add(messageInfo.getConversationId());

       }

       for (String conversationId : conversationIds) {

           // создаем необходимые условия поиска для потока

           XGMThreadSearchConditions conditions = new XGMThreadSearchConditions();

            conditions.setConversationId(conversationId);

            conditions.setUseUId(true);

           // получаем результаты

           List<MessageThreadResult> conversation = client.getMessageThreads(conditions);

           // печатаем переписку по электронной почте в иерархическом порядке

           printConversaton("", conversation, messages);

            System.out.println("--------------------");

       }

   }

} finally {

    client.dispose();

}

/**

 * <p>

 * Печатает переписку по электронной почте в иерархическом порядке

 * </p>

 */

public static void printConversaton(String indent, Iterable<MessageThreadResult> conversation,

    Iterable<ImapMessageInfo> messages) {

   for (MessageThreadResult thread : conversation) {

       for (ImapMessageInfo messageInfo : messages) {

           if (thread.getUniqueId().equals(messageInfo.getUniqueId())) {

                System.out.println(indent + " (" + thread.getUniqueId() + ") " + messageInfo.getSubject());

               break;

           }

       }

       if (thread.getChildMessages().size() != 0) {

            printConversaton(indent += "-", thread.getChildMessages(), messages);

       }

   }

}
```
Код немного меняется, если IMAP-сервер поддерживает возможность THREAD:

Проверьте, поддерживает ли IMAP-сервер расширение THREAD:

```java
 if (client.getThreadSupported())
```
Создайте подходящие условия поиска для потока:
```java
 ThreadSearchConditions conditions = new ThreadSearchConditions();

conditions.setAlgorithm(client.getThreadAlgorithms()[0]);

conditions.setUseUId(true);
```

## **Получение списков сообщений с поддержкой постраничного отображения**

В ситуациях, когда почтовый сервер содержит большое количество сообщений в почтовом ящике, часто требуется перечислить или извлечь сообщения с поддержкой постраничного отображения. API Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) позволяет извлекать сообщения с сервера с поддержкой постраничного отображения.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Этот пример показывает поддержку постраничного отображения ImapClient для получения сообщений с сервера
// Доступно в Aspose.Email для Java и более поздних версий
final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    try {
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        // Создайте несколько тестовых сообщений и добавьте их в папку "Входящие" сервера
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157 - " + UUID.randomUUID(),
                    "EMAILNET-35157 Переместить параметры постраничной навигации в отдельный класс");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        // Перечислить сообщения из папки "Входящие"
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages();
        // Проверьте количество добавленных сообщений
        System.out.println(totalMessageInfoCol.size());

        ////////////////// ПОЛУЧИТЕ СООБЩЕНИЯ С ИСПОЛЬЗОВАНИЕМ ПОДДЕРЖКИ ПОСТРАНИЧНОГО ОТОБРАЖЕНИЯ////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();
        PageSettings pageSettings = new PageSettings();
        ImapPageInfo pageInfo = client.listMessagesByPage(itemsPerPage, 0, pageSettings);
        System.out.println(pageInfo.getTotalCount());
        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(itemsPerPage, pageInfo.getNextPage().getPageOffset(), pageSettings);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;

        // преобразование foreach в циклы while
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Получение папок и чтение сообщений рекурсивно**

В этой статье используются многие функции [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) для создания приложения, которое рекурсивно перечисляет все папки и подкаталоги с IMAP-сервера. Оно также сохраняет сообщения в каждой папке и подкаталоге в формате MSG на локальном диске. На диске папки и сообщения создаются и сохраняются в той же иерархической структуре, что и на IMAP-сервере. Следующий фрагмент кода показывает, как рекурсивно получать информацию о сообщениях и подкаталогах.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() throws Exception {
    // Создайте экземпляр класса ImapClient
    ImapClient client = new ImapClient();

    // Укажите хост, имя пользователя, пароль, порт и параметры безопасности для вашего клиента
    client.setHost("imap.gmail.com");
    client.setUsername("your.username@gmail.com");
    client.setPassword("your.password");
    client.setPort(993);
    client.setSecurityOptions(SecurityOptions.Auto);
    try {
        // Корневая папка (которая будет создана на диске) состоит из хоста и имени пользователя
        String rootFolder = client.getHost() + "-" + client.getUsername();

        // Создайте корневую папку и перечислите все папки с IMAP-сервера
        new File(rootFolder).mkdirs();
        ImapFolderInfoCollection folderInfoCollection = client.listFolders();
        for (ImapFolderInfo folderInfo : folderInfoCollection) {
            // Вызовите рекурсивный метод для чтения сообщений и получения подкаталогов
            listMessagesInFolder(folderInfo, rootFolder, client);
        }
        // Отключитесь от удаленного IMAP-сервера
        client.dispose();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex);
    }

    System.out.println("Загруженные сообщения рекурсивно с IMAP-сервера.");
}

/// Рекурсивный метод получения сообщений из папок и подкаталогов
private static void listMessagesInFolder(ImapFolderInfo folderInfo, String rootFolder, ImapClient client) {
    // Создайте папку на диске (с тем же именем, что и на IMAP-сервере)
    String currentFolder = "data/";
    new File(currentFolder).mkdirs();

    // Прочитайте сообщения из текущей папки, если она выбираемая
    if (folderInfo.getSelectable()) {
        // Отправьте команду состояния для получения информации о папке
        ImapFolderInfo folderInfoStatus = client.getFolderInfo(folderInfo.getName());
        System.out.println(folderInfoStatus.getName() + " папка выбрана. Новые сообщения: " + folderInfoStatus.getNewMessageCount() + ", Всего сообщений: "
                + folderInfoStatus.getTotalMessageCount());

        // Выберите текущую папку и перечислите сообщения
        client.selectFolder(folderInfo.getName());
        ImapMessageInfoCollection msgInfoColl = client.listMessages();
        System.out.println("Перечисление сообщений....");
        for (ImapMessageInfo msgInfo : msgInfoColl) {
            // Получите тему и другие свойства сообщения
            System.out.println("Тема: " + msgInfo.getSubject());
            System.out.println("Прочитано: " + msgInfo.isRead() + ", Недавнее: " + msgInfo.getRecent() + ", Ответ: " + msgInfo.getAnswered());

            // Удалите символы, такие как ? и :, которые не должны включаться в имя файла, и сохраните сообщение в формате MSG
            String fileName = msgInfo.getSubject().replace(":", " ").replace("?", " ");
            MailMessage msg = client.fetchMessage(msgInfo.getSequenceNumber());
            msg.save(currentFolder + "\\" + fileName + "-" + msgInfo.getSequenceNumber() + ".msg", SaveOptions.getDefaultMsgUnicode());
        }
        System.out.println("============================\n");
    } else {
        System.out.println(folderInfo.getName() + " не выбираемая.");
    }

    try {
        // Если у этой папки есть подкаталоги, вызовите этот метод рекурсивно для получения сообщений
        ImapFolderInfoCollection folderInfoCollection = client.listFolders(folderInfo.getName());
        for (ImapFolderInfo subfolderInfo : folderInfoCollection) {
            listMessagesInFolder(subfolderInfo, rootFolder, client);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~

## **Получение UID или номера последовательности сообщения**

Общий API Aspose.Email предоставляет следующие функции для получения идентификационной информации о сообщении, такой как UID или номер последовательности, которые могут потребоваться при обработке сообщений, полученных с сервера:

[MailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/) - представляет собой идентификационную информацию о сообщении в почтовом ящике.
- [getSequenceNumber()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getSequenceNumber--) - получает номер последовательности сообщения.
- [getUniqueId()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getUniqueId--) - получает уникальный идентификатор сообщения.

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) - представляет собой электронное сообщение и позволяет получить доступ к свойствам сообщения, например, теме, содержимому, отправителю и адресам получателей и т.д.
- [getItemId](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getItemId--) - представляет собой идентификационную информацию о сообщении в почтовом ящике.

Ниже приведен пример кода, который демонстрирует, как извлечь и отобразить детали сообщений из папки "Входящие" на IMAP-сервере с использованием класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
try (ImapClient client = new ImapClient(imapHost, port, emailAddress, password, securityOption)) {
    ImapMessageInfoCollection msgs = client.listMessages("INBOX");
    List<Integer> seqIds = new ArrayList<>();
    for (ImapMessageInfo msg : msgs) {
        seqIds.add(msg.getSequenceNumber());
    }
    Iterable<MailMessage> msgsViaFetch = client.fetchMessagesBySequences(seqIds);
    for (MailMessage thisMsg : msgsViaFetch) {
        System.out.println("Message ID: " + thisMsg.getItemId().getUniqueId()
                + " SequenceNumber: " + thisMsg.getItemId().getSequenceNumber()
                + " Subject: " + thisMsg.getSubject());
    }
}
```
## **Получение дополнительных параметров в качестве сводной информации**

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("host.domain.com", "username", "password");
try {
    MailMessage message = new MailMessage("from@domain.com", "to@doman.com", "EMAILNET-38466 - " + UUID.randomUUID().toString(),
            "EMAILNET-38466 Добавить дополнительные параметры для команды UID FETCH");

    // добавьте сообщение на сервер
    String uid = client.appendMessage(message);

    // подождите, пока сообщение будет добавлено
    Thread.sleep(5000);

    // Определите свойства, которые должны быть извлечены с сервера вместе с сообщением
    List<String> messageExtraFields = Arrays.asList("X-GM-MSGID", "X-GM-THRID");

    // получите сводную информацию о сообщении, используя его UID
    ImapMessageInfo messageInfoUID = client.listMessage(uid, messageExtraFields);

    // получите сводную информацию о сообщении, используя его номер последовательности
    ImapMessageInfo messageInfoSeqNum = client.listMessage(1, messageExtraFields);

    // Перечислите сообщения с сервера в общем порядке на основе определенных свойств
    ImapMessageInfoCollection messageInfoCol = client.listMessages(messageExtraFields);

    ImapMessageInfo messageInfoFromList = messageInfoCol.get_Item(0);

    // проверьте, что параметры извлекаются в сводной информации
    for (String paramName : messageExtraFields) {
        System.out.println(messageInfoFromList.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoUID.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoSeqNum.getExtraParameters().containsKey(paramName));
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Получение информации заголовка List-Unsubscribe**

Заголовок List-Unsubscribe содержит URL для отказа от подписки на списки электронной почты, например, рекламные письма, информационные бюллетени и т.д. Чтобы получить заголовок List-Unsubscribe, используйте свойство [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) класса [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/). Следующий пример показывает использование свойства [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) для получения заголовка List-Unsubscribe.

~~~Java
// Для полных примеров и файлов данных перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient имапКлиент = новый ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
for (ImapMessageInfo imapMessageInfo : messageInfoCol) {
    System.out.println("Заголовок ListUnsubscribe: " + imapMessageInfo.getListUnsubscribe());
}
~~~