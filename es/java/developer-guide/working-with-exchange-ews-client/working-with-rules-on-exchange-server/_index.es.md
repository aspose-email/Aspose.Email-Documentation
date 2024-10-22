---
title: "Trabajando con Reglas en Exchange Server"
url: /es/java/trabajando-con-reglas-en-exchange-server/
weight: 90
type: docs
---


## **Gestión de Reglas**
Aspose.Email para Java se puede usar para gestionar las reglas en Exchange Server utilizando la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Esta clase utiliza Exchange Web Services (EWS), que están disponibles en Exchange Server 2007 y versiones posteriores. Para mostrar cómo gestionar reglas, este artículo explica cómo:

- Leer las reglas ya existentes en el servidor.
- Crear una nueva regla.
- Actualizar una regla existente.

Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funciones descritas en este artículo.
### **Leer Reglas**
Para obtener todas las reglas del Exchange Server:

1. Conéctese a un Exchange Server utilizando la clase IEWSClient.
1. Llama al método IEWSClient.getInboxRules() para obtener todas las reglas.
1. En un bucle foreach, recorre todas las reglas y muestra las propiedades de la regla como condiciones, acciones y nombre.

El siguiente fragmento de código muestra cómo leer reglas.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Conectado al servidor de Exchange");

// Obtener todas las Reglas de Bandeja de Entrada
InboxRule[] inboxRules = client.getInboxRules();

// Mostrar información sobre cada regla
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Nombre para Mostrar: " + inboxRule.getDisplayName());

    // Verificar si hay una condición de "Dirección de Remitente"
    if (inboxRule.getConditions().getFromAddresses().size() > 0) {
        for (MailAddress fromAddress : (Iterable<MailAddress>) inboxRule.getConditions().getFromAddresses()) {
            System.out.println("De: " + fromAddress.getDisplayName() + " - " + fromAddress.getAddress());
        }
    }
    // Verificar si hay una condición de "Asunto Contiene"
    if (inboxRule.getConditions().containsSubjectStrings().size() > 0) {
        // conversión de foreach a while
        for (String subject : inboxRule.getConditions().containsSubjectStrings()) {
            System.out.println("El asunto contiene: " + subject);
        }
    }
    // Verificar si hay una acción de "Mover a Carpeta"
    if (inboxRule.getActions().getMoveToFolder().length() > 0) {
        System.out.println("Mover el mensaje a la carpeta: " + inboxRule.getActions().getMoveToFolder());
    }
}
~~~
### **Creando una Nueva Regla**
Para crear una nueva regla en el Exchange Server, realiza los siguientes pasos:

1. Conéctese a un Exchange Server utilizando la clase IEWSClient.
1. Crea una nueva instancia de la clase InboxRule y establece las siguientes propiedades obligatorias:
   1. DisplayName
   1. Conditions
   1. Actions
1. Llama al método IEWSClient.createInboxRule() para crear la regla.

El siguiente fragmento de código muestra cómo crear una nueva regla.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Conectado al servidor de Exchange");

InboxRule rule = new InboxRule();
rule.setDisplayName("Mensaje del cliente ABC");

// Agregar condiciones
RulePredicates newRules = new RulePredicates();
// Establecer Asunto contiene la cadena "ABC" y agregar las condiciones
newRules.containsSubjectStrings().addItem("ABC");
newRules.getFromAddresses().addMailAddress(new MailAddress("administrator@ex2010.local", true));
rule.setConditions(newRules);

// Agregar Acciones y mover el mensaje a una carpeta
RuleActions newActions = new RuleActions();
newActions.setMoveToFolder("120:AAMkADFjMjNjMmNjLWE3NzgtNGIzNC05OGIyLTAwNTgzNjRhN2EzNgAuAAAAAABbwP+Tkhs0TKx1GMf0D/cPAQD2lptUqri0QqRtJVHwOKJDAAACL5KNAAA=AQAAAA==");
rule.setActions(newActions);
client.createInboxRule(rule);
~~~
### **Actualizando una Regla**
Para actualizar una regla en el Exchange Server:

1. Conéctese a un Exchange Server utilizando la clase IEWSClient.
1. Llama al método IEWSClient.getInboxRules() para obtener todas las reglas.
1. En un bucle foreach, recorre todas las reglas y obtiene la regla que deseas cambiar al coincidir el DisplayName en una condición.
1. Actualiza las propiedades de la regla.
1. Llama al método IEWSClient.updateInboxRule() para actualizar la regla.

El siguiente fragmento de código muestra cómo actualizar una regla.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxURI, credential);

System.out.println("Conectado al servidor de Exchange");

// Obtener todas las Reglas de Bandeja de Entrada
InboxRule[] inboxRules = client.getInboxRules();

// Recorrer cada regla
for (InboxRule inboxRule : inboxRules) {
    System.out.println("Nombre para Mostrar: " + inboxRule.getDisplayName());
    if ("Mensaje del cliente ABC".equals(inboxRule.getDisplayName())) {
        System.out.println("Actualizando la regla....");
        inboxRule.getConditions().getFromAddresses().set_Item(0, new MailAddress("administrator@ex2010.local", true));
        client.updateInboxRule(inboxRule);
    }
}
~~~