---
title: "Obtener lista de mensajes de la carpeta de Bandeja de entrada del buzón de Microsoft Exchange Server"
url: /es/java/obtener-lista-de-mensajes-de-la-carpeta-de-bandeja-de-entrada-del-buzón-de-microsoft-exchange-server/
weight: 50
type: docs
---


{{% alert color="primary" %}} 

Nuestros consejos de migración muestran cómo los productos de Aspose pueden ser utilizados para mejorar sus aplicaciones y liberar su dependencia de la automatización tradicional.

Este consejo de migración se conecta a un buzón de Microsoft Exchange Server y obtiene una lista de mensajes de la carpeta de Bandeja de entrada. Los ejemplos de código a continuación muestran cómo utilizar [Microsoft Office Interop](#using-microsoft-office-interop) para obtener una lista de mensajes antes de hacer lo mismo utilizando las clases en [Aspose.Email Exchange](#using-asposeemail), utilizando Java.

{{% /alert %}} 
## **Usando Microsoft Office Interop**
Para utilizar objetos de automatización de Office para Microsoft Outlook, agregue referencias a las bibliotecas de Microsoft Office y Microsoft Office Interop para Outlook al proyecto. Microsoft Office Outlook también debe estar instalado en la máquina donde se ejecuta el código.
### **Ejemplos de Programación**
**C#**

~~~cs

 // Crear clase Application y obtener espacio de nombres

Outlook.Application outlook = new Outlook.ApplicationClass();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Obtener información de Bandeja de entrada en objeto de tipo MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Correos no leídos

int unread = inbox.UnReadItemCount;

// Mostrar el asunto de los correos en la carpeta de Bandeja de entrada
foreach (Outlook.MailItem mail in inbox.Items)

{

    Console.WriteLine(Wmail.Subject);


}


~~~
## **Usando Aspose.Email**
Los siguientes fragmentos de código hacen lo mismo que [los fragmentos anteriores](#using-microsoft-office-interop) pero utilizan Aspose.Email.

Sin embargo, Microsoft Outlook no necesita estar instalado en la máquina donde se ejecuta el código. Haga referencia a Aspose.Email para construir y ejecutar el proyecto con éxito.
### **Ejemplos de Programación**

~~~java

// Crear instancia de la clase IEWSClient proporcionando credenciales
try (IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", "username", "password", "domain")) {
    // Llamar al método listMessages para listar la información de los mensajes de la Bandeja de entrada

    ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

    // Iterar a través de la colección para mostrar la información básica
    for (ExchangeMessageInfo msgInfo : msgCollection) {
        System.out.println("Asunto: " + msgInfo.getSubject());
        System.out.println("De: " + msgInfo.getFrom().toString());
        System.out.println("Para: " + msgInfo.getTo().toString());
        System.out.println("ID del mensaje: " + msgInfo.getMessageId());
        System.out.println("URI único: " + msgInfo.getUniqueUri());
        System.out.println("==================================");
    }
}

~~~