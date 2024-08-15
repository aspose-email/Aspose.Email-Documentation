---
title: "Работа с правилами на сервере Exchange"
url: /ru/java/working-with-rules-on-exchange-server/
weight: 90
type: docs
---


## **Управление правилами**
Aspose.Email для Java можно использовать для управления правилами на сервере Exchange с помощью [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс. В этом классе используются веб-службы Exchange (EWS), доступные в Exchange Server 2007 и более поздних версиях. Чтобы показать, как управлять правилами, в этой статье объясняется, как:

- Ознакомьтесь с правилами, уже имеющимися на сервере.
- Создайте новое правило.
- Обновите существующее правило.

Для всех функций, описанных в этой статье, требуется пакет обновления 1 для Microsoft Exchange Server 2010.
### **Ознакомьтесь с правилами**
Чтобы получить все правила с сервера Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.getInboxRules (), чтобы получить все правила.
1. В цикле foreach просмотрите все правила и отобразите свойства правила, такие как условия, действия и имя.

В следующем фрагменте кода показано, как читать правила.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Connected to Exchange server");

// Get all Inbox Rules
InboxRule[] inboxRules = client.getInboxRules();

// Display information about each rule
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Display Name: " + inboxRule.getDisplayName());

    // Check if there is a "From Address" condition
    if (inboxRule.getConditions().getFromAddresses().size() > 0) {
        for (MailAddress fromAddress : (Iterable<MailAddress>) inboxRule.getConditions().getFromAddresses()) {
            System.out.println("From: " + fromAddress.getDisplayName() + " - " + fromAddress.getAddress());
        }
    }
    // Check if there is a "Subject Contains" condition
    if (inboxRule.getConditions().containsSubjectStrings().size() > 0) {
        // foreach to while statements conversion
        for (String subject : inboxRule.getConditions().containsSubjectStrings()) {
            System.out.println("Subject contains: " + subject);
        }
    }
    // Check if there is a "Move to Folder" action
    if (inboxRule.getActions().getMoveToFolder().length() > 0) {
        System.out.println("Move message to folder: " + inboxRule.getActions().getMoveToFolder());
    }
}
~~~
### **Создание нового правила**
Чтобы создать новое правило на сервере Exchange, выполните следующие шаги:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Создайте новый экземпляр класса InboxRule и задайте следующие обязательные свойства:
   1. DisplayName
   1. Conditions
   1. Actions
1. Для создания правила вызовите метод IEWSclient.createInboxRule ().

В следующем фрагменте кода показано, как создать новое правило.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Connected to Exchange server");

InboxRule rule = new InboxRule();
rule.setDisplayName("Message from client ABC");

// Add conditions
RulePredicates newRules = new RulePredicates();
// Set Subject contains string "ABC" and Add the conditions
newRules.containsSubjectStrings().addItem("ABC");
newRules.getFromAddresses().addMailAddress(new MailAddress("administrator@ex2010.local", true));
rule.setConditions(newRules);

// Add Actions and Move the message to a folder
RuleActions newActions = new RuleActions();
newActions.setMoveToFolder("120:AAMkADFjMjNjMmNjLWE3NzgtNGIzNC05OGIyLTAwNTgzNjRhN2EzNgAuAAAAAABbwP+Tkhs0TKx1GMf0D/cPAQD2lptUqri0QqRtJVHwOKJDAAACL5KNAAA=AQAAAA==");
rule.setActions(newActions);
client.createInboxRule(rule);
~~~
### **Обновление правила**
Чтобы обновить правило на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.getInboxRules (), чтобы получить все правила.
1. В цикле foreach просмотрите все правила и выберите правило, которое вы хотите изменить, сопоставив DisplayName в условии.
1. Обновите свойства правила
1. Вызовите метод IEWSclient.updateInboxRule (), чтобы обновить правило.

В следующем фрагменте кода показано, как обновить правило.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Connected to Exchange server");

// Get all Inbox Rules
InboxRule[] inboxRules = client.getInboxRules();

// Loop through each rule
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Display Name: " + inboxRule.getDisplayName());
    if ("Message from client ABC".equals(inboxRule.getDisplayName())) {
        System.out.println("Updating the rule....");
        inboxRule.getConditions().getFromAddresses().set_Item(0, new MailAddress("administrator@ex2010.local", true));
        client.updateInboxRule(inboxRule);
    }
}
~~~