---
title: "Подключение к Exchange Server"
url: /ru/java/connecting-to-exchange-server/
weight: 10
type: docs
---


Для подключения к Exchange Server 2007, 2010 и 2013 с использованием Exchange Web Service, Aspose.Email предоставляет интерфейс [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient), который реализует класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Метод [EWSClient.getEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#getEWSClient\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\)) создает и возвращает объект [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient), который далее используется для выполнения операций, связанных с почтовым ящиком Exchange и другими папками. Эта статья показывает, как создавать объекты [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
## **Подключение к Exchange Server через EWS**
Следующий фрагмент кода демонстрирует, как подключиться, используя Exchange Web Service (EWS).



~~~Java
private static IEWSClient getExchangeEWSClient() {
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String domain = "";
    final String username = "username@onmicrosoft.com";
    final String password = "password";
    NetworkCredential credentials = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
    return client;
}
~~~
## **Подключение к Exchange Server через IMAP**
Microsoft Exchange Server поддерживает протокол IMAP для доступа к элементам в почтовом ящике. Используйте класс Aspose.Email [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) для подключения к Exchange Server с использованием протокола IMAP. Для получения дополнительной информации о классе [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) сначала убедитесь, что службы IMAP включены на вашем Exchange Server:

1. Откройте Панель управления.
1. Перейдите в Администраторские инструменты, затем в Службы.
1. Проверьте статус службы Microsoft Exchange IMAP4.
1. Если она еще не работает, включите/запустите ее.

Следующий фрагмент кода демонстрирует, как подключиться и перечислить сообщения из папки «Входящие» на сервере Microsoft Exchange с использованием протокола IMAP.



~~~Java
// Подключение к Exchange Server с использованием класса ImapClient
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.setSecurityOptions(SecurityOptions.Auto);

// Выбор папки "Входящие"
imapClient.selectFolder(ImapFolderInfo.IN_BOX);

// Получение списка сообщений
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    System.out.println(msgInfo.getSubject());
}
// Отключение от сервера
imapClient.dispose();
~~~



Следующий фрагмент кода демонстрирует, как использовать SSL.



~~~Java
public static void run() {
    // Подключение к Exchange Server с использованием класса ImapClient
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1");
    imapClient.setSecurityOptions(SecurityOptions.SSLExplicit);

    // Выбор папки "Входящие"
    imapClient.selectFolder(ImapFolderInfo.IN_BOX);

    // Получение списка сообщений
    ImapMessageInfoCollection msgCollection = imapClient.listMessages();
    for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
        System.out.println(msgInfo.getSubject());
    }
    // Отключение от сервера
    imapClient.dispose();
}
~~~



После подключения к Exchange Server с использованием IMAP и получения [IMapMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfoCollection), следующий фрагмент кода демонстрирует, как использовать номер последовательности объекта [MessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/MessageInfo) для сохранения конкретного сообщения.



~~~Java
// Выбор папки "Входящие"
imapClient.selectFolder(ImapFolderInfo.IN_BOX);
// Получение списка сообщений
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    // Получение сообщения из папки "Входящие" по номеру последовательности из msgInfo
    MailMessage message = imapClient.fetchMessage(msgInfo.getSequenceNumber());

    // Сохранение сообщения на диск сейчас
    message.save(dataDir + msgInfo.getSequenceNumber() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~