---
title: "Работа с правилами на Exchange Server"
url: /ru/java/working-with-rules-on-exchange-server/
weight: 90
type: docs
---

## **Управление правилами**
Aspose.Email для Java можно использовать для управления правилами на Exchange Server с помощью класса [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Этот класс использует Exchange Web Services (EWS), которые доступны в Exchange Server 2007 и более поздних версиях. Чтобы показать, как управлять правилами, в этой статье объясняется, как:

- Получить правила, уже существующие на сервере.
- Создать новое правило.
- Обновить существующее правило.

Требуется Microsoft Exchange Server 2010 Service Pack 1 для всех функций, описанных в этой статье.
### **Чтение правил**
Чтобы получить все правила с Exchange Server:

1. Подключитесь к Exchange Server, используя класс IEWSClient.
1. Вызовите метод IEWSClient.getInboxRules(), чтобы получить все правила.
1. В цикле foreach просмотрите все правила и отобразите свойства правила, такие как условия, действия и имя.

Следующий фрагмент кода показывает, как читать правила.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Подключено к серверу Exchange");

// Получите все правила для папки «Входящие»
InboxRule[] inboxRules = client.getInboxRules();

// Отобразите информацию о каждом правиле
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Отображаемое имя: " + inboxRule.getDisplayName());

    // Проверьте, есть ли условие "От кого"
    if (inboxRule.getConditions().getFromAddresses().size() > 0) {
        for (MailAddress fromAddress : (Iterable<MailAddress>) inboxRule.getConditions().getFromAddresses()) {
            System.out.println("От: " + fromAddress.getDisplayName() + " - " + fromAddress.getAddress());
        }
    }
    // Проверьте, есть ли условие "Тема содержит"
    if (inboxRule.getConditions().containsSubjectStrings().size() > 0) {
        // преобразование из foreach в while
        for (String subject : inboxRule.getConditions().containsSubjectStrings()) {
            System.out.println("Тема содержит: " + subject);
        }
    }
    // Проверьте, есть ли действие "Переместить в папку"
    if (inboxRule.getActions().getMoveToFolder().length() > 0) {
        System.out.println("Переместить сообщение в папку: " + inboxRule.getActions().getMoveToFolder());
    }
}
~~~
### **Создание нового правила**
Чтобы создать новое правило на Exchange Server, выполните следующие шаги:

1. Подключитесь к Exchange Server, используя класс IEWSClient.
1. Создайте новый экземпляр класса InboxRule и установите следующие обязательные свойства:
   1. DisplayName
   1. Условия
   1. Действия
1. Вызовите метод IEWSClient.createInboxRule(), чтобы создать правило.

Следующий фрагмент кода показывает, как создать новое правило.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Подключено к серверу Exchange");

InboxRule rule = new InboxRule();
rule.setDisplayName("Сообщение от клиента ABC");

// Добавьте условия
RulePredicates newRules = new RulePredicates();
// Установите строку, содержащую тему "ABC", и добавьте условия
newRules.containsSubjectStrings().addItem("ABC");
newRules.getFromAddresses().addMailAddress(new MailAddress("administrator@ex2010.local", true));
rule.setConditions(newRules);

// Добавьте действия и переместите сообщение в папку
RuleActions newActions = new RuleActions();
newActions.setMoveToFolder("120:AAMkADFjMjNjMmNjLWE3NzgtNGIzNC05OGIyLTAwNTgzNjRhN2EzNgAuAAAAAABbwP+Tkhs0TKx1GMf0D/cPAQD2lptUqri0QqRtJVHwOKJDAAACL5KNAAA=AQAAAA==");
rule.setActions(newActions);
client.createInboxRule(rule);
~~~
### **Обновление правила**
Чтобы обновить правило на Exchange Server:

1. Подключитесь к Exchange Server, используя класс IEWSClient.
1. Вызовите метод IEWSClient.getInboxRules(), чтобы получить все правила.
1. В цикле foreach просмотрите все правила и получите правило, которое вы хотите изменить, сопоставив DisplayName в условии.
1. Обновите свойства правила
1. Вызовите метод IEWSClient.updateInboxRule(), чтобы обновить правило.

Следующий фрагмент кода показывает, как обновить правило.

~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Подключено к серверу Exchange");

// Получите все правила для папки «Входящие»
InboxRule[] inboxRules = client.getInboxRules();

// Перебор каждого правила
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Отображаемое имя: " + inboxRule.getDisplayName());
    if ("Сообщение от клиента ABC".equals(inboxRule.getDisplayName())) {
        System.out.println("Обновление правила....");
        inboxRule.getConditions().getFromAddresses().set_Item(0, new MailAddress("administrator@ex2010.local", true));
        client.updateInboxRule(inboxRule);
    }
}
~~~