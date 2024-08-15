---
title: "Obtener la lista de mensajes de la carpeta Bandeja de entrada del buzón de Microsoft Exchange Server"
url: /es/java/getting-list-of-messages-from-inbox-folder-of-microsoft-exchange-server-mailbox/
weight: 50
type: docs
---


{{% alert color="primary" %}}

Nuestros consejos de migración muestran cómo se pueden usar los productos de Aspose para mejorar sus aplicaciones y liberarlo de la dependencia de la automatización tradicional.

Este consejo de migración se conecta a un buzón de correo de Microsoft Exchange Server y obtiene una lista de los mensajes de la carpeta Bandeja de entrada. En los ejemplos de código que aparecen a continuación se muestra cómo utilizar [Interoperabilidad de Microsoft Office](#using-microsoft-office-interop) para obtener una lista de mensajes antes de hacer lo mismo usando las clases del [Intercambio de correo electrónico Aspose.Email](#using-asposeemail), utilizando Java.

{{% /alert %}}
## **Uso de Interoperabilidad de Microsoft Office**
Para usar objetos de automatización de oficina para Microsoft Outlook, añada al proyecto referencias a las bibliotecas de Microsoft Office y Interoperabilidad de Microsoft Office for Outlook. Microsoft Office Outlook también debe estar instalado en la máquina en la que se ejecuta el código.
### **Ejemplos de programación**
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
## **Uso de Aspose.Email**
Los siguientes fragmentos de código hacen lo mismo que [los fragmentos de arriba](#using-microsoft-office-interop) pero usa Aspose.Email.

Sin embargo, no es necesario instalar Microsoft Outlook en la máquina en la que se ejecuta el código. Consulte el archivo Aspose.Email para crear y ejecutar el proyecto correctamente.
### **Ejemplos de programación**

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
