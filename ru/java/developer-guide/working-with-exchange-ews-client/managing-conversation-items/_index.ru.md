---
title: "Управление элементами беседы"
url: /ru/java/managing-conversation-items/
weight: 40
type: docs
---


Aspose.Email для Java может использоваться для управления элементами беседы на Exchange Server с помощью класса [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Этот класс использует Exchange Web Services, которые доступны только в Exchange Server 2007 и более поздних версиях. Эта статья показывает, как [найти](#finding-conversations), [скопировать](#copying-conversations), [переместить](#moving-conversations) и [удалить](#deleting-conversations) элементы беседы на Exchange Server 2010. Microsoft Exchange Server 2010 Service Pack 1 требуется для всех функций, включенных в этот раздел.
## **Поиск бесед**
Чтобы получить информацию о беседе из определенной папки на Exchange Server:

1. Подключитесь к Exchange Server с использованием класса IEWSClient.
1. Вызовите метод IEWSClient.findConversations(), чтобы найти все элементы беседы из папки.
1. Отобразите свойства элемента беседы, такие как ID, тема беседы и статус флага.

Следующий фрагмент кода показывает, как найти беседы.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Подключено к Exchange 2010");

// Найдите элементы беседы в папке Входящие
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
// Покажите все беседы
for (ExchangeConversation conversation : conversations) {
    // Отобразите свойства беседы, такие как Id и Тема
    System.out.println("Тема: " + conversation.getConversationTopic());
    System.out.println("Статус флага: " + conversation.getFlagStatus());
    System.out.println();
}
~~~
## **Копирование бесед**
Чтобы скопировать беседы из одной папки в другую:

1. Подключитесь к Exchange Server с использованием класса IEWSClient.
1. Вызовите метод IEWSClient.copyConversationItems(), чтобы скопировать элемент беседы из исходной папки в целевую папку.

Следующий фрагмент кода показывает, как копировать беседы.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Подключено к Exchange 2010");

// Найдите элементы беседы в папке Входящие, которые мы хотим скопировать
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Тема: " + conversation.getConversationTopic());
    // Скопируйте элемент беседы на основе некоторого условия
    if (conversation.getConversationTopic().contains("test email")) {
        client.copyConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Скопирован элемент беседы в другую папку");
    }
}
~~~
## **Перемещение бесед**
Чтобы переместить беседы из одной папки в другую:

1. Подключитесь к Exchange Server с использованием класса IEWSClient.
1. Вызовите метод IEWSClient.moveConversationItems(), чтобы переместить беседу из исходной папки в целевую папку.

Следующий фрагмент кода показывает, как перемещать беседы.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Подключено к Exchange 2010");

// Найдите элементы беседы в папке Входящие, которые мы хотим переместить
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());

for (ExchangeConversation conversation : conversations) {
    System.out.println("Тема: " + conversation.getConversationTopic());
    // Переместите элемент беседы на основе некоторого условия
    if (conversation.getConversationTopic().contains("test email") == true) {
        client.moveConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Перемещен элемент беседы в другую папку");
    }
}
~~~
## **Удаление бесед**
Чтобы удалить беседы из папки:

1. Подключитесь к Exchange Server с использованием класса IEWSClient.
1. Вызовите метод IEWSClient.deleteConversationItems(), чтобы удалить элемент беседы из исходной папки.

Следующий фрагмент кода показывает, как удалить беседы.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Подключено к Exchange 2010");

// Найдите элементы беседы в папке Входящие, которые мы хотим удалить
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Тема: " + conversation.getConversationTopic());
    // Удалите элемент беседы на основе некоторого условия
    if (conversation.getConversationTopic().contains("test email") == true) {
        client.deleteConversationItems(conversation.getConversationId());
        System.out.println("Элемент беседы удален");
    }
}
~~~