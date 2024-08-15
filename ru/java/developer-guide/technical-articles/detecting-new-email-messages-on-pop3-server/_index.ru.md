---
title: "Обнаружение новых сообщений электронной почты на сервере POP3"
url: /ru/java/detecting-new-email-messages-on-pop3-server/
weight: 100
type: docs
---


С помощью учетных записей POP3 вы можете оставлять сообщения на сервере при их загрузке и чтении. Оставление сообщений электронной почты на сервере означает, что они доступны другим приложениям и отдельным пользователям, например пользователям, которые получают доступ к электронной почте с нескольких устройств. Или вы можете захотеть загружать только те сообщения, которые соответствуют определенным критериям, например сообщения с определенной темой. Для управления электронной почтой вы можете:

- Прочитайте все сообщения с почтового сервера POP3 с помощью Aspose.Email.
- Загрузите сообщения в локальную базу данных.

Сообщения не удаляются, а остаются на сервере. При первом запуске этот процесс работает нормально. Все необходимые сообщения загружаются в базу данных. Но при втором запуске загружаются те же сообщения, потому что они все еще находятся на почтовом сервере. Это приводит к дублированию записей. Чтобы решить эту проблему, используйте [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/email/java/com.aspose.email/Pop3MessageInfo#getUniqueId\(\)) свойство для проверки того, было ли уже загружено сообщение. Уникальный идентификатор сообщения должен храниться в базе данных: это ключ поиска для обнаружения новых сообщений.
## **Обнаружение новых сообщений**
Чтобы идентифицировать новые электронные письма из списка писем на сервере POP3, выполните следующие действия:

1. Подключитесь к серверу.
1. Получите список электронных писем.
1. Подключитесь к базе данных.
1. Получите список электронных писем.
1. Сравните списки.
1. Сохраняйте новые письма в базе данных.

Процесс ускоряется, если вы:

1. Извлеките все уникальные идентификаторы сообщений в хеш-таблицу.
1. Ищите каждое сообщение электронной почты в хеш-таблице, а не в базе данных в цикле for (...).

Вместо запроса к базе данных каждого сообщения, требующего многократных вызовов базы данных, этот метод требует только одного вызова. В следующем фрагменте кода показано, как обнаруживать новые сообщения электронной почты на сервере POP3.



~~~Java
public static void run() {
    try {
        // Connect to the POP3 mail server and check messages.
        Pop3Client pop3Client = new Pop3Client("pop.domain.com", 993, "username", "password");

        // List all the messages
        Pop3MessageInfoCollection msgList = pop3Client.listMessages();
        for (Pop3MessageInfo msgInfo : msgList) {
            // Get the POP3 message's unique ID
            String strUniqueID = msgInfo.getUniqueId();

            // Search your local database or data store on the unique ID. If a match is found, that means it's already downloaded. Otherwise download and save it.
            if (searchPop3MsgInLocalDB(strUniqueID) == true) {
                // The message is already in the database. Nothing to do with this message. Go to next message.
            } else {
                // Save the message
                savePop3MsgInLocalDB(msgInfo);
            }
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }

}

private static void savePop3MsgInLocalDB(Pop3MessageInfo msgInfo) {
    // Open the database connection according to your database. Use public properties (for example msgInfo.Subject) and store in database,
    // for example, " INSERT INTO POP3Mails (UniqueID, Subject) VALUES ('" + msgInfo.UniqueID + "' , '" + msgInfo.Subject + "') and Run the query to store in database.
}

private static boolean searchPop3MsgInLocalDB(String strUniqueID) {
    // Open the database connection according to your database. Use strUniqueID in the search query to find existing records,
    // for example, " SELECT COUNT(*) FROM POP3Mails WHERE UniqueID = '" + strUniqueID + "' Run the query, return true if count == 1. Return false if count == 0.
    return false;
}
~~~