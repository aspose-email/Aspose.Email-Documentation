---
title: "Trabajar con reglas en Exchange Server"
url: /es/java/working-with-rules-on-exchange-server/
weight: 90
type: docs
---


## **Gestión de reglas**
Aspose.Email para Java se puede usar para administrar las reglas de Exchange Server mediante el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase. Esta clase usa los servicios web de Exchange (EWS), que están disponibles en Exchange Server 2007 y versiones posteriores. Para mostrar cómo administrar las reglas, en este artículo se explica cómo:

- Lea las reglas que ya están en el servidor.
- Crea una regla nueva.
- Actualiza una regla existente.

Se requiere el Service Pack 1 de Microsoft Exchange Server 2010 para todas las funciones descritas en este artículo.
### **Lea las reglas**
Para obtener todas las reglas del servidor Exchange:

1. Conéctese a un servidor Exchange mediante la clase IewsClient.
1. Llame al método IewsClient.getInboxRules () para obtener todas las reglas.
1. En un bucle para cada uno, examine todas las reglas y muestre sus propiedades, como las condiciones, las acciones y el nombre.

El siguiente fragmento de código muestra cómo leer las reglas.



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
### **Creación de una nueva regla**
Para crear una nueva regla en el servidor Exchange, lleve a cabo los siguientes pasos:

1. Conéctese a un servidor Exchange mediante la clase IewsClient.
1. Cree una nueva instancia de la clase InboxRule y defina las siguientes propiedades obligatorias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Llame al método IewsClient.createInboxRule () para crear la regla.

El siguiente fragmento de código muestra cómo crear una regla nueva.



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
### **Actualización de una regla**
Para actualizar una regla en Exchange Server:

1. Conéctese a un servidor Exchange mediante la clase IewsClient.
1. Llame al método IewsClient.getInboxRules () para obtener todas las reglas.
1. En un bucle de foreach, examine todas las reglas y obtenga la regla que desea cambiar haciendo coincidir el nombre de visualización de una condición.
1. Actualizar las propiedades de la regla
1. Llame al método iewsClient.UpdateInboxRule () para actualizar la regla.

El siguiente fragmento de código muestra cómo actualizar una regla.



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