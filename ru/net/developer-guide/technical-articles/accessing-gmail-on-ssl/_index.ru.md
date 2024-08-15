---
title: "Доступ к Gmail по протоколу SSL"
url: /ru/net/accessing-gmail-on-ssl/
weight: 40
type: docs
---

## **SMTP**
В этой статье показано, как выполнить [подключиться к серверу Gmail](#connecting-to-gmail-smtp-server) and [отправить электронное письмо](#sending-an-email-message) используя протокол SMTP на SSL.
### **Подключение к SMTP-серверу Gmail**
В следующем фрагменте кода показано, как подключиться к SMTP-серверу с поддержкой SSL.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectingGmailSMTPServer-ConnectingGmailSMTPServer.cs" >}}
### **Отправка сообщения по электронной почте**
Приведенный выше код настраивает объект SMTPClient для подключения к серверу Gmail. Чтобы отправить сообщение с использованием того же клиентского объекта, создайте [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) объект класса и отправьте сообщение с помощью объекта SMTP-клиента. В следующем фрагменте кода показано, как задать свойства сообщения, например тему, текст и текст сообщения:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendEmailMessage-SendEmailMessage.cs" >}}
## **IMAP**
В этой статье показано, как выполнить ряд действий на почтовом сервере с поддержкой SSL с использованием протокола IMAP:

- Подключитесь к почтовому серверу.
- Получите общее количество сообщений в папке «Входящие».
- Сохраняйте сообщения локально.
- Создайте сообщение и добавьте его в папку.
### **Подключение к почтовому серверу**
Используйте электронную почту Aspos.Email [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) объект класса для подключения к почтовому серверу. Адрес сервера, порт, имя пользователя и пароль необходимы для установления соединения. Gmail использует порт 993 для протокола IMAP. В следующем фрагменте кода показано, как подключиться к Gmail с помощью этого порта.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingIMAP-ConnectToGmailUsingIMAP.cs" >}}
### **Выбор папки и получение общего количества сообщений**
Проверка папки «Входящие» — самая частая задача при проверке электронной почты. Используя Aspose.Email, это можно сделать, используя всего две простые строки кода. В следующем фрагменте кода показано, как получить доступ к папке «Входящие» и узнать общее количество сообщений в этой папке.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetGmailMessageCountUsingIMAP-GetGmailMessageCountUsingIMAP.cs" >}}
### **Сохранение сообщений на локальном жестком диске**
После выбора папки методом SelectFolder используйте функцию ListMessages, чтобы получить список всех сообщений в папке в объекте IMapMessagesInfoCollection. Просмотрите эту коллекцию и сохраните сообщения электронной почты на локальном диске компьютера следующим образом:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SaveGmailMessages-SaveGmailMessages.cs" >}}
### **Создание новой папки**
Протокол IMAP также позволяет создать новую папку на почтовом сервере. Это можно сделать с помощью простого вызова функции.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CreateNewGmailFolderUsingIMAP-CreateNewGmailFolderUsingIMAP.cs" >}}
### **Создание нового сообщения в папке**
Добавьте новое сообщение в папку, используя [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) and [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) классы. В приведенных ниже примерах сначала создается объект MailMessage путем указания темы, «куда» и «откуда». Затем пользователь подписывается на папку и добавляет в нее сообщение. В следующем фрагменте кода показано, как вы создаете новое сообщение в папке.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AddingMessageToGmailFolderUsingIMAP-AddingMessageToGmailFolderUsingIMAP.cs" >}}
## **POP3**
В этой статье приведены несколько примеров использования протокола POP3 в протоколе SSL. Чтобы подключиться к серверу, защищенному SSL, нам необходимо определить порт SSL и два дополнительных свойства. В остальном код такой же, как и при подключении к обычному серверу POP3.

В приведенных ниже примерах кода показано, как:

- Подключитесь к серверу SSL.
- Проверьте состояние почтового ящика
- Получите информацию о сообщении
- Получайте электронные письма.
### **Подключение к почтовому серверу**
Подключитесь к почтовому серверу с поддержкой SSL, используя [Pop3client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) класс, как описано ниже.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingPOP3-ConnectToGmailUsingPOP3.cs" >}}
### **Проверка состояния почтового ящика**
В следующем фрагменте кода показано, как проверяется количество сообщений, хранящихся в почтовом ящике, и размер почтового ящика. Используйте [Pop3MailboxInfo](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo) класс для этой цели.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMailboxStatus-CheckGmailMailboxStatus.cs" >}}
### **Проверка информации о сообщении**
В этом примере проверяются все сообщения в почтовом ящике с помощью [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection) класс. Используйте [Pop3Client.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/listmessages/index) функция для получения [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection) коллекция. Затем просмотрите коллекцию, чтобы прочитать информацию о сообщении: идентификатор сообщения, индекс, тему и размер



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMessageInformation-CheckGmailMessageInformation.cs" >}}
### **Получение сообщений**
Чтобы получить сообщения из почтового ящика, используйте [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) метод класса fetchMessage () для преобразования сообщения в [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) введите объект. В следующем фрагменте кода показано, как подсчитывать количество писем в почтовом ящике, а затем перебирать их, чтобы получить каждое из них.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-RetrieveGmailMessages-RetrieveGmailMessages.cs" >}}
