---
title: "Получение списка сообщений из папки «Входящие» почтового ящика Microsoft Exchange Server"
url: /ru/java/getting-list-of-messages-from-inbox-folder-of-microsoft-exchange-server-mailbox/
weight: 50
type: docs
---


{{% alert color="primary" %}}

Наши советы по миграции показывают, как продукты Aspose можно использовать для улучшения приложений и избавления вас от зависимости от традиционной автоматизации.

Этот совет по миграции подключается к почтовому ящику Microsoft Exchange Server и получает список сообщений из папки «Входящие». В приведенных ниже примерах кода показано, как использовать [Взаимодействие с Microsoft Office](#using-microsoft-office-interop) чтобы получить список сообщений, прежде чем делать то же самое, используя классы в [Aspose.Обмен электронной почтой](#using-asposeemail), используя Java.

{{% /alert %}}
## **Использование интерфейса Microsoft Office**
Чтобы использовать объекты автоматизации делопроизводства для Microsoft Outlook, добавьте в проект ссылки на библиотеки Microsoft Office и Взаимодействие с Microsoft Office для Outlook. Microsoft Office Outlook также должен быть установлен на компьютере, на котором работает код.
### **Примеры программирования**
**C#**

~~~cs

 // Create Application class and get namespace

Outlook.Application outlook = new Outlook.ApplicationClass();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Get Inbox information in objec of type MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Unread emails

int unread = inbox.UnReadItemCount;

// Display the subject of emails in the Inbox folder
foreach (Outlook.MailItem mail in inbox.Items)

{

    Console.WriteLine(Wmail.Subject);


}


~~~
## **Использование Aspose.Email**
Следующие фрагменты кода делают то же самое, что и [приведенные выше фрагменты](#using-microsoft-office-interop) но использует Aspose.Email.

Однако Microsoft Outlook не нужно устанавливать на компьютер, на котором выполняется код. Для успешной сборки и запуска проекта обратитесь к Aspose.Email.
### **Примеры программирования**

~~~java

// Create instance of IEWSClient class by giving credentials
try (IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", "username", "password", "domain")) {
    // Call listMessages method to list messages info from Inbox

    ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

    // Loop through the collection to display the basic information
    for (ExchangeMessageInfo msgInfo : msgCollection) {
        System.out.println("Subject: " + msgInfo.getSubject());
        System.out.println("From: " + msgInfo.getFrom().toString());
        System.out.println("To: " + msgInfo.getTo().toString());
        System.out.println("Message ID: " + msgInfo.getMessageId());
        System.out.println("Unique URI: " + msgInfo.getUniqueUri());
        System.out.println("==================================");
    }
}

~~~
