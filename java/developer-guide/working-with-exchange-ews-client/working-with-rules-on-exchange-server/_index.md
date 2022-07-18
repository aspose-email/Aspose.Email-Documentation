---
title: Working with Rules On Exchange Server
type: docs
weight: 90
url: /java/working-with-rules-on-exchange-server/
---


## **Managing Rules**
Aspose.Email for Java can be used to manage the rules on Exchange Server using the [EWSClient](https://reference.aspose.com/email/java/com.aspose.email/ewsclient) class. This class uses Exchange Web Services (EWS), which are available in Exchange Server 2007 and later releases. To show how to manage rules, this article explains how to:

- Read the rules already on the server.
- Create a new rule.
- Update an existing rule.

Microsoft Exchange Server 2010 Service Pack 1 is required for all features described in this article.
### **Read Rules**
To get all the rules from the Exchange Server:

1. Connect to an Exchange Server using the IEWSClient class.
1. Call the IEWSClient.getInboxRules() method to get all the rules.
1. In a foreach loop, browse through all the rules and display the rule properties like conditions, actions, and name.

The following code snippet shows you how to read rules.



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
### **Creating a New Rule**
To create a new rule on the Exchange Server, perform the following steps:

1. Connect to an Exchange Server using the IEWSClient class.
1. Create a new instance of the InboxRule class and set the following mandatory properties:
   1. DisplayName
   1. Conditions
   1. Actions
1. Call the IEWSClient.createInboxRule() method to create the rule.

The following code snippet shows you how to create a new rule.



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
### **Updating a Rule**
To update a rule on the Exchange Server:

1. Connect to an Exchange Server using the IEWSClient class.
1. Call the IEWSClient.getInboxRules() method to get all the rules.
1. In a foreach loop, browse through all the rules and get the rule you want to change by matching the DisplayName in a condition.
1. Update the rule properties
1. Call the IEWSClient.updateInboxRule() method to update the rule.

The following code snippet shows you how to update a rule.



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