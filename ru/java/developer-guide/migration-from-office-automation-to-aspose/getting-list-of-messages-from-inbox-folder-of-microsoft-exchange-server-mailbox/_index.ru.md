---
title: "Получение списка сообщений из папки "Входящие" почтового ящика Microsoft Exchange Server"
url: /ru/java/getting-list-of-messages-from-inbox-folder-of-microsoft-exchange-server-mailbox/
weight: 50
type: docs
---


{{% alert color="primary" %}} 

Наши советы по миграции показывают, как продукты Aspose могут быть использованы для улучшения ваших приложений и освобождения от зависимости от традиционной автоматизации.

Этот совет по миграции подключается к почтовому ящику Microsoft Exchange Server и получает список сообщений из папки "Входящие". Примеры кода ниже демонстрируют, как использовать [Microsoft Office Interop](#using-microsoft-office-interop) для получения списка сообщений, прежде чем сделать то же самое, используя классы из [Aspose.Email Exchange](#using-asposeemail), на Java.

{{% /alert %}} 
## **Использование Microsoft Office Interop**
Для использования объектов автоматизации Office для Microsoft Outlook добавьте ссылки на библиотеки Microsoft Office и Microsoft Office Interop для Outlook в проект. Microsoft Office Outlook также должен быть установлен на машине, на которой выполняется код.
### **Примеры программирования**
**C#**

~~~cs

 // Создаем класс Application и получаем пространство имен

Outlook.Application outlook = new Outlook.ApplicationClass();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Получаем информацию о папке "Входящие" в объекте типа MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Непрочитанные письма

int unread = inbox.UnReadItemCount;

// Отображаем темы писем в папке "Входящие"
foreach (Outlook.MailItem mail in inbox.Items)

{

    Console.WriteLine(Wmail.Subject);


}


~~~
## **Использование Aspose.Email**
Следующие фрагменты кода выполняют ту же задачу, что и [фрагменты выше](#using-microsoft-office-interop), но используют Aspose.Email.

Однако Microsoft Outlook не нужно устанавливать на машине, где выполняется код. Ссылаясь на Aspose.Email, чтобы успешно собрать и запустить проект.
### **Примеры программирования**

~~~java

// Создание экземпляра класса IEWSClient с указанием учетных данных
try (IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", "username", "password", "domain")) {
    // Вызов метода listMessages для получения информации о сообщениях из "Входящих"

    ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

    // Перебираем коллекцию для отображения основной информации
    for (ExchangeMessageInfo msgInfo : msgCollection) {
        System.out.println("Тема: " + msgInfo.getSubject());
        System.out.println("От: " + msgInfo.getFrom().toString());
        System.out.println("Кому: " + msgInfo.getTo().toString());
        System.out.println("ID сообщения: " + msgInfo.getMessageId());
        System.out.println("Уникальный URI: " + msgInfo.getUniqueUri());
        System.out.println("==================================");
    }
}

~~~