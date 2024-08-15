---
title: "Conexión a Exchange Server"
url: /es/java/connecting-to-exchange-server/
weight: 10
type: docs
---


Para conectarse a los servidores Exchange 2007, 2010 y 2013 mediante el servicio web de Exchange, Aspose.Email proporciona [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) interfaz que implementa el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase. El [EWSClient.getEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#getEWSClient\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\)) el método crea una instancia y devuelve un [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) objeto que se utiliza además para realizar operaciones relacionadas con un buzón de Exchange y otras carpetas. En este artículo se muestra cómo crear instancias de objetos de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
## **Conexión a Exchange Server mediante EWS**
El siguiente fragmento de código muestra cómo conectarse mediante Exchange Web Service (EWS).



~~~Java
private static IEWSClient getExchangeEWSClient() {
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String domain = "";
    final String username = "username@onmicrosoft.com";
    final String password = "password";
    NetworkCredential credentials = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
    return client;
}
~~~
## **Conexión a Exchange Server mediante IMAP**
Microsoft Exchange Server admite el protocolo IMAP para acceder a los elementos de un buzón. Utilice los correos electrónicos de Aspose.Email [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) clase para conectarse al servidor Exchange mediante el protocolo IMAP. Para obtener más información acerca de [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) clase. En primer lugar, asegúrese de que los servicios IMAP estén habilitados para su servidor Exchange:

1. Abre el panel de control.
1. Vaya a Herramientas de administración y, a continuación, a Servicios.
1. Compruebe el estado del servicio IMAP4 de Microsoft Exchange.
1. Si aún no se está ejecutando, habilítelo o inícielo.

El siguiente fragmento de código muestra cómo conectar y enumerar los mensajes de la carpeta Bandeja de entrada del servidor Microsoft Exchange mediante el protocolo IMAP.



~~~Java
// Connect to Exchange Server using ImapClient class
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.setSecurityOptions(SecurityOptions.Auto);

// Select the Inbox folder
imapClient.selectFolder(ImapFolderInfo.IN_BOX);

// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    System.out.println(msgInfo.getSubject());
}
// Disconnect from the server
imapClient.dispose();
~~~



El siguiente fragmento de código muestra cómo usar SSL.



~~~Java
public static void run() {
    // Connect to Exchange Server using ImapClient class
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1");
    imapClient.setSecurityOptions(SecurityOptions.SSLExplicit);

    // Select the Inbox folder
    imapClient.selectFolder(ImapFolderInfo.IN_BOX);

    // Get the list of messages
    ImapMessageInfoCollection msgCollection = imapClient.listMessages();
    for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
        System.out.println(msgInfo.getSubject());
    }
    // Disconnect from the server
    imapClient.dispose();
}
~~~



Tras conectarse a un servidor de Exchange mediante IMAP y obtener el [IMapMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfoCollection), El siguiente fragmento de código muestra cómo usar el [MessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/MessageInfo) número de secuencia del objeto para guardar un mensaje específico.



~~~Java
// Select the Inbox folder
imapClient.selectFolder(ImapFolderInfo.IN_BOX);
// Get the list of messages
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    // Fetch the message from inbox using its SequenceNumber from msgInfo
    MailMessage message = imapClient.fetchMessage(msgInfo.getSequenceNumber());

    // Save the message to disc now
    message.save(dataDir + msgInfo.getSequenceNumber() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~