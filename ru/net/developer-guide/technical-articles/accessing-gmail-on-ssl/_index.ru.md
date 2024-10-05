---
title: "Доступ к Gmail через SSL"
url: /ru/net/accessing-gmail-on-ssl/
weight: 40
type: docs
---

## **SMTP**
Эта статья демонстрирует, как выполнить [подключение к серверу Gmail](#connecting-to-gmail-smtp-server) и [отправить электронное письмо](#sending-an-email-message) с использованием протокола SMTP через SSL.
### **Подключение к серверу Gmail SMTP**
Следующий фрагмент кода показывает, как подключиться к SMTP серверу с поддержкой SSL.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectingGmailSMTPServer-ConnectingGmailSMTPServer.cs" >}}
### **Отправка электронного сообщения**
Код выше настраивает объект SMTPClient для подключения к серверу Gmail. Чтобы отправить сообщение, используя тот же объект клиента, создайте объект класса [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) и отправьте сообщение с помощью объекта SMTP клиента. Следующий фрагмент кода показывает, как задать свойства сообщения, например, тему, кому и текст:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendEmailMessage-SendEmailMessage.cs" >}}
## **IMAP**
Эта статья показывает, как выполнить ряд действий на почтовом сервере с поддержкой SSL, используя протокол IMAP:

- Подключиться к почтовому серверу.
- Получить общее количество сообщений в почтовом ящике.
- Сохранить сообщения локально.
- Создать сообщение и добавить его в папку.
### **Подключение к почтовому серверу**
Используйте объект класса [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) от Aspose.Email для подключения к почтовому серверу. Для установления соединения требуются адрес сервера, порт, имя пользователя и пароль. Gmail использует порт 993 для IMAP протокола, следующий фрагмент кода показывает, как подключиться к Gmail с использованием этого порта.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingIMAP-ConnectToGmailUsingIMAP.cs" >}}
### **Выбор папки и получение общего числа сообщений**
Проверка папки Входящие - это наиболее частая задача при проверке электронной почты. С помощью Aspose.Email это можно сделать всего двумя простыми строками кода. Следующий фрагмент кода показывает, как получить доступ к папке Входящие и получить общее количество сообщений в папке.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetGmailMessageCountUsingIMAP-GetGmailMessageCountUsingIMAP.cs" >}}
### **Сохранение сообщений на локальный жесткий диск**
После того, как папка была выбрана с помощью метода SelectFolder, используйте функцию ListMessages для получения списка всех сообщений в папке в объекте ImapMessagesInfoCollection. Пройдите через эту коллекцию и сохраните электронные сообщения на локальном диске компьютера следующим образом:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SaveGmailMessages-SaveGmailMessages.cs" >}}
### **Создание новой папки**
Протокол IMAP также позволяет создавать новую папку на почтовом сервере. Это можно сделать с помощью простого вызова функции.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CreateNewGmailFolderUsingIMAP-CreateNewGmailFolderUsingIMAP.cs" >}}
### **Создание нового сообщения в папке**
Добавьте новое сообщение в папку, используя классы [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) и [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient). Примеры ниже показывают, как сначала создать объект MailMessage, указав тему, получателя и отправителя. Затем он подписывается на папку и добавляет сообщение в нее. Следующий фрагмент кода показывает, как создать новое сообщение в папке.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AddingMessageToGmailFolderUsingIMAP-AddingMessageToGmailFolderUsingIMAP.cs" >}}
## **POP3**
Эта статья показывает несколько примеров, использующих протокол POP3 через SSL. Для подключения к защищённому SSL серверу нужно определить SSL порт и два дополнительных свойства. Остальная часть кода такая же, как для подключения к обычному POP3 серверу.

Примеры кода ниже показывают, как:

- Подключиться к SSL серверу.
- Проверить состояние почтового ящика.
- Получить информацию о сообщении.
- Извлечь электронные письма.
### **Подключение к почтовому серверу**
Подключитесь к почтовому серверу с поддержкой SSL, используя класс [Pop3client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client), как описано ниже.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingPOP3-ConnectToGmailUsingPOP3.cs" >}}
### **Проверка состояния почтового ящика**
Следующий фрагмент кода показывает, как проверить количество сообщений, хранящихся в почтовом ящике, и размер почтового ящика. Используйте класс [Pop3MailboxInfo](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo) для этой цели.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMailboxStatus-CheckGmailMailboxStatus.cs" >}}
### **Проверка информации о сообщениях**
Этот пример проверяет все сообщения в почтовом ящике, используя класс [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection). Используйте функцию [Pop3Client.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/listmessages/index) для получения коллекции [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection). Затем пройдите через коллекцию, чтобы прочитать информацию о сообщении: идентификатор сообщения, индекс, тему и размер.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMessageInformation-CheckGmailMessageInformation.cs" >}}
### **Извлечение сообщений**
Чтобы получить сообщения из почтового ящика, используйте метод FetchMessage() класса [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client), чтобы получить сообщение в объект типа [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). Следующий фрагмент кода показывает, как подсчитать количество электронных писем в почтовом ящике, а затем пройтись через них, чтобы извлечь каждое.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-RetrieveGmailMessages-RetrieveGmailMessages.cs" >}}