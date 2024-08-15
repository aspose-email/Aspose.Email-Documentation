---
title: "Подключение к серверу Exchange"
url: /ru/java/connecting-to-exchange-server/
weight: 10
type: docs
---


Чтобы подключиться к серверам Exchange 2007, 2010 и 2013 с помощью веб-службы Exchange, Aspose.Email предоставляет [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) интерфейс, реализующий [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс. [EWSClient.getEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#getEWSClient\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\)) метод создает экземпляр и возвращает [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) объект, который в дальнейшем используется для выполнения операций, связанных с почтовым ящиком Exchange и другими папками. В этой статье показано, как создавать экземпляры объектов [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
## **Подключение к серверу Exchange с помощью EWS**
В следующем фрагменте кода показано, как подключиться с помощью веб-службы Exchange (EWS).



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
## **Подключение к серверу Exchange с помощью протокола IMAP**
Microsoft Exchange Server поддерживает протокол IMAP для доступа к элементам в почтовом ящике. Используйте электронную почту Aspose.Email [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) класс для подключения к серверу Exchange по протоколу IMAP. Для получения дополнительной информации о [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) класс. Во-первых, убедитесь, что службы IMAP включены на вашем сервере Exchange:

1. Откройте панель управления.
1. Перейдите в раздел «Инструменты администратора», затем «Службы».
1. Проверьте состояние службы Microsoft Exchange IMAP4.
1. Если он еще не запущен, включите/запустите его.

В следующем фрагменте кода показано, как подключать и отображать сообщения из папки «Входящие» на сервере Microsoft Exchange с использованием протокола IMAP.



~~~Java
// Connect to Exchange Server using ImapClient class
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.setSecurityOptions(SecurityOptions.Auto);

// Select the Inbox folder
imapClient.selectFolder(ImapFolderInfo.IN_BOX);

// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    System.out.println(msgInfo.getSubject());
}
// Disconnect from the server
imapClient.dispose();
~~~



В следующем фрагменте кода показано, как использовать SSL.



~~~Java
public static void run() {
    // Connect to Exchange Server using ImapClient class
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1");
    imapClient.setSecurityOptions(SecurityOptions.SSLExplicit);

    // Select the Inbox folder
    imapClient.selectFolder(ImapFolderInfo.IN_BOX);

    // Get the list of messages
    ImapMessageInfoCollection msgCollection = imapClient.listMessages();
    for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
        System.out.println(msgInfo.getSubject());
    }
    // Disconnect from the server
    imapClient.dispose();
}
~~~



После подключения к серверу Exchange по протоколу IMAP и получения [IMapMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfoCollection), В следующем фрагменте кода показано, как использовать [MessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/MessageInfo) порядковый номер объекта для сохранения определенного сообщения.



~~~Java
// Select the Inbox folder
imapClient.selectFolder(ImapFolderInfo.IN_BOX);
// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    // Fetch the message from inbox using its SequenceNumber from msgInfo
    MailMessage message = imapClient.fetchMessage(msgInfo.getSequenceNumber());

    // Save the message to disc now
    message.save(dataDir + msgInfo.getSequenceNumber() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~